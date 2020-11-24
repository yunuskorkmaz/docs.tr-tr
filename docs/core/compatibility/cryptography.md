---
title: Şifreleme son değişiklikleri
description: .NET Core 2.1-3.0 içindeki şifrelemeye ilişkin önemli değişiklikleri listeler.
ms.date: 04/22/2020
ms.openlocfilehash: a4801bb4d5a859e2c8c2b536ee0597cb4db2f65d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682659"
---
# <a name="cryptography-breaking-changes-for-net-core-21-30"></a><span data-ttu-id="78b6f-103">.NET Core 2.1-3.0 için şifreleme bozan değişiklikler</span><span class="sxs-lookup"><span data-stu-id="78b6f-103">Cryptography breaking changes for .NET Core 2.1-3.0</span></span>

<span data-ttu-id="78b6f-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="78b6f-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="78b6f-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="78b6f-105">Breaking change</span></span> | <span data-ttu-id="78b6f-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="78b6f-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="78b6f-107">Linux 'ta artık desteklenmeyen GÜVENILEN SERTIFIKA sözdizimini Başlat</span><span class="sxs-lookup"><span data-stu-id="78b6f-107">BEGIN TRUSTED CERTIFICATE syntax no longer supported on Linux</span></span>](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | <span data-ttu-id="78b6f-108">3,0</span><span class="sxs-lookup"><span data-stu-id="78b6f-108">3.0</span></span> |
| [<span data-ttu-id="78b6f-109">EnvelopedCms varsayılan değer AES-256 şifrelemesi</span><span class="sxs-lookup"><span data-stu-id="78b6f-109">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="78b6f-110">3,0</span><span class="sxs-lookup"><span data-stu-id="78b6f-110">3.0</span></span> |
| [<span data-ttu-id="78b6f-111">RSAOpenSsl anahtar üretimi için en düşük boyut arttı</span><span class="sxs-lookup"><span data-stu-id="78b6f-111">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="78b6f-112">3,0</span><span class="sxs-lookup"><span data-stu-id="78b6f-112">3.0</span></span> |
| [<span data-ttu-id="78b6f-113">.NET Core 3,0 OpenSSL 1.1. x ile OpenSSL 1.0. x tercih eder</span><span class="sxs-lookup"><span data-stu-id="78b6f-113">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="78b6f-114">3,0</span><span class="sxs-lookup"><span data-stu-id="78b6f-114">3.0</span></span> |
| [<span data-ttu-id="78b6f-115">CryptoStream. Dispose, son bloğu yalnızca yazma sırasında dönüştürür</span><span class="sxs-lookup"><span data-stu-id="78b6f-115">CryptoStream.Dispose transforms final block only when writing</span></span>](#cryptostreamdispose-transforms-final-block-only-when-writing) | <span data-ttu-id="78b6f-116">3,0</span><span class="sxs-lookup"><span data-stu-id="78b6f-116">3.0</span></span> |
| [<span data-ttu-id="78b6f-117">SignedCms. ComputeSignature Boolean parametresi dikkate alındı</span><span class="sxs-lookup"><span data-stu-id="78b6f-117">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="78b6f-118">2.1</span><span class="sxs-lookup"><span data-stu-id="78b6f-118">2.1</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="78b6f-119">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="78b6f-119">.NET Core 3.0</span></span>

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

***

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

<span data-ttu-id="78b6f-120">\*\*_</span><span class="sxs-lookup"><span data-stu-id="78b6f-120">\*\*_</span></span>

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

_*_

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

_*_

[!INCLUDE [CryptoStream.Dispose transforms final block only when writing](~/includes/core-changes/cryptography/3.0/cryptography-cryptostream-dispose-final-block-write.md)]

_*_

## <a name="net-core-21"></a><span data-ttu-id="78b6f-121">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="78b6f-121">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

<span data-ttu-id="78b6f-122">_\*\*</span><span class="sxs-lookup"><span data-stu-id="78b6f-122">_\*\*</span></span>
