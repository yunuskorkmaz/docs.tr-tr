---
ms.openlocfilehash: 6a5cd260a2820e2a81142f6d55e32e91173ca503
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147457"
---
### <a name="openssl-versions-on-macos"></a><span data-ttu-id="2246c-101">macOS'ta OpenSSL sürümleri</span><span class="sxs-lookup"><span data-stu-id="2246c-101">OpenSSL versions on macOS</span></span>

<span data-ttu-id="2246c-102">.NET Core 3.0 ve daha sonra macOS'taki çalışma süreleri artık OpenSSL 1.1.x sürümlerini <xref:System.Security.Cryptography.AesCcm> <xref:System.Security.Cryptography.AesGcm>OpenSSL <xref:System.Security.Cryptography.RSAOpenSsl>1.0.x sürümleriiçin <xref:System.Security.Cryptography.SafeEvpPKeyHandle> <xref:System.Security.Cryptography.DSAOpenSsl> <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl>tercih ediyor.</span><span class="sxs-lookup"><span data-stu-id="2246c-102">The .NET Core 3.0 and later runtimes on macOS now prefer OpenSSL 1.1.x versions to OpenSSL 1.0.x versions for the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, and <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

<span data-ttu-id="2246c-103">.NET Core 2.1 çalışma süresi artık OpenSSL 1.1.x sürümlerini destekler, ancak yine de OpenSSL 1.0.x sürümlerini tercih eder.</span><span class="sxs-lookup"><span data-stu-id="2246c-103">The .NET Core 2.1 runtime now supports OpenSSL 1.1.x versions, but still prefers OpenSSL 1.0.x versions.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2246c-104">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="2246c-104">Change description</span></span>

<span data-ttu-id="2246c-105">Daha önce,.NET Core çalışma zamanı OpenSSL ile etkileşime geçen türler için macOS'ta OpenSSL 1.0.x sürümlerini kullansA.</span><span class="sxs-lookup"><span data-stu-id="2246c-105">Previously, the .NET Core runtime used OpenSSL 1.0.x versions on macOS for types that interact with OpenSSL.</span></span> <span data-ttu-id="2246c-106">En son OpenSSL 1.0.x sürümü OpenSSL 1.0.2, şimdi destek dışında.</span><span class="sxs-lookup"><span data-stu-id="2246c-106">The most recent OpenSSL 1.0.x version, OpenSSL 1.0.2, is now out of support.</span></span> <span data-ttu-id="2246c-107">OpenSSL'nin desteklenen sürümlerinde OpenSSL kullanan türleri tutmak için .NET Core 3.0 ve daha sonraki çalışma süreleri artık macOS'ta OpenSSL'nin yeni sürümlerini kullansın.</span><span class="sxs-lookup"><span data-stu-id="2246c-107">To keep types that use OpenSSL on supported versions of OpenSSL, the .NET Core 3.0 and later runtimes now use newer versions of OpenSSL on macOS.</span></span>

<span data-ttu-id="2246c-108">Bu değişiklikle, macOS'taki .NET Core çalışma sürelerini içeren davranış aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="2246c-108">With this change, the behavior for the .NET Core runtimes on macOS is as follows:</span></span>

- <span data-ttu-id="2246c-109">.NET Core 3.0 ve sonraki sürüm çalışma süreleri OpenSSL 1.1.x'i kullanır, eğer varsa ve yalnızca 1.1.x sürümü yoksa OpenSSL 1.0.x'e geri döner.</span><span class="sxs-lookup"><span data-stu-id="2246c-109">The .NET Core 3.0 and later version runtimes use OpenSSL 1.1.x, if available, and fall back to OpenSSL 1.0.x only if there's no 1.1.x version available.</span></span>

  <span data-ttu-id="2246c-110">OpenSSL interop türlerini özel P/Invokes ile kullanan arayanlar <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> için, açıklamalartaki kılavuzu izleyin.</span><span class="sxs-lookup"><span data-stu-id="2246c-110">For callers that use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span> <span data-ttu-id="2246c-111"><xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> Değeri kontrol etmezseniz uygulamanız çökebilir.</span><span class="sxs-lookup"><span data-stu-id="2246c-111">Your app may crash if you don't check the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> value.</span></span>

- <span data-ttu-id="2246c-112">.NET Core 2.1 çalışma süresi varsa OpenSSL 1.0.x kullanır ve varsa OpenSSL 1.1.x sürümü yoksa geri düşer.</span><span class="sxs-lookup"><span data-stu-id="2246c-112">The .NET Core 2.1 runtime uses OpenSSL 1.0.x, if available, and falls back to OpenSSL 1.1.x if there's no 1.0.x version available.</span></span>

  <span data-ttu-id="2246c-113"><xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> Özellik .NET Core 2.1'de bulunmadığından, 2.1 çalışma süresi OpenSSL'in önceki sürümünü tercih eder, bu nedenle OpenSSL sürümü çalışma zamanında güvenilir bir şekilde belirlenemez.</span><span class="sxs-lookup"><span data-stu-id="2246c-113">The 2.1 runtime prefers the earlier version of OpenSSL because the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property does not exist in .NET Core 2.1, so the OpenSSL version cannot be reliably determined at run time.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2246c-114">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="2246c-114">Version introduced</span></span>

- <span data-ttu-id="2246c-115">.NET Çekirdek 2.1.16</span><span class="sxs-lookup"><span data-stu-id="2246c-115">.NET Core 2.1.16</span></span>
- <span data-ttu-id="2246c-116">.NET Çekirdek 3.0.3</span><span class="sxs-lookup"><span data-stu-id="2246c-116">.NET Core 3.0.3</span></span>
- <span data-ttu-id="2246c-117">.NET Çekirdek 3.1.2</span><span class="sxs-lookup"><span data-stu-id="2246c-117">.NET Core 3.1.2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2246c-118">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="2246c-118">Recommended action</span></span>

- <span data-ttu-id="2246c-119">Artık gerekli değilse OpenSSL sürüm 1.0.2'yi kaldırın.</span><span class="sxs-lookup"><span data-stu-id="2246c-119">Uninstall OpenSSL version 1.0.2 if it's no longer needed.</span></span>

- <span data-ttu-id="2246c-120">OpenSSL 1.1.x'i <xref:System.Security.Cryptography.AesCcm>yüklerseniz , <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl> <xref:System.Security.Cryptography.AesGcm> <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.SafeEvpPKeyHandle> , , veya türleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="2246c-120">Install OpenSSL 1.1.x if you use the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, or <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

- <span data-ttu-id="2246c-121">OpenSSL interop türlerini özel P/Invokes ile kullanıyorsanız, <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> açıklamalartaki kılavuzu izleyin.</span><span class="sxs-lookup"><span data-stu-id="2246c-121">If you use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span>

#### <a name="category"></a><span data-ttu-id="2246c-122">Kategori</span><span class="sxs-lookup"><span data-stu-id="2246c-122">Category</span></span>

<span data-ttu-id="2246c-123">CoreFx</span><span class="sxs-lookup"><span data-stu-id="2246c-123">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2246c-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="2246c-124">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->
