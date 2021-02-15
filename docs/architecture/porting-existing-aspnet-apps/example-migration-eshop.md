---
title: ASP.NET Core için eShop 'ın örnek geçişi
description: Bir başvuru olarak örnek bir çevrimiçi mağaza uygulaması kullanarak, mevcut bir ASP.NET MVC uygulamasını ASP.NET Core 'e geçirmeye yönelik yönergeler.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 2b7e3aaf70d7400cf84814c7c9845d5444321f1f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488900"
---
# <a name="example-migration-of-eshop-to-aspnet-core"></a>ASP.NET Core için eShop 'ın örnek geçişi

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bu bölümde, bir .NET Framework uygulamasının .NET Core 'a nasıl geçirileceği göreceksiniz. Bu bölümde, ASP.NET 5,0 için yazılmış bir örnek çevrimiçi mağaza uygulaması incelenir. Uygulama, bu kitapta daha önce açıklanan kavramların ve araçların birçoğunu kullanacaktır. Başlangıç noktası uygulamasını [ *Eshopmodernize* GitHub deposunda](https://github.com/dotnet-architecture/eShopModernizing)bulacaksınız. Birçok farklı başlangıç noktası uygulaması vardır. Bu bölüm *Eshoplegacymvcsolution*' a odaklanır.

Projenin ilk sürümü Şekil 4-1 ' de gösterilmiştir. Bu, oldukça standart bir ASP.NET MVC 5 uygulamasıdır.

![Şekil 4-1](media/Figure4-1.png)

**Şekil 4-1.** MVC örnek proje yapısı *Eshopmodernize* .

## <a name="run-apiport-to-identify-problematic-apis"></a>Sorunlu API 'Leri tanımlamak için *Apiport* çalıştırma

Geçirmeye hazırlanın ilk adımı, *Apiport* aracını çalıştırıyordu. Araç, uygulamanın kaç .NET Framework API 'sini ve bunların kaç tane .NET Standard veya .NET Core eşdeğerlerine sahip olduğunu tanımlar. Birincil olarak kendi uygulamanızın mantığına odaklanın, üçüncü taraf bağımlılıklara değil, ve `System.Web` bu yana, bir arada olması gereken bağımlılıklara dikkat edin. ApiPort Aracı, son bölümde [bağımlılıkları anlama ve güncelleştirme](/understand-update-dependencies.md)konusunda sunulmuştur.

[ *Apiport* aracını yükledikten ve yapılandırdıktan](https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer)sonra, Şekil 4-2 ' de gösterildiği gibi Analizi Visual Studio içinden çalıştırın.

![Şekil 4-2](media/Figure4-2.png)

**Şekil 4-2.** Visual Studio 'da bütünleştirilmiş kod taşınabilirliği çözümleyin.

Şekil 4-3 ' de gösterildiği gibi, projenin *bin* klasöründen Web projesinin derlemesini seçin.

![Şekil 4-3](media/Figure4-3.png)

**Şekil 4-3.** Projenin Web derlemesini seçin.

Çözümünüz birden çok proje içeriyorsa, bunların tümünü seçebilirsiniz. *EShop* örneği yalnızca tek bir MVC projesi içerir.

Rapor oluşturulduktan sonra dosyayı açın ve sonuçları gözden geçirin. Özet, uygulamanızın uyumlu sürüme sahip olduğu .NET Framework çağrısı yüzdesinin üst düzey bir görünümünü sağlar. Şekil 4-4, *eShop* MVC projesinin özetini gösterir.

![Şekil 4-4](media/Figure4-4.png)

**Şekil 4-4.** ApiPort Özeti.

Bu uygulama için .NET Framework çağrılarının yüzde 80 ' unun uyumlu olduğunu öğrenin. taşıma işlemi sırasında çağrıların yüzde 20 ' si ile ilgilenilmesi gerekir. Ayrıntıları görüntülemek, uyumsuz çağrıların tümünün bir parçası olduğunu `System.Web` ve beklenen bir uyumsuzluk olduğunu gösterir. `System.Web`Çağrılardaki bağımlılıklar, uygulamanın denetleyicileri ve ilgili sınıfları sonraki bir adımda geçirildiğinde değinilmesi gerekir. Şekil 4-5 araç tarafından bulunan belirli türlerden bazılarını listeler:

![Şekil 4-5](media/Figure4-5.png)

**Şekil 4-5.** *Apiport* uyumsuz tür ayrıntıları.

Uyumsuz türlerin çoğu, `Controller` ve ASP.NET Core eşdeğerleri olan çeşitli ilgili özniteliklere başvurur.

## <a name="update-project-files-and-nuget-reference-syntax"></a>Proje dosyalarını ve NuGet başvuru sözdizimini Güncelleştir

Daha sonra, eski *. csproj* dosya yapısından .NET Core ile tanıtılan daha yeni, daha basit bir yapıya geçiş yapın. Bunu yaparken, proje dosyasındaki öğeleri kullanmak için NuGet başvuruları için bir *packages.config* dosyası kullanmaktan da geçiş yapabilirsiniz `<PackageReference>` .

Orijinal projenin *Eshoplegacymvc. csproj* dosyası 418 satır uzunluğundadır. Şekil 4-6 ' de proje dosyasının bir örneği gösterilir. Genel boyutunun ve karmaşıklığının bir fikir sunmak için görüntünün sağ tarafı dosyanın tamamının küçük bir görünümünü içerir.

![Şekil 4-6](media/Figure4-6.png)

**Şekil 4-6.** *Eshoplegacymvc. csproj* dosya yapısı.

Mevcut bir ASP.NET projesi için yeni bir proje dosyası oluşturmanın yaygın bir yolu, `dotnet new`   >    >  Visual Studio 'da yeni bir **Proje** kullanarak yeni bir ASP.NET Core uygulaması oluşturmaktır. Ardından, geçiş işleminin tamamlanabilmesi için dosyalar eski projeden yeni birine kopyalanabilir.

C# proje dosyasına ek olarak, NuGet bağımlılıkları Şekil 4-7 ' de gösterildiği gibi ayrı bir 45 satırı *packages.config* dosyasında depolanır.

![Şekil 4-7](media/Figure4-7.png)

**Şekil 4-7.** *packages.config* dosyası.

Yeni *. csproj* dosya biçimine yükselttikten sonra Visual Studio 'yu kullanarak sınıf kitaplığı projelerinde *packages.config* geçirebilirsiniz. Ancak, bu işlevsellik ASP.NET projeleriyle birlikte çalışmaz. [ *packages.config* `<PackageReference>` Visual Studio 'da ' a geçirme hakkında daha fazla bilgi edinin](https://docs.microsoft.com/nuget/consume-packages/migrate-packages-config-to-package-reference). Geçirilecek çok sayıda projeniz varsa, [Bu topluluk aracı yardımcı olabilir](https://github.com/MarkKharitonov/NuGetPCToPRMigrator).

## <a name="create-new-aspnet-core-project"></a>Yeni ASP.NET Core projesi oluştur

Çalışma dosyalarının çoğu Visual Studio 'nun **Çözüm Gezgini** içinden yapılabilmesini sağlamak için mevcut uygulamanın çözümüne yeni bir ASP.NET Core projesi ekleyin. Visual Studio 'da uygulamanızın çözümüne sağ tıklayın ve **Yeni Proje Ekle**' yi seçin. **ASP.NET Core Web uygulaması**' nı seçin ve Şekil 4-8 ' de gösterildiği gibi yeni projeye bir ad verin.

![Şekil 4-8](media/Figure4-8.png)

