---
title: Şifreleme son değişiklikleri
description: .NET Core ile ilgili şifrelemeye ilişkin önemli değişiklikleri listeler.
ms.date: 04/22/2020
ms.openlocfilehash: 66049473083d87b4c84408f35a04193a4563c2b3
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135613"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="7f508-103">Şifreleme son değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="7f508-103">Cryptography breaking changes</span></span>

<span data-ttu-id="7f508-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="7f508-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="7f508-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="7f508-105">Breaking change</span></span> | <span data-ttu-id="7f508-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7f508-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="7f508-107">Linux 'ta artık desteklenmeyen GÜVENILEN SERTIFIKA sözdizimini Başlat</span><span class="sxs-lookup"><span data-stu-id="7f508-107">BEGIN TRUSTED CERTIFICATE syntax no longer supported on Linux</span></span>](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | <span data-ttu-id="7f508-108">3.0</span><span class="sxs-lookup"><span data-stu-id="7f508-108">3.0</span></span> |
| [<span data-ttu-id="7f508-109">EnvelopedCms varsayılan değer AES-256 şifrelemesi</span><span class="sxs-lookup"><span data-stu-id="7f508-109">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="7f508-110">3.0</span><span class="sxs-lookup"><span data-stu-id="7f508-110">3.0</span></span> |
| [<span data-ttu-id="7f508-111">RSAOpenSsl anahtar üretimi için en düşük boyut arttı</span><span class="sxs-lookup"><span data-stu-id="7f508-111">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="7f508-112">3.0</span><span class="sxs-lookup"><span data-stu-id="7f508-112">3.0</span></span> |
| [<span data-ttu-id="7f508-113">.NET Core 3,0 OpenSSL 1.1. x ile OpenSSL 1.0. x tercih eder</span><span class="sxs-lookup"><span data-stu-id="7f508-113">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="7f508-114">3.0</span><span class="sxs-lookup"><span data-stu-id="7f508-114">3.0</span></span> |
| [<span data-ttu-id="7f508-115">Pkcs8PrivateKeyInfo oluşturucusunda daha iyi bağımsız değişken doğrulaması</span><span class="sxs-lookup"><span data-stu-id="7f508-115">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>](#better-argument-validation-in-the-pkcs8privatekeyinfo-constructor) | <span data-ttu-id="7f508-116">3.0</span><span class="sxs-lookup"><span data-stu-id="7f508-116">3.0</span></span> |
| [<span data-ttu-id="7f508-117">SignedCms. ComputeSignature Boolean parametresi dikkate alındı</span><span class="sxs-lookup"><span data-stu-id="7f508-117">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="7f508-118">2.1</span><span class="sxs-lookup"><span data-stu-id="7f508-118">2.1</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="7f508-119">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7f508-119">.NET Core 3.0</span></span>

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

***

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

[!INCLUDE[Better argument validation in the Pkcs8PrivateKeyInfo constructor](~/includes/core-changes/cryptography/3.0/better-argument-validation-in-pkcs8privatekeyinfo-ctor.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="7f508-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="7f508-120">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
