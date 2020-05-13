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
# <a name="how-resource-manifest-files-are-named"></a>Kaynak bildirim dosyaları nasıl adlandırılır

MSBuild bir .NET Core projesi derlediğinde, *. resx* dosya UZANTıSıNA sahip XML kaynak dosyaları ikili *. resources* dosyalarına dönüştürülür. İkili dosyalar derleyicinin çıktısına katıştırılır ve tarafından okunabilir <xref:System.Resources.ResourceManager> . Bu makalede, MSBuild 'in her *. resources* dosyası için bir ad nasıl seçtiği açıklanır.

> [!TIP]
> Proje dosyanıza açıkça bir kaynak öğesi eklerseniz ve bu, [.NET Core için varsayılan içerme genelleştirmeler dahil edilmiştir](../project-sdk/overview.md#default-compilation-includes), bir derleme hatası alırsınız. Kaynak dosyalarını öğe olarak el ile eklemek için `EmbeddedResource` , `EnableDefaultEmbeddedResourceItems` özelliğini false olarak ayarlayın.

## <a name="default-name"></a>Varsayılan ad

.NET Core 3,0 ve üzeri sürümlerde, aşağıdaki koşulların her ikisi de karşılandığında bir kaynak bildirimi için varsayılan ad kullanılır:

- Kaynak dosyası proje dosyasına `EmbeddedResource` `LogicalName` ,, `ManifestResourceName` veya meta verileri içeren bir öğe olarak açıkça dahil edilmez `DependentUpon` .
- `EmbeddedResourceUseDependentUponConvention`Özelliği `false` Proje dosyasında olarak ayarlanmamış. Varsayılan olarak, bu özellik olarak ayarlanır `true` . Daha fazla bilgi için bkz. [Embeddedresourceusebağımlıtuponconvention](../project-sdk/msbuild-props.md#embeddedresourceusedependentuponconvention).

Kaynak dosyası aynı kök dosya adının bir kaynak dosyası (*. cs* veya *. vb*) ile birlikte bulunuyorsa, bildirim dosyası adı için kaynak dosyada tanımlanan ilk türün tam adı kullanılır. Örneğin, `MyNamespace.Form1` *Form1.cs*içinde tanımlanan ilk tür ve *Form1.cs* *Form1. resx*ile birlikte bulunuyorsa, bu kaynak dosyası için oluşturulan bildirim adı *MyNamespace. Form1. resources*olur.

## <a name="logicalname-metadata"></a>LogicalName meta verileri

Bir kaynak dosyası, meta veri içeren bir öğe olarak proje dosyasına açıkça dahil edilip, bu `EmbeddedResource` `LogicalName` `LogicalName` değer bildirim adı olarak kullanılır. `LogicalName`diğer meta veriler veya ayarlardan önceliklidir.

Örneğin, aşağıdaki proje dosyası kod parçacığında tanımlanan kaynak dosyasının bildirim adı *someName. resources*olur.

```xml
<EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
```

-veya-

```xml
<EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
```

## <a name="manifestresourcename-metadata"></a>ManifestResourceName meta verileri

Bir kaynak dosyası, meta veri içeren bir öğe olarak proje dosyasına açıkça dahil edilirse `EmbeddedResource` `ManifestResourceName` (ve `LogicalName` yoksa), `ManifestResourceName` dosya uzantısıyla birleştirilmiş değeri, bildirim dosyası adı olarak *.resources*kullanılır.

Örneğin, aşağıdaki proje dosyası kod parçacığında tanımlanan kaynak dosyasının bildirim adı *someName. resources*olur.

```xml
<EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
```

Aşağıdaki proje dosyası kod parçacığında tanımlanan kaynak dosyasının bildirim adı *someName.fr-fr. resources*' dir.

```xml
<EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
```

## <a name="dependentupon-metadata"></a>Meta veriler üzerinde Dependent

Bir kaynak dosyası, meta veri içeren bir öğe olarak proje dosyasına açıkça dahil edilip `EmbeddedResource` `DependentUpon` (ve `LogicalName` `ManifestResourceName` yoksa), tarafından tanımlanan kaynak dosyadan alınan bilgiler `DependentUpon` kaynak bildirim dosyası adı için kullanılır. Özellikle, kaynak dosyada tanımlanan ilk türün adı, bildirim adında şu şekilde kullanılır: *Namespace. ClassName \[ . Kültür]. resources*.

Örneğin, aşağıdaki proje dosyası kod parçacığında tanımlanan kaynak dosyasının bildirim adı *Namespace. ClassName. resources* (burada `Namespace.Classname` *MyTypes.cs*içinde tanımlanan ilk sınıftır).

```xml
<EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
```

Aşağıdaki proje dosyası kod parçacığında tanımlanan kaynak dosyasının bildirim adı *Namespace.ClassName.fr-fr. resources* olur (burada `Namespace.Classname` , *MyTypes.cs*içinde tanımlanan ilk sınıftır).

```xml
<EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
```

## <a name="embeddedresourceusedependentuponconvention-property"></a>Embeddedresourceusebağımlıtuponconvention özelliği

, `EmbeddedResourceUseDependentUponConvention` `false` Proje dosyasında olarak ayarlandıysa, her kaynak bildirimi dosya adı proje için kök ad alanını ve proje kökünden *. resx* dosyasına göreli yolu temel alan olur. Daha belirgin olarak, oluşturulan kaynak bildirim dosyası adı *RootNamespace. Relativepathwithdotsforeğik çizgileri olur. \[ Kültür.] kaynaklar*. Bu Ayrıca, 3,0 ' dan önceki .NET Core sürümlerinde bildirim adları oluşturmak için kullanılan mantığdır.

> [!NOTE]
>
> - `RootNamespace`Tanımlı değilse, varsayılan olarak proje adı olur.
> - Eğer `LogicalName` , `ManifestResourceName` veya `DependentUpon` meta veriler `EmbeddedResource` Proje dosyasındaki bir öğe için belirtilmişse, bu adlandırma kuralı bu kaynak dosyasına uygulanmaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Bildirim kaynak adlandırması nasıl kullanılır?](https://gist.github.com/BenVillalobos/041673b9a73bec60fdc3bf0f86fae62a)
- [.NET Core SDK projeleri için MSBuild özellikleri](../project-sdk/msbuild-props.md)
- [MSBuild kırılmaya yönelik değişiklikler](../compatibility/msbuild.md)