**Şekil 4-8.** Yeni ASP.NET Core Web uygulaması ekleyin.

Sonraki iletişim kutusunda hangi şablonun kullanılacağını seçmeniz istenir. **Boş** şablonu seçin. Ayrıca, açılan menüyü de **.NET Core** 'tan **.NET Framework** olarak değiştirdiğinizden emin olun. Şekil 4-9 ' de gösterildiği gibi **ASP.NET Core 2,2**' u seçin.

![Şekil 4-9](media/Figure4-9.png)

**Şekil 4-9.** ASP.NET Core 2,2 ile .NET Framework Hedefleme boş bir proje şablonu seçin.

### <a name="migrating-nuget-packages"></a>NuGet paketleri geçiriliyor

*packages.config* geçirmek için yerleşik geçiş aracı `<PackageReference>` ASP.net projelerinde çalışmadıklarından, bunun yerine bir topluluk aracı kullanabilir veya el ile geçiş yapabilirsiniz. [Kullandığım bir topluluk aracı](https://gist.github.com/tomkuijsten/2d75074d9a3c19c04ee8ea19a6289ddf) bir biçimden diğerine dönüştürmek IÇIN bir xsl dosyası kullanıyor. Bunu kullanmak için önce *packages.config* dosyasını yeni oluşturulan ASP.NET Core proje klasörüne kopyalayın. Bu komut dosyası, komut dosyasını çalıştırdığınız tüm klasörlerden *packages.config* dosyasını kaldırdığında dosyalarınızın bir yedeğini alın. Sonra bu komutları proje klasöründen (veya tercih ediyorsanız tüm çözüm için) çalıştırın:

```powershell
iwr https://git.io/vdKaV -OutFile Convert-ToPackageReference.ps1
iwr https://git.io/vdKar -OutFile  Convert-ToPackageReference.xsl
./Convert-ToPackageReference.ps1 | Out-Null
```

İlk iki komut dosyaları yerel olarak mevcut olacak şekilde indirir. Son satır betiği çalıştırır. Çalıştırdıktan sonra yeni projeyi oluşturmayı deneyin. Büyük olasılıkla bazı hatalar alabilirsiniz. Bunları çözmek için bazı başvuruları ( `Microsoft.AspNet` ve paketlerin çoğu gibi `System` ) ortadan kaldırmak isteyeceksiniz ve bazı öznitelikleri kaldırmanız gerekebilir `xmlns` .

Çoğu ASP.NET MVC uygulamasında, önyükleme ve jQuery gibi birçok istemci tarafı bağımlılığı NuGet paketleri kullanılarak dağıtılır. ASP.NET Core, NuGet paketleri yalnızca sunucu tarafı işlevleri için kullanılır. İstemci dosyaları diğer yollarla yönetilmelidir. `<PackageReference>`Eklenen ve bulunan öğelerin listesini gözden geçirin ve aşağıdakiler dahil olmak üzere istemci kitaplıkları için olan öğeleri unutmayın:

- Bootstrap
- jQuery
- jQuery. Validation
- Modernize
- popper.js
- Yanıtlama

Bu paketler için NuGet tarafından yüklenen statik istemci dosyaları, yeni projenin *Wwwroot* klasörüne kopyalanacak ve oradan barındırılacak. Bu dosyaların uygulama için hala gerekli olup olmadığını ve bunun yerine bunları barındırmayı veya bir içerik teslim ağı (CDN) kullanmayı bir anlam taşıdığını düşünürken. Bu kitaplık sürümleri, [Libman](https://docs.microsoft.com/aspnet/core/client-side/libman/) veya [NPM](https://www.npmjs.com/)gibi araçlar kullanılarak derleme zamanında yönetilebilir. Şekil 4-10, gösterilen dönüştürme aracını kullanarak paket başvurularını geçirdikten sonra ve gereksiz paketleri kaldırarak tam *Esatlamalı. csproj* dosyasını gösterir.

![Şekil 4-10](media/Figure4-10.png)

**Şekil 4-10.** *Eshopcat. csproj* dosyasındaki paket başvuruları.

Paket başvuruları, `<Version>1.0.0.0</Version>` öğesi üzerinde bir özniteliği yaparak daha sonra sıkıştırabilirsiniz `Version=1.0.0.0` `<PackageReference>` .

### <a name="migrate-static-files"></a>Statik dosyaları geçirme

Uygulamanın kullandığı, üçüncü taraf betikler ve çerçeveler de dahil olmak üzere, özel görüntüler ve stil sayfaları da dahil olmak üzere tüm statik dosyalar eski projeden yeni bir projeye kopyalanmalıdır. ASP.NET MVC uygulamalarında, dosyalar genellikle proje klasörü içindeki konumlarına göre erişilir. ASP.NET Core uygulamalarda, bu statik dosyalara *Wwwroot* klasörü içindeki konumlarına göre erişilir. *EShop* projesi için aşağıdaki klasörlerde statik dosyalar bulunur:

* *İçerik*
* *tiplerini*
* *Görüntüler*
* *PICS*
* *Betikleri*

Önceki adımda kullanılan **boş** proje şablonu, varsayılan olarak bu klasörü veya bunun çalışması için gerekli olan ara yazılımı içermez. Bunları eklemeniz gerekir.

Projenin köküne bir *Wwwroot* klasörü ekleyin.

NuGet paketinin sürüm 2.2.0 ekleyin `Microsoft.AspNetCore.StaticFiles` .

*Startup.cs*' de yöntemine bir çağrı ekleyin `app.UseStaticFiles()` `Configure` :

```csharp
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseStaticFiles();
    
    // ...
}
```

ASP.NET MVC uygulamasındaki *içerik* klasörünü yeni projenin *Wwwroot* klasörüne kopyalayın.

Uygulamayı çalıştırın ve statik dosyanın beklenen yoldan doğru şekilde sunulduğunu doğrulamak için */Content/Base.css* klasörüne gidin. Statik dosyaları içeren klasörlerin geri kalanını yeni projeye kopyalamaya devam edin. Ayrıca, görevin kökündeki izin *simgesi. ico* dosyasını *Wwwroot* klasörüne kopyalamak isteyeceksiniz. Şekil 4-11, bu dosyaların ve klasörlerinin tümünün kopyalandığı sonuçları gösterir.

![Şekil 4-11](media/Figure4-11.png)

**Şekil 4-11.** *Wwwroot* klasörüne kopyalanmış statik klasörler.

### <a name="migrate-c-files"></a>C# dosyalarını geçirme

Ardından, standart MVC klasörleri ve *denetleyiciler*, *modeller*, *ViewModel* ve *Hizmetler* gibi Içerikleri de dahil olmak üzere uygulama tarafından kullanılan C# dosyalarını kopyalayın. Bu dosyalarda büyük olasılıkla bazı değişiklikler yapılması gerekir. Tek seferde bir klasör (veya alt klasör) kopyalamak ve ne zaman giteceğinden ilgilenilmesi gerektiğini görmek için derlemek en iyisidir.

*EShop* örneği için, geçiş için seçeceğim ilk klasör, C# varlıklarını ve Entity Framework sınıflarını içeren *modeller* klasörüdür. Bu klasörün sınıfları çoğu başkaları tarafından kullanılır, bu nedenle bu sınıflar kopyalanana kadar çalışmaz. Klasörü kopyaladıktan ve oluşturduktan sonra, derleyici eksik ad alanıyla ilgili hatalar `System.Web.Hosting` , ile ilgili erişim ve başvuru olarak ortaya çıkartiliyor `HostingEnvironment` `ConfigurationManager.AppSettings` . Bu sorunlara yönelik çözüm, gerekli yol verilerini geçirmek olacaktır; Şimdilik, son satırlar için açıklama alınır ve `TODO:` her birine izlemek için bir açıklama eklenir. Beş satırı değiştirdikten sonra **görev listesi** beş öğeyi ve proje yapılarını gösterir.

Daha sonra, bir sınıfı olan *ViewModel* klasörü üzerine kopyalanır. Bu çok kolay bir işlemdir ve anında oluşturulur.

*Hizmetler* klasörü üzerine kopyalanır. Bu klasörün sınıfları *modeller* klasöründen, bu klasörden sonra kopyalanması gereken Entity Framework sınıflara bağımlıdır. Neyse ki, hata olmadan derleme Yapılımı.

Bu, *denetleyiciler* klasörünü ve iki sınıfını bırakır `Controller` . Klasörü yeni projeye kopyaladıktan ve derlemeden sonra yedi derleme hatası vardır. Bunlardan dördü, erişim ile ilgilidir `ViewBag` ve hata bildirin:

> `Missing compiler required member 'Microsoft.CSharp.RuntimeBinder.CSharpArgumentInfo.Create'`

Bu hatayı çözmek için C# öğesine bir NuGet paket başvurusu ekleyin:

```xml
<PackageReference Include="Microsoft.CSharp" Version="4.7.0" />
```

Kalan üç hata, başvurulmayan bir derlemede tanımlanan türleri belirtir. Özellikle bu türler:

- `HttpServerUtilityBase`
- `RouteValueDictionary`
- `HttpRequestBase`

Her hatayı tek tek göz atalım. `Server`Öğesinin özelliğine başvurulmasına çalışırken ilk hata oluşur `Controller` , ancak artık mevcut değildir. İşlemin hedefi, uygulamadaki bir görüntü dosyasının yolunu almak olur:

```csharp
if (item != null)
{
    var webRoot = Server.MapPath("~/Pics"); // compiler error on this line
    var path = Path.Combine(webRoot, item.PictureFileName);

    string imageFileExtension = Path.GetExtension(item.PictureFileName);
    string mimetype = GetImageMimeTypeFromImageFileExtension(imageFileExtension);

    var buffer = System.IO.File.ReadAllBytes(path);

    return File(buffer, mimetype);
}
```

Bu sorunun iki olası çözümü vardır. Birincisi, işlevselliği olduğu gibi tutdır. Bu durumda, kullanmak yerine, `Server.MapPath` *Wwwroot* 'daki görüntü dosyalarının konumuna başvuran sabit bir yol kullanılmalıdır. Alternatif olarak, bu eylem yönteminin tek amacı bir statik görüntü dosyası döndürmesidir, bu eyleme ilişkin başvurular, doğrudan statik dosyalara başvuracak şekilde, çalışma zamanı performansını artıran şekilde güncelleştirilemeyebilir. Bu eylemin bir parçası olarak herhangi bir işlem yapılmadığından, yalnızca dosyaları doğrudan sunmanıza bir neden yoktur. Bu eyleme yapılan tüm başvuruları güncelleştirebilmezse, statik dosyanın konumuna yeniden yönlendirme oluşturmak için eylem yeniden yazılabilir.

Sonraki iki hata, aynı kod satırında aynı özel yöntemde oluşur:

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    item.PictureUri = this.Url.RouteUrl(PicController.GetPicRouteName, new { catalogItemId = item.Id }, this.Request.Url.Scheme);
}
```

Hem hem de `this.Url` `this.Request` derleyici hatalarına neden olur. Bu kodun nasıl kullanıldığına bakarak, amacı `PicController` görüntü dosyalarını işleyen eyleme bir bağlantı oluşturmak için kullanılır. Yeni bulduğumuz, büyük olasılıkla *Wwwroot*'da bulunan statik dosyaların doğrudan bağlantılarıyla değiştirilebilir. Şimdilik, bu kodu yoruma ve bu kodun `TODO:` başka bir şekilde başvuruda bulunmak için bir açıklama eklemeye değecektir.

`Controller` `CatalogController` Bu, bu kodun göründüğü sınıf tarafından kullanılan temel sınıfın, hala öğesine başvurmakta olduğunu belirtmekte bir değer `System.Web.Mvc.Controller` . Bunu, ASP.NET Core kullanmak için güncelleştirdiğimiz bir kez daha fazla hata çözeceğiz. İlk olarak, `using System.Web.Mvc;` içindeki deyim listesinden satırı kaldırın `using` `CatalogController` . Sonra, NuGet paketini ekleyin `Microsoft.AspNetCore.Mvc` . Son olarak, bir `using Microsoft.AspNetCore.Mvc;` ifade ekleyin ve uygulamayı yeniden derleyin.

Bu kez, 16 hata vardır:

- `Include` geçerli bir adlandırılmış öznitelik bağımsız değişkeni değil (2)
- `HttpStatusCodeResult` bulunamadı (3)
- `HttpNotFound` yok (3)
- `SelectList` bulunamadı (8)

Daha fazla bilgi için bu hataları tek tek gözden geçirelim. İlk olarak, `SelectList` `using Microsoft.AspNetCore.Mvc.Rendering;` hatanın yarısını ortadan kaldıran ekleyerek düzeltilebilir.

Öğesine yapılan tüm başvurular `return HttpNotFound();` ile değiştirilmelidir `return NotFound();` .

Öğesine yapılan tüm başvurular `return new HttpStatusCodeResult(HttpStatusCode.BadRequest);` ile değiştirilmelidir `return BadRequest();` .

Bu, yalnızca `Include` `[Bind]` birkaç eylem yöntemi üzerinde aşağıdaki gibi bir özniteliği ile kullanımını bırakır:

```csharp
[HttpPost]
[ValidateAntiForgeryToken]
public ActionResult Create([Bind(Include = "Id,Name,Description,Price,PictureFileName,CatalogTypeId,CatalogBrandId,AvailableStock,RestockThreshold,MaxStockThreshold,OnReorder")] CatalogItem catalogItem)
{
```

Yukarıdaki kod, model bağlamasını dizede listelenen özelliklerle kısıtlar `Include` . ASP.NET Core MVC 'de `[Bind]` öznitelik hala var, ancak artık `Include =` bağımsız değişkene ihtiyaç yoktur. Özellik listesini doğrudan `[Bind]` özniteliğine geçirin:

```csharp
[HttpPost]
[ValidateAntiForgeryToken]
public ActionResult Create([Bind("Id,Name,Description,Price,PictureFileName,CatalogTypeId,CatalogBrandId,AvailableStock,RestockThreshold,MaxStockThreshold,OnReorder")] CatalogItem catalogItem)
{
```

Bu değişikliklerle proje bir kez daha derlenir. Genellikle etki alanı modelinize veya veri modeli türlerine doğrudan model bağlamayı kullanmak yerine, denetleyici girişleri için ayrı model türleri kullanmak daha iyi bir uygulamadır.

## <a name="migrate-views"></a>Görünümleri geçirme

Görünümlerle ilgili iki en büyük ASP.NET Core MVC özelliği [Razor Pages](https://docs.microsoft.com/aspnet/core/razor-pages/) ve [etiket yardımcılardır](https://docs.microsoft.com/aspnet/core/mvc/views/tag-helpers/built-in/). İlk geçiş için, her iki özelliği de kullanmayacağız. Ancak, geçiş yapıldıktan sonra uygulamayı desteklemeye devam ederseniz özellikleri aklınızda bulundurmanız gerekir. Bir sonraki adım, *Görünümler* klasörünü özgün projeden yeni bir kopyaya kopyalamadır. Derlemeden sonra dokuz hata vardır:

- HttpContext yok (2)
- Betikler yok (5)
- Stiller yok (1)
- HtmlString bulunamadı (1)

Bu hataları araştırmak, büyük *_Layout. cshtml*'de, komut dosyası ve stil etiketlerinin işlenmesinin yanı sıra, uygulamayı barındıran sunucunun en son yeniden başlatılması sırasında görüntülenmesini sağlar. Aşağıdaki kod listesi *_Layout. cshtml* dosyasındaki sorun bölgelerini gösterir:

```razor
// other lines omitted; only errors shown
@Styles.Render("~/Content/css")
@Scripts.Render("~/bundles/modernizr")

@{ var sessionInfo = new HtmlString($"{HttpContext.Current.Session["MachineName"]}, {HttpContext.Current.Session["SessionStartTime"]}");}

@Scripts.Render("~/bundles/jquery")
@Scripts.Render("~/bundles/bootstrap")
```

Modernizr başvurusu kaldırılabilir. Önyükleme ve jQuery başvuruları, uygun sürüme yönelik CDN bağlantılarıyla değiştirilebilir.

`@Styles.Render`Satırı Değiştir:

```html
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
```

Son iki satırı şu `Scripts.Render` metinle değiştirin:

```html
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>
```

Son olarak, önyükleme sonrasında `<link>` , `<link>` uygulamanızın kullandığı yerel stiller için ek öğeler ekleyin. *EShop* için sonuç burada gösterilir:

```html
<link rel="stylesheet" href="~/Content/custom.css" />
<link rel="stylesheet" href="~/Content/base.css" />
<link rel="stylesheet" href="~/Content/Site.css" />
```

Öğelerin görünmesi için gereken sırayı öğrenmek için `<link>` , orijinal uygulamanızın IŞLENMIŞ HTML dosyasına bakın. Alternatif olarak, *eShop* örneği için, uygun sırayı belirten bu kodu içeren *BundleConfig.cs* öğesini gözden geçirin:

```csharp
bundles.Add(new StyleBundle("~/Content/css").Include(
          "~/Content/bootstrap.css",
          "~/Content/custom.css",
          "~/Content/base.css",
          "~/Content/site.css"));
```

Yeniden oluşturma, *oluşturma* ve *düzenleme* görünümlerinde jQuery doğrulaması yüklenirken bir hata daha ortaya çıkarır. Bu kodla değiştirin:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery-validate/1.17.0/jquery.validate.min.js" integrity="sha512-O/nUTF5mdFkhEoQHFn9N5wmgYyW323JO6v8kr6ltSRKriZyTr/8417taVWeabVS4iONGk2V444QD0P2cwhuTkg==" crossorigin="anonymous"></script>
```

Görünümlerde düzeltilmek üzere en son şey `Session` , uygulamanın ne kadar süreyle çalıştığını ve hangi makinede olduğunu göstermek için başvuru içerir. Bu verileri `Startup` statik değişkenler olarak toplayabiliriz ve değişkenleri Düzen sayfasında görüntüleriz. Aşağıdaki özellikleri *Startup.cs* öğesine ekleyin:

```csharp
public static DateTime StartTime { get; } = DateTime.UtcNow;
public static string MachineName { get; } = Environment.MachineName;
```

Sonra, düzen içindeki altbilginin içeriğini aşağıdaki kodla değiştirin:

```razor
<section class="col-sm-6">
    <img class="esh-app-footer-text hidden-xs" src="~/images/main_footer_text.png" width="335" height="26" alt="footer text image" />
    <br />
<small>@eShopPorted.Startup.MachineName - @eShopPorted.Startup.StartTime.ToString() UTC</small>
</section>
```

Bu noktada, daha sonra uygulama başarıyla oluşturulur. Ancak, bunu çalıştırmaya çalışmak yalnızca Merhaba Dünya verir *!* **boş** ASP.NET Core şablonu yalnızca herhangi bir isteğe yanıt olarak görüntülenecek şekilde yapılandırıldığından. Sonraki bölümde, bağımlılığı ekleme ve yapılandırma dahil olmak üzere uygulamayı ASP.NET Core MVC kullanacak şekilde yapılandırarak geçişi tamamlayacağım. Bu bir yerde, uygulamanın çalışması gerekir. Daha sonra, `TODO:` daha önce oluşturulmuş görevlerin düzeltilmesi zaman alabilir.

## <a name="migrate-app-startup-components"></a>Uygulama başlangıç bileşenlerini geçirme

Son geçiş adımı, uygulama başlangıç görevlerinin *Global. asax* ve çağrı yaptığı sınıflardan sürme ve bunları ASP.NET Core eşdeğerlerine geçirmekte. Bu görevler, MVC 'nin yapılandırmasını, bağımlılık ekleme işlemini ayarlamayı ve yeni yapılandırma sistemiyle çalışmayı içerir. ASP.NET Core, bu görevler *Startup.cs* dosyasında işlenir.

### <a name="configure-mvc"></a>MVC 'yi yapılandırma

Özgün ASP.NET MVC uygulaması, `Application_Start` uygulamanın başlatıldığı zaman çalışan *Global. asax* dosyasında aşağıdaki koda sahiptir:

```csharp
protected void Application_Start()
{
    container = RegisterContainer();
    AreaRegistration.RegisterAllAreas();
    FilterConfig.RegisterGlobalFilters(GlobalFilters.Filters);
    RouteConfig.RegisterRoutes(RouteTable.Routes);
    BundleConfig.RegisterBundles(BundleTable.Bundles);
    ConfigDataBase();
}
```

Bu satırlara tek tek bakarak, `RegisterContainer` yöntemi aşağıda yer alacak bağımlılık ekleme işlemini ayarlar. Sonraki üç satır MVC 'nin farklı kısımlarını yapılandırır: bölgeler, filtreler ve rotalar. Paketler, bağlantı verilen uygulamadaki statik dosyalarla değiştirilmiştir. Son satır, daha sonraki bir bölümde gösterilecek olan uygulama için veri erişimini ayarlar.

Bu uygulama aslında alanlar kullandığından, alan kayıt çağrısını geçirmek için yapılması gereken hiçbir şey yok. Uygulamanızın alan geçirilmesi gerekiyorsa, [docs ASP.NET Core alanların nasıl yapılandırılacağını belirtir](https://docs.microsoft.com/aspnet/core/mvc/controllers/areas).

Genel filtreleri kaydetme çağrısı, `FilterConfig` uygulamanın *App_Start* klasöründeki sınıfında bir yardımcı çağırır:

```csharp
public static void RegisterGlobalFilters(GlobalFilterCollection filters)
{
    filters.Add(new HandleErrorAttribute());
}
```

Uygulamaya eklenen tek öznitelik ASP.NET MVC filtresidir `HandleErrorAttribute` . Bu filtre, bir isteğin parçası olarak bir özel durum oluştuğunda, özel durum ayrıntıları yerine varsayılan bir eylem ve görünümün görüntülenmesini sağlar. ASP.NET Core, bu işlevsellik, `UseExceptionHandler` Ara yazılım tarafından gerçekleştirilir. Ayrıntılı hata iletileri varsayılan olarak etkinleştirilmez. Bunlar, ara yazılım kullanılarak yapılandırılmalıdır `UseDeveloperExceptionPage` . Bu davranışı özgün uygulamayla eşleşecek şekilde yapılandırmak için, `Configure` *Startup.cs* içinde yönteminin başlangıcına aşağıdaki kod eklenmelidir:

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }
    else
    {
        app.UseExceptionHandler("/Error");
    }
    // ...
}
```

Bu, eShop uygulaması tarafından kullanılan tek filtreyi ele alır ve bu durumda yerleşik ara yazılım kullanılarak yapılır. Uygulamanızda yapılandırılması gereken genel filtrelerinizin varsa, bu `ConfigureServices` bölümde daha sonra gösterilen YÖNTEME MVC eklendiğinde bu işlem yapılır.

Bulunması gereken MVC ile ilgili mantık 'nin en son parçası uygulamanın varsayılan yollardır. `RouteConfig.RegisterRoutes(RouteTable.Routes)` `RegisterRoutes` Aşağıdaki kodun uygulama başlatıldığında YÜRÜTÜLDÜĞÜ, MVC yol tablosunu yardımcı yönteme geçirir:

```csharp
public static void RegisterRoutes(RouteCollection routes)
{
    routes.MapMvcAttributeRoutes();
    routes.IgnoreRoute("{resource}.axd/{*pathInfo}");

    routes.MapRoute(
        name: "Default",
        url: "{controller}/{action}/{id}",
        defaults: new { controller = "Catalog", action = "Index", id = UrlParameter.Optional }
    );
}
```

Bu kod satırı satır içine alınıyor, ilk satır öznitelik yolları için desteği ayarlar. Bu ASP.NET Core yerleşik olarak bulunur, bu nedenle ayrı olarak yapılandırmak gereksizdir. Benzer şekilde, *{Resource}. axd* dosyaları ASP.NET Core ile kullanılmaz, bu nedenle bu yolların yoksayılmasına gerek yoktur. `MapRoute`Yöntemi, tipik yol şablonunu kullanan MVC için varsayılanı yapılandırır `{controller}/{action}/{id}` . Bu, `CatalogController` varsayılan denetleyicinin kullanıldığı ve `Index` yöntemi varsayılan eylem olduğu gibi, bu şablon için varsayılan değerleri de belirtir. Daha büyük uygulamalar genellikle `MapRoute` ek rotalar ayarlamak için daha fazla çağrı içerecektir.

ASP.NET Core MVC [geleneksel yönlendirme ve öznitelik yönlendirmeyi](https://docs.microsoft.com/aspnet/core/mvc/controllers/routing?view=aspnetcore-2.2&preserve-view=true)destekler. Geleneksel yönlendirme, yol tablosunun `RegisterRoutes` daha önce listelenen yöntemde nasıl yapılandırıldığına benzer. *EShop* uygulamasında kullanılan gibi varsayılan bir yol ile geleneksel yönlendirmeyi ayarlamak için, `Configure` *Startup.cs* içindeki yönteminin sonuna aşağıdaki kodu ekleyin:

```csharp
app.UseMvc(routes =>
{
   routes.MapRoute("default", "{controller=Catalog}/{action=Index}/{id?}");
});
```

> [!NOTE]
> ASP.NET Core 3,0 ve üzeri ile, bu, uç noktaları kullanacak şekilde değiştirilmiştir. İlk bağlantı noktasının 2,2 ASP.NET Core için, geleneksel yolların eşlenmesiyle ilgili doğru sözdizimidir.

Bu değişiklikler varken, `Configure` yöntemi neredeyse yapılır. Merhaba Dünya yazdıran orijinal şablonun `app.Run` yöntemi *!* silinmelidir. Bu noktada, yöntemi burada gösterildiği gibidir:

```csharp
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }
    else
    {
        app.UseExceptionHandler("/Home/Error");
    }

    app.UseStaticFiles();

    app.UseMvc(routes =>
    {
        routes.MapRoute("default", "{controller=Catalog}/{action=Index}/{id?}");
    });
}
```

Şimdi MVC hizmetlerini yapılandırmak ve ardından uygulamanın bağımlılık ekleme (DI) desteğinin geri kalanı tarafından sağlananı. Şimdiye kadar, *Esatlamalı* projenin `ConfigureServices` yöntemi boş kaldı. Şimdi doldurmaya başlama zamanı.

İlk olarak, ASP.NET Core MVC 'nin düzgün şekilde çalışmasını sağlamak için, eklenmesi gerekir:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
}
```

