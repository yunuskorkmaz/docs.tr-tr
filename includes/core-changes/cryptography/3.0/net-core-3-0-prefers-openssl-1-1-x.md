---
ms.openlocfilehash: 65d8ca480d41a3807473583355fe8be41e0e9701
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275095"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a><span data-ttu-id="6c7e7-101">.NET Core 3.0 OpenSSL 1.1.x openssl 1.0.x tercih</span><span class="sxs-lookup"><span data-stu-id="6c7e7-101">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>

<span data-ttu-id="6c7e7-102">Birden fazla Linux dağıtımında çalışan .NET Core for Linux, OpenSSL 1.0.x ve OpenSSL 1.1.x'i destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="6c7e7-102">.NET Core for Linux, which works across multiple Linux distributions, can support both OpenSSL 1.0.x and OpenSSL 1.1.x.</span></span>  <span data-ttu-id="6c7e7-103">.NET Core 2.1 ve .NET Core 2.2 önce 1.0.x arayın, sonra 1.1.x'e geri düşer; .NET Core 3.0 önce 1.1.x arar.</span><span class="sxs-lookup"><span data-stu-id="6c7e7-103">.NET Core 2.1 and .NET Core 2.2 look for 1.0.x first, then fall back to 1.1.x; .NET Core 3.0 looks for 1.1.x first.</span></span> <span data-ttu-id="6c7e7-104">Bu değişiklik, yeni şifreleme standartları için destek eklemek için yapıldı.</span><span class="sxs-lookup"><span data-stu-id="6c7e7-104">This change was made to add support for new cryptographic standards.</span></span>

<span data-ttu-id="6c7e7-105">Bu değişiklik, .NET Core'daki OpenSSL'ye özgü interop türleri ile platform interop yapan kitaplıkları veya uygulamaları etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="6c7e7-105">This change may impact libraries or applications that do platform interop with the OpenSSL-specific interop types in .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6c7e7-106">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="6c7e7-106">Change description</span></span>

<span data-ttu-id="6c7e7-107">.NET Core 2.2 ve önceki sürümlerde, çalışma zamanı OpenSSL 1.0.x'i 1.1.x'in üzerine yüklemeyi tercih eder.</span><span class="sxs-lookup"><span data-stu-id="6c7e7-107">In .NET Core 2.2 and earlier versions, the runtime prefers loading OpenSSL 1.0.x over 1.1.x.</span></span> <span data-ttu-id="6c7e7-108">Bu openssl ile interop için <xref:System.IntPtr> <xref:System.Runtime.InteropServices.SafeHandle> türleri ve libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 tercihe göre kullanılır anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6c7e7-108">This means that the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 by preference.</span></span>

<span data-ttu-id="6c7e7-109">.NET Core 3.0 ile başlayarak, çalışma zamanı OpenSSL 1.0.x üzerinden OpenSSL <xref:System.IntPtr> 1.1.x yüklemeyi tercih eder, bu nedenle OpenSSL ile interop <xref:System.Runtime.InteropServices.SafeHandle> türleri libcrypto.so.1.1 / libcrypto.so.11 / libcrypto.so.1.1.1.0 / crypto lib.so.so.1.1.1.1.1 tercihe göre kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6c7e7-109">Starting with .NET Core 3.0, the runtime prefers loading OpenSSL 1.1.x over OpenSSL 1.0.x, so the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.1 / libcrypto.so.11 / libcrypto.so.1.1.0 / libcrypto.so.1.1.1 by preference.</span></span> <span data-ttu-id="6c7e7-110">Sonuç olarak, OpenSSL ile doğrudan çalışan kitaplıklar ve uygulamalar,.NET Core 2.1 veya .NET Core 2.2'den yükseltme yaparken .NET Core'a maruz kalan değerlerle uyumsuz işaretçilere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="6c7e7-110">As a result, libraries and applications that interoperate with OpenSSL directly may have incompatible pointers with the .NET Core-exposed values when upgrading from .NET Core 2.1 or .NET Core 2.2.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6c7e7-111">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="6c7e7-111">Version introduced</span></span>

<span data-ttu-id="6c7e7-112">3,0</span><span class="sxs-lookup"><span data-stu-id="6c7e7-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6c7e7-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="6c7e7-113">Recommended action</span></span>

<span data-ttu-id="6c7e7-114">OpenSSL ile doğrudan işlem yapan kitaplıklar ve uygulamalar, OpenSSL'nin .NET Core çalışma zamanı ile aynı sürümünü kullandıklarından emin olmak için dikkatli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c7e7-114">Libraries and applications that do direct operations with OpenSSL need to be careful to ensure they are using the same version of OpenSSL as the .NET Core runtime.</span></span>

<span data-ttu-id="6c7e7-115">.NET Core şifreleme <xref:System.IntPtr> türlerini doğrudan OpenSSL ile kullanan <xref:System.Runtime.InteropServices.SafeHandle> tüm kitaplıklar veya uygulamalar, işaretçilerin <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> uyumlu olduğundan emin olmak için kullandıkları kitaplığın sürümünü yeni özellik ile karşılaştırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c7e7-115">All libraries or applications that use <xref:System.IntPtr> or <xref:System.Runtime.InteropServices.SafeHandle> values from the .NET Core cryptographic types directly with OpenSSL should compare the version of the library they use with the new <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property to ensure the pointers are compatible.</span></span>

#### <a name="category"></a><span data-ttu-id="6c7e7-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="6c7e7-116">Category</span></span>

<span data-ttu-id="6c7e7-117">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="6c7e7-117">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6c7e7-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6c7e7-118">Affected APIs</span></span>

- <xref:System.Security.Cryptography.SafeEvpPKeyHandle.%23ctor%2A>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
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
