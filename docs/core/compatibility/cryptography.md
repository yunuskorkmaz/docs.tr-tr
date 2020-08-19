---
title: Şifreleme son değişiklikleri
description: .NET Core ile ilgili şifrelemeye ilişkin önemli değişiklikleri listeler.
ms.date: 04/22/2020
ms.openlocfilehash: f7d580938fb7620728b8ff7f67412c9f5bbbb6c3
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558015"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="2db0d-103">Şifreleme son değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="2db0d-103">Cryptography breaking changes</span></span>

<span data-ttu-id="2db0d-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="2db0d-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="2db0d-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="2db0d-105">Breaking change</span></span> | <span data-ttu-id="2db0d-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="2db0d-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="2db0d-107">System. Security. Cryptography. OID yalnızca işlev olarak init</span><span class="sxs-lookup"><span data-stu-id="2db0d-107">System.Security.Cryptography.Oid is functionally init-only</span></span>](#systemsecuritycryptographyoid-is-functionally-init-only) | <span data-ttu-id="2db0d-108">5.0</span><span class="sxs-lookup"><span data-stu-id="2db0d-108">5.0</span></span> |
| [<span data-ttu-id="2db0d-109">Linux 'ta artık desteklenmeyen GÜVENILEN SERTIFIKA sözdizimini Başlat</span><span class="sxs-lookup"><span data-stu-id="2db0d-109">BEGIN TRUSTED CERTIFICATE syntax no longer supported on Linux</span></span>](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | <span data-ttu-id="2db0d-110">3,0</span><span class="sxs-lookup"><span data-stu-id="2db0d-110">3.0</span></span> |
| [<span data-ttu-id="2db0d-111">EnvelopedCms varsayılan değer AES-256 şifrelemesi</span><span class="sxs-lookup"><span data-stu-id="2db0d-111">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="2db0d-112">3,0</span><span class="sxs-lookup"><span data-stu-id="2db0d-112">3.0</span></span> |
| [<span data-ttu-id="2db0d-113">RSAOpenSsl anahtar üretimi için en düşük boyut arttı</span><span class="sxs-lookup"><span data-stu-id="2db0d-113">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="2db0d-114">3,0</span><span class="sxs-lookup"><span data-stu-id="2db0d-114">3.0</span></span> |
| [<span data-ttu-id="2db0d-115">.NET Core 3,0 OpenSSL 1.1. x ile OpenSSL 1.0. x tercih eder</span><span class="sxs-lookup"><span data-stu-id="2db0d-115">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="2db0d-116">3,0</span><span class="sxs-lookup"><span data-stu-id="2db0d-116">3.0</span></span> |
| [<span data-ttu-id="2db0d-117">SignedCms. ComputeSignature Boolean parametresi dikkate alındı</span><span class="sxs-lookup"><span data-stu-id="2db0d-117">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="2db0d-118">2.1</span><span class="sxs-lookup"><span data-stu-id="2db0d-118">2.1</span></span> |

## <a name="net-50"></a><span data-ttu-id="2db0d-119">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="2db0d-119">.NET 5.0</span></span>

[!INCLUDE [cryptography-oid-init-only](../../../includes/core-changes/cryptography/5.0/cryptography-oid-init-only.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="2db0d-120">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2db0d-120">.NET Core 3.0</span></span>

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

***

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="2db0d-121">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2db0d-121">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