Yukarıdaki kod, MVC özelliklerinin çalışmasını sağlamak için gereken en düşük yapılandırmadır. Bu çağrıdan yapılandırılanılabilecek birçok ek özellik vardır, ancak şimdilik uygulamayı derlemek yeterli olacaktır. Bunu çalıştırmak artık varsayılan isteği doğru şekilde yönlendirdik, ancak henüz DI 'yi yapılandırdığımız için, henüz bir `CatalogController` uygulama türü sağlanmadığından bir hata oluştu `ICatalogService` . MVC 'yi bir süre sonra yapılandırmak için geri döneceğiz. Şimdilik uygulamanın bağımlılık ekleme işlemini geçirelim.

#### <a name="migrate-dependency-injection-configuration"></a>Bağımlılık ekleme yapılandırmasını geçirme

Orijinal uygulamanın *Global. asax* dosyası, uygulama başladığında çağrılan aşağıdaki yöntemi tanımlar:

```csharp
protected IContainer RegisterContainer()
{
  var builder = new ContainerBuilder();

  builder.RegisterControllers(typeof(MvcApplication).Assembly);

  var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);
  builder.RegisterModule(new ApplicationModule(mockData));

  var container = builder.Build();
  DependencyResolver.SetResolver(new AutofacDependencyResolver(container));

  return container;
}
```

