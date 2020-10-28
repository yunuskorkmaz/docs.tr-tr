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
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="01b63-103">Şifreleme son değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="01b63-103">Cryptography breaking changes</span></span>

<span data-ttu-id="01b63-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="01b63-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="01b63-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="01b63-105">Breaking change</span></span> | <span data-ttu-id="01b63-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="01b63-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="01b63-107">TripleDES tarafından oluşturulan örnekler için varsayılan FeedbackSize değeri. oluşturma değiştirildi</span><span class="sxs-lookup"><span data-stu-id="01b63-107">Default FeedbackSize value for instances created by TripleDES.Create changed</span></span>](#default-feedbacksize-value-for-instances-created-by-tripledescreate-changed) | <span data-ttu-id="01b63-108">5.0</span><span class="sxs-lookup"><span data-stu-id="01b63-108">5.0</span></span> |
| [<span data-ttu-id="01b63-109">Şifrelenmiş soyutlamalar için varsayılan uygulamaların örneği oluşturma desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="01b63-109">Instantiating default implementations of cryptographic abstractions is not supported</span></span>](#instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported) | <span data-ttu-id="01b63-110">5.0</span><span class="sxs-lookup"><span data-stu-id="01b63-110">5.0</span></span> |
| [<span data-ttu-id="01b63-111">Linux 'ta .NET için varsayılan TLS şifre paketleri</span><span class="sxs-lookup"><span data-stu-id="01b63-111">Default TLS cipher suites for .NET on Linux</span></span>](#default-tls-cipher-suites-for-net-on-linux) | <span data-ttu-id="01b63-112">5.0</span><span class="sxs-lookup"><span data-stu-id="01b63-112">5.0</span></span> |
| [<span data-ttu-id="01b63-113">System. Security. Cryptography API 'Leri Blazor WebAssembly üzerinde desteklenmez</span><span class="sxs-lookup"><span data-stu-id="01b63-113">System.Security.Cryptography APIs not supported on Blazor WebAssembly</span></span>](#systemsecuritycryptography-apis-not-supported-on-blazor-webassembly) | <span data-ttu-id="01b63-114">5.0</span><span class="sxs-lookup"><span data-stu-id="01b63-114">5.0</span></span> |
| [<span data-ttu-id="01b63-115">System. Security. Cryptography. OID yalnızca işlev olarak init</span><span class="sxs-lookup"><span data-stu-id="01b63-115">System.Security.Cryptography.Oid is functionally init-only</span></span>](#systemsecuritycryptographyoid-is-functionally-init-only) | <span data-ttu-id="01b63-116">5.0</span><span class="sxs-lookup"><span data-stu-id="01b63-116">5.0</span></span> |
| [<span data-ttu-id="01b63-117">Linux 'ta artık desteklenmeyen GÜVENILEN SERTIFIKA sözdizimini Başlat</span><span class="sxs-lookup"><span data-stu-id="01b63-117">BEGIN TRUSTED CERTIFICATE syntax no longer supported on Linux</span></span>](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | <span data-ttu-id="01b63-118">3,0</span><span class="sxs-lookup"><span data-stu-id="01b63-118">3.0</span></span> |
| [<span data-ttu-id="01b63-119">EnvelopedCms varsayılan değer AES-256 şifrelemesi</span><span class="sxs-lookup"><span data-stu-id="01b63-119">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="01b63-120">3,0</span><span class="sxs-lookup"><span data-stu-id="01b63-120">3.0</span></span> |
| [<span data-ttu-id="01b63-121">RSAOpenSsl anahtar üretimi için en düşük boyut arttı</span><span class="sxs-lookup"><span data-stu-id="01b63-121">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="01b63-122">3,0</span><span class="sxs-lookup"><span data-stu-id="01b63-122">3.0</span></span> |
| [<span data-ttu-id="01b63-123">.NET Core 3,0 OpenSSL 1.1. x ile OpenSSL 1.0. x tercih eder</span><span class="sxs-lookup"><span data-stu-id="01b63-123">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="01b63-124">3,0</span><span class="sxs-lookup"><span data-stu-id="01b63-124">3.0</span></span> |
| [<span data-ttu-id="01b63-125">CryptoStream. Dispose, son bloğu yalnızca yazma sırasında dönüştürür</span><span class="sxs-lookup"><span data-stu-id="01b63-125">CryptoStream.Dispose transforms final block only when writing</span></span>](#cryptostreamdispose-transforms-final-block-only-when-writing) | <span data-ttu-id="01b63-126">3,0</span><span class="sxs-lookup"><span data-stu-id="01b63-126">3.0</span></span> |
| [<span data-ttu-id="01b63-127">SignedCms. ComputeSignature Boolean parametresi dikkate alındı</span><span class="sxs-lookup"><span data-stu-id="01b63-127">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="01b63-128">2.1</span><span class="sxs-lookup"><span data-stu-id="01b63-128">2.1</span></span> |

## <a name="net-50"></a><span data-ttu-id="01b63-129">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="01b63-129">.NET 5.0</span></span>

[!INCLUDE [tripledes-default-feedback-size-change](../../../includes/core-changes/cryptography/5.0/tripledes-default-feedback-size-change.md)]

***

[!INCLUDE [instantiating-default-implementations-of-cryptographic-abstractions-not-supported](../../../includes/core-changes/cryptography/5.0/instantiating-default-implementations-of-cryptographic-abstractions-not-supported.md)]

<span data-ttu-id="01b63-130">\*\*_</span><span class="sxs-lookup"><span data-stu-id="01b63-130">\*\*_</span></span>

[!INCLUDE [default-cipher-suites-for-tls-on-linux](../../../includes/core-changes/cryptography/5.0/default-cipher-suites-for-tls-on-linux.md)]

_*_

[!INCLUDE[Cryptography APIs not supported on Blazor WebAssembly](~/includes/core-changes/cryptography/5.0/cryptography-apis-not-supported-on-blazor-webassembly.md)]

_*_

[!INCLUDE [cryptography-oid-init-only](../../../includes/core-changes/cryptography/5.0/cryptography-oid-init-only.md)]

_*_

## <a name="net-core-30"></a><span data-ttu-id="01b63-131">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="01b63-131">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="01b63-132">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="01b63-132">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

<span data-ttu-id="01b63-133">_\*\*</span><span class="sxs-lookup"><span data-stu-id="01b63-133">_\*\*</span></span>
