---
title: Paketler, metapackages ve çerçeveleri
description: Paketler, metapackages ve çerçeveleri terminolojisi öğrenin.
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: 915ccadbb4d2cca50fd1caa53d90aa05d83d9378
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="packages-metapackages-and-frameworks"></a>Paketler, metapackages ve çerçeveleri

.NET core NuGet paketlerini yapılan bir platformdur. Bazı Ürün Avantajı paketlerinden diğerlerinin parçalı, hassas tanımından karşılaşır. Bu duality uyum sağlamak için ürün paketleri hassas bir dizi dağıtılır ve ardından basit bir "metapackage" adlı bir paket türüyle kaba yığınlar halinde açıklanan.

Her .NET Core paketleri çerçeveleri temsil birden çok .NET uygulamaları üzerinde çalıştırılmasını destekler. Bu çerçeveleri geleneksel çerçeveler gibi bazıları `net46`, .NET Framework temsil eden. "Hangi çerçeveleri tanımlamak için yeni bir model oluşturmak paket tabanlı frameworks" olarak düşünülebilir yeni çerçeveler başka bir kümesidir. Bu paket tabanlı çerçeveler tamamen biçimlendirilmiş ve paketleri ve çerçeveleri arasında güçlü bir ilişki oluşturan paketler olarak tanımlanmış.

## <a name="packages"></a>Paketler