Bu kod bir [Autofac](https://autofac.org/) kapsayıcısını yapılandırır, gerçek veya sahte verilerin kullanılması gerekip gerekmediğini belirleyecek bir yapılandırma ayarı okur ve bu ayarı bir Autofac modülüne (uygulamanın */modules* dizininde bulunur) geçirir. Neyse ki, Autofac .NET Core 'u destekler, bu nedenle modül doğrudan geçirilebilirler. Klasörü yeni projeye kopyalayın ve sınıfın ad alanını ve derlenmesi gerekir.

ASP.NET Core, bağımlılık ekleme için yerleşik desteğe sahiptir, ancak gerekirse Autofac gibi üçüncü taraf bir kapsayıcıyı daha kolay bir şekilde oluşturabilirsiniz. Bu durumda, uygulama zaten Autofac kullanmak üzere yapılandırılmış olduğundan, en basit çözüm kullanımını sürdürmenize olanak sağlar. Bunu yapmak için `ConfigureServices` yöntem imzasının bir döndürecek şekilde değiştirilmesi gerekir `IServiceProvider` ve Autofac kapsayıcı örneği yapılandırılmalı ve yönteminden döndürülmelidir.

**Note:** .NET Core 3,0 ve üzeri sürümlerde, üçüncü taraf bir dı kapsayıcısını tümleştirme işlemi değişmiştir.

Autofac yapılandırmasının bir bölümü için bir çağrısı gerekir `builder.Populate(services)` . Bu uzantı, `Autofac.Extensions.DependencyInjection` kod derlemeden önce yüklenmesi gereken NuGet paketinde bulunur.

`ConfigureServices`Bir Autofac kapsayıcısını yapılandırmak için değiştirdikten sonra, yeni yöntem burada gösterildiği gibidir:

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    services.AddMvc();

    // Create Autofac container builder
    var builder = new ContainerBuilder();
    builder.Populate(services);
    bool useMockData = true; // TODO: read from config
    builder.RegisterModule(new ApplicationModule(useMockData));

    ILifetimeScope container = builder.Build();

    return new AutofacServiceProvider(container);
}
```

Şimdilik ayarı `useMockData` olarak ayarlanır `true` . Bu ayar, bir süre sonra yapılandırmadan okunacak. Bu noktada uygulama, Şekil 4-12 ' de gösterildiği gibi, çalıştırıldığında derlenir ve başarıyla yüklenir.

![Şekil 4-12](media/Figure4-12.png)

**Şekil 4-12.** Sahte verilerle yerel olarak çalışan bir bağlantı *noktası* uygulama.

#### <a name="migrate-app-settings"></a>Uygulama ayarlarını geçirme

ASP.NET Core yeni bir [yapılandırma sistemi](https://docs.microsoft.com/aspnet/core/fundamentals/configuration/?view=aspnetcore-2.2&preserve-view=true)kullanır ve bu, varsayılan olarak dosya *üzerinde birappsettings.js* yararlanır. Program.cs ' `CreateDefaultBuilder` de kullanarak varsayılan yapılandırma uygulamada zaten ayarlanmıştır. Yapılandırmaya erişmek için sınıfların yalnızca kendi kurucusunda istemesi gerekir. `Startup`Sınıf özel durum değildir. İçindeki yapılandırmaya `Startup` ve uygulamanın geri kalanına erişmeye başlamak için oluşturucudan bir örneği isteyin `IConfiguration` :

```csharp
public Startup(IConfiguration configuration)
{
    Configuration = configuration;
}

