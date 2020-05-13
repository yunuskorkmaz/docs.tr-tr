---
ms.openlocfilehash: f24a29a00a1bff34a452c43716d76bf72ef277b5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206227"
---
### <a name="resource-manifest-file-name-change"></a><span data-ttu-id="ba9fc-101">Kaynak bildirimi dosya adı değişikliği</span><span class="sxs-lookup"><span data-stu-id="ba9fc-101">Resource manifest file name change</span></span>

<span data-ttu-id="ba9fc-102">.NET Core 3,0 ' den başlayarak, MSBuild varsayılan durumda kaynak dosyaları için farklı bir bildirim dosyası adı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ba9fc-102">Starting in .NET Core 3.0, in the default case, MSBuild generates a different manifest file name for resource files.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ba9fc-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="ba9fc-103">Version introduced</span></span>

<span data-ttu-id="ba9fc-104">3,0</span><span class="sxs-lookup"><span data-stu-id="ba9fc-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="ba9fc-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="ba9fc-105">Change description</span></span>

<span data-ttu-id="ba9fc-106">.NET Core 3,0 ' den önce `LogicalName` `ManifestResourceName` `DependentUpon` Proje dosyasındaki bir öğe için bir, veya meta veri belirtilmemişse, `EmbeddedResource` MSBuild, düzende bir bildirim dosyası adı oluşturdu `<RootNamespace>.<ResourceFilePathFromProjectRoot>.resources` .</span><span class="sxs-lookup"><span data-stu-id="ba9fc-106">Prior to .NET Core 3.0, if no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata was specified for an `EmbeddedResource` item in the project file, MSBuild generated a manifest file name in the pattern `<RootNamespace>.<ResourceFilePathFromProjectRoot>.resources`.</span></span> <span data-ttu-id="ba9fc-107">`RootNamespace`Proje dosyasında tanımlanmamışsa, varsayılan olarak proje adı olur.</span><span class="sxs-lookup"><span data-stu-id="ba9fc-107">If `RootNamespace` is not defined in the project file, it defaults to the project name.</span></span> <span data-ttu-id="ba9fc-108">Örneğin, kök proje dizininde *Form1. resx* adlı bir kaynak dosyası için oluşturulan bildirim adı *Myprojem. Form1. resources*idi.</span><span class="sxs-lookup"><span data-stu-id="ba9fc-108">For example, the generated manifest name for a resource file named *Form1.resx* in the root project directory was *MyProject.Form1.resources*.</span></span>

<span data-ttu-id="ba9fc-109">.NET Core 3,0 ' den itibaren, bir kaynak dosyası aynı ada sahip bir kaynak dosya (örneğin, *Form1. resx* ve *Form1.cs*) ile birlikte bulunuyorsa MSBuild, kaynak dosyasındaki tür bilgilerini kullanarak bildirim dosyası adını oluşturur `<Namespace>.<ClassName>.resources` .</span><span class="sxs-lookup"><span data-stu-id="ba9fc-109">Starting in .NET Core 3.0, if a resource file is colocated with a source file of the same name (for example, *Form1.resx* and *Form1.cs*), MSBuild uses type information from the source file to generate the manifest file name in the pattern `<Namespace>.<ClassName>.resources`.</span></span> <span data-ttu-id="ba9fc-110">Ad alanı ve sınıf adı, birlikte bulunan kaynak dosyadaki ilk türden ayıklanır.</span><span class="sxs-lookup"><span data-stu-id="ba9fc-110">The namespace and class name are extracted from the first type in the colocated source file.</span></span> <span data-ttu-id="ba9fc-111">Örneğin, *Form1.cs* adlı bir kaynak dosyayla birlikte bulunan *Form1. resx* adlı bir kaynak dosyası Için üretilen bildirim adı *MyNamespace. Form1. resources*' dir.</span><span class="sxs-lookup"><span data-stu-id="ba9fc-111">For example, the generated manifest name for a resource file named *Form1.resx* that's colocated with a source file named *Form1.cs* is *MyNamespace.Form1.resources*.</span></span> <span data-ttu-id="ba9fc-112">Önemli şey, dosya adının ilk bölümünün .NET Core 'un önceki sürümleriyle ( *MyProject*yerine*MyNamespace* ) farklı olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="ba9fc-112">The key thing to note is that the first part of the file name is different to prior versions of .NET Core (*MyNamespace* instead of *MyProject*).</span></span>