.NET core temelleri, üst düzey veri türleri, uygulama birleşim türleri ve ortak yardımcı programları sağlamak paketleri kümesine ayrılır. Her bu paketleri aynı ada sahip tek bir derleme temsil eder. Örneğin, [modülüyle](https://www.nuget.org/packages/System.Runtime) System.Runtime.dll içerir. 

Paket hassas bir şekilde tanımlamak için avantajları şunlardır:

- Hassas paketleri görece sınırlı diğer paketleri test ile kendi zamanlamada gönderebilirsiniz.
- Hassas paketleri farklı işletim sistemi ve CPU desteği sağlayabilir.
- Hassas paketler yalnızca bir kitaplığa belirli bağımlılıkları olabilir.
- Uygulamalar daha küçük olduğu başvurulmayan paketleri uygulama dağıtım parçası dönüşmez.

Bazı avantajlar yalnızca bazı durumlarda kullanılır. Örneğin, NET çekirdek paketleri genellikle aynı zamanlamayla aynı platform desteği ile birlikte. Hizmet verme durumunda düzeltmeleri dağıtılabilen ve küçük tek Paket güncelleştirmesi yüklü. Değişiklik dar kapsamını nedeniyle, bir düzeltme kullanılabilir yapmak için saat ve doğrulama için tek bir kitaplık gerekenleri sınırlı.

.NET Core anahtar NuGet paketleri listesi aşağıdadır:

- [Modülüyle](https://www.nuget.org/packages/System.Runtime) -en temel .NET Core paket dahil olmak üzere <xref:System.Object>, <xref:System.String>, <xref:System.Array>, <xref:System.Action>, ve <xref:System.Collections.Generic.IList%601>.
- [System.Collections](https://www.nuget.org/packages/System.Collections) -dahil olmak üzere (birincil) genel koleksiyonlar kümesi <xref:System.Collections.Generic.List%601> ve <xref:System.Collections.Generic.Dictionary%602>.
- [System.Net.Http](https://www.nuget.org/packages/System.Net.Http) -bir dizi türleri, HTTP ağ iletişimi için de dahil olmak üzere <xref:System.Net.Http.HttpClient> ve <xref:System.Net.Http.HttpResponseMessage>.
- [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) -okuma ve yerel ya da ağa bağlı disk tabanlı depolama alanına yazmak için türleri kümesi de dahil olmak üzere <xref:System.IO.File> ve <xref:System.IO.Directory>.
- [System.Linq](https://www.nuget.org/packages/System.Linq) -türleri dahil olmak üzere nesneleri, sorgulama için bir dizi `Enumerable` ve <xref:System.Linq.ILookup%602>.
- [System.Reflection](https://www.nuget.org/packages/System.Reflection) -yüklenirken, inceleme ve türleri dahil olmak üzere, etkinleştirme için türleri kümesi <xref:System.Reflection.Assembly>, <xref:System.Reflection.TypeInfo> ve <xref:System.Reflection.MethodInfo>.

Genellikle, paketleri projelerinizi paketini tarafından temelinde dahil olmak üzere yerine, bunu dahil etmek şu ana kadar kolaydır bir *metapackage*, genellikle birlikte kullanılan paketler kümesi olduğu. (Metapackages hakkında daha fazla bilgi için aşağıdaki bölümüne bakın.) Tek bir paket gerektiğinde, ancak bunu hangi başvuruları aşağıdaki örnekte olduğu gibi dahil edebileceğiniz [modülüyle](https://www.nuget.org/packages/System.Runtime/) paket. 

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

## <a name="metapackages"></a>Metapackages

Metapackages birlikte anlamlı paket kümesini tanımlayan bir NuGet paketi kuralı var. Bunlar, bu paket kümesini bağımlılıkları yaparak temsil eder. Bir çerçeve belirterek bunlar bu paketler kümesi için bir çerçeve isteğe bağlı olarak kurabilirsiniz. 

Varsayılan olarak .NET Core araçlarının (project.json ve csproj tabanlı araçlar) önceki sürümleri bir çerçeve ve bir metapackage ikisi de belirtilmiş. Böylece her metapackage bir hedef framework bağlıdır şu anda, ancak metapackage örtük olarak hedef çerçevesi tarafından başvuruluyor. Örneğin, `netstandard1.6` framework NetStandard.Library sürüm 1.6.0 metapackage başvuruyor. Benzer şekilde, `netcoreapp1.1` framework Microsoft.NETCore.App sürüm 1.1.0 metapackage başvuruyor. Daha fazla bilgi için bkz: [örtük metapackage paket .NET Core SDK başvurusunda](https://github.com/dotnet/core/blob/master/release-notes/1.0/sdk/1.0-rc3-implicit-package-refs.md).

Bir çerçeve hedefleme ve örtük olarak bir metapackage başvuran, yürürlükte bağımlı paketler her bir başvuru tek bir hareketi eklemekte olduğunuz anlamına gelir. Tüm kitaplıkların bu paketleri IntelliSense (veya benzer bir deneyim) ve uygulamanızı yayımlamak için kullanılabilmesini sağlar.  

Metapackages kullanmanın avantajları şunlardır:

- Çok sayıda hassas paketleri başvurmak için uygun kullanıcı deneyimi sağlar. 
- Test edilmiş ve birlikte çalışma (belirli sürümleri dahil olmak üzere) paketleri kümesini tanımlar.

.NET standart metapackage aşağıdaki gibidir:

- [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) -".NET standart" parçası olan kitaplıkları açıklar. .NET standardını destekleyen tüm .NET uygulamaları için (örneğin, .NET Framework, .NET Core ve Mono) uygulanır. 'Netstandard' framework oluşturur.

Anahtar .NET Core metapackages şunlardır:

- [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) -.NET Core dağıtım parçası olan kitaplıkları açıklar. Kurar [ `.NETCoreApp` framework](https://github.com/dotnet/core-setup/blob/release/1.1.0/pkg/projects/Microsoft.NETCore.App/Microsoft.NETCore.App.pkgproj). Bağımlı küçük üzerinde `NETStandard.Library`.
- [Microsoft.AspNetCore.All](https://www.nuget.org/packages/Microsoft.AspNetCore.All) -ASP.NET Core, Entity Framework Core ve ASP.NET Core ve Entity Framework Çekirdek tarafından kullanılan iç ve üçüncü taraf bağımlılıkları desteklenen tüm paketleri içerir. Bkz: [ASP.NET Core Microsoft.AspNetCore.All metapackage 2.x](/aspnet/core/fundamentals/metapackage) daha fazla bilgi için.
- [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) -mscorlib tabanlı taşınabilir sınıf kitaplıkları (.NET Core üzerinde çalıştırmak için PCLs) etkinleştirmek uyumluluk cepheleri kümesi.

## <a name="frameworks"></a>çerçeveler

.NET core paketleri çalışma zamanı çerçeveleri kümesini destekler. Çerçeveler açıklamak kullanılabilir bir API kümesini (ve olasılıkla diğer özellikleri) belirli bir çerçeve hedeflediğinizde üzerinde güvenebilirsiniz. Yeni API eklendikçe sürümlü.

Örneğin, [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) aşağıdaki çerçevelerini destekler:

- . NETFramework, sürüm 4.6 =
- . NETStandard, sürüm = 1,3
- 6 Xamarin platformları (örneğin, xamarinios10)

Çerçeveler tanımlanan iki farklı şekilde örnekleri olduğundan bu çerçeveleri ilk iki Karşıtlık kullanışlıdır.

`.NETFramework,Version=4.6` Çerçevesini .NET Framework 4.6 kullanılabilir API'lerinde temsil eder. İle .NET Framework 4.6 başvuru derlemeleri derlenmiş kitaplıkları oluşturmak ve ardından bu kitaplıkları NuGet paketlerini net46 lib klasöründeki dağıtabilirsiniz. .NET Framework 4.6 hedef veya ile uyumlu olmayan uygulamalar için kullanılır. Bu tüm çerçeveler geleneksel çalıştıktan nasıl.

`.NETStandard,Version=1.3` Paket tabanlı çerçeve çerçevedir. Tanımlamak ve API bakımından framework kullanıma sunmak için framework hedefleyen paketlerle kullanır.

## <a name="package-based-frameworks"></a>Paket tabanlı çerçeveler

Çerçeveler ve paketler arasında iki yönlü bir ilişkisi yok. İlk bölümü örneğin belirli bir çerçeve için kullanılabilen API'leri tanımlama `netstandard1.3`. Hedefleyen paketler `netstandard1.3` (veya uyumlu çerçeveleri `netstandard1.0`) tanımlamak için kullanılabilen API'leri `netstandard1.3`. Döngüsel bir tanıma gibi görünebilir, ancak bu değildir. "Paketin tabanlı" olmaya sayesinde, Framework API tanımı paketlerinden gelir. Framework herhangi API'leri tanımlamıyor.

İlişki ikinci bölümü varlık seçimdir. Paketler birden çok çerçeveyi varlıklarının içerebilir. Paketler ve/veya metapackages kümesine başvuru verildiğinde, framework hangi varlık, örneğin seçilmelidir belirlemek için gereken `net46` veya `netstandard1.3`. Doğru varlık seçmek önemlidir. Örneğin, bir `net46` varlık büyük olasılıkla .NET Framework 4.0 veya .NET Core 1.0 ile uyumlu değil.

![Paket tabanlı çerçeve oluşturma](./media/packages/package-framework.png)

Yukarıdaki resimde bu ilişkiyi görebilirsiniz. *API* hedefler ve tanımlar *framework*. *Framework* için kullanılan *varlık seçimi*. *Varlık* API sağlar.

.NET Core ile kullanılan iki birincil paket tabanlı çerçeveler şunlardır:

- `netstandard`
- `netcoreapp`

### <a name="net-standard"></a>.NET standart

.NET standart (hedef framework ad: `netstandard`) framework tarafından tanımlanan ve üstünde oluşturulmuş API'leri temsil eden [.NET standart](../standard/net-standard.md). Birden çok çalışma zamanları üzerinde çalıştırmak için tasarlanmıştır kitaplıkları bu framework hedeflemelidir. Üzerindeki tüm .NET standart uyumlu çalışma zamanı, .NET Core, .NET Framework ve Mono/Xamarin gibi desteklenecektir. Bu çalışma zamanları her bağlı olarak hangi API'leri uyguladıkları .NET standart sürümlerinin bir kümesini destekler.

`netstandard` Framework örtük olarak başvuran [ `NETStandard.Library` ](https://www.nuget.org/packages/NETStandard.Library) metapackage. Örneğin, aşağıdaki MSBuild proje dosyası belirten Proje hedefleri `netstandard1.6`, hangi başvuruları [ `NETStandard.Library` sürüm 1.6](https://www.nuget.org/packages/NETStandard.Library/1.6.0) metapackage.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
</Project>
```

Ancak, proje dosyasında framework ve metapackage başvuruları eşleşmesi gerekmez ve kullanabileceğiniz `<NetStandardImplicitPackageVersion>` metapackage sürümden daha düşük bir framework sürüm belirtmek için proje dosyanızdaki öğesi. Örneğin, aşağıdaki proje dosyası geçerli değil.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

Hedefe garip görünebilir `netstandard1.3` ancak sürümünü kullanın 1.6.0 `NETStandard.Library`. Metapackage desteği tutar bu olduğu bir geçerli kullanım örneği, eski `netstandard` sürümleri. Üzerinde 1.6.0 standartlaştırılmış durum olabilir metapackage sürümü ve çeşitli hedef tüm Kitaplıklarınızı için kullanmak `netstandard` sürümleri. Bu yaklaşımda, yalnızca geri yüklemeniz gereken `NETStandard.Library` 1.6.0 ve değil önceki sürümleri. 

Bu durumun tersi geçerli olmaz: hedefleme `netstandard1.6` 1.3.0 ile sürümü `NETStandard.Library`. Alt sürüm metapackage bu daha yüksek çerçevesi için tüm varlıkları kullanıma değil olduğundan daha düşük bir metapackage daha yüksek bir çerçevesiyle hedefleyemez. Sürüm oluşturma şema metapackages için metapackages tanımladıkları framework yüksek sürümüyle eşleşen onaylar. Sürüm oluşturma düzeni, ilk sürümünde, `NETStandard.Library` içerdiği v1.6.0 düşünüldüğünde `netstandard1.6` varlıklar. V1.3.0, yukarıdaki örnekte simetrisi Yukarıdaki örnek için kullanılır, ancak gerçekte yok.

### <a name="net-core-application"></a>.NET core uygulama

.NET Core uygulaması (TFM: `netcoreapp`) paketleri ve .NET Core dağıtım ve sağladığı konsol uygulama modeli gelen ilişkili API'ler framework temsil eder. .NET core uygulamaları, yalnızca .NET Core üzerinde çalıştırmak istediğiniz kitaplıkları gerektiği gibi konsol uygulama modeli hedefleme nedeniyle bu çerçeve kullanmanız gerekir. Bu çerçeve kullanarak uygulamalar ve kitaplıkları yalnızca .NET Core üzerinde çalışan kısıtlar. 

`Microsoft.NETCore.App` Metapackage hedefleri `netcoreapp` framework. ~ 60 kitaplıkları, ~ 40 tarafından sağlanan erişim sağlayan `NETStandard.Library` paketi ve ~ 20 daha fazla giriş eklenmesi. Ek kitaplıklar hedefleyen başvuru `netcoreapp` veya uyumlu çerçeveleri gibi `netstandard`, ek API'leri erişmek için. 

Tarafından sağlanan ek kitaplıklara çoğu `Microsoft.NETCore.App` de hedeflemek `netstandard` bağımlılıklarını diğer tarafından karşılanır o `netstandard` kitaplıkları. Anlamına `netstandard` kitaplıkları da bu paketleri bağımlılık başvurusu. 