public IConfiguration Configuration { get; }
```

Özgün uygulamanın ayarlarını kullanarak başvurduğu `ConfigurationManager.AppSettings` . Bu terimin tüm başvuruları için hızlı arama, yeni uygulama gereksinimlerinin ayar kümesini verir. Yalnızca iki tane vardır:

- `UseMockData`
- `UseCustomizationData`

Uygulamanızda daha karmaşık bir yapılandırma varsa, özellikle özel yapılandırma bölümleri kullanılıyorsa, büyük olasılıkla nesneleri oluşturup uygulamanızın yapılandırmasının farklı bölümlerine bağlamak isteyeceksiniz. Bu türlere daha sonra [Seçenekler deseninin](https://docs.microsoft.com/dotnet/core/extensions/options)kullanılması erişilebilir. Ancak, başvurulan belge ' de belirtildiği gibi bu düzenin içinde kullanılmaması gerekir `ConfigureServices` . Bunun yerine, bağlantı verilen uygulama `UseMockData` yapılandırma değerine doğrudan başvuracaktır.

İlk olarak, bağlantı verilen uygulamanın `appsettings.json` dosyasını değiştirin ve iki ayarı köke ekleyin:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Warning"
    }
  },
  "AllowedHosts": "*",
  "UseMockData": "true",
  "UseCustomizationData" :  "true"
}
```

