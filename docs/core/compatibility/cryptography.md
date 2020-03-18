---
title: Şifreleme kırma değişiklikleri
description: .NET Core'da şifrelemeyle ilgili kırılma değişikliklerini listeler.
ms.date: 02/10/2020
ms.openlocfilehash: c25eefa8e3ee01ed7a1df4ec4aa9225f2c347a4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449237"
---
# <a name="cryptography-breaking-changes"></a>Şifreleme kırma değişiklikleri

Aşağıdaki kesme değişiklikleri bu sayfada belgelenmiştir:

| Son dakika değişikliği | Sürüm tanıtıldı |
| - | :-: |
| [EnvelopedCms varsayılan olarak AES-256 şifrelemesi için](#envelopedcms-defaults-to-aes-256-encryption) | 3,0 |
| [RSAOpenSsl anahtar üretimi için minimum boyut arttı](#minimum-size-for-rsaopenssl-key-generation-has-increased) | 3,0 |
| [.NET Core 3.0 OpenSSL 1.1.x openssl 1.0.x tercih](#net-core-30-prefers-openssl-11x-to-openssl-10x) | 3,0 |
| [Pkcs8PrivateKeyInfo oluşturucu daha iyi argüman doğrulama](#better-argument-validation-in-the-pkcs8privatekeyinfo-constructor) | 3,0 |
| [İmzaCms.ComputeSignature boolean parametre saygı duyulur](#boolean-parameter-of-signedcmscomputesignature-is-respected) | 2.1 |

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

[!INCLUDE[Better argument validation in the Pkcs8PrivateKeyInfo constructor](~/includes/core-changes/cryptography/3.0/better-argument-validation-in-pkcs8privatekeyinfo-ctor.md)]

***

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
