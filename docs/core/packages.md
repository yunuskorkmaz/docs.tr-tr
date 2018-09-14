---
title: Paketler, meta paketler ve çerçeveler
description: Paketler, meta paketler ve çerçeveler için terimler öğrenin.
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: e68c63d26133ac76b718bb3696d16c81bd943dc2
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519961"
---
# <a name="packages-metapackages-and-frameworks"></a>Paketler, meta paketler ve çerçeveler

.NET core NuGet paketlerini yapılan bir platformdur. Bazı ürün paketlerden diğerlerinin parçalı ayrıntılı tanımını avantajından karşılaşır. Bu duality uyum sağlamak için ürün paketleri ayrıntılı bir dizi dağıtılır ve sonra basit bir "metapackage" adlı bir paket türü ile kaba öbekler halinde açıklanmıştır.

Her bir .NET Core paketleri çerçeveler temsil edilen birden çok .NET uygulamaları üzerinde çalıştırılmasını destekler. Bu çerçeveler geleneksel çerçeveleri gibi bazıları `net46`, .NET Framework temsil eden. Başka bir kümesi, "hangi çerçeveleri tanımlamak için yeni bir model oluşturmak paket tabanlı altyapılarını" olarak düşünülebilir yeni çerçeveleri kümesidir. Bu paket tabanlı çerçeveler tamamen biçimlendirilmiş ve paketler ve çerçeveler arasında güçlü bir ilişki oluşturan paketleri olarak tanımlanır.

## <a name="packages"></a>Paketler