Şimdi, `ConfigureServices` özelliği özelliğinden erişmek için değiştirin `UseMockData` `Configuration` (daha önce değeri olarak ayarlarız `true` ):

```csharp
  bool useMockData = Configuration.GetValue<bool>("UseMockData");
```

Bu noktada, ayar yapılandırmadan çekilir. Diğer ayarı, `UseCustomizationData` sınıfı tarafından kullanılır `CatalogDBInitializer` . Bu sınıfı ilk kez aldığınızda, erişimi size yorum yaptı `ConfigurationManager.AppSettings["UseCustomizationData"]` . Şimdi de ASP.NET Core yapılandırma kullanmak için değiştirme zamanı. Yapıcısını `CatalogDBInitializer` aşağıdaki gibi değiştirin:

```csharp
  // add using Microsoft.Extensions.Configuration
  public CatalogDBInitializer(CatalogItemHiLoGenerator indexGenerator,
      IConfiguration configuration)
  {
      this.indexGenerator = indexGenerator;
      useCustomizationData = configuration.GetValue<bool>("UseCustomizationData");
  }
```

Web uygulaması içindeki yapılandırmaya yapılan tüm erişim, yeni türü kullanmak için bu şekilde değiştirilmelidir `IConfiguration` . .NET Framework yapılandırmasına erişim gerektiren bağımlılıklar, web projesine eklenen bir *app.config* dosyasında bu tür ayarları içerebilir. Bağımlı projeler `ConfigurationManager` , ayarlarına erişmek için ile çalışabilir ve bu yaklaşımı zaten kullanıyorsa herhangi bir değişiklik gerektirmemelidir. Ancak, ASP.NET Core uygulamalar kendi yürütülebilir dosyası olarak çalıştığı için, *web.config* başvurmazlar, ancak bunun yerine *app.config*. Ayarları eski uygulamanın *web.config* dosyasından ASP.NET Core uygulamasındaki yeni bir *app.config* dosyasına geçirerek, `ConfigurationManager` ayarlarına erişmek için kullanılan bileşenler düzgün şekilde çalışmaya devam edecektir.

Uygulamanın geçişi neredeyse tamamlanmıştır. Kalan tek görev, veri erişim yapılandırması.
  
## <a name="data-access-considerations"></a>Veri erişim konuları

.NET Framework çalıştıran ASP.NET Core uygulamalar Entity Framework (EF) ile yararlanmaya devam edebilir. Artımlı geçiş gerçekleştirmede, uygulamanın veri erişiminin bağlantı noktasında kullanım için bağlantı kurmaya çalışmadan önce EF 6 ile çalışmaya alınması EF Core çalışıyor olabilir. Bu şekilde, başka bir geçiş çabasında başlamadan önce uygulamanın geçişine ilişkin herhangi bir sorun belirlenebilir ve çözülebilir.

Bu durumda, bu iş Autofac içinde gerçekleştirildiğinden, eShop örnek geçişinin içindeki EF 6 ' ı yapılandırmak özel bir iş gerektirmez `ApplicationModule` . Tek sorun şu anda `CatalogDBContext` sınıfın *web.config* bağlantı dizesini okumaya çalışacağı bir sorundur. Bunu çözmek için bağlantı ayrıntılarının *appsettings.js* için eklenmesi gerekir. Sonra bağlantı dizesinin oluşturulduğu sırada içine geçirilmesi gerekir `CatalogDBContext` .

Bağlantı dizesini içerecek şekilde *appsettings.js* güncelleştirin. Tam dosya burada listelenmiştir:

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=(localdb)\\mssqllocaldb;Database=eShopPorted;Trusted_Connection=True;MultipleActiveResultSets=true"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Warning"
    }
  },
  "AllowedHosts": "*",
  "UseMockData": "false",
  "UseCustomizationData": "true"
}
```

Bağlantı dizesinin oluşturulduğu sırada oluşturucuya geçirilmesi gerekir `DbContext` . Örnekler Autofac tarafından oluşturulduğundan, değişikliğin ' de yapılması gerekir `ApplicationModule` . Modülünü oluşturucusunda bir içinde olacak şekilde değiştirin `connectionString` ve bir alana atayın. Sonra `CatalogDBContext` bağlantı dizesini parametre olarak eklemek için kaydını değiştirin:

```csharp
builder.RegisterType<CatalogDBContext>()
  .WithParameter("connectionString", _connectionString)
  .InstancePerLifetimeScope();