> [!NOTE]
> <span data-ttu-id="ba9fc-113">`LogicalName` `ManifestResourceName` `DependentUpon` Proje dosyasındaki bir öğe üzerinde, veya meta veriler belirtilmişse, `EmbeddedResource` Bu değişiklik bu kaynak dosyasını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="ba9fc-113">If you have `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata specified on an `EmbeddedResource` item in the project file, then this change does not affect that resource file.</span></span>

<span data-ttu-id="ba9fc-114">Bu son değişiklik, `EmbeddedResourceUseDependentUponConvention` özelliğin .NET Core projelerine eklenmesiyle birlikte sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="ba9fc-114">This breaking change was introduced with the addition of the `EmbeddedResourceUseDependentUponConvention` property to .NET Core projects.</span></span> <span data-ttu-id="ba9fc-115">Varsayılan olarak, kaynak dosyaları .NET Core proje dosyasında açık olarak listelenmez, bu nedenle `DependentUpon` oluşturulan *. resources* dosyasının adını belirtmek için meta verileri yoktur.</span><span class="sxs-lookup"><span data-stu-id="ba9fc-115">By default, resource files aren't explicitly listed in a .NET Core project file, so they have no `DependentUpon` metadata to specify how to name the generated *.resources* file.</span></span> <span data-ttu-id="ba9fc-116">, `EmbeddedResourceUseDependentUponConvention` `true` Varsayılan olan olarak ayarlandığında, MSBuild, birlikte bulunan bir kaynak dosyayı arar ve bu dosyadan bir ad alanı ve sınıf adı ayıklar.</span><span class="sxs-lookup"><span data-stu-id="ba9fc-116">When `EmbeddedResourceUseDependentUponConvention` is set to `true`, which is the default, MSBuild looks for a colocated source file and extracts a namespace and class name from that file.</span></span> <span data-ttu-id="ba9fc-117">`EmbeddedResourceUseDependentUponConvention`Olarak ayarlarsanız `false` , MSBuild, bildirim adını, `RootNamespace` ve göreli dosya yolunu birleştiren önceki davranışa göre oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ba9fc-117">If you set `EmbeddedResourceUseDependentUponConvention` to `false`, MSBuild generates the manifest name according to the previous behavior, which combines `RootNamespace` and the relative file path.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ba9fc-118">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="ba9fc-118">Recommended action</span></span>

<span data-ttu-id="ba9fc-119">Çoğu durumda, geliştiricinin bölümünde herhangi bir eylem gerekmez ve uygulamanız çalışmaya devam etmelidir.</span><span class="sxs-lookup"><span data-stu-id="ba9fc-119">In most cases, no action is required on the part of the developer, and your app should continue to work.</span></span> <span data-ttu-id="ba9fc-120">Ancak, bu değişiklik uygulamanızı kopararsa şunlardan birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ba9fc-120">However, if this change breaks your app, you can either:</span></span>

- <span data-ttu-id="ba9fc-121">Kodunuzu, yeni bildirim adını beklediği şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ba9fc-121">Change your code to expect the new manifest name.</span></span>

- <span data-ttu-id="ba9fc-122">Yeni adlandırma kuralını, `EmbeddedResourceUseDependentUponConvention` proje dosyanızda olarak ayarlayarak geri çevirin `false` .</span><span class="sxs-lookup"><span data-stu-id="ba9fc-122">Opt out of the new naming convention by setting `EmbeddedResourceUseDependentUponConvention` to `false` in your project file.</span></span>

  ```xml
  <PropertyGroup>
    <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
  </PropertyGroup>
  ```

#### <a name="category"></a><span data-ttu-id="ba9fc-123">Kategori</span><span class="sxs-lookup"><span data-stu-id="ba9fc-123">Category</span></span>

<span data-ttu-id="ba9fc-124">MSBuild</span><span class="sxs-lookup"><span data-stu-id="ba9fc-124">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ba9fc-125">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ba9fc-125">Affected APIs</span></span>

<span data-ttu-id="ba9fc-126">Yok</span><span class="sxs-lookup"><span data-stu-id="ba9fc-126">N/A</span></span>