.NET core temelleri, üst düzey veri türleri, uygulama oluşturma türleri ve genel yardımdı gereksinimleri sağlayan paketleri kümesine ayrılır. Bu paketlerin her aynı ada sahip tek bir derleme temsil eder. Örneğin, [System.Runtime](https://www.nuget.org/packages/System.Runtime) System.Runtime.dll içerir. 

Ayrıntılı bir şekilde paketleri tanımlama avantajları vardır:

- Ayrıntılı paketleri oldukça sınırlı diğer paketleri test ile kendi zamanlamalarında sevk edebilir.
- Ayrıntılı paketleri farklı işletim sistemi ve CPU desteği sağlar.
- Ayrıntılı paketler yalnızca bir kitaplığa belirli bağımlılıkları olabilir.
- Uygulamaları daha küçük olduğu başvurulmayan paketleri uygulama dağıtımı bir parçası haline yok.

Bazı avantajlar, yalnızca belirli durumlarda kullanılır. Örneğin, NET Core paketleri genellikle aynı platformu desteğine sahip aynı zamanlamaya sevk edilir. Bakım söz konusu olduğunda, düzeltmeleri dağıtılabilen ve yüklü küçük tek bir paket güncelleştirmeleri. Dar değişiklik nedeniyle, bir düzeltme kullanılabilir hale getirmek için saat ve doğrulama kapsamındaysa tek bir kitaplık için gereken için sınırlı.

.NET Core için anahtar NuGet paketlerinin bir listesi verilmiştir:

- [System.Runtime](https://www.nuget.org/packages/System.Runtime) -en temel .NET Core paketi dahil olmak üzere <xref:System.Object>, <xref:System.String>, <xref:System.Array>, <xref:System.Action>, ve <xref:System.Collections.Generic.IList%601>.
- [System.Collections](https://www.nuget.org/packages/System.Collections) -dahil olmak üzere (birincil) genel koleksiyonları kümesi <xref:System.Collections.Generic.List%601> ve <xref:System.Collections.Generic.Dictionary%602>.
- [System.Net.Http](https://www.nuget.org/packages/System.Net.Http) -bir HTTP ağ iletişimi türleri dahil olmak üzere <xref:System.Net.Http.HttpClient> ve <xref:System.Net.Http.HttpResponseMessage>.
- [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) -yerel veya ağa bağlı disk tabanlı depolama alanına, yazma ve okuma için türleri kümesi dahil olmak üzere <xref:System.IO.File> ve <xref:System.IO.Directory>.
- [System.Linq](https://www.nuget.org/packages/System.Linq) -türleri dahil olmak üzere nesneleri sorgulamak için bir dizi `Enumerable` ve <xref:System.Linq.ILookup%602>.
- [System.Reflection](https://www.nuget.org/packages/System.Reflection) -yükleme, inceleme ve türleri dahil olmak üzere, etkinleştirme türleri kümesi <xref:System.Reflection.Assembly>, <xref:System.Reflection.TypeInfo> ve <xref:System.Reflection.MethodInfo>.

Genellikle, projelerinizde paketini tarafından temelinde paketleri dahil yerine, dahil etmek çok daha kolay olduğu bir *metapackage*, kümesine paketlerin genellikle birlikte kullanılır. (Aşağıdaki bölümde meta paketler hakkında daha fazla bilgi için bkz.) Tek bir paket gerektiğinde, ancak bunu başvuran aşağıdaki örnekte olduğu gibi ekleyebilirsiniz [System.Runtime](https://www.nuget.org/packages/System.Runtime/) paket. 

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

## <a name="metapackages"></a>Meta paketler

Meta paketler birlikte anlamlı olan paketleri bir kümesini tanımlamak için bir NuGet paketi kuralı var. Bunlar, bu paketler kümesi bağımlılıkların hale getirerek temsil eder. Bir çerçeve belirterek bunların paketlerini bu dizi için bir çerçeve isteğe bağlı olarak oluşturabilirsiniz. 

Önceki sürümlerinde varsayılan olarak .NET Core Araçları (project.json ve csproj tabanlı araçlar), bir çerçeve ve bir metapackage ikisi de belirtilmiş. Böylece her metapackage bağlı bir hedef çerçeve için şu anda, ancak metapackage örtük olarak hedef framework tarafından başvuruluyor. Örneğin, `netstandard1.6` framework NetStandard.Library sürüm 1.6.0 metapackage başvuruyor. Benzer şekilde, `netcoreapp2.1` framework Microsoft.NETCore.App sürüm 2.1.0 metapackage başvuruyor. Daha fazla bilgi için [örtük metapackage paket başvurusu .NET Core SDK'sındaki](https://github.com/dotnet/core/blob/master/release-notes/1.0/sdk/1.0-rc3-implicit-package-refs.md).

Çerçeve hedefleme ve örtük olarak bir metapackage başvuru tek bir hareket geçerli bir başvuru, bağımlı paketlerin her ekliyoruz anlamına gelir. Tüm kitaplıkları bu paketlerde IntelliSense (veya benzer bir deneyim) ve uygulamanızı yayımlamak için kullanılabilmesini sağlar.  

Meta paketler kullanmanın avantajları şunlardır:

- Çok sayıda hassas paketleri başvurmak için uygun kullanıcı deneyimi sağlar. 
- Sınanır ve birlikte düzgün çalışacak (belirli sürümleri dahil) paketleri kümesini tanımlar.

.NET Standard metapackage aşağıdaki gibidir:

- [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) -".NET Standard" parçası olan kitaplıkları açıklar. .NET Standard'ı destekleyen tüm .NET uygulamaları için (örneğin, .NET Framework, .NET Core ve Mono) uygular. 'Netstandard' çerçeve oluşturur.

Anahtar .NET Core meta paketler şunlardır:

- [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) -.NET Core dağıtımı parçası olan kitaplıkları açıklar. Kurar [ `.NETCoreApp` framework](https://github.com/dotnet/core-setup/blob/release/1.1.0/pkg/projects/Microsoft.NETCore.App/Microsoft.NETCore.App.pkgproj). Bağlı küçük üzerinde `NETStandard.Library`.
- [Microsoft.AspNetCore.All](https://www.nuget.org/packages/Microsoft.AspNetCore.All) -ASP.NET Core, Entity Framework Core ve ASP.NET Core ve Entity Framework Core tarafından kullanılan iç ve üçüncü taraf bağımlılıkları desteklenen tüm paketleri içerir. Bkz: [Microsoft.AspNetCore.All metapackage ASP.NET Core 2.x](/aspnet/core/fundamentals/metapackage) daha fazla bilgi için.
- [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) -mscorlib tabanlı taşınabilir sınıf kitaplıkları (.NET Core üzerinde çalıştırılacak PCLs) olanak tanıyan uyumluluk cepheleri kümesi.

## <a name="frameworks"></a>Çerçeveler

.NET core paketleri, çalışma zamanı çerçeveleri bir kümesini destekler. Çerçeveleri tanımlamak için kullanılabilir bir API kümesi (ve olasılıkla diğer özelliklerini) belirli bir çerçeve hedeflediğinizde üzerinde güvenebilirsiniz. Bunlar, yeni API'ler eklendikçe tutulur.

Örneğin, [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) aşağıdaki çerçevelerini destekler:

- . NETFramework, sürüm = 4.6
- . NETStandard, sürüm = 1,3
- 6 Xamarin platformları (örneğin, xamarinios10)

Bu çerçeveler ilk iki çerçeveleri tanımlanan iki farklı şekilde örnekleridir bu yana karşılaştırın kullanışlıdır.

`.NETFramework,Version=4.6` Framework, .NET Framework 4.6 API'leri temsil eder. .NET Framework 4.6 başvuru bütünleştirilmiş kodları ile derlenmiş kitaplıkları oluşturmak ve bu kitaplıkları NuGet paketlerinde net46 LIB klasöründeki dağıtın. .NET Framework 4.6 hedef veya onunla uyumlu olmayan uygulamalar için kullanılır. Bu, tüm çerçeveleri geleneksel hakkında deneyimli olduğunuzu nasıl.

`.NETStandard,Version=1.3` Bir paket tabanlı çerçeve bir çerçevedir. Tanımlamak ve API'leri çerçevesine bağlı olarak kullanıma sunmak için Framework'ü hedefleyen paketler kullanır.

## <a name="package-based-frameworks"></a>Paket tabanlı çerçeveleri

Çerçeveler ve paketler arasında iki yönlü bir ilişki yoktur. İlk bölümü örneğin belirtilen bir çerçeve için mevcut API'lere tanımlama `netstandard1.3`. Hedefleyen paketler `netstandard1.3` (veya uyumlu çerçeveleri `netstandard1.0`) tanımlamak için mevcut API'lere `netstandard1.3`. Döngüsel başvuru gibi görünebilir, ancak bu değildir. "Paket tabanlı" olmasının da, API tanımı Framework paketleri gelir. Framework, tüm API tanımlamıyor.

İlişki ikinci bölümü, varlık seçimdir. Paketler, birden çok çerçeve varlıklar içerebilir. Paketler ve/veya meta paketler kümesine başvuru göz önünde bulundurulduğunda, framework varlık, örneğin seçilmelidir belirlemek için gerekli `net46` veya `netstandard1.3`. Doğru varlık seçilmesi gerekir. Örneğin, bir `net46` varlık büyük olasılıkla .NET Framework 4.0 veya .NET Core 1.0 ile uyumlu değil.


Aşağıdaki görüntüde bu ilişkileri görebilirsiniz. *API* hedefler ve tanımlar *framework*. *Framework* için kullanılan *varlık seçimi*. *Varlık* API sağlar.

![Paket tabanlı çerçeve oluşturma](./media/packages/package-framework.png)

.NET Core ile kullanılan iki birincil paket tabanlı çerçeveler şunlardır:

- `netstandard`
- `netcoreapp`

### <a name="net-standard"></a>.NET standard

.NET Standard (hedef çerçeve adı: `netstandard`) çerçevesini temsil eder, API tarafından tanımlanan ve üst kısmındaki yerleşik [.NET Standard](../standard/net-standard.md). Bu çerçeve, birden çok çalışma zamanları üzerinde çalışması amaçlanmıştır kitaplıkları hedeflemelidir. Tüm .NET Standard uyumlu çalışma zamanı üzerinde .NET Core, .NET Framework ve Mono/Xamarin gibi desteklenecektir. Bu çalışma zamanları her bir dizi uyguladıkları bağlı olarak hangi API'ler, .NET Standard sürümleri destekler.

`netstandard` Framework örtülü olarak başvuran [ `NETStandard.Library` ](https://www.nuget.org/packages/NETStandard.Library) metapackage. Örneğin, aşağıdaki MSBuild proje dosyası belirten Proje hedefleri `netstandard1.6`, hangi başvurular [ `NETStandard.Library` sürüm 1.6](https://www.nuget.org/packages/NETStandard.Library/1.6.0) metapackage.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
</Project>
```

Ancak, proje dosyasında çerçeve ve metapackage başvuruları eşleşmesi gerekmez ve kullanabileceğiniz `<NetStandardImplicitPackageVersion>` metapackage sürümünden daha düşük bir framework sürümüne belirtmek için proje dosyanızdaki öğesi. Örneğin, aşağıdaki proje dosyası geçerli değil.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

Hedef garip görünebilir `netstandard1.3` ancak sürümünü kullanın 1.6.0 `NETStandard.Library`. Desteği metapackage tutar, olduğu bir geçerli kullanım örneği, eski `netstandard` sürümleri. 1.6.0 standartlaşmış durum olabilir metapackage sürümünü ve çeşitli hedefleyen tüm Kitaplıklarınızı için kullanılmakta `netstandard` sürümleri. Bu yaklaşımda, yalnızca geri yüklemeniz gereken `NETStandard.Library` 1.6.0 ve değil önceki sürümleri. 

Tersi geçerli olmaz: hedefleyen `netstandard1.6` 1.3.0 ile sürümünü `NETStandard.Library`. Alt sürüm metapackage, daha yüksek çerçevesi için tüm varlıkları açığa çıkarmamak olduğundan daha düşük bir metapackage ile daha yüksek bir çerçeve hedefleyemez. Sürüm oluşturma düzeni için meta paketler, meta paketler tanımladıkları framework'ün en yüksek sürümü eşleştiğini onaylar. Sürüm oluşturma düzeni, ilk sürümü da `NETStandard.Library` içerdiği düşünüldüğünde v1.6.0 olduğundan `netstandard1.6` varlıklar. V1.3.0 Simetri Yukarıdaki örnek için yukarıdaki örnekte kullanılan, ancak gerçekte yok.

### <a name="net-core-application"></a>.NET core uygulaması

.NET Core uygulaması (TFM: `netcoreapp`) framework paketleri ve .NET Core dağıtımı ve sağladığı konsol uygulama modeli ile ilişkili API'ler temsil eder. .NET core uygulamaları, yalnızca .NET Core üzerinde çalışma üzere tasarlanan kitaplıkları gibi konsol uygulama modeli, hedefleme nedeniyle bu çerçeve kullanmanız gerekir. Bu çerçevesini kullanarak uygulamalar ve kitaplıklar yalnızca .NET Core üzerinde çalıştırmayla kısıtlar. 

`Microsoft.NETCore.App` Metapackage hedefleri `netcoreapp` framework. Yaklaşık 60 kitaplıkları, yaklaşık 40 tarafından sağlanan erişim sağlayan `NETStandard.Library` paket ve yaklaşık 20 daha fazla giriş toplama. Ek kitaplıklar hedefleyen başvurabilirsiniz `netcoreapp` veya uyumlu çerçeveleri gibi `netstandard`, erişmek için ek API'ler. 

Tarafından sağlanan ek kitaplıklar çoğu `Microsoft.NETCore.App` de hedef `netstandard` bağımlılıklarını diğer tarafından karşılandığından emin düşünüldüğünde `netstandard` kitaplıkları. Bu anlamına `netstandard` kitaplıkları, bağımlılık olarak bu paketleri de başvurabilir. 
