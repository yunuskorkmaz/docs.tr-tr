---
title: MSBuild bildirim dosyası adlarını nasıl oluşturur
description: Derleme zamanında MSBuild tarafından oluşturulan bir kaynak bildirim dosyası adının adını etkileyen faktörleri açıklar.
ms.date: 05/08/2020
ms.topic: conceptual
ms.openlocfilehash: 383bf6a077b0631e70ddaa4721b20e992127a73c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83232328"
---
# <a name="how-resource-manifest-files-are-named"></a><span data-ttu-id="f2960-103">Kaynak bildirim dosyaları nasıl adlandırılır</span><span class="sxs-lookup"><span data-stu-id="f2960-103">How resource manifest files are named</span></span>

<span data-ttu-id="f2960-104">MSBuild bir .NET Core projesi derlediğinde, *. resx* dosya UZANTıSıNA sahip XML kaynak dosyaları ikili *. resources* dosyalarına dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="f2960-104">When MSBuild compiles a .NET Core project, XML resource files, which have the *.resx* file extension, are converted into binary *.resources* files.</span></span> <span data-ttu-id="f2960-105">İkili dosyalar derleyicinin çıktısına katıştırılır ve tarafından okunabilir <xref:System.Resources.ResourceManager> .</span><span class="sxs-lookup"><span data-stu-id="f2960-105">The binary files are embedded into the output of the compiler and can be read by the <xref:System.Resources.ResourceManager>.</span></span> <span data-ttu-id="f2960-106">Bu makalede, MSBuild 'in her *. resources* dosyası için bir ad nasıl seçtiği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="f2960-106">This article describes how MSBuild chooses a name for each *.resources* file.</span></span>

