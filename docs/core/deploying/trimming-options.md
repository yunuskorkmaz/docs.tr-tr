---
title: Kırpma seçenekleri
description: Kendi içindeki uygulamaların kırpılacağını nasıl denetleyeceğinizi öğrenin.
author: sbomer
ms.author: svbomer
ms.date: 08/25/2020
ms.openlocfilehash: 5597d4cdb9e8e96dcec6545e039d43295ca991bd
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142264"
---
# <a name="trimming-options"></a>Kırpma seçenekleri

Aşağıdaki MSBuild özellikleri ve öğeleri, [kırpılan kendi içindeki dağıtımların](trim-self-contained.md)davranışını etkiler. Bir kısmı `ILLink` , kırpmayı uygulayan temel aracın adı olan bahsetme seçenekleridir. Komut satırı aracı hakkında daha fazla bilgi için `ILLink` [ıllink seçenekleri](https://github.com/mono/linker/blob/master/docs/illink-options.md)adresinde bulabilirsiniz.

## <a name="enable-trimming"></a>Kırpmayı etkinleştir

- `<PublishTrimmed>true</PublishTrimmed>`

   SDK tarafından tanımlanan varsayılan ayarlarla yayınlama sırasında kırpmayı etkinleştirin.

Kullanırken `Microsoft.NET.Sdk` , bu, netcoreapp çalışma zamanı paketinden çerçeve derlemelerinin derleme düzeyinde kırpmasını gerçekleştirir. Uygulama kodu ve Framework olmayan kitaplıklar kırpılmamış. Diğer SDK 'lar farklı varsayılanlar tanımlayabilir.

## <a name="trimming-granularity"></a>Parçalı yapısı kırpma

Aşağıdaki ayrıntı düzeyi ayarları, kullanılmamış olmayan Il 'nin nasıl atılma olduğunu denetler. Bu, bir özellik olarak veya [tek bir derlemede](#Trimmed-assemblies)meta veriler olarak ayarlanabilir.

- `<TrimMode>copyused</TrimMode>`

   Derleme düzeyinde kırpmasını etkinleştirin ve bu, herhangi bir bölümü (statik olarak anlaşılmış bir şekilde) kullanılırsa tüm bütünleştirilmiş kodu saklar.

- `<TrimMode>link</TrimMode>`

    Kullanılmayan üyeleri türlerden kaldıran üye düzeyinde kırpmayı etkinleştirin.

`<IsTrimmable>true</IsTrimmable>`Meta veri içeren derlemeler, ancak açık olmaz `TrimMode` Global kullanır `TrimMode` . İçin varsayılandır `TrimMode` `Microsoft.NET.Sdk` `copyused` .

## <a name="trimmed-assemblies"></a>Kırpılan derlemeler

Kırpılan bir uygulamayı yayımlarken, SDK, `ItemGroup` `ManagedAssemblyToLink` kırpma için işlenecek dosya kümesini temsil eden bir çağrılan öğesini hesaplar. `ManagedAssemblyToLink` derleme başına kırpma davranışını denetleyen meta verilere sahip olabilir. Bu meta verileri ayarlamak için, yerleşik hedeften önce çalışan bir hedef oluşturun `PrepareForILLink` . Bu örnek, kırpılacağını nasıl etkinleştireceğinizi göstermektedir `MyAssembly` :

```xml
<Target Name="ConfigureTrimming"
        BeforeTargets="PrepareForILLink">
  <ItemGroup>
    <ManagedAssemblyToLink Condition="'%(Filename)' == 'MyAssembly'">
      <IsTrimmable>true</IsTrimmable>
    </ManagedAssemblyToLink>
  </ItemGroup>
</Target>
```

`ManagedAssemblyToLink`SDK bu kümeyi yayımlama sırasında hesapladığı ve değişmemelidir beklediği için öğe ekleme veya kaldırma. Desteklenen meta veriler şunlardır:

- `<IsTrimmable>true</IsTrimmable>`

  Verilen derlemenin kırpılmadığını denetleyin.

- `<TrimMode>copyused</TrimMode>` veya `<TrimMode>link</TrimMode>`

  Bu derlemenin [kırpma parçalı yapısını](#Trimming-granularity) denetleyin. Bu genel olarak önceliklidir `TrimMode` . `TrimMode`Bir derlemenin ayarlanması, ' i belirtir `<IsTrimmable>true</IsTrimmable>` .

## <a name="root-assemblies"></a>Kök derlemeler

Olmayan tüm derlemeler `<IsTrimmable>true</IsTrimmable>` analize yönelik kökleri olarak kabul edilir, bu da bunların ve statik olarak anladıkları bağımlılıkların tutulduğu anlamına gelir. Ek derlemeler ada göre "kökü belirtilmiş" olabilir (uzantı olmadan `.dll` ):

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="MyAssembly" />
</ItemGroup>
```

## <a name="root-descriptors"></a>Kök tanımlayıcıları

Analize yönelik kökleri belirtmenin başka bir yolu, bağlayıcı [tanımlayıcı biçimini](https://github.com/mono/linker/blob/master/docs/data-formats.md#descriptor-format)kullanan bir XML dosyası kullanmaktır. Bu, tüm derleme yerine belirli üyeleri köklemenizi sağlar.

```xml
<ItemGroup>
  <TrimmerRootDescriptor Include="MyRoots.xml" />
</ItemGroup>
```

Örneğin, `MyRoots.xml` uygulama tarafından dinamik olarak erişilen belirli bir yöntemi kökleyebilir:

```xml
<linker>
  <assembly fullname="MyAssembly">
    <type fullname="MyAssembly.MyClass">
      <method name="DynamicallyAccessedMethod" />
    </type>
  </assembly>
</linker>
```

## <a name="analysis-warnings"></a>Analiz uyarıları

Kırpma statik olarak erişilebilen Il 'yi kaldırır. Yansıma veya dinamik bağımlılıklar oluşturan diğer desenleri kullanan uygulamalar, kırparak kırılabilir. Bu tür desenler hakkında uyarı almak için:

- `<SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>`

    Kırpma Analizi uyarılarını etkinleştirin.

Bu, kendi kodunuz, kitaplık kodu ve çerçeve kodunuz da dahil olmak üzere tüm uygulama hakkındaki uyarıları içerir.

## <a name="warning-versions"></a>Uyarı sürümleri

Kırpma analizi, [`AnalysisLevel`](../project-sdk/msbuild-props.md#AnalysisLevel) SDK genelinde analiz uyarıları sürümünü denetleyen özelliği uyar. Kırpma Analizi uyarılarının sürümünü bağımsız olarak denetleyen başka bir özellik vardır (derleyiciye benzer şekilde `WarningLevel` ):

- `<ILLinkWarningLevel>5</ILLinkWarningLevel>`

    Yalnızca verilen düzeyin veya daha düşük olan uyarıları yay. Bu, `9999` tüm uyarı sürümlerinin dahil olması olabilir.

## <a name="suppressing-warnings"></a>Gizleme uyarıları

Tek [uyarı kodları](https://github.com/mono/linker/blob/master/docs/error-codes.md#warning-codes) ,,, ve dahil olmak üzere araç zinciri tarafından kullanılan olağan MSBuild özellikleri kullanılarak `NoWarn` gizlenebilir `WarningsAsErrors` `WarningsNotAsErrors` `TreatWarningsAsErrors` . Illınk hata durumu davranışını bağımsız olarak denetleyen ek bir seçenek vardır:

- `<ILLinkTreatWarningsAsErrors>false</ILLinkTreatWarningsAsErrors>`

    Illınk uyarılarını hata olarak değerlendirin. Bu durum, derleyici uyarılarını hata olarak bir genel olarak düşünerek uyarı çözümleme uyarılarını hatalara karşı açıp çözmemek için yararlı olabilir.

## <a name="removing-symbols"></a>Sembolleri kaldırma

Simgeler normalde kırpılan Derlemelerle eşleşecek şekilde kırpılacak. Tüm sembolleri de kaldırabilirsiniz:

- `<TrimmerRemoveSymbols>true</TrimmerRemoveSymbols>`

    Katıştırılmış pdb 'leri ve ayrı PDB dosyaları dahil olmak üzere kırpılan uygulamadan sembolleri kaldırın. Bu hem uygulama kodu hem de simgelerle gelen bağımlılıklar için geçerlidir.

SDK, özelliği kullanarak hata ayıklayıcı desteğini devre dışı bırakmayı da mümkün kılar `DebuggerSupport` . Hata ayıklayıcı desteği devre dışı bırakıldığında, kırpma sembolleri otomatik olarak kaldırır ( `TrimmerRemoveSymbols` Varsayılan olarak true olur).
