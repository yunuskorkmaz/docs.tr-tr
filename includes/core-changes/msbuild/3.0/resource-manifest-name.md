---
ms.openlocfilehash: f24a29a00a1bff34a452c43716d76bf72ef277b5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206227"
---
### <a name="resource-manifest-file-name-change"></a>Kaynak bildirimi dosya adı değişikliği

.NET Core 3,0 ' den başlayarak, MSBuild varsayılan durumda kaynak dosyaları için farklı bir bildirim dosyası adı oluşturur.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 ' den önce `LogicalName` `ManifestResourceName` `DependentUpon` Proje dosyasındaki bir öğe için bir, veya meta veri belirtilmemişse, `EmbeddedResource` MSBuild, düzende bir bildirim dosyası adı oluşturdu `<RootNamespace>.<ResourceFilePathFromProjectRoot>.resources` . `RootNamespace`Proje dosyasında tanımlanmamışsa, varsayılan olarak proje adı olur. Örneğin, kök proje dizininde *Form1. resx* adlı bir kaynak dosyası için oluşturulan bildirim adı *Myprojem. Form1. resources*idi.

.NET Core 3,0 ' den itibaren, bir kaynak dosyası aynı ada sahip bir kaynak dosya (örneğin, *Form1. resx* ve *Form1.cs*) ile birlikte bulunuyorsa MSBuild, kaynak dosyasındaki tür bilgilerini kullanarak bildirim dosyası adını oluşturur `<Namespace>.<ClassName>.resources` . Ad alanı ve sınıf adı, birlikte bulunan kaynak dosyadaki ilk türden ayıklanır. Örneğin, *Form1.cs* adlı bir kaynak dosyayla birlikte bulunan *Form1. resx* adlı bir kaynak dosyası Için üretilen bildirim adı *MyNamespace. Form1. resources*' dir. Önemli şey, dosya adının ilk bölümünün .NET Core 'un önceki sürümleriyle ( *MyProject*yerine*MyNamespace* ) farklı olmasıdır.

> [!NOTE]
> `LogicalName` `ManifestResourceName` `DependentUpon` Proje dosyasındaki bir öğe üzerinde, veya meta veriler belirtilmişse, `EmbeddedResource` Bu değişiklik bu kaynak dosyasını etkilemez.

Bu son değişiklik, `EmbeddedResourceUseDependentUponConvention` özelliğin .NET Core projelerine eklenmesiyle birlikte sunulmuştur. Varsayılan olarak, kaynak dosyaları .NET Core proje dosyasında açık olarak listelenmez, bu nedenle `DependentUpon` oluşturulan *. resources* dosyasının adını belirtmek için meta verileri yoktur. , `EmbeddedResourceUseDependentUponConvention` `true` Varsayılan olan olarak ayarlandığında, MSBuild, birlikte bulunan bir kaynak dosyayı arar ve bu dosyadan bir ad alanı ve sınıf adı ayıklar. `EmbeddedResourceUseDependentUponConvention`Olarak ayarlarsanız `false` , MSBuild, bildirim adını, `RootNamespace` ve göreli dosya yolunu birleştiren önceki davranışa göre oluşturur.

#### <a name="recommended-action"></a>Önerilen eylem

Çoğu durumda, geliştiricinin bölümünde herhangi bir eylem gerekmez ve uygulamanız çalışmaya devam etmelidir. Ancak, bu değişiklik uygulamanızı kopararsa şunlardan birini yapabilirsiniz:

- Kodunuzu, yeni bildirim adını beklediği şekilde değiştirin.

- Yeni adlandırma kuralını, `EmbeddedResourceUseDependentUponConvention` proje dosyanızda olarak ayarlayarak geri çevirin `false` .

  ```xml
  <PropertyGroup>
    <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
  </PropertyGroup>
  ```

#### <a name="category"></a>Kategori

MSBuild

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok
