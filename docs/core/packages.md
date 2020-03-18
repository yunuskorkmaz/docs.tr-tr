---
title: Paketler, meta paketler ve çerçeveler - .NET Core
description: Paketler, meta paketler ve çerçeveler için terminolojiyi öğrenin.
author: richlander
ms.date: 06/20/2016
ms.openlocfilehash: 657519edf1c0860ee3222c71ce85723e19029a9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398981"
---
# <a name="packages-metapackages-and-frameworks"></a>Paketler, meta paketler ve çerçeveler

.NET Core, NuGet paketlerinden oluşan bir platformdur. Bazı ürün deneyimleri paketlerin ince taneli tanımından yararlanırken, diğerleri kaba taneli paketlerden yararlanır. Bu ikiliği karşılamak için,.NET Core, gayrı resmi olarak [meta paket](#metapackages)olarak adlandırılan bir paket türüne sahip, ince taneli bir paket kümesi ve daha kaba parçalar halinde dağıtılır.

.NET Core paketlerinin her biri, çerçeve olarak temsil edilen birden çok .NET uygulamasında çalıştırılmanı destekler. Bu çerçevelerden bazıları ,.NET `net46`Framework'ü temsil eden geleneksel çerçevelerdir. Bir diğer küme de, çerçeveleri tanımlamak için yeni bir model oluşturan "paket tabanlı çerçeveler" olarak düşünülebilecek yeni çerçevelerdir. Bu paket tabanlı çerçeveler tamamen oluşturulur ve paketler olarak tanımlanır ve paketler ve çerçeveler arasında güçlü bir ilişki oluşturur.

## <a name="packages"></a>Paketler

.NET Core, ilkel, üst düzey veri türleri, uygulama kompozisyonu türleri ve ortak yardımcı programlar sağlayan bir paket kümesine ayrılmıştır. Bu paketlerin her biri aynı adı taşıyan tek bir derlemeyi temsil eder. Örneğin, [System.Runtime paketi](https://www.nuget.org/packages/System.Runtime) System.Runtime.dll içerir.

Paketleri ince taneli bir şekilde tanımlamanın avantajları vardır:

- İnce taneli paketler, diğer paketlerin nispeten sınırlı test ile kendi programlarına göre sevk edebilirsiniz.
- İnce taneli paketler farklı işletim sistemi ve CPU desteği sağlayabilir.
- İnce taneli paketlerde yalnızca bir kitaplıközel bağımlılıklar olabilir.
- Başvurulmamış paketler uygulama dağıtımının bir parçası olmadığı için uygulamalar daha küçüktür.

Bu faydaların bazıları sadece belirli durumlarda kullanılır. Örneğin, NET Core paketleri genellikle aynı platform desteği ile aynı zamanlamaüzerinde sevk edilecektir. Servis durumunda, düzeltmeler küçük tek paket güncelleştirmeleri olarak dağıtılabilir ve yüklenebilir. Değişikliğin dar kapsamı nedeniyle, düzeltmeyi kullanılabilir hale getirmek için geçerlilik ve zaman, tek bir kitaplık için gerekenle sınırlıdır.

Aşağıda .NET Core için anahtar NuGet paketlerinin bir listesi vetir:

- [System.Runtime](https://www.nuget.org/packages/System.Runtime) - Dahil olmak üzere en <xref:System.Object>temel <xref:System.String> <xref:System.Array>.NET Core paketi, , , <xref:System.Action>, ve <xref:System.Collections.Generic.IList%601>.
- [System.Collections](https://www.nuget.org/packages/System.Collections) - Dahil olmak üzere <xref:System.Collections.Generic.List%601> (öncelikle) genel <xref:System.Collections.Generic.Dictionary%602>koleksiyonlar kümesi.
- [System.Net.Http](https://www.nuget.org/packages/System.Net.Http) - HTTP ağ iletişimi için <xref:System.Net.Http.HttpClient> bir <xref:System.Net.Http.HttpResponseMessage>dizi tür, dahil ve.
- [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) - Yerel veya ağa bağlı disk tabanlı depolamaya okuma <xref:System.IO.File> ve <xref:System.IO.Directory>yazma türleri kümesi, ve.
- [System.Linq](https://www.nuget.org/packages/System.Linq) - Nesneleri sorgulamak için bir dizi `Enumerable` <xref:System.Linq.ILookup%602>tür, dahil ve.
- [System.Reflection](https://www.nuget.org/packages/System.Reflection) - Yükleme, denetleme ve etkinleştirme türleri için bir dizi <xref:System.Reflection.Assembly> <xref:System.Reflection.TypeInfo> tür, dahil olmak üzere , ve <xref:System.Reflection.MethodInfo>.

Genellikle, her paketi dahil etmek yerine, bir [meta paket](#metapackages)eklemek daha kolay ve daha sağlamdır. Ancak, tek bir pakete ihtiyacınız olduğunda, [sistemi System.Runtime](https://www.nuget.org/packages/System.Runtime/) paketine başvuran aşağıdaki örnekte ekleyebilirsiniz.

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

Metapaket, birlikte anlamlı olan bir paket kümesini tanımlamak için bir NuGet paketi kuralıdır. Meta paket, bu paket kümesini bağımlılık yaparak temsil eder. Meta paket isteğe bağlı olarak bir çerçeve belirterek paket kümesi için bir çerçeve oluşturabilirsiniz.

.NET Core araçlarının önceki sürümleri (hem project.json hem de csproj tabanlı araçlar) varsayılan olarak hem bir çerçeve hem de bir meta paket belirtilmiştir. Ancak şu anda, metapaket dolaylı olarak hedef çerçeve tarafından başvurulmakta, böylece her meta paket bir hedef çerçeveye bağlıdır. Örneğin, `netstandard1.6` çerçeve NetStandard.Library sürümü 1.6.0 metapaketine başvurur. Benzer şekilde, `netcoreapp2.1` çerçeve Microsoft.NETCore.App Sürüm 2.1.0 metapaketine başvurur. Daha fazla bilgi için [.NET Core SDK'daki Örtük metapaket paket başvurusuna](https://github.com/dotnet/core/blob/master/release-notes/1.0/sdk/1.0-rc3-implicit-package-refs.md)bakın.

Bir çerçeveyi hedeflemek ve bir meta pakete dolaylı olarak başvurmak, aslında bağımlı paketlerinin her birine tek bir hareket olarak bir referans eklediğiniz anlamına gelir. Bu, bu paketlerdeki tüm kitaplıkları IntelliSense (veya benzer bir deneyim) ve uygulamanızı yayınlamak için kullanılabilir hale getirir.

Metapaketleri kullanmanın avantajları vardır:

- Büyük bir ince taneli paket kümesine başvurmak için kullanışlı bir kullanıcı deneyimi sağlar.
- Sınanan ve birlikte iyi çalışan bir paket kümesini (belirli sürümler dahil) tanımlar.

.NET Standart metapaketi:

- [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) - .NET Standard'ın parçası olan kitaplıkları açıklar. .NET Standard'ı destekleyen tüm .NET uygulamaları (örneğin, .NET Framework, .NET Core ve Mono) için geçerlidir. Çerçeveyi `netstandard` kurar.

Anahtar .NET Core metapaketleri şunlardır:

- [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) - .NET Core dağıtımının bir parçası olan kitaplıkları açıklar. Çerçeveyi `.NETCoreApp` kurar. Küçük `NETStandard.Library`bağlıdır.
- [Microsoft.AspNetCore.App](https://www.nuget.org/packages/Microsoft.AspNetCore.App) - Üçüncü taraf bağımlılıkları içerenler hariç, ASP.NET Core ve Entity Framework Core'dan desteklenen tüm paketleri içerir. Daha fazla bilgi [için ASP.NET Core için Microsoft.AspNetCore.App meta paketine](/aspnet/core/fundamentals/metapackage-app) bakın.
- [Microsoft.AspNetCore.All](https://www.nuget.org/packages/Microsoft.AspNetCore.All) - ASP.NET Core, Entity Framework Core ve ASP.NET Core ve Entity Framework Core tarafından kullanılan dahili ve üçüncü taraf bağımlılıklarından desteklenen tüm paketleri içerir. Daha fazla bilgi [için ASP.NET Core 2.x için Microsoft.AspNetCore.All metapaketine](/aspnet/core/fundamentals/metapackage) bakın.
- [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) - mscorlib tabanlı Taşınabilir Sınıf Kitaplıkları 'nın (PCL' ler) .NET Core'da çalışmasını sağlayan bir uyumluluk cephesi kümesi.

## <a name="frameworks"></a>Framework’ler

.NET Core paketlerinin her biri bir çalışma zamanı çerçevelerini destekler. Çerçeveler, belirli bir çerçeveyi hedeflediğinizde güvenebileceğiniz kullanılabilir bir API kümesini (ve potansiyel olarak diğer özellikleri) açıklar. Yeni API'ler eklendikçe sürülürler.

Örneğin, [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) aşağıdaki çerçeveleri destekler:

- . NETFramework,Sürüm=4.6
- . NETStandard,Sürüm=1.3
- 6 Xamarin platformu (örneğin, xamarinios10)

Çerçevelerin tanımlandığı iki farklı yönteme örnek olduğundan, bu çerçevelerin ilk ikisinin karşıtlığı yararlıdır:

- Çerçeve,.NET `.NETFramework,Version=4.6` Framework 4.6'daki kullanılabilir API'leri temsil eder. .NET Framework 4.6 başvuru derlemeleri ile derlenmiş kitaplıklar üretebilir ve bu kitaplıkları NuGet paketlerinde net46 lib klasöründe dağıtabilirsiniz. .NET Framework 4.6'yı hedefleyen veya onunla uyumlu uygulamalar için kullanılacaktır. Tüm çerçeveler geleneksel olarak böyle çalışır.

- Çerçeve `.NETStandard,Version=1.3` paket tabanlı bir çerçevedir. Api'leri çerçeve açısından tanımlamak ve ortaya çıkarmak için çerçeveyi hedefleyen paketlere dayanır.

## <a name="package-based-frameworks"></a>Paket tabanlı çerçeveler

Çerçeveler ve paketler arasında iki yönlü bir ilişki vardır. İlk bölüm, örneğin `netstandard1.3`belirli bir çerçeve için kullanılabilir API'leri tanımlamaktır. Hedef olan `netstandard1.3` paketler (veya uyumlu `netstandard1.0`çerçeveler, örneğin) `netstandard1.3`için kullanılabilir API'leri tanımlar. Bu dairesel bir tanım gibi gelebilir, ama değil. "Paket tabanlı" olması nedeniyle, çerçeve için API tanımı paketlerden gelir. Çerçevenin kendisi herhangi bir API tanımlamaz.

İlişkinin ikinci bölümü varlık seçimidir. Paketler birden çok çerçeve için varlıklar içerebilir. Bir dizi paket ve/veya meta pakete atıfta bulunularak, örneğin `net46` hangi varlığın seçilmesi `netstandard1.3`gerektiğini belirlemek için çerçeve gereklidir. Doğru varlığı seçmek önemlidir. Örneğin, bir `net46` varlığın .NET Framework 4.0 veya .NET Core 1.0 ile uyumlu olması olası değildir.

Bu ilişkiyi aşağıdaki resimde görebilirsiniz. *API,* *çerçeveyi*hedefler ve tanımlar. *Çerçeve* *varlık seçimi*için kullanılır. *Varlık* size API verir.

![Paket Tabanlı Çerçeve Kompozisyonu](./media/packages/package-framework.png)

.NET Core ile kullanılan iki birincil paket tabanlı çerçeveler şunlardır:

- `netstandard`
- `netcoreapp`

### <a name="net-standard"></a>.NET Standard

.NET Standardı ([Hedef Çerçeve](../standard/frameworks.md)Adı `netstandard`: ) [çerçevesi,.NET Standardı](../standard/net-standard.md)tarafından tanımlanan ve üzerine inşa edilen API'leri temsil eder. Birden çok çalışma zamanında çalışması amaçlanan kitaplıklar bu çerçeveyi hedeflemelidir. .NET Core, .NET Framework ve Mono/Xamarin gibi .NET Standart uyumlu çalışma zamanında desteklenirler. Bu çalışma sürelerinin her biri, uyguladıkları API'lara bağlı olarak bir dizi .NET Standart sürümü destekler.

Çerçeve `netstandard` örtülü [`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) meta paketi başvurur. Örneğin, aşağıdaki MSBuild proje dosyası, `netstandard1.6` [ `NETStandard.Library` sürüm 1.6](https://www.nuget.org/packages/NETStandard.Library/1.6.0) metapaketine başvuran proje hedeflerini gösterir.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
</Project>
```

Ancak, proje dosyasındaki çerçeve ve metapaket başvurularının eşleşmesine gerek `<NetStandardImplicitPackageVersion>` yoktur ve proje dosyanızdaki öğeyi metapaket sürümünden daha düşük bir çerçeve sürümünü belirtmek için kullanabilirsiniz. Örneğin, aşağıdaki proje dosyası geçerlidir.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

Bu hedef `netstandard1.3` garip görünebilir ama 1.6.0 `NETStandard.Library`sürümünü kullanın . Metapaket eski `netstandard` sürümler için desteği koruduğundan, geçerli bir kullanım örneğidir. Bu, meta paketin 1.6.0 sürümünde standartlaştırdığınız ve çeşitli `netstandard` sürümleri hedefleyen tüm kitaplıklarınız için kullandığınız durum olabilir. Bu yaklaşımla, yalnızca önceki `NETStandard.Library` sürümleri değil, 1.6.0 geri yüklemeniz gerekir.

Tersi geçerli olmaz: 1.3.0 sürümü ile `netstandard1.6` hedefleme `NETStandard.Library`. Alt sürüm metapaketi bu daha yüksek çerçeve için herhangi bir varlık ortaya çıkarmaz, çünkü daha düşük bir metapaketi ile daha yüksek bir çerçeve hedefleyemezsiniz. Metapackages için sürüm şeması, metapaketlerin tanımladıkları çerçevenin en yüksek sürümüyle eşleşin. Sürüm şeması sayesinde, varlıkların içerdiği `NETStandard.Library` `netstandard1.6` göz önüne alındığında v1.6.0'ın ilk sürümüdür. (Önceki örnekte simetri için, v1.3.0 burada kullanılır, ancak gerçekte yok.)

### <a name="net-core-application"></a>.NET Core uygulaması

.NET Core ([Target Framework Moniker](../standard/frameworks.md): `netcoreapp`) çerçevesi, .NET Core dağıtımı ve sağladığı konsol uygulama modeliyle birlikte gelen paketleri ve ilişkili API'leri temsil eder. .NET Core uygulamaları, konsol uygulama modelini hedeflemesi nedeniyle bu çerçeveyi ve yalnızca .NET Core'da çalışması amaçlanan kitaplıkları kullanmalıdır. Bu çerçevenin kullanılması, uygulamaların ve kitaplıkların yalnızca .NET Core'da çalışmasını kısıtlar.

Metapaket `Microsoft.NETCore.App` çerçeveyi `netcoreapp` hedefler. Bu ~ 60 kütüphaneler, ~ 40 `NETStandard.Library` paket ve ~ 20 ek olarak daha fazla tarafından sağlanan erişim sağlar. Ek API'lere `netcoreapp` erişmek için hedefleyen `netstandard`veya uyumlu çerçeveler oluşturan ek kitaplıklara başvuruda bulunabilirsiniz.

Ek kitaplıkların `Microsoft.NETCore.App` çoğu, `netstandard` bağımlılıklarının diğer `netstandard` kitaplıklar tarafından karşılandığı göz önüne alındığında da hedeflenir. Bu, `netstandard` kitaplıkların bu paketleri bağımlılık olarak da gösterebileceği anlamına gelir.
