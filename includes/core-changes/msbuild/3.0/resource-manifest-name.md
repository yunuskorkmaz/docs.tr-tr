---
ms.openlocfilehash: 276268d31670b5e7dcd0ae9c0b7a61c3c38ca663
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451907"
---
### <a name="resource-manifest-file-names"></a><span data-ttu-id="2ffb2-101">Kaynak bildirim dosyası adları</span><span class="sxs-lookup"><span data-stu-id="2ffb2-101">Resource manifest file names</span></span>

<span data-ttu-id="2ffb2-102">.NET Core 3,0 ' den başlayarak, oluşturulan kaynak bildirim dosyası adı değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="2ffb2-102">Starting in .NET Core 3.0, the generated resource manifest file name has changed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2ffb2-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="2ffb2-103">Version introduced</span></span>

<span data-ttu-id="2ffb2-104">3.0</span><span class="sxs-lookup"><span data-stu-id="2ffb2-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="2ffb2-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="2ffb2-105">Change description</span></span>

<span data-ttu-id="2ffb2-106">.NET Core 3,0 ' den önce, MSBuild proje dosyasındaki bir kaynak ( *. resx*) dosyası için [bir veri kümesi ayarlandığında,](/visualstudio/msbuild/common-msbuild-project-items#compile) oluşturulan bildirim adı *Namespace. ClassName. resources*idi.</span><span class="sxs-lookup"><span data-stu-id="2ffb2-106">Prior to .NET Core 3.0, when [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) metadata was set for a resource (*.resx*) file in the MSBuild project file, the generated manifest name was *Namespace.Classname.resources*.</span></span> <span data-ttu-id="2ffb2-107">[Dependentno](/visualstudio/msbuild/common-msbuild-project-items#compile) ayarlanınca, oluşturulan bildirim adı *Namespace. ClassName. FolderPathRelativeToRoot. Culture. resources*idi.</span><span class="sxs-lookup"><span data-stu-id="2ffb2-107">When [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) was not set, the generated manifest name was *Namespace.Classname.FolderPathRelativeToRoot.Culture.resources*.</span></span>

<span data-ttu-id="2ffb2-108">.NET Core 3,0 ' den itibaren, bir *. resx* dosyası aynı ada sahip bir kaynak dosyayla birlikte kullanılırken, örneğin Windows Forms uygulamalarda kaynak bildirimi adı kaynak dosyadaki ilk türün tam adından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2ffb2-108">Starting in .NET Core 3.0, when a *.resx* file is colocated with a source file of the same name, for example, in Windows Forms apps, the resource manifest name is generated from the full name of the first type in the source file.</span></span> <span data-ttu-id="2ffb2-109">Örneğin, *Type.cs* *Type. resx*ile birlikte bulunuyorsa, oluşturulan bildirim adı *Namespace. ClassName. resources*olur.</span><span class="sxs-lookup"><span data-stu-id="2ffb2-109">For example, if *Type.cs* is colocated with *Type.resx*, the generated manifest name is *Namespace.Classname.resources*.</span></span> <span data-ttu-id="2ffb2-110">Ancak, *. resx* dosyası için `EmbeddedResource` özelliğindeki özniteliklerin herhangi birini değiştirirseniz, oluşturulan bildirim dosyası adı farklı olabilir:</span><span class="sxs-lookup"><span data-stu-id="2ffb2-110">However, if you modify any of the attributes on the `EmbeddedResource` property for the *.resx* file, the generated manifest file name may be different:</span></span>

- <span data-ttu-id="2ffb2-111">`EmbeddedResource` özelliğindeki `LogicalName` özniteliği ayarlandıysa, bu değer kaynak bildirimi dosya adı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2ffb2-111">If the `LogicalName` attribute on the `EmbeddedResource` property is set, that value is used as the resource manifest file name.</span></span>

  <span data-ttu-id="2ffb2-112">Örnekler:</span><span class="sxs-lookup"><span data-stu-id="2ffb2-112">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  <span data-ttu-id="2ffb2-113">**Oluşturulan kaynak bildirim dosyası adı**: *someName. resources* ( *. resx* dosya adı veya kültür ya da diğer meta veriler ne olursa olsun).</span><span class="sxs-lookup"><span data-stu-id="2ffb2-113">**Generated resource manifest file name**: *SomeName.resources* (regardless of the *.resx* file name or culture or any other metadata).</span></span>

