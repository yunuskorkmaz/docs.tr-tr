---
ms.openlocfilehash: 0d6847b7a937094f36efae70ae450cc37824221d
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955569"
---
### <a name="assembly-related-api-behavior-changes-for-single-file-publishing-format"></a><span data-ttu-id="636b3-101">Tek dosya yayımlama biçimi için derlemeden ilgili API davranışı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="636b3-101">Assembly-related API behavior changes for single-file publishing format</span></span>

<span data-ttu-id="636b3-102">Bir derlemenin dosya konumuyla ilgili birden çok API, tek dosya yayımlama biçiminde çağrıldığında davranış değişikliklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="636b3-102">Multiple APIs related to an assembly's file location have behavior changes when they're invoked in a single-file publishing format.</span></span>

#### <a name="change-description"></a><span data-ttu-id="636b3-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="636b3-103">Change description</span></span>

<span data-ttu-id="636b3-104">.NET 5,0 ve üzeri sürümler için tek dosya yayımlama sürümünde, paketlenmiş derlemeler diske ayıklanmak yerine bellekten yüklenir.</span><span class="sxs-lookup"><span data-stu-id="636b3-104">In single-file publishing for .NET 5.0 and later versions, bundled assemblies are loaded from memory instead of extracted to disk.</span></span> <span data-ttu-id="636b3-105">Tek dosya yayımlanan uygulamalar için bu, konum ile ilgili bazı API 'Lerin .NET 5,0 ve üzeri sürümlerde .net 'in önceki sürümlerinden farklı değerler döndürdüğü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="636b3-105">For single-file published apps, this means that certain location-related APIs return different values on .NET 5.0 and later than on previous versions of .NET.</span></span> <span data-ttu-id="636b3-106">Değişiklikler aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="636b3-106">The changes are as follows:</span></span>

| <span data-ttu-id="636b3-107">API</span><span class="sxs-lookup"><span data-stu-id="636b3-107">API</span></span> | <span data-ttu-id="636b3-108">Önceki sürümler</span><span class="sxs-lookup"><span data-stu-id="636b3-108">Previous versions</span></span> | <span data-ttu-id="636b3-109">.NET 5,0 ve üzeri</span><span class="sxs-lookup"><span data-stu-id="636b3-109">.NET 5.0 and later</span></span> |
| - | - | - |
| <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> | <span data-ttu-id="636b3-110">Ayıklanan DLL dosyası yolunu döndürür</span><span class="sxs-lookup"><span data-stu-id="636b3-110">Returns extracted DLL file path</span></span> | <span data-ttu-id="636b3-111">Paketlenmiş derlemeler için boş dize döndürür</span><span class="sxs-lookup"><span data-stu-id="636b3-111">Returns empty string for bundled assemblies</span></span> |
| <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> | <span data-ttu-id="636b3-112">Ayıklanan DLL dosyası yolunu döndürür</span><span class="sxs-lookup"><span data-stu-id="636b3-112">Returns extracted DLL file path</span></span> | <span data-ttu-id="636b3-113">Paketlenmiş derlemeler için özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="636b3-113">Throws exception for bundled assemblies</span></span> |
| <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType> | <span data-ttu-id="636b3-114">`null`Paketlenmiş derlemeler için döndürür</span><span class="sxs-lookup"><span data-stu-id="636b3-114">Returns `null` for bundled assemblies</span></span> | <span data-ttu-id="636b3-115">Paketlenmiş derlemeler için özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="636b3-115">Throws exception for bundled assemblies</span></span> |
| `Environment.GetCommandLineArgs()[0]` | <span data-ttu-id="636b3-116">Değer, giriş noktası DLL 'inin adıdır</span><span class="sxs-lookup"><span data-stu-id="636b3-116">Value is the name of the entry point DLL</span></span> | <span data-ttu-id="636b3-117">Değer, ana bilgisayarın yürütülebilir dosyasının adıdır</span><span class="sxs-lookup"><span data-stu-id="636b3-117">Value is the name of the host executable</span></span> |
| <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> | <span data-ttu-id="636b3-118">Değer, geçici ayıklama dizinidir</span><span class="sxs-lookup"><span data-stu-id="636b3-118">Value is the temporary extraction directory</span></span> | <span data-ttu-id="636b3-119">Değer, ana bilgisayarın yürütülebilir dosyasının bulunduğu dizin</span><span class="sxs-lookup"><span data-stu-id="636b3-119">Value is the containing directory of the host executable</span></span> |

#### <a name="version-introduced"></a><span data-ttu-id="636b3-120">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="636b3-120">Version introduced</span></span>

<span data-ttu-id="636b3-121">5.0</span><span class="sxs-lookup"><span data-stu-id="636b3-121">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="636b3-122">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="636b3-122">Recommended action</span></span>

<span data-ttu-id="636b3-123">Tek bir dosya olarak yayımlarken derlemelerin dosya konumundaki bağımlılıklardan kaçının.</span><span class="sxs-lookup"><span data-stu-id="636b3-123">Avoid dependencies on the file location of assemblies when publishing as a single file.</span></span>

#### <a name="category"></a><span data-ttu-id="636b3-124">Kategori</span><span class="sxs-lookup"><span data-stu-id="636b3-124">Category</span></span>

- <span data-ttu-id="636b3-125">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="636b3-125">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="636b3-126">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="636b3-126">Affected APIs</span></span>

- <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType>
- <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType>
- <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Reflection.Assembly.Location`
- `P:System.Reflection.Assembly.CodeBase`
- `M:System.Reflection.Assembly.GetFile(System.String)`
- `M:System.Environment.GetCommandLineArgs`
- `P:System.AppContext.BaseDirectory`

-->
