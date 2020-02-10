---
title: Şifreleme son değişiklikleri
description: .NET Core 'da şifreleme ile ilgili son değişiklikleri listeler.
ms.date: 09/20/2019
ms.openlocfilehash: fcef4b65245a5dd9219cbdbb548ca575a823a949
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093038"
---
# <a name="cryptography-breaking-changes"></a>Şifreleme son değişiklikleri

Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:

- [EnvelopedCms varsayılan değer AES-256 şifrelemesi](#envelopedcms-defaults-to-aes-256-encryption)
- [RSAOpenSsl anahtar üretimi için en düşük boyut arttı](#minimum-size-for-rsaopenssl-key-generation-has-increased)
- [.NET Core 3,0 OpenSSL 1.1. x ile OpenSSL 1.0. x tercih eder](#net-core-30-prefers-openssl-11x-to-openssl-10x)
- [Pkcs8PrivateKeyInfo oluşturucusunda daha iyi bağımsız değişken doğrulaması](#better-argument-validation-in-the-pkcs8privatekeyinfo-constructor)

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

## <a name="net-core-30-preview-9"></a>.NET Core 3,0 Preview 9

[!INCLUDE[Better argument validation in the Pkcs8PrivateKeyInfo constructor](~/includes/core-changes/cryptography/3.0/better-argument-validation-in-pkcs8privatekeyinfo-ctor.md)]

***