- <span data-ttu-id="2ffb2-114">`LogicalName` ayarlanmamışsa, ancak `EmbeddedResource` özelliğindeki `ManifestResourceName` özniteliği ayarlanmışsa, kaynak bildirim dosyası adı olarak, değeri *. resources*ile birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2ffb2-114">If `LogicalName` is not set, but the `ManifestResourceName` attribute on the `EmbeddedResource` property is set, its value, combined with the file extension *.resources*, is used as the resource manifest file name.</span></span>

  <span data-ttu-id="2ffb2-115">Örnekler:</span><span class="sxs-lookup"><span data-stu-id="2ffb2-115">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  <span data-ttu-id="2ffb2-116">**Kaynak bildirim dosyası adı oluşturuldu**: *someName. resources* veya *someName.fr-fr. resources*.</span><span class="sxs-lookup"><span data-stu-id="2ffb2-116">**Generated resource manifest file name**: *SomeName.resources* or *SomeName.fr-FR.resources*.</span></span>

- <span data-ttu-id="2ffb2-117">Önceki kurallar uygulanmıyorsanız ve `EmbeddedResource` öğesindeki `DependentUpon` özniteliği bir kaynak dosyaya ayarlanırsa, kaynak dosyadaki ilk sınıfın tür adı kaynak bildirim dosyası adında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2ffb2-117">If the previous rules don't apply, and the `DependentUpon` attribute on the `EmbeddedResource` element is set to a source file, the type name of the first class in the source file is used in the resource manifest file name.</span></span> <span data-ttu-id="2ffb2-118">Daha belirgin olarak, oluşturulan dosya adı *Namespace. Classname\[. Kültür]. resources*.</span><span class="sxs-lookup"><span data-stu-id="2ffb2-118">More specifically, the generated file name is *Namespace.Classname\[.Culture].resources*.</span></span>

  <span data-ttu-id="2ffb2-119">Örnekler:</span><span class="sxs-lookup"><span data-stu-id="2ffb2-119">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  <span data-ttu-id="2ffb2-120">**Oluşturulan kaynak bildirim dosyası adı**: *Namespace. ClassName. resources* veya *Namespace.ClassName.fr-fr. resources* (`Namespace.Classname`, *MyTypes.cs*içindeki ilk sınıfın adıdır).</span><span class="sxs-lookup"><span data-stu-id="2ffb2-120">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>

- <span data-ttu-id="2ffb2-121">Önceki kurallar uygulanmamışsa, `EmbeddedResourceUseDependentUponConvention` `true` (.NET Core için varsayılan) ve aynı temel dosya adına sahip bir *. resx* dosyası ile birlikte bulunan bir kaynak dosya varsa, *. resx* dosyası eşleşen kaynak dosyaya bağımlıdır ve oluşturulan ad önceki kuraldaki ile aynı olur.</span><span class="sxs-lookup"><span data-stu-id="2ffb2-121">If the previous rules don't apply, `EmbeddedResourceUseDependentUponConvention` is `true` (the default for .NET Core), and there's a source file colocated with a *.resx* file that has the same base file name, the *.resx* file is made dependent upon the matching source file, and the generated name is the same as in the previous rule.</span></span> <span data-ttu-id="2ffb2-122">Bu, .NET Core projeleri için "varsayılan ayarlar" kuralıdır.</span><span class="sxs-lookup"><span data-stu-id="2ffb2-122">This is the "default settings" rule for .NET Core projects.</span></span>
  
  <span data-ttu-id="2ffb2-123">Örnekler:</span><span class="sxs-lookup"><span data-stu-id="2ffb2-123">Examples:</span></span>
  
  <span data-ttu-id="2ffb2-124">*MyTypes.cs* ve *myTypes. resx* veya *MyTypes.fr-fr. resx* dosyaları aynı klasörde bulunur.</span><span class="sxs-lookup"><span data-stu-id="2ffb2-124">Files *MyTypes.cs* and *MyTypes.resx* or *MyTypes.fr-FR.resx* exist in the same folder.</span></span>
  
  <span data-ttu-id="2ffb2-125">**Oluşturulan kaynak bildirim dosyası adı**: *Namespace. ClassName. resources* veya *Namespace.ClassName.fr-fr. resources* (`Namespace.Classname`, *MyTypes.cs*içindeki ilk sınıfın adıdır).</span><span class="sxs-lookup"><span data-stu-id="2ffb2-125">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>
    
