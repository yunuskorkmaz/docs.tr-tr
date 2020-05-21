---
ms.openlocfilehash: a4476fbff572c004632153e5a98812c241efca57
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721069"
---
### <a name="openssl-versions-on-macos"></a><span data-ttu-id="c72d6-101">MacOS üzerinde OpenSSL sürümleri</span><span class="sxs-lookup"><span data-stu-id="c72d6-101">OpenSSL versions on macOS</span></span>

<span data-ttu-id="c72d6-102">MacOS 'ta .NET Core 3,0 ve üzeri çalışma zamanları artık OpenSSL 1.1. x sürümlerini,,,,, <xref:System.Security.Cryptography.AesCcm> <xref:System.Security.Cryptography.AesGcm> <xref:System.Security.Cryptography.DSAOpenSsl> <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl> ve <xref:System.Security.Cryptography.SafeEvpPKeyHandle> türleri için OpenSSL 1.0. x sürümlerine tercih ediyor.</span><span class="sxs-lookup"><span data-stu-id="c72d6-102">The .NET Core 3.0 and later runtimes on macOS now prefer OpenSSL 1.1.x versions to OpenSSL 1.0.x versions for the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, and <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

<span data-ttu-id="c72d6-103">.NET Core 2,1 çalışma zamanı artık OpenSSL 1.1. x sürümlerini destekliyor, ancak yine de OpenSSL 1.0. x sürümlerini tercih ediyor.</span><span class="sxs-lookup"><span data-stu-id="c72d6-103">The .NET Core 2.1 runtime now supports OpenSSL 1.1.x versions, but still prefers OpenSSL 1.0.x versions.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c72d6-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="c72d6-104">Change description</span></span>

<span data-ttu-id="c72d6-105">Daha önce .NET Core çalışma zamanı, OpenSSL ile etkileşime geçen türler için macOS üzerinde OpenSSL 1.0. x sürümlerini kullandı.</span><span class="sxs-lookup"><span data-stu-id="c72d6-105">Previously, the .NET Core runtime used OpenSSL 1.0.x versions on macOS for types that interact with OpenSSL.</span></span> <span data-ttu-id="c72d6-106">En son OpenSSL 1.0. x sürümü olan OpenSSL 1.0.2 artık destek dışındadır.</span><span class="sxs-lookup"><span data-stu-id="c72d6-106">The most recent OpenSSL 1.0.x version, OpenSSL 1.0.2, is now out of support.</span></span> <span data-ttu-id="c72d6-107">OpenSSL 'nin desteklenen sürümlerinde OpenSSL kullanan türleri tutmak için, .NET Core 3,0 ve üzeri çalışma zamanları artık macOS 'ta OpenSSL 'nin daha yeni sürümlerini kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="c72d6-107">To keep types that use OpenSSL on supported versions of OpenSSL, the .NET Core 3.0 and later runtimes now use newer versions of OpenSSL on macOS.</span></span>

<span data-ttu-id="c72d6-108">Bu değişiklik ile, macOS 'ta .NET Core çalışma zamanları için davranış aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="c72d6-108">With this change, the behavior for the .NET Core runtimes on macOS is as follows:</span></span>

- <span data-ttu-id="c72d6-109">.NET Core 3,0 ve sonraki sürüm çalışma zamanları, varsa OpenSSL 1.1. x kullanır ve yalnızca 1.1. x sürümü yoksa OpenSSL 1.0. x ' e geri döner.</span><span class="sxs-lookup"><span data-stu-id="c72d6-109">The .NET Core 3.0 and later version runtimes use OpenSSL 1.1.x, if available, and fall back to OpenSSL 1.0.x only if there's no 1.1.x version available.</span></span>

  <span data-ttu-id="c72d6-110">Özel P/Invoke ile OpenSSL birlikte çalışma türlerini kullanan çağıranlar için, açıklamalar bölümündeki yönergeleri izleyin <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c72d6-110">For callers that use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span> <span data-ttu-id="c72d6-111">Değeri denetmezseniz uygulamanız kilitlenebilir <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> .</span><span class="sxs-lookup"><span data-stu-id="c72d6-111">Your app may crash if you don't check the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> value.</span></span>

- <span data-ttu-id="c72d6-112">.NET Core 2,1 çalışma zamanı, varsa OpenSSL 1.0. x kullanır ve kullanılabilir 1.0. x sürümü yoksa OpenSSL 1.1. x ' e geri döner.</span><span class="sxs-lookup"><span data-stu-id="c72d6-112">The .NET Core 2.1 runtime uses OpenSSL 1.0.x, if available, and falls back to OpenSSL 1.1.x if there's no 1.0.x version available.</span></span>

  <span data-ttu-id="c72d6-113">2,1 çalışma zamanı, OpenSSL 'nin önceki sürümünü tercih eder çünkü <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> özellik .NET Core 2,1 ' de mevcut olmadığından, OpenSSL sürümü çalışma zamanında güvenilir bir şekilde belirlenemez.</span><span class="sxs-lookup"><span data-stu-id="c72d6-113">The 2.1 runtime prefers the earlier version of OpenSSL because the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property does not exist in .NET Core 2.1, so the OpenSSL version cannot be reliably determined at run time.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c72d6-114">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="c72d6-114">Version introduced</span></span>

- <span data-ttu-id="c72d6-115">.NET Core 2.1.16</span><span class="sxs-lookup"><span data-stu-id="c72d6-115">.NET Core 2.1.16</span></span>
- <span data-ttu-id="c72d6-116">.NET Core 3.0.3</span><span class="sxs-lookup"><span data-stu-id="c72d6-116">.NET Core 3.0.3</span></span>
- <span data-ttu-id="c72d6-117">.NET Core 3.1.2</span><span class="sxs-lookup"><span data-stu-id="c72d6-117">.NET Core 3.1.2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c72d6-118">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c72d6-118">Recommended action</span></span>

- <span data-ttu-id="c72d6-119">Artık gerekmiyorsa OpenSSL sürüm 1.0.2 'yi kaldırın.</span><span class="sxs-lookup"><span data-stu-id="c72d6-119">Uninstall OpenSSL version 1.0.2 if it's no longer needed.</span></span>

- <span data-ttu-id="c72d6-120">,,,,, <xref:System.Security.Cryptography.AesCcm> <xref:System.Security.Cryptography.AesGcm> <xref:System.Security.Cryptography.DSAOpenSsl> <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl> Veya <xref:System.Security.Cryptography.SafeEvpPKeyHandle> türlerini kullanıyorsanız OpenSSL 1.1. x ' i yükler.</span><span class="sxs-lookup"><span data-stu-id="c72d6-120">Install OpenSSL 1.1.x if you use the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, or <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

- <span data-ttu-id="c72d6-121">OpenSSL birlikte çalışma türlerini özel P/Invoke ile birlikte kullanıyorsanız, açıklamalar bölümündeki yönergeleri izleyin <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c72d6-121">If you use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span>

#### <a name="category"></a><span data-ttu-id="c72d6-122">Kategori</span><span class="sxs-lookup"><span data-stu-id="c72d6-122">Category</span></span>

<span data-ttu-id="c72d6-123">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="c72d6-123">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c72d6-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c72d6-124">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->
