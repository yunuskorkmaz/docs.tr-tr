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
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="c523a-103">Şifreleme kırma değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="c523a-103">Cryptography breaking changes</span></span>

<span data-ttu-id="c523a-104">Aşağıdaki kesme değişiklikleri bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="c523a-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="c523a-105">Son dakika değişikliği</span><span class="sxs-lookup"><span data-stu-id="c523a-105">Breaking change</span></span> | <span data-ttu-id="c523a-106">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="c523a-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="c523a-107">EnvelopedCms varsayılan olarak AES-256 şifrelemesi için</span><span class="sxs-lookup"><span data-stu-id="c523a-107">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="c523a-108">3,0</span><span class="sxs-lookup"><span data-stu-id="c523a-108">3.0</span></span> |
| [<span data-ttu-id="c523a-109">RSAOpenSsl anahtar üretimi için minimum boyut arttı</span><span class="sxs-lookup"><span data-stu-id="c523a-109">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="c523a-110">3,0</span><span class="sxs-lookup"><span data-stu-id="c523a-110">3.0</span></span> |
| [<span data-ttu-id="c523a-111">.NET Core 3.0 OpenSSL 1.1.x openssl 1.0.x tercih</span><span class="sxs-lookup"><span data-stu-id="c523a-111">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="c523a-112">3,0</span><span class="sxs-lookup"><span data-stu-id="c523a-112">3.0</span></span> |
| [<span data-ttu-id="c523a-113">Pkcs8PrivateKeyInfo oluşturucu daha iyi argüman doğrulama</span><span class="sxs-lookup"><span data-stu-id="c523a-113">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>](#better-argument-validation-in-the-pkcs8privatekeyinfo-constructor) | <span data-ttu-id="c523a-114">3,0</span><span class="sxs-lookup"><span data-stu-id="c523a-114">3.0</span></span> |
| [<span data-ttu-id="c523a-115">İmzaCms.ComputeSignature boolean parametre saygı duyulur</span><span class="sxs-lookup"><span data-stu-id="c523a-115">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="c523a-116">2.1</span><span class="sxs-lookup"><span data-stu-id="c523a-116">2.1</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="c523a-117">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c523a-117">.NET Core 3.0</span></span>

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

[!INCLUDE[Better argument validation in the Pkcs8PrivateKeyInfo constructor](~/includes/core-changes/cryptography/3.0/better-argument-validation-in-pkcs8privatekeyinfo-ctor.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="c523a-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c523a-118">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
