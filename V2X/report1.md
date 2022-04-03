# V2X standards research report
This report is only a draft where I note down my discovery. It is by no mean a complete academic report.

## Difference in Secured protocol data units (SPDUs)
SPDUs are defined in subclause 6.3 in *IEEE std 1609.2* and subclause 6.4 in *YD/T 3957*


### HashAlgorithm

HashAlgorithm defined in *YD/T 3957* :
```
HashAlgorithm ::= ENUMERATED {
  sha256,
  ...,
  sha384,
  sm3
}
```
Compare to IEEE other Hash algorithms are added. In which SM3 is the hash algorithm defined in *GM/T 0004-2012*.

In IEEE it is marked clearly that only sha256 is used in the standard.
>The only hash algorithm approved for use in this standard is SHA-256 as specified in the Federal
Information Processing Standard (FIPS) 180-4. In this standard, the phrase “the SHA-256 hash of [an octet
string]” is used to mean “the hash of [that octet string] obtained using SHA-256 as specified in FIPS
180-4”.

### HashedData
```
HashedData::= CHOICE {
  sha256HashedData    OCTET STRING (SIZE(32)),
  ...,
  sha384HashedData    OCTET STRING (SIZE(48)),
  sm3HashedData       OCTET STRING (SIZE(32))
  }
```
Again, multiple hash algorithms are supported. Note that SM3 digest has the same length as SHA256.

### HeaderInfo
```
HeaderInfo ::= SEQUENCE{
  psid                  Psid
  generationTime        Time64 OPTIONAL,
  expiryTime Time64     OPTIONAL,
  generationLocation    ThreeDLocation OPTIONAL,
  p2pcdLearningRequest  HashedId3 OPTIONAL,
  missingCrlIdentifier  MissingCrlIdentifier OPTIONAL,
  encryptionKey         EncryptionKey OPTIONAL,
  ...
```
**psid** is called **aid** in *YD/T 3957*. It is defined as follow.
```
Aid ::= INTEGER (0..MAX)
```
And it is encoded as decimal number.

__Three more data field is added in *YD/T 3957*__
```
inlineP2pcdRequest    SequenceOfHashedId3 OPTIONAL,
requestedCertificate  Certificate OPTIONAL,
pduFunctionalType     PduFunctionalType OPTIONAL
```

- `inlineP2pcdRequest`, if present, is used to request an unknown certificate. This field only exist when `p2pcdLearningRequest` is not present.

- `requestedCertificate`, if present, is used to provide certificate according to P2PCD mechanism.

- `—pduFunctionalType`, if present, indicate that SPDU will be used by processes outside the application process. This is [defined bellow](#pdufunctionaltype)

### SymmetricEncryptionKey
It is defined as follow in *YD/T 3957*
```
SymmetricEncryptionKey ::= CHOICE {
  aes128Ccm     OCTET STRING(SIZE(16)),
  ...,
  sm4Ccm        OCTET STRING(SIZE(16))
}
```
In addition to aes128 specified in *IEEE std 1609.2*, SM4 in CCM mode is also supported.

### SymmAlgorithm
```
SymmAlgorithm ::= ENUMERATED {
  aes128Ccm,
  ...,
  sm4Ccm
}
```
SM4 is added.

### BasePublicEncryptionKey
```
BasePublicEncryptionKey ::= CHOICE {
  eciesNistP256           EccP256CurvePoint,
  eciesBrainpoolP256r1    EccP256CurvePoint,
  ...,
  ecencSm2                EccP256CurvePoint
}
```
Sm2 is also used here. Which is another elliptic curve cryptography algorithm.

### PduFunctionalType
```
PduFunctionalType ::= INTEGER (0..255)
tlsHandshake          PduFunctionalType ::= 1
iso21177ExtendedAuth  PduFunctionalType ::= 2
```
This data structure identifies the functional entity intended to use the SPDU. For SPDUs that contain a PduFunctionalType, it shall conform to the the security attribute corresponding to the PduFunctionalType value, not the applied SPDU security attribute of the AID. The data structure contains :

- `tlsHandshake` indicates that the signed SPDU cannot be used directly as an application PDU, but is used to provide information about the holder's access to the Transport Layer Security (TLS) handshake process, which is used to protect communication with the application process;

- `iso21177ExtendedAuth` indicates that signed SPDU cannot be used directly as an application PDU, but is used to provide additional information about holder's access to the ISO 21177 security subsystem.


### SingerIdentifier
```
SignerIdentifier ::= CHOICE {
  digest          HashedId8,
  certificate     SequenceOfCertificate,
  self            NULL,
  ...,
  x509            OCTET STRING
}
```
x509 certificate is added here in addition to those specified in *IEEE std 1609.2* (The first three here). But no explanation is given in *YD/T 3957*


### Signature
