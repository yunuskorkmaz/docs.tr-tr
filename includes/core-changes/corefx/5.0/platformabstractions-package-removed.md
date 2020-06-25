---
ms.openlocfilehash: d85fb8df7afdc5f4c3faecebcd24d11677798bc9
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365627"
---
### <a name="microsoftdotnetplatformabstractions-package-removed"></a><span data-ttu-id="b9ad7-101">Microsoft. DotNet. PlatformAbstractions paketi kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="b9ad7-101">Microsoft.DotNet.PlatformAbstractions package removed</span></span>

<span data-ttu-id="b9ad7-102">[Microsoft. DotNet. PlatformAbstractions NuGet paketinin](https://www.nuget.org/packages/Microsoft.DotNet.PlatformAbstractions/) yeni sürümleri üretilmeyecek.</span><span class="sxs-lookup"><span data-stu-id="b9ad7-102">No new versions of the [Microsoft.DotNet.PlatformAbstractions NuGet package](https://www.nuget.org/packages/Microsoft.DotNet.PlatformAbstractions/) will be produced.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b9ad7-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="b9ad7-103">Change description</span></span>

<span data-ttu-id="b9ad7-104">Daha önce, kitaplığın yeni sürümleri <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> .NET Core 'un yeni sürümleriyle birlikte üretildi.</span><span class="sxs-lookup"><span data-stu-id="b9ad7-104">Previously, new versions of the <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> library were produced alongside new versions of .NET Core.</span></span> <span data-ttu-id="b9ad7-105">İleri giderek kitaplığa yeni bir işlev eklenmez ve hiçbir yeni ana sürüm yayınlanmayacak.</span><span class="sxs-lookup"><span data-stu-id="b9ad7-105">Going forward, no new functionality will be added to the library, and no new major versions will be released.</span></span> <span data-ttu-id="b9ad7-106">Ancak, kitaplığın var olan sürümleri çalışmaya ve hizmet verilmeye devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="b9ad7-106">However, existing versions of the library will continue to work and be serviced.</span></span>

<span data-ttu-id="b9ad7-107"><xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName>Kitaplık, System. Namespaces içinde zaten belirlenmiş olan API 'lerle örtüşüyor \* .</span><span class="sxs-lookup"><span data-stu-id="b9ad7-107">The <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> library overlaps with APIs that are already established in the System.\* namespaces.</span></span> <span data-ttu-id="b9ad7-108">Ayrıca, bazı <xref:Microsoft.DotNet.PlatformAbstractions> API 'ler, sistemin geri kalanı ile aynı düzeyde scrutine ve uzun süreli desteklenebilirliği ile tasarlanmadı. \* GetVersionEx.</span><span class="sxs-lookup"><span data-stu-id="b9ad7-108">Also, some <xref:Microsoft.DotNet.PlatformAbstractions> APIs weren't designed with the same level of scrutiny and long-term supportability as the rest of the System.\* APIs.</span></span> <span data-ttu-id="b9ad7-109">Örneğin, <xref:Microsoft.DotNet.PlatformAbstractions> `Platform` geçerli işletim sistemi platformunu anlatmak için sabit listesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b9ad7-109">For example, <xref:Microsoft.DotNet.PlatformAbstractions> uses the `Platform` enumeration to describe the current operating system platform.</span></span> <span data-ttu-id="b9ad7-110">Bu numaralandırma tasarımı, <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> API tasarlandıkça, yeni platformlar ve gelecek esnekliğe izin vermek için açıkça reddedildi.</span><span class="sxs-lookup"><span data-stu-id="b9ad7-110">This enumeration design was explicitly rejected when the <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> API was designed, to allow for new platforms and future flexibility.</span></span>

<span data-ttu-id="b9ad7-111">Kitaplık tarafından etkinleştirilen senaryolar <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> artık bu olmadan mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b9ad7-111">The scenarios enabled by the <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> library are now possible without it.</span></span> <span data-ttu-id="b9ad7-112">Mevcut sürümler, .NET 5,0 ve üzeri sürümlerde bile çalışmaya devam eder ve önceki .NET Core sürümleriyle birlikte hizmet alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="b9ad7-112">Existing versions will continue to work, even in .NET 5.0 and later, and will be serviced along with previous versions of .NET Core.</span></span> <span data-ttu-id="b9ad7-113">Ancak, kitaplığa yeni işlevler eklenmez.</span><span class="sxs-lookup"><span data-stu-id="b9ad7-113">However, new functionality won't be added to the library.</span></span> <span data-ttu-id="b9ad7-114">Bunun yerine, diğer kitaplıklara ve API 'lere yeni işlevsellik eklenecektir.</span><span class="sxs-lookup"><span data-stu-id="b9ad7-114">Instead, new functionality will be added to other libraries and APIs.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b9ad7-115">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="b9ad7-115">Version introduced</span></span>

<span data-ttu-id="b9ad7-116">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="b9ad7-116">5.0 Preview 6</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b9ad7-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="b9ad7-117">Recommended action</span></span>

- <span data-ttu-id="b9ad7-118">Gereksinimlerinizi karşılıyorsa Kitaplığın eski sürümlerini kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9ad7-118">You can continue to use older versions of the library if they meet your requirements.</span></span>

- <span data-ttu-id="b9ad7-119">Eski sürümler gereksinimlerinizi karşılamıyorsa, API 'lerin kullanımlarını `PlatformAbstractions` Önerilen değişikliklerle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b9ad7-119">If the older versions don't meet your requirements, replace usages of the `PlatformAbstractions` APIs with the recommended replacements.</span></span>

  | <span data-ttu-id="b9ad7-120">`PlatformAbstractions`'SINDEKI</span><span class="sxs-lookup"><span data-stu-id="b9ad7-120">`PlatformAbstractions` API</span></span> | <span data-ttu-id="b9ad7-121">Önerilen değiştirme</span><span class="sxs-lookup"><span data-stu-id="b9ad7-121">Recommended replacement</span></span> |
  |-|-|
  | `ApplicationEnvironment.ApplicationBasePath` | <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> |
  | <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner> | <xref:System.HashCode?displayProperty=nameWithType> |
  | `RuntimeEnvironment.GetRuntimeIdentifier()` | <xref:System.Runtime.InteropServices.RuntimeInformation.RuntimeIdentifier?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemPlatform` | <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> |
  | `RuntimeEnvironment.RuntimeArchitecture` | <xref:System.Runtime.InteropServices.RuntimeInformation.ProcessArchitecture?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystem` | <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemVersion` | <span data-ttu-id="b9ad7-122"><xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> ve <xref:System.Environment.OSVersion?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b9ad7-122"><xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> and <xref:System.Environment.OSVersion?displayProperty=nameWithType></span></span> |

  > [!NOTE]
  > <span data-ttu-id="b9ad7-123">Ve için çoğu kullanım `RuntimeEnvironment.OperatingSystem` `RuntimeEnvironment.OperatingSystemVersion` örneği, örneğin, bir kullanıcıya, günlüğe kaydetmeye ve telemetrisine görüntüleme amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="b9ad7-123">Most use cases for `RuntimeEnvironment.OperatingSystem` and `RuntimeEnvironment.OperatingSystemVersion` are for display purposes, for example, displaying to a user, logging, and telemetry.</span></span> <span data-ttu-id="b9ad7-124">Çalışma zamanı kararlarını bir işletim sistemi (OS) sürümüne göre yapmanız önerilmez.</span><span class="sxs-lookup"><span data-stu-id="b9ad7-124">It's not recommended to make run-time decisions based on an operating system (OS) version.</span></span> <span data-ttu-id="b9ad7-125"><xref:System.Environment.OSVersion?displayProperty=nameWithType>Şimdi Windows ve macOS işletim sistemleri için doğru sürümü döndürür.</span><span class="sxs-lookup"><span data-stu-id="b9ad7-125"><xref:System.Environment.OSVersion?displayProperty=nameWithType> now returns the correct version for Windows and macOS operating systems.</span></span> <span data-ttu-id="b9ad7-126">Ancak, çoğu UNIX dağıtımı için "işletim sistemi sürümü" olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="b9ad7-126">However, for most Unix distributions, what is considered to be the "OS version" is not as straightforward.</span></span> <span data-ttu-id="b9ad7-127">Örneğin, Linux çekirdek sürümü olabilir veya sürüm sürümü olabilir.</span><span class="sxs-lookup"><span data-stu-id="b9ad7-127">For example, it could be the Linux kernel version, or it could be the distro version.</span></span> <span data-ttu-id="b9ad7-128">Birçok UNIX platformu için <xref:System.Environment.OSVersion?displayProperty=nameWithType> ve <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> tarafından döndürülen sürümünü döndürün `uname` .</span><span class="sxs-lookup"><span data-stu-id="b9ad7-128">For most Unix platforms, <xref:System.Environment.OSVersion?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> return the version that's returned by `uname`.</span></span> <span data-ttu-id="b9ad7-129">Linux 'un adı ve sürüm bilgilerini almak için önerilen yaklaşım, */etc/OS-Release* dosyasını okumalıdır.</span><span class="sxs-lookup"><span data-stu-id="b9ad7-129">To get the Linux distro name and version information, the recommended approach is to read the */etc/os-release* file.</span></span>

#### <a name="category"></a><span data-ttu-id="b9ad7-130">Kategori</span><span class="sxs-lookup"><span data-stu-id="b9ad7-130">Category</span></span>

<span data-ttu-id="b9ad7-131">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="b9ad7-131">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b9ad7-132">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b9ad7-132">Affected APIs</span></span>

- `Microsoft.DotNet.PlatformAbstractions.ApplicationEnvironment.ApplicationBasePath`
- <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner?displayProperty=fullName>
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.GetRuntimeIdentifier()`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystem`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemPlatform`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemVersion`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.RuntimeArchitecture`

<!--

#### Affected APIs

- `P:Microsoft.DotNet.PlatformAbstractions.ApplicationEnvironment.ApplicationBasePath`
- `T:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner`
- `M:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.GetRuntimeIdentifier`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystem`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemPlatform`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemVersion`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.RuntimeArchitecture`

-->