```

Parametresi ayrıca kendi kendine yeni bir Oluşturucu aşırı yüküne eklenmelidir `CatalogDBContext` :

```csharp
public CatalogDBContext(string connectionString) : base(connectionString)
{
}
```

Son olarak, `ConfigureServices` öğesinden bağlantı dizesini okumalı `Config` ve onu `ApplicationModule` örnekleyen zaman içine iletmelidir:

```csharp
bool useMockData = Configuration.GetValue<bool>("UseMockData");
string connectionString = Configuration.GetConnectionString("DefaultConnection");
builder.RegisterModule(new ApplicationModule(useMockData, connectionString));
```

Bu kodla birlikte, uygulama daha önce olduğu gibi çalışır, bir SQL Server veritabanına bağlanarak `UseMockData` `false` .

Uygulama bu noktada dağıtılabilir ve çalıştırılabilir, ASP.NET Core dönüştürülür, ancak yine de .NET Framework ve EF 6 ' da çalışır. İsterseniz, uygulama .NET Core ve Entity Framework Core çalışmak üzere geçirilebilir ve bu, önceki bölümlerde açıklanan ek avantajları getirir. Entity Framework özel olarak, [Bu belge EF Core ve EF 6](https://docs.microsoft.com/ef/efcore-and-ef6/) ' ı karşılaştırır ve hangi kitaplığın her bir onlarca ayrı özelliği desteklediğini gösteren bir kılavuz içerir.

### <a name="migrate-to-entity-framework-core"></a>Entity Framework Core geçir

EF Core geçirilecek bir kararın olduğu varsayıldığında, özellikle özgün uygulama kod tabanlı bir model yaklaşımı kullanıyorsa, adımlar oldukça basittir. [EF 6 ' dan EF Core bağlantı noktasına hazırlarken](https://docs.microsoft.com/ef/efcore-and-ef6/porting/), kullanacağınız EF Core hedef sürümündeki özelliklerin kullanılabilirliğini gözden geçirin. [Kod tabanlı bir modelden taşıma](https://docs.microsoft.com/ef/efcore-and-ef6/porting/port-code) [ve edmx tabanlı modelden taşıma ile](https://docs.microsoft.com/ef/efcore-and-ef6/porting/port-edmx) ilgili belgeleri gözden geçirin.

EF Core 2,2 ' ye yükseltmek için, ilgili temel adımlar uygun NuGet paketlerini ve güncelleştirme ad alanlarını eklemektir. Sonra bağlantı dizesinin türüne nasıl geçtiğini `DbContext` ve bunların bağımlılık ekleme için nasıl bağlı olduklarını ayarlayın.

EF Core, projeye bir paket başvurusu olarak eklenir:

```xml
<PackageReference Include="Microsoft.EntityFrameworkCore" Version="2.2.6" />
```

EF 6 başvurusu kaldırılır:

```xml
<PackageReference Include="EntityFramework" Version="6.2.0" />
```

Derleyici ve içindeki hataları rapor eder `CatalogDBContext` `CatalogDBInitializer` . `CatalogDbContext` eski ad alanlarının kaldırılıp değiştirilmeleri gerekir `Microsoft.EntityFrameworkCore` . Oluşturucuları kaldırılabilir. `DbModelBuilder` ile değiştirilmelidir `ModelBuilder` . Türleri yapılandırmaya yönelik yardımcı yöntemler, uygulayan ayrı sınıflara taşınır `IEntityTypeConfiguration<T>` . Sonra `CatalogDBContext` sınıfın `OnModelCreating` yöntemi yalnızca şu şekilde olur:

```csharp
protected override void OnModelCreating(ModelBuilder builder)
{
    builder.ApplyConfigurationsFromAssembly(Assembly.GetExecutingAssembly());

    base.OnModelCreating(builder);
}
```

Dahil edilen diğer değişiklikler şunlardır:

- `HasDatabaseGeneratedOption(DatabaseGeneratedOption.None)` yenisiyle değiştirilmiş `ValueGeneratedNever()`
- `HasRequired<T>` yenisiyle değiştirilmiş `HasOne<T>`
- `Microsoft.EntityFrameworkCore.Relational`Paket yüklendi
- `CatalogDBContext` `DbContextOptions` Temel oluşturucuya almak ve iletmek için bir Oluşturucu ekleyin

İçin örnek bir yapılandırma sınıfı `CatalogType` aşağıda gösterilmiştir:

```csharp
using Microsoft.EntityFrameworkCore;
using Microsoft.EntityFrameworkCore.Metadata.Builders;

namespace eShopPorted.Models.Config
{
    public class CatalogTypeConfig : IEntityTypeConfiguration<CatalogType>
    {
        public void Configure(EntityTypeBuilder<CatalogType> builder)
        {
            builder.ToTable(nameof(CatalogType));

            builder.HasKey(ci => ci.Id);

            builder.Property(ci => ci.Id)
               .IsRequired();

            builder.Property(cb => cb.Type)
                .IsRequired()
                .HasMaxLength(100);
        }
    }
}
```

`CatalogDBInitializer`Ve temel sınıfı, `CreateDatabaseIfNotExists<T>` EF Core ile uyumsuzdur. Bu sınıfın amacı, veritabanını oluşturmak ve tohum sağlamaktır. EF Core kullanmak, bu yöntemleri kullanarak [bir `DbContext` için ilişkili veritabanını oluşturup bırakacak](https://docs.microsoft.com/ef/core/managing-schemas/ensure-created) :

```csharp
dbContext.Database.EnsureDeleted();
dbContext.Database.EnsureCreated();
```

EF Core içindeki sağlama verileri el ile betiklerle veya tür yapılandırmasının bir parçası olarak yapılabilir. Diğer varlık özellikleriyle birlikte, çekirdek veriler `IEntityTypeConfiguration` kullanılarak sınıflarda yapılandırılabilir `builder.HasData()` . Özgün uygulama, *Kurulum* dizinindeki CSV dosyalarından çekirdek verileri yükledi. Yalnızca birkaç öğe olduğu verildiğine göre, bu veri kayıtları varlık yapılandırmasının bir parçası olarak eklenebilir. Bu yaklaşım, seyrek olarak değişen tablolardaki arama verileri için iyi sonuç verir. Aşağıdaki ' `CatalogTypeConfig` ın metodunu eklemek, `Configure` veritabanı oluşturulduğunda ilişkili satırların mevcut olmasını sağlar:

```csharp
builder.HasData(
    new CatalogType { Id = 1, Type = "Mug" },
    new CatalogType { Id = 2, Type = "T-Shirt" },
    new CatalogType { Id = 3, Type = "Sheet" },
    new CatalogType { Id = 4, Type = "USB Memory Stick" }
);
```

İlk uygulama, `PreconfiguredData` ve için veri içeren bir sınıfı içerir `CatalogBrand` `CatalogType` , bu nedenle bu yöntemi kullanarak çağrı şu `HasData` şekilde azaltılır:

```csharp
builder.HasData(
    PreconfiguredData.GetPreconfiguredCatalogBrands()
);
```

`CatalogItem`Verilerin de çekilmesi `PreconfiguredData` ve ilişkili görüntülerin kaynak denetimde tutulup tutulmalarından ve uygulamanın çalışması için gereken son tablo olduğu varsayıldığında. `CatalogDBInitializer`Sınıfı, tüm başvuruları ile birlikte kaldırılabilir. Bu `CatalogItemHiLoGenerator` sınıf ve DIZINDEKI SQL dosyaları `Infrastructure` , bunlara yapılan başvurularla birlikte da kaldırılır (içinde `CatalogService` `ApplicationModule` ).

İçin özel anahtar Oluşturucu sınıflarının yok etme özelliğiyle `CatalogItem` , bu kod şu kaynaktan kaldırılmıştır `CatalogItemConfig` :

```csharp
builder.Property(ci => ci.Id)
    .ValueGeneratedNever()
    .IsRequired();
