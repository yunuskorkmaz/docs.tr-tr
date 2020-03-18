---
ms.openlocfilehash: 16ee73bfc0ab33b04ea3e2fa6d0eec521a9b8634
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78968294"
---
### <a name="resource-manifest-file-names"></a><span data-ttu-id="f461e-101">Kaynak bildirimi dosya adları</span><span class="sxs-lookup"><span data-stu-id="f461e-101">Resource manifest file names</span></span>

<span data-ttu-id="f461e-102">.NET Core 3.0'dan başlayarak oluşturulan kaynak bildirimi dosya adı değişti.</span><span class="sxs-lookup"><span data-stu-id="f461e-102">Starting in .NET Core 3.0, the generated resource manifest file name has changed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f461e-103">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="f461e-103">Version introduced</span></span>

<span data-ttu-id="f461e-104">3,0</span><span class="sxs-lookup"><span data-stu-id="f461e-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="f461e-105">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="f461e-105">Change description</span></span>

<span data-ttu-id="f461e-106">MSBuild proje dosyasındaki bir kaynak (*.resx*) dosyası için [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) meta verileri ayarlandığında ,.NET Core 3.0'dan önce oluşturulan bildirim adı *Namespace.Classname.resources*idi.</span><span class="sxs-lookup"><span data-stu-id="f461e-106">Prior to .NET Core 3.0, when [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) metadata was set for a resource (*.resx*) file in the MSBuild project file, the generated manifest name was *Namespace.Classname.resources*.</span></span> <span data-ttu-id="f461e-107">[DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) ayarlanmadığında, oluşturulan bildirim adı *Namespace.Classname.FolderPathRelativeToRoot.Culture.resources*oldu.</span><span class="sxs-lookup"><span data-stu-id="f461e-107">When [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) was not set, the generated manifest name was *Namespace.Classname.FolderPathRelativeToRoot.Culture.resources*.</span></span>

<span data-ttu-id="f461e-108">.NET Core 3.0'dan başlayarak, bir *.resx* dosyası aynı adı taşıyan bir kaynak dosyayla birlikte konumlandığında, örneğin Windows Forms uygulamalarında kaynak bildirimi adı kaynak dosyadaki ilk türün tam adından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f461e-108">Starting in .NET Core 3.0, when a *.resx* file is colocated with a source file of the same name, for example, in Windows Forms apps, the resource manifest name is generated from the full name of the first type in the source file.</span></span> <span data-ttu-id="f461e-109">Örneğin, *Type.cs* *Type.resx*ile birlikte bulunursa, oluşturulan bildirim adı *Namespace.Classname.resources'tır.*</span><span class="sxs-lookup"><span data-stu-id="f461e-109">For example, if *Type.cs* is colocated with *Type.resx*, the generated manifest name is *Namespace.Classname.resources*.</span></span> <span data-ttu-id="f461e-110">Ancak, *.resx* dosyasının `EmbeddedResource` özelliğindeki özniteliklerden herhangi birini değiştirirseniz, oluşturulan bildirim dosyası adı farklı olabilir:</span><span class="sxs-lookup"><span data-stu-id="f461e-110">However, if you modify any of the attributes on the `EmbeddedResource` property for the *.resx* file, the generated manifest file name may be different:</span></span>

- <span data-ttu-id="f461e-111">`LogicalName` Özellik teki öznitelik `EmbeddedResource` ayarlanırsa, bu değer kaynak bildirimi dosya adı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f461e-111">If the `LogicalName` attribute on the `EmbeddedResource` property is set, that value is used as the resource manifest file name.</span></span>

  <span data-ttu-id="f461e-112">Örnekler:</span><span class="sxs-lookup"><span data-stu-id="f461e-112">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  <span data-ttu-id="f461e-113">**Oluşturulan kaynak bildirimi dosya adı**: *SomeName.resources* *(.resx* dosya adı veya kültürü veya diğer meta verilerden bağımsız olarak).</span><span class="sxs-lookup"><span data-stu-id="f461e-113">**Generated resource manifest file name**: *SomeName.resources* (regardless of the *.resx* file name or culture or any other metadata).</span></span>

- <span data-ttu-id="f461e-114">`LogicalName` Ayarlanmaz, ancak `ManifestResourceName` `EmbeddedResource` özellik üzerindeki öznitelik ayarlanırsa, değeri, dosya uzantısı *.resources*ile birlikte, kaynak bildirimi dosya adı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f461e-114">If `LogicalName` is not set, but the `ManifestResourceName` attribute on the `EmbeddedResource` property is set, its value, combined with the file extension *.resources*, is used as the resource manifest file name.</span></span>

  <span data-ttu-id="f461e-115">Örnekler:</span><span class="sxs-lookup"><span data-stu-id="f461e-115">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  <span data-ttu-id="f461e-116">**Oluşturulan kaynak bildirimi dosya adı**: *SomeName.resources* veya *SomeName.fr-FR.resources*.</span><span class="sxs-lookup"><span data-stu-id="f461e-116">**Generated resource manifest file name**: *SomeName.resources* or *SomeName.fr-FR.resources*.</span></span>