> [!TIP]
> <span data-ttu-id="f2960-107">Proje dosyanıza açıkça bir kaynak öğesi eklerseniz ve bu, [.NET Core için varsayılan içerme genelleştirmeler dahil edilmiştir](../project-sdk/overview.md#default-compilation-includes), bir derleme hatası alırsınız.</span><span class="sxs-lookup"><span data-stu-id="f2960-107">If you explicitly add a resource item to your project file, and it's also [included with the default include globs for .NET Core](../project-sdk/overview.md#default-compilation-includes), you will get a build error.</span></span> <span data-ttu-id="f2960-108">Kaynak dosyalarını öğe olarak el ile eklemek için `EmbeddedResource` , `EnableDefaultEmbeddedResourceItems` özelliğini false olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f2960-108">To manually include resource files as `EmbeddedResource` items, set the `EnableDefaultEmbeddedResourceItems` property to false.</span></span>

## <a name="default-name"></a><span data-ttu-id="f2960-109">Varsayılan ad</span><span class="sxs-lookup"><span data-stu-id="f2960-109">Default name</span></span>

<span data-ttu-id="f2960-110">.NET Core 3,0 ve üzeri sürümlerde, aşağıdaki koşulların her ikisi de karşılandığında bir kaynak bildirimi için varsayılan ad kullanılır:</span><span class="sxs-lookup"><span data-stu-id="f2960-110">In .NET Core 3.0 and later, the default name for a resource manifest is used when both of the following conditions are met:</span></span>

- <span data-ttu-id="f2960-111">Kaynak dosyası proje dosyasına `EmbeddedResource` `LogicalName` ,, `ManifestResourceName` veya meta verileri içeren bir öğe olarak açıkça dahil edilmez `DependentUpon` .</span><span class="sxs-lookup"><span data-stu-id="f2960-111">The resource file is not explicitly included in the project file as an `EmbeddedResource` item with `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata.</span></span>
- <span data-ttu-id="f2960-112">`EmbeddedResourceUseDependentUponConvention`Özelliği `false` Proje dosyasında olarak ayarlanmamış.</span><span class="sxs-lookup"><span data-stu-id="f2960-112">The `EmbeddedResourceUseDependentUponConvention` property is not set to `false` in the project file.</span></span> <span data-ttu-id="f2960-113">Varsayılan olarak, bu özellik olarak ayarlanır `true` .</span><span class="sxs-lookup"><span data-stu-id="f2960-113">By default, this property is set to `true`.</span></span> <span data-ttu-id="f2960-114">Daha fazla bilgi için bkz. [Embeddedresourceusebağımlıtuponconvention](../project-sdk/msbuild-props.md#embeddedresourceusedependentuponconvention).</span><span class="sxs-lookup"><span data-stu-id="f2960-114">For more information, see [EmbeddedResourceUseDependentUponConvention](../project-sdk/msbuild-props.md#embeddedresourceusedependentuponconvention).</span></span>

<span data-ttu-id="f2960-115">Kaynak dosyası aynı kök dosya adının bir kaynak dosyası (*. cs* veya *. vb*) ile birlikte bulunuyorsa, bildirim dosyası adı için kaynak dosyada tanımlanan ilk türün tam adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f2960-115">If the resource file is colocated with a source file (*.cs* or *.vb*) of the same root file name, the full name of the first type that's defined in the source file is used for the manifest file name.</span></span> <span data-ttu-id="f2960-116">Örneğin, `MyNamespace.Form1` *Form1.cs*içinde tanımlanan ilk tür ve *Form1.cs* *Form1. resx*ile birlikte bulunuyorsa, bu kaynak dosyası için oluşturulan bildirim adı *MyNamespace. Form1. resources*olur.</span><span class="sxs-lookup"><span data-stu-id="f2960-116">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, and *Form1.cs* is colocated with *Form1.resx*, the generated manifest name for that resource file is *MyNamespace.Form1.resources*.</span></span>

## <a name="logicalname-metadata"></a><span data-ttu-id="f2960-117">LogicalName meta verileri</span><span class="sxs-lookup"><span data-stu-id="f2960-117">LogicalName metadata</span></span>

<span data-ttu-id="f2960-118">Bir kaynak dosyası, meta veri içeren bir öğe olarak proje dosyasına açıkça dahil edilip, bu `EmbeddedResource` `LogicalName` `LogicalName` değer bildirim adı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f2960-118">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `LogicalName` metadata, the `LogicalName` value is used as the manifest name.</span></span> <span data-ttu-id="f2960-119">`LogicalName`diğer meta veriler veya ayarlardan önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="f2960-119">`LogicalName` takes precedence over any other metadata or setting.</span></span>

<span data-ttu-id="f2960-120">Örneğin, aşağıdaki proje dosyası kod parçacığında tanımlanan kaynak dosyasının bildirim adı *someName. resources*olur.</span><span class="sxs-lookup"><span data-stu-id="f2960-120">For example, the manifest name for the resource file that's defined in the following project file snippet is *SomeName.resources*.</span></span>

```xml
<EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
```

<span data-ttu-id="f2960-121">-veya-</span><span class="sxs-lookup"><span data-stu-id="f2960-121">-or-</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
```

## <a name="manifestresourcename-metadata"></a><span data-ttu-id="f2960-122">ManifestResourceName meta verileri</span><span class="sxs-lookup"><span data-stu-id="f2960-122">ManifestResourceName metadata</span></span>

<span data-ttu-id="f2960-123">Bir kaynak dosyası, meta veri içeren bir öğe olarak proje dosyasına açıkça dahil edilirse `EmbeddedResource` `ManifestResourceName` (ve `LogicalName` yoksa), `ManifestResourceName` dosya uzantısıyla birleştirilmiş değeri, bildirim dosyası adı olarak *.resources*kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f2960-123">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `ManifestResourceName` metadata (and `LogicalName` is absent), the `ManifestResourceName` value, combined with the file extension *.resources*, is used as the manifest file name.</span></span>

<span data-ttu-id="f2960-124">Örneğin, aşağıdaki proje dosyası kod parçacığında tanımlanan kaynak dosyasının bildirim adı *someName. resources*olur.</span><span class="sxs-lookup"><span data-stu-id="f2960-124">For example, the manifest name for the resource file that's defined in the following project file snippet is *SomeName.resources*.</span></span>

```xml
<EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
```

<span data-ttu-id="f2960-125">Aşağıdaki proje dosyası kod parçacığında tanımlanan kaynak dosyasının bildirim adı *someName.fr-fr. resources*' dir.</span><span class="sxs-lookup"><span data-stu-id="f2960-125">The manifest name for the resource file that's defined in the following project file snippet is *SomeName.fr-FR.resources*.</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
```

## <a name="dependentupon-metadata"></a><span data-ttu-id="f2960-126">Meta veriler üzerinde Dependent</span><span class="sxs-lookup"><span data-stu-id="f2960-126">DependentUpon metadata</span></span>

<span data-ttu-id="f2960-127">Bir kaynak dosyası, meta veri içeren bir öğe olarak proje dosyasına açıkça dahil edilip `EmbeddedResource` `DependentUpon` (ve `LogicalName` `ManifestResourceName` yoksa), tarafından tanımlanan kaynak dosyadan alınan bilgiler `DependentUpon` kaynak bildirim dosyası adı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f2960-127">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `DependentUpon` metadata (and `LogicalName` and `ManifestResourceName` are absent), information from the source file defined by `DependentUpon` is used for the resource manifest file name.</span></span> <span data-ttu-id="f2960-128">Özellikle, kaynak dosyada tanımlanan ilk türün adı, bildirim adında şu şekilde kullanılır: *Namespace. ClassName \[ . Kültür]. resources*.</span><span class="sxs-lookup"><span data-stu-id="f2960-128">Specifically, the name of the first type that's defined in the source file is used in the manifest name as follows: *Namespace.Classname\[.Culture].resources*.</span></span>

<span data-ttu-id="f2960-129">Örneğin, aşağıdaki proje dosyası kod parçacığında tanımlanan kaynak dosyasının bildirim adı *Namespace. ClassName. resources* (burada `Namespace.Classname` *MyTypes.cs*içinde tanımlanan ilk sınıftır).</span><span class="sxs-lookup"><span data-stu-id="f2960-129">For example, the manifest name for the resource file that's defined in the following project file snippet is *Namespace.Classname.resources* (where `Namespace.Classname` is the first class that's defined in *MyTypes.cs*).</span></span>

```xml
<EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
```

<span data-ttu-id="f2960-130">Aşağıdaki proje dosyası kod parçacığında tanımlanan kaynak dosyasının bildirim adı *Namespace.ClassName.fr-fr. resources* olur (burada `Namespace.Classname` , *MyTypes.cs*içinde tanımlanan ilk sınıftır).</span><span class="sxs-lookup"><span data-stu-id="f2960-130">The manifest name for the resource file that's defined in the following project file snippet is *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the first class that's defined in *MyTypes.cs*).</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
```

## <a name="embeddedresourceusedependentuponconvention-property"></a><span data-ttu-id="f2960-131">Embeddedresourceusebağımlıtuponconvention özelliği</span><span class="sxs-lookup"><span data-stu-id="f2960-131">EmbeddedResourceUseDependentUponConvention property</span></span>

<span data-ttu-id="f2960-132">, `EmbeddedResourceUseDependentUponConvention` `false` Proje dosyasında olarak ayarlandıysa, her kaynak bildirimi dosya adı proje için kök ad alanını ve proje kökünden *. resx* dosyasına göreli yolu temel alan olur.</span><span class="sxs-lookup"><span data-stu-id="f2960-132">If `EmbeddedResourceUseDependentUponConvention` is set to `false` in the project file, each resource manifest file name is based off the root namespace for the project and the relative path from the project root to the *.resx* file.</span></span> <span data-ttu-id="f2960-133">Daha belirgin olarak, oluşturulan kaynak bildirim dosyası adı *RootNamespace. Relativepathwithdotsforeğik çizgileri olur. \[ Kültür.] kaynaklar*.</span><span class="sxs-lookup"><span data-stu-id="f2960-133">More specifically, the generated resource manifest file name is *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources*.</span></span> <span data-ttu-id="f2960-134">Bu Ayrıca, 3,0 ' dan önceki .NET Core sürümlerinde bildirim adları oluşturmak için kullanılan mantığdır.</span><span class="sxs-lookup"><span data-stu-id="f2960-134">This is also the logic used to generate manifest names in .NET Core versions prior to 3.0.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="f2960-135">`RootNamespace`Tanımlı değilse, varsayılan olarak proje adı olur.</span><span class="sxs-lookup"><span data-stu-id="f2960-135">If `RootNamespace` is not defined, it defaults to the project name.</span></span>
> - <span data-ttu-id="f2960-136">Eğer `LogicalName` , `ManifestResourceName` veya `DependentUpon` meta veriler `EmbeddedResource` Proje dosyasındaki bir öğe için belirtilmişse, bu adlandırma kuralı bu kaynak dosyasına uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="f2960-136">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item in the project file, this naming rule does not apply to that resource file.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2960-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2960-137">See also</span></span>

- [<span data-ttu-id="f2960-138">Bildirim kaynak adlandırması nasıl kullanılır?</span><span class="sxs-lookup"><span data-stu-id="f2960-138">How Manifest Resource Naming Works</span></span>](https://gist.github.com/BenVillalobos/041673b9a73bec60fdc3bf0f86fae62a)
- [<span data-ttu-id="f2960-139">.NET Core SDK projeleri için MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="f2960-139">MSBuild properties for .NET Core SDK projects</span></span>](../project-sdk/msbuild-props.md)
- [<span data-ttu-id="f2960-140">MSBuild kırılmaya yönelik değişiklikler</span><span class="sxs-lookup"><span data-stu-id="f2960-140">MSBuild breaking changes</span></span>](../compatibility/msbuild.md)