```

Bu değişikliklerle ASP.NET Core uygulaması oluşturulur, ancak yine de bağımlılık ekleme için yapılandırılması gereken EF Core çalışmaz. EF Core ile, yapılandırmanın en kolay yolu `ConfigureServices` :

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
    bool useMockData = Configuration.GetValue<bool>("UseMockData");
    if (!useMockData)
    {
        string connectionString = Configuration.GetConnectionString("DefaultConnection");

        services.AddDbContext<CatalogDBContext>(options =>
            options.UseSqlServer(connectionString)
        );
    }

    // Create Autofac container builder
    var builder = new ContainerBuilder();
    builder.Populate(services);
    builder.RegisterModule(new ApplicationModule(useMockData));

    ILifetimeScope container = builder.Build();

    return new AutofacServiceProvider(container);
}
```

Autofac 'in son sürümü `ApplicationModule` , uygulamanın sahte verileri kullanmak üzere yapılandırılıp yapılandırılmadığını bağlı olarak yalnızca bir tür yapılandırır:

```csharp
public class ApplicationModule : Module
{
    private bool _useMockData;

    public ApplicationModule(bool useMockData)
    {
        _useMockData = useMockData;
    }
    
    protected override void Load(ContainerBuilder builder)
    {
        if (_useMockData)
        {
            builder.RegisterType<CatalogServiceMock>()
                .As<ICatalogService>()
                .SingleInstance();
        }
        else
        {
            builder.RegisterType<CatalogService>()
                .As<ICatalogService>()
                .InstancePerLifetimeScope();
        }
    }
}
```

Çapraz olmayan uygulama çalışır, ancak sahte verileri kullanmak üzere yapılandırıldıysa hiçbir veri görüntülemez. Üzerinden eklenen çekirdek veriler `HasData` yalnızca geçişler uygulandığında eklenir. Kaynak uygulama geçişleri kullanmamıştı ve varsa, olarak geçirilmez. En iyi yaklaşım, yeni bir geçiş betiği ile başlamadır. Bunu yapmak için, için bir paket başvurusu ekleyin `Microsoft.EntityFrameworkCore.Design` ve proje kökünde bir Terminal penceresi açın. Ardından şunu çalıştırın:

```dotnetcli
dotnet ef migrations add Initial
```

Varsa, var olan *Esatlamalı* veritabanını bırakın, ardından şunu çalıştırın:

```dotnetcli
dotnet ef database update
```

Bu, veritabanını oluşturur ve ekler. Şimdi, bir kaç küçük güncelleştirme bırakılmış olacak şekilde çalıştırılmaya hazır.

## <a name="fix-all-todo-tasks"></a>Tüm TODO görevlerini düzeltir

Bu noktada, bağlantı verilen uygulamayı çalıştırmak sayfada hiçbir resmin gösterildiğine işaret edilir. Bunun nedeni `PictureUri` öğesinin özelliğinin hiçbir şekilde `CatalogItem` ayarlanmayacağı. `TODO`Visual Studio 'nun **görev listesi** kullanarak oluşturduğumuz öğelerin listesine bakarak, `CatalogController` "Wwwroot 'dan başvuru PIC" notunda yer alan tek bir tane. Söz konusu kod şu şekilde yapılır:

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    //TODO: Reference pic from wwwroot
    //item.PictureUri = this.Url.RouteUrl(PicController.GetPicRouteName, new { catalogItemId = item.Id }, this.Request.Url.Scheme);
}
```

En basit çözüm, sitenin genel *Wwwroot/PICS* dizinindeki ortak görüntü dosyalarına başvurmanız. Bu görev, yöntemi aşağıdaki kodla değiştirilerek gerçekleştirilebilir:

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    item.PictureUri = $"/Pics/{item.Id}.png";
}
```

Bu değişiklik ile, uygulamayı çalıştırmak görüntüleri daha önce olduğu gibi çalışır.

## <a name="additional-mvc-customizations"></a>Ek MVC özelleştirmeleri

*Eshoplegacymvc* uygulaması oldukça basittir, bu nedenle varsayılan MVC davranışı açısından yapılandırılması çok önemlidir. Ancak, CORS, filtreler ve yol kısıtlamaları gibi ek MVC bileşenleri yapılandırmanız gerekiyorsa, genellikle bu bilgileri ' de sağlarsınız; `Startup.ConfigureServices` burada `UseMvc` çağrılır. Örneğin, aşağıdaki kod listesi [CORS](https://docs.microsoft.com/aspnet/core/security/cors?view=aspnetcore-2.2&preserve-view=true) 'yi yapılandırır ve genel eylem filtresi ayarlıyor:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddCors(options =>
    {
        options.AddPolicy(MyAllowSpecificOrigins,
            builder =>
                builder.WithOrigins("http://example.com", "http://www.contoso.com")
                    .AllowAnyHeader()
                    .AllowAnyMethod());
    });

    services.AddMvc(options =>
    {
      options.Filters.Add(new SampleGlobalActionFilter());
    }).SetCompatibilityVersion(CompatibilityVersion.Version_2_2);
}
```

> [!Note]
> CORS 'yi yapılandırmayı bitirebilmeniz için de ' de çağırmanız gerekir `app.UseCors()` `Configure` .

[Özel model ciltçileri](https://docs.microsoft.com/aspnet/core/mvc/advanced/custom-model-binding?view=aspnetcore-2.2&preserve-view=true), Formatters ve daha fazlasını ekleme gibi diğer gelişmiş senaryolar, ayrıntılı ASP.NET Core belgeleri kapsamında ele alınmıştır. Genellikle bunlar tek bir denetleyiciye veya eyleme göre veya bir önceki kod listesinde gösterilen aynı seçenek yaklaşımını kullanarak küresel olarak uygulanabilir.

## <a name="other-dependencies"></a>Diğer bağımlılıklar

WCF istemci türü ve izleme kodu gibi eski yapılandırma modeline bağımlılığı olan .NET Framework özellikleri kullanan bağımlılıklar, bu sırada değiştirilmeli. Bu türlerin yapılandırma bilgilerini doğrudan çekmesini yerine, kod içinde yapılandırılması gerekir. Örneğin, bir ASP.NET uygulamasının kullanılmak üzere *web.config* YAPıLANDıRıLMıŞ bir WCF hizmetine bağlantı, `basicHttpBinding` bunun yerine aşağıdaki kodla programlı olarak yapılandırılabilir:

```csharp
var binding = new BasicHttpBinding();
binding.MaxReceivedMessageSize = 2_000_000;

var endpointAddress = new EndpointAddress("http://localhost:9200/ExampleService");

var myClient = new MyServiceClient(binding, endpointAddress);
```

Ayarları için yapılandırma dosyalarına güvenmek yerine, WCF istemcileri ve diğer .NET Framework türleri kodda belirtilen ayarlara sahip olmalıdır. Bu şekilde yapılandırıldığında, bu türler ASP.NET Core 2,2 uygulamalarında çalışmaya devam edebilir.

## <a name="references"></a>Başvurular

- [GitHub deposu için Eshopmodernize](https://github.com/dotnet-architecture/eShopModernizing)
- [API ve Viewmodelleriniz etki alanı modellerine başvurmamalıdır](https://ardalis.com/your-api-and-view-models-should-not-reference-domain-models/)
- [Geliştirici özel durum sayfası ara yazılımı](https://docs.microsoft.com/aspnet/core/fundamentals/error-handling#developer-exception-page)
- [HasData EF Core derinlemesine bakış](https://docs.microsoft.com/archive/msdn-magazine/2018/august/data-points-deep-dive-into-ef-core-hasdata-seeding)

>[!div class="step-by-step"]
>[Önceki](strategies-migrating-in-production.md) 
> [Sonraki](deployment-scenarios.md)
