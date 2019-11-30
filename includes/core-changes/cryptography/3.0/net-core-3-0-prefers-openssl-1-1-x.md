---
ms.openlocfilehash: b49b2f88b130bb952b77964d5bf38374dc606385
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567966"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a><span data-ttu-id="2ea5c-101">.NET Core 3,0 OpenSSL 1.1. x ile OpenSSL 1.0. x tercih eder</span><span class="sxs-lookup"><span data-stu-id="2ea5c-101">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>

<span data-ttu-id="2ea5c-102">Birden çok Linux dağıtımı arasında çalışarak Linux için .NET Core, hem OpenSSL 1.0. x hem de OpenSSL 1.1. x ' i destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="2ea5c-102">.NET Core for Linux, which works across multiple Linux distributions, can support both OpenSSL 1.0.x and OpenSSL 1.1.x.</span></span>  <span data-ttu-id="2ea5c-103">.NET Core 2,1 ve .NET Core 2,2 önce 1.0. x için arama yapın ve ardından 1.1. x ' e geri dönün ve .NET Core 3,0, önce 1.1. x için arama yapar.</span><span class="sxs-lookup"><span data-stu-id="2ea5c-103">.NET Core 2.1 and .NET Core 2.2 look for 1.0.x first, then fall back to 1.1.x; .NET Core 3.0 looks for 1.1.x first.</span></span> <span data-ttu-id="2ea5c-104">Yeni şifreleme standartları desteği eklemek için bu değişiklik yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="2ea5c-104">This change was made to add support for new cryptographic standards.</span></span>

<span data-ttu-id="2ea5c-105">Bu değişiklik, .NET Core 'da OpenSSL 'e özgü birlikte çalışma türleriyle platform birlikte çalışabilirliğine yönelik kitaplıkları veya uygulamaları etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="2ea5c-105">This change may impact libraries or applications that do platform interop with the OpenSSL-specific interop types in .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2ea5c-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="2ea5c-106">Change description</span></span>

<span data-ttu-id="2ea5c-107">.NET Core 2,2 ve önceki sürümlerinde, çalışma zamanı OpenSSL 1.0. x sürümünü 1.1. x üzerinden yüklemeyi tercih eder.</span><span class="sxs-lookup"><span data-stu-id="2ea5c-107">In .NET Core 2.2 and earlier versions, the runtime prefers loading OpenSSL 1.0.x over 1.1.x.</span></span> <span data-ttu-id="2ea5c-108">Bu, OpenSSL ile birlikte çalışabilirlik için <xref:System.IntPtr> ve <xref:System.Runtime.InteropServices.SafeHandle> türlerinin libşifre ile birlikte kullanıldığı anlamına gelir. bu nedenle. 1.0.0/libşifre. so. 1.0/libşifre. so. 10 tercihe göre.</span><span class="sxs-lookup"><span data-stu-id="2ea5c-108">This means that the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 by preference.</span></span>

<span data-ttu-id="2ea5c-109">.NET Core 3,0 ile başlayarak, çalışma zamanı OpenSSL 1.0. x üzerinden OpenSSL 1.1. x ' i yüklemeyi tercih eder, bu nedenle OpenSSL ile birlikte çalışma için <xref:System.IntPtr> ve <xref:System.Runtime.InteropServices.SafeHandle> türleri libşifre ile birlikte kullanılır. bu nedenle. 1.1/libşifre. so. 11/libşifre. so. 1.1.0/libşifre. bu so. 1.1.1 tercihe göre.</span><span class="sxs-lookup"><span data-stu-id="2ea5c-109">Starting with .NET Core 3.0, the runtime prefers loading OpenSSL 1.1.x over OpenSSL 1.0.x, so the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.1 / libcrypto.so.11 / libcrypto.so.1.1.0 / libcrypto.so.1.1.1 by preference.</span></span> <span data-ttu-id="2ea5c-110">Sonuç olarak, OpenSSL ile birlikte çalışan kitaplıklar ve uygulamalar, .NET Core 2,1 veya .NET Core 2,2 ' den yükseltirken .NET Core tarafından sunulan değerlerle uyumsuz işaretçilere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="2ea5c-110">As a result, libraries and applications that interoperate with OpenSSL directly may have incompatible pointers with the .NET Core-exposed values when upgrading from .NET Core 2.1 or .NET Core 2.2.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2ea5c-111">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="2ea5c-111">Version introduced</span></span>

<span data-ttu-id="2ea5c-112">3.0</span><span class="sxs-lookup"><span data-stu-id="2ea5c-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2ea5c-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="2ea5c-113">Recommended action</span></span>

<span data-ttu-id="2ea5c-114">OpenSSL ile doğrudan işlem yapan kitaplıklar ve uygulamaların, .NET Core çalışma zamanı ile aynı OpenSSL sürümünü kullandığından emin olmak için dikkatli olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2ea5c-114">Libraries and applications that do direct operations with OpenSSL need to be careful to ensure they are using the same version of OpenSSL as the .NET Core runtime.</span></span>

<span data-ttu-id="2ea5c-115">.NET Core şifreleme türlerinden doğrudan OpenSSL ile <xref:System.IntPtr> veya <xref:System.Runtime.InteropServices.SafeHandle> değerlerini kullanan tüm kitaplıklar veya uygulamalar, işaretçilerin uyumlu olduğundan emin olmak için yeni <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> özelliğiyle kullandıkları kitaplığın sürümünü karşılaştırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2ea5c-115">All libraries or applications that use <xref:System.IntPtr> or <xref:System.Runtime.InteropServices.SafeHandle> values from the .NET Core cryptographic types directly with OpenSSL should compare the version of the library they use with the new <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property to ensure the pointers are compatible.</span></span>

#### <a name="category"></a><span data-ttu-id="2ea5c-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="2ea5c-116">Category</span></span>

<span data-ttu-id="2ea5c-117">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="2ea5c-117">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2ea5c-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="2ea5c-118">Affected APIs</span></span>

- <xref:System.Security.Cryptography.SafeEvpPKeyHandle.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Handle?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Security.Cryptography.SafeEvpPKeyHandle.#ctor`
- `M:System.Security.Cryptography.RSAOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.RSAOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.DSAOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.DSAOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.ECDsaOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.ECDsaOpenSsl.#ctor(System.Security.CryptographySafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle`
- `P:System.Security.Cryptography.X509Certificates.X509Certificate.Handle`

-->