- <span data-ttu-id="2ffb2-126">Önceki kuralların hiçbiri uygulanmadığı takdirde, oluşturulan kaynak bildirim dosyası adı *RootNamespace. Relativepathwithdotsforçizgiler.\[kültür.] kaynaklar*.</span><span class="sxs-lookup"><span data-stu-id="2ffb2-126">If none of the previous rules apply, the generated resource manifest file name is *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources*.</span></span> <span data-ttu-id="2ffb2-127">Göreli yol, ayarlandıysa `EmbeddedResource` öğenin `Link` özniteliğinin değeridir.</span><span class="sxs-lookup"><span data-stu-id="2ffb2-127">The relative path is the value of the `Link` attribute of the `EmbeddedResource` element if it's set.</span></span> <span data-ttu-id="2ffb2-128">Aksi takdirde, göreli yol `EmbeddedResource` öğesinin `Identity` özniteliğinin değeridir.</span><span class="sxs-lookup"><span data-stu-id="2ffb2-128">Otherwise, the relative path is the value of the `Identity` attribute of the `EmbeddedResource` element.</span></span> <span data-ttu-id="2ffb2-129">Visual Studio 'da, bu yol proje kökünden Çözüm Gezgini dosyanın yoludur.</span><span class="sxs-lookup"><span data-stu-id="2ffb2-129">In Visual Studio, this is the path from the project root to the file in Solution Explorer.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2ffb2-130">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="2ffb2-130">Recommended action</span></span>

<span data-ttu-id="2ffb2-131">Oluşturulan bildirim adlarından memnun kaldıysanız şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2ffb2-131">If you're unsatisfied with the generated manifest names, you can:</span></span>

- <span data-ttu-id="2ffb2-132">Kaynak dosyası meta verilerinizi, daha önce açıklanan adlandırma kurallarından birine göre değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2ffb2-132">Modify your resource file metadata according to one of the previously described naming rules.</span></span>

- <span data-ttu-id="2ffb2-133">Yeni kuralı tamamen devre dışı bırakmak için `EmbeddedResourceUseDependentUponConvention`, proje dosyanızda `false` olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="2ffb2-133">Set `EmbeddedResourceUseDependentUponConvention` to `false` in your project file to opt out of the new convention entirely:</span></span>

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > <span data-ttu-id="2ffb2-134">`LogicalName` veya `ManifestResourceName` öznitelikleri varsa, bu değerler oluşturulan dosya adı için yine de kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="2ffb2-134">If the `LogicalName` or `ManifestResourceName` attributes are present, their values will still be used for the generated file name.</span></span>

#### <a name="category"></a><span data-ttu-id="2ffb2-135">Kategori</span><span class="sxs-lookup"><span data-stu-id="2ffb2-135">Category</span></span>

<span data-ttu-id="2ffb2-136">MSBuild</span><span class="sxs-lookup"><span data-stu-id="2ffb2-136">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2ffb2-137">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="2ffb2-137">Affected APIs</span></span>

<span data-ttu-id="2ffb2-138">YOK</span><span class="sxs-lookup"><span data-stu-id="2ffb2-138">N/A</span></span>
