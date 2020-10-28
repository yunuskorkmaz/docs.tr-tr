---
title: Şifreleme son değişiklikleri
description: .NET Core ile ilgili şifrelemeye ilişkin önemli değişiklikleri listeler.
ms.date: 04/22/2020
ms.openlocfilehash: b755876624a7709cfe08b5993655e78be9f8e1f2
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888619"
---
# <a name="cryptography-breaking-changes"></a>Şifreleme son değişiklikleri

Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:

| Son değişiklik | Sunulan sürüm |
| - | :-: |
| [TripleDES tarafından oluşturulan örnekler için varsayılan FeedbackSize değeri. oluşturma değiştirildi](#default-feedbacksize-value-for-instances-created-by-tripledescreate-changed) | 5.0 |
| [Şifrelenmiş soyutlamalar için varsayılan uygulamaların örneği oluşturma desteklenmiyor](#instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported) | 5.0 |
| [Linux 'ta .NET için varsayılan TLS şifre paketleri](#default-tls-cipher-suites-for-net-on-linux) | 5.0 |
| [System. Security. Cryptography API 'Leri Blazor WebAssembly üzerinde desteklenmez](#systemsecuritycryptography-apis-not-supported-on-blazor-webassembly) | 5.0 |
| [System. Security. Cryptography. OID yalnızca işlev olarak init](#systemsecuritycryptographyoid-is-functionally-init-only) | 5.0 |
| [Linux 'ta artık desteklenmeyen GÜVENILEN SERTIFIKA sözdizimini Başlat](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | 3,0 |
| [EnvelopedCms varsayılan değer AES-256 şifrelemesi](#envelopedcms-defaults-to-aes-256-encryption) | 3,0 |
| [RSAOpenSsl anahtar üretimi için en düşük boyut arttı](#minimum-size-for-rsaopenssl-key-generation-has-increased) | 3,0 |
| [.NET Core 3,0 OpenSSL 1.1. x ile OpenSSL 1.0. x tercih eder](#net-core-30-prefers-openssl-11x-to-openssl-10x) | 3,0 |
| [CryptoStream. Dispose, son bloğu yalnızca yazma sırasında dönüştürür](#cryptostreamdispose-transforms-final-block-only-when-writing) | 3,0 |
| [SignedCms. ComputeSignature Boolean parametresi dikkate alındı](#boolean-parameter-of-signedcmscomputesignature-is-respected) | 2.1 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [tripledes-default-feedback-size-change](../../../includes/core-changes/cryptography/5.0/tripledes-default-feedback-size-change.md)]

***

[!INCLUDE [instantiating-default-implementations-of-cryptographic-abstractions-not-supported](../../../includes/core-changes/cryptography/5.0/instantiating-default-implementations-of-cryptographic-abstractions-not-supported.md)]

**_

[!INCLUDE [default-cipher-suites-for-tls-on-linux](../../../includes/core-changes/cryptography/5.0/default-cipher-suites-for-tls-on-linux.md)]

_*_

[!INCLUDE[Cryptography APIs not supported on Blazor WebAssembly](~/includes/core-changes/cryptography/5.0/cryptography-apis-not-supported-on-blazor-webassembly.md)]

_*_

[!INCLUDE [cryptography-oid-init-only](../../../includes/core-changes/cryptography/5.0/cryptography-oid-init-only.md)]

_*_

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

_*_

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

_*_

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

_*_

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

_*_

[!INCLUDE [CryptoStream.Dispose transforms final block only when writing](~/includes/core-changes/cryptography/3.0/cryptography-cryptostream-dispose-final-block-write.md)]

_*_

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

_**
