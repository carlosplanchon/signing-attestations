# OpenPGP Key Binding Attestation (Uruguay eID)

This repository publicly binds my OpenPGP (GPG) signing key to my Uruguayan eID (Cédula de Identidad) digital signature.

## What’s inside

- `openpgp/carlos_pubkey.asc` - my public OpenPGP key
- `openpgp/fingerprint.txt` - key fingerprint
- `openpgp/pubkey.sha256` - SHA-256 of the public key file (integrity check)
- `attestations/key-binding.md` - human-readable declaration
- `attestations/key-binding-firmado.pdf` - the same declaration as a PDF **digitally signed with my Uruguayan eID**

## Verify (Git/GPG)

Verify the signed tag:

```bash
git fetch --tags
git tag -v v1
```

Verify the last commit signature:

```bash
git log --show-signature -1
# or
git verify-commit HEAD
```


## Verify (OpenPGP key material)

Check integrity of the exported public key:

```bash
sha256sum -c openpgp/pubkey.sha256
```

Inspect fingerprint:

```bash
gpg --show-keys --fingerprint openpgp/carlos_pubkey.asc
```

## Verify (Uruguay eID PDF signature)

You can verify the digital signature on the PDF in two ways:

### 1) Online (firma.gub.uy)
Upload `attestations/key-binding-firmado.pdf` to the official validator at firma.gub.uy and check that the signature is valid.

### 2) Locally (Arch Linux)
```bash
sudo pacman -S poppler
pdfsig attestations/key-binding-firmado.pdf
```

Or use a trusted PDF signature validator compatible with Uruguay eID signatures.

## Versioning

* `v1`: key binding (PDF signed with Uruguay eID)
* `v2`: scope clarification note (GPG-signed)

## Notes

* If I ever rotate my OpenPGP key, a new attestation will be added and tagged (e.g. `v2`), keeping previous versions intact.

## Disclaimer

This repository is provided for transparency and technical verification purposes only.

- It does **not** constitute notarial certification (“fe pública notarial”), legal advice, or a guarantee of legal validity in any specific jurisdiction.
- A valid OpenPGP signature proves that a given Git object was signed by a corresponding private key and that the signed content has not been modified.
- The Uruguay eID–signed PDF attests to the identity binding stated in the document, but it does not replace any formal notarial/legal procedure that may be required for contracts or other legal acts.

## Descargo (en español):

Este repositorio se publica únicamente con fines de transparencia y verificación técnica.

- **No** constituye certificación notarial (“fe pública”), asesoramiento legal, ni garantiza validez jurídica para un caso o jurisdicción específica.
- La firma OpenPGP (GPG) acredita técnicamente la integridad del objeto firmado y que fue firmado por la clave correspondiente, pero **no** equivale por sí sola a una intervención notarial.
- El PDF firmado con cédula respalda la declaración de vinculación allí contenida, sin sustituir trámites o formalidades legales/notariales que puedan corresponder.