- <span data-ttu-id="f461e-117">Önceki kurallar geçerli değilse ve `DependentUpon` `EmbeddedResource` öğedeki öznitelik bir kaynak dosyasına ayarlanırsa, kaynak dosyasındaki birinci sınıfın tür adı kaynak bildirimi dosya adında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f461e-117">If the previous rules don't apply, and the `DependentUpon` attribute on the `EmbeddedResource` element is set to a source file, the type name of the first class in the source file is used in the resource manifest file name.</span></span> <span data-ttu-id="f461e-118">Daha spesifik olarak, oluşturulan dosya adı *\[Namespace.Classname olduğunu. Kültür].kaynaklar*.</span><span class="sxs-lookup"><span data-stu-id="f461e-118">More specifically, the generated file name is *Namespace.Classname\[.Culture].resources*.</span></span>

  <span data-ttu-id="f461e-119">Örnekler:</span><span class="sxs-lookup"><span data-stu-id="f461e-119">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  <span data-ttu-id="f461e-120">**Oluşturulan kaynak bildirimi dosya adı**: *Namespace.Classname.resources* veya `Namespace.Classname` *Namespace.Classname.fr-FR.resources* *(MyTypes.cs'daki*birinci sınıfın adı nerededir).</span><span class="sxs-lookup"><span data-stu-id="f461e-120">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>

- <span data-ttu-id="f461e-121">Önceki kurallar `EmbeddedResourceUseDependentUponConvention` geçerli değilse, (.NET `true` Core için varsayılan varsayılan) ve aynı temel dosya adı olan bir *.resx* dosyasıyla birlikte bir kaynak dosyası varsa, *.resx* dosyası eşleşen kaynak dosyaya bağımlı hale getirilir ve oluşturulan ad önceki kuraldakiyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="f461e-121">If the previous rules don't apply, `EmbeddedResourceUseDependentUponConvention` is `true` (the default for .NET Core), and there's a source file colocated with a *.resx* file that has the same base file name, the *.resx* file is made dependent upon the matching source file, and the generated name is the same as in the previous rule.</span></span> <span data-ttu-id="f461e-122">Bu, .NET Core projeleri için "varsayılan ayarlar" kuralıdır.</span><span class="sxs-lookup"><span data-stu-id="f461e-122">This is the "default settings" rule for .NET Core projects.</span></span>
  
  <span data-ttu-id="f461e-123">Örnekler:</span><span class="sxs-lookup"><span data-stu-id="f461e-123">Examples:</span></span>
  
  <span data-ttu-id="f461e-124">MyTypes.cs *MyTypes.cs* ve *MyTypes.resx* veya *MyTypes.fr-FR.resx* dosyaları aynı klasörde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f461e-124">Files *MyTypes.cs* and *MyTypes.resx* or *MyTypes.fr-FR.resx* exist in the same folder.</span></span>
  
  <span data-ttu-id="f461e-125">**Oluşturulan kaynak bildirimi dosya adı**: *Namespace.Classname.resources* veya `Namespace.Classname` *Namespace.Classname.fr-FR.resources* *(MyTypes.cs'daki*birinci sınıfın adı nerededir).</span><span class="sxs-lookup"><span data-stu-id="f461e-125">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>

- <span data-ttu-id="f461e-126">Önceki kuralların hiçbiri geçerli değilse, oluşturulan kaynak bildirimi dosya adı *RootNamespace.RelativePathWithDotsForSlashes olduğunu.\[ Kültür.] kaynaklar*.</span><span class="sxs-lookup"><span data-stu-id="f461e-126">If none of the previous rules apply, the generated resource manifest file name is *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources*.</span></span> <span data-ttu-id="f461e-127">Göreli yol, ayarlanırsa `Link` `EmbeddedResource` öğenin özniteliğinin değeridir.</span><span class="sxs-lookup"><span data-stu-id="f461e-127">The relative path is the value of the `Link` attribute of the `EmbeddedResource` element if it's set.</span></span> <span data-ttu-id="f461e-128">Aksi takdirde, göreli yol `Identity` `EmbeddedResource` öğenin özniteliğinin değeridir.</span><span class="sxs-lookup"><span data-stu-id="f461e-128">Otherwise, the relative path is the value of the `Identity` attribute of the `EmbeddedResource` element.</span></span> <span data-ttu-id="f461e-129">Visual Studio'da bu, çözüm gezgininde proje kökünden dosyaya giden yoldur.</span><span class="sxs-lookup"><span data-stu-id="f461e-129">In Visual Studio, this is the path from the project root to the file in Solution Explorer.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f461e-130">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f461e-130">Recommended action</span></span>

<span data-ttu-id="f461e-131">Oluşturulan bildirim adlarıyla memnun değilseniz şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f461e-131">If you're unsatisfied with the generated manifest names, you can:</span></span>

- <span data-ttu-id="f461e-132">Kaynak dosyası meta verilerinizi daha önce açıklanan adlandırma kurallarından birine göre değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f461e-132">Modify your resource file metadata according to one of the previously described naming rules.</span></span>

- <span data-ttu-id="f461e-133">Yeni kuralı tamamen devre dışı bırakmak için proje dosyanızda ayarlayın: `EmbeddedResourceUseDependentUponConvention` `false`</span><span class="sxs-lookup"><span data-stu-id="f461e-133">Set `EmbeddedResourceUseDependentUponConvention` to `false` in your project file to opt out of the new convention entirely:</span></span>

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > <span data-ttu-id="f461e-134">`LogicalName` Öznitelikler varsa, bunların değerleri yine de oluşturulan dosya adı için `ManifestResourceName` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f461e-134">If the `LogicalName` or `ManifestResourceName` attributes are present, their values will still be used for the generated file name.</span></span>

#### <a name="category"></a><span data-ttu-id="f461e-135">Kategori</span><span class="sxs-lookup"><span data-stu-id="f461e-135">Category</span></span>

<span data-ttu-id="f461e-136">MSBuild</span><span class="sxs-lookup"><span data-stu-id="f461e-136">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f461e-137">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f461e-137">Affected APIs</span></span>

<span data-ttu-id="f461e-138">Yok</span><span class="sxs-lookup"><span data-stu-id="f461e-138">N/A</span></span>
