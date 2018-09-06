---
title: Taşınabilir Sınıf Kitaplığı ile Platformlar Arası Geliştirme
ms.date: 07/18/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bd5ad69cc661005d20db4c4bcdda762c6432f416
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43886064"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>Taşınabilir Sınıf Kitaplığı ile Platformlar Arası Geliştirme
.NET Framework taşınabilir sınıf kitaplığı proje türü Visual Studio'da platformlar arası uygulamalar ve kitaplıklar Microsoft platformları için hızlı ve kolay bir şekilde oluşturmanıza yardımcı olur.  

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 Taşınabilir sınıf kitaplıkları, saat ve geliştirme ve test maliyetlerini azaltmaya yardımcı olabilir. Bu proje türü .NET Framework taşınabilir derlemeler yazmak ve oluşturmak için kullanın ve ardından Windows ve Windows Phone gibi birden çok platformu hedefleyen uygulamalar bu derlemelerin başvuru.  
  
 Visual Studio'da bir taşınabilir sınıf kitaplığı projesi oluşturun ve bunu geliştirmeye başlayın bile sonra hedef platformlar değiştirebilirsiniz. Visual Studio, kodunuzda yapmanız gereken değişiklikleri belirlemenize yardımcı olur, yeni derlemeler kitaplığıyla derlenir.  
  
 Bu makalede, Visual Studio'da uygulama geliştirme ele alınmaktadır ancak Microsoft uygulamaları ve kitaplıkları Xamarin gibi diğer araçları ile geliştirmek için kullanabileceğiniz taşınabilir sınıf kitaplığı başvuru bütünleştirilmiş kodları da sağlar. Tüm .NET Framework tabanlı çalışma zamanı üzerinde Microsoft dışındaki platformlar üzerinde bu uygulamaları ve kitaplıkları'nı kullanabilirsiniz. Başvuru bütünleştirilmiş kodları hakkında daha fazla bilgi için blog girişine bakın [taşınabilir sınıf kitaplığı (PCL) tüm platformlarda kullanılabilir](https://blogs.msdn.com/b/dotnet/archive/2013/10/14/portable-class-library-pcl-now-available-on-all-platforms.aspx). Derlemeleri yüklemek için bkz [Microsoft .NET taşınabilir kitaplık başvuru derlemelerini](https://www.microsoft.com/download/details.aspx?id=40727) Microsoft Download Center'daki. Xamarin ile derlemeleri kullanma hakkında daha fazla bilgi için blog girişine bakın [PCL ve Xamarin için artık etkin .NET NuGet kitaplıklarını](https://blogs.msdn.com/b/dotnet/archive/2013/11/13/pcl-and-net-nuget-libraries-are-now-enabled-for-xamarin.aspx).  
  
 Visual Studio ile taşınabilir sınıf kitaplığı geliştirmenize yardımcı olması için şablonlar sağlar. Visual Studio'nun hangi sürümünün kullanmakta olduğunuz bağlı olarak, kullanılabilir şablonlar ve menüler bu makalede açıklanan olanlardan farklı olabilir.  
  
> [!WARNING]
>  Visual Studio 2013 Update 2, güncelleştirmeleri taşınabilir sınıf kitaplığı şablonları içerir. Visual Studio ve Visual Studio 2013 ile aynı bilgisayara yüklenmiş önceki bir sürümü varsa ve güncelleştirme 2, değişiklikleri yüklemeyi **hedef Framework'ü** seçimleri her iki Visual Studio sürümlerine uygulanır.  
  
 Bu konuda:  
  
 [Visual Studio desteği](#vs_support)  
 [Taşınabilir sınıf kitaplığı projesi oluşturma](#create_pcl)  
 [Hedef seçenekleri](#platforms)  
 [Hedefleri değiştirme](#change_targets)  
 [Desteklenen özellikler](#features)  
 [Desteklenen türler ve Üyeler](#members)  
 [Taşınabilir Sınıf kitaplığındaki API farklılıkları](#API_diff)  
 [Taşınabilir sınıf kitaplığı kullanma](#using)  
  
<a name="vs_support"></a>   
## <a name="visual-studio-support"></a>Visual Studio desteği  
 Taşınabilir sınıf kitaplığı için Visual Studio desteği, kullanmakta olduğunuz Visual Studio sürümüne bağlıdır. Bazı durumlarda, ihtiyacınız olan her şey gerekir ve diğer durumlarda, ek öğeleri yüklemek aşağıdaki tabloda gösterildiği gibi gerekir.  
  
|Visual Studio SKU|Taşınabilir sınıf kitaplığı oluşturma desteği|  
|-----------------------|---------------------------------------------------|  
|Visual Studio 2010, Professional, Premium veya Ultimate|Evet, yükleme sırasında [taşınabilir Kütüphane Araçları](https://marketplace.visualstudio.com/items?itemName=BCLTeam.PortableLibraryTools2).|  
|Visual Studio 2010 Express sürümleri|Hayır.|  
|Visual Studio 2012 Professional, Premium veya Ultimate|Evet. Windows Phone 8.0 podporu androidu Pro [Windows Phone SDK 8.0](https://www.microsoft.com/download/details.aspx?id=35471).|  
|Visual Studio Express 2012 sürümleri|Hayır.|  
|Visual Studio 2013 Professional, Premium veya Ultimate|Evet. Windows Phone 8.1 podporu androidu Pro [Visual Studio 2013'ün en son sürümü](https://visualstudio.microsoft.com/vs/older-downloads/).|  
|Windows için Visual Studio Community 2013|Evet, yükleme sırasında [en son sürümünü Visual Studio Community 2013](https://visualstudio.microsoft.com/vs/older-downloads/), güncelleştirme 2 içerir.|  
  
<a name="create_pcl"></a>   
## <a name="creating-a-portable-class-library-project"></a>Taşınabilir sınıf kitaplığı projesi oluşturma  
 Taşınabilir sınıf kitaplığı oluşturmak için Visual Studio'da sağlanan şablonlarından birini kullanmanız gerekir. Yeni bir proje oluşturun ve **yeni proje** iletişim kutusunun **şablonları**(C# veya Visual Basic) hedef dilinizi seçin ve ardından hedeflemek istediğiniz platformları seçin. Sonraki adımda ek platformları seçebilirsiniz.  
  
 Visual Studio 2013 güncelleştirme 2'de seçtiğiniz **sınıf kitaplığı (taşınabilir)** seçtiğiniz dili ve taşınabilir sınıf kitaplığı oluşturmak için platform şablonu. Aşağıdaki platformlar için bu şablonu görürsünüz:  
  
-   Store uygulamaları  
  
-   Windows Masaüstü  
  
-   Silverlight  
  
 Bir kitaplığı hedef Windows Phone 8.1 ve Windows 8.1 için C# dilinde oluşturmak istiyorsanız, seçebileceğiniz **Store uygulamaları**ve ardından **sınıf kitaplığı (Evrensel uygulamaları için taşınabilir)**.  
  
 ![Store uygulamaları için taşınabilir sınıf kitaplığı](../../../docs/standard/cross-platform/media/storeuniversalpcl.png "StoreUniversalPCL")  
  
 Bu şablon, hedefler olarak Windows 8.1 ve Windows Phone 8.1 otomatik olarak seçer. Yalnızca Windows Phone 8.1 veya Windows 8.1 hedefleyen bir kitaplık oluşturursanız, hedef platformları değiştirmek ve platformları daha sonra ekleyebilirsiniz.  
  
 Visual Studio 2012 veya Visual Studio 2013 güncelleştirme 2 olmadan kullanıyorsanız, yeni bir proje oluşturup **taşınabilir sınıf kitaplığı** taslağı altından Visual C# veya Visual Basic.  
  
 ![Seçim taşınabilir kitaplık projesinin](../../../docs/standard/cross-platform/media/portablelibrary-start.png "PortableLibrary_start")  
  
 **Taşınabilir sınıf kitaplığı Ekle** iletişim kutusu görünür ve ek platformları seçebilirsiniz. İletişim kutusu seçtiğiniz hedeflerini temel alarak uyumluluğu uyarı verir.  
  
 ![VS2013 için değişiklik hedef çerçeveleri iletişim](../../../docs/standard/cross-platform/media/clr-pcl-changeframeworks.png "CLR_PCL_ChangeFrameworks")  
Visual Studio 2013 güncelleştirme 2 için taşınabilir sınıf kitaplığı iletişim kutusu Ekle  
  
 Visual Studio 2012 veya Visual Studio 2013 kullanıp bağımsız olarak, bir taşınabilir sınıf kitaplığı projesi oluşturun veya projeyi oluşturduktan sonra hedef platformları değiştirmek için proje özelliklerini kullanabilirsiniz platformları seçebilirsiniz.  
  
<a name="platforms"></a>   
## <a name="target-options"></a>Hedef seçenekleri  
 Taşınabilir sınıf kitaplığı projesi oluşturduğunuzda, işletim sistemi ve .NET Framework sürümünü hedeflemek istediğinizi seçebilirsiniz. Visual Studio 2013 kullanıyorsanız ve yüklediğiniz güncelleştirme 2 veya daha sonra seçebileceğiniz **sınıf kitaplığı (Evrensel uygulamaları için taşınabilir)** Windows 8.1 ve Windows Phone 8. 1'i hedefleyen taşınabilir sınıf kitaplığı oluşturmak için şablon. Aşağıdaki tabloda kullanılabilir hedeflerden kullanmakta olduğunuz Visual Studio sürümüne bağlı olarak gösterilir.  
  
|Hedef seçeneği|Visual Studio 2012|Visual Studio 2013|Visual Studio 2013 Update 2 veya üzeri|  
|-|-|-|-|  
|.NET Framework|-.NET framework 4 ve üzeri<br /><br /> -.NET framework 4.0.3 ve üstü cihazları<br /><br /> -.NET framework 4.5|-.NET framework 4 ve üzeri<br /><br /> -.NET framework 4.0.3 ve üstü cihazları<br /><br /> -.NET framework 4.5 ve üzeri<br /><br /> -.NET framework 4.5.1|-.NET framework 4<br /><br /> -.NET framework 4.0.3<br /><br /> -.NET framework 4.5<br /><br /> -.NET framework 4.5.1|  
|Windows Phone|-Windows Phone 7 ve üzeri<br /><br /> -Windows Phone 7.5 ve üzeri<br /><br /> -Windows Phone 8|-Windows Phone 8|-Windows Phone Silverlight 8<br /><br /> -Windows Phone Silverlight 8.1<br /><br /> Windows çalışma zamanı ve XAML desteği için seçin:<br /><br /> -Windows Phone 8.1|  
|Windows Mağazası|-Windows Store uygulamaları için .NET|-Windows Store Apps (Windows 8) ve üzeri<br /><br /> -Windows Store Apps (Windows 8.1)|-Windows 8<br /><br /> -Windows 8.1|  
|-Silverlight|-Silverlight 4 ve üzeri<br /><br /> -Silverlight 5|-Silverlight 5|-Silverlight 5|  
|Xbox|-Xbox 360|Yok|Yok|  
  
<a name="change_targets"></a>   
## <a name="changing-targets"></a>Hedefleri değiştirme  
 Taşınabilir sınıf kitaplığı şablonu seçin, varsayılan platformları, seçilir, ancak bu varsayılan değişir bağlı olarak Visual Studio'nun hangi sürümünün yüklü olduğunu ve hangi hedeflerin, daha önce seçtiğiniz. Platformları, taşınabilir sınıf kitaplığı oluşturduğunuzda veya taşınabilir sınıf kitaplığı geliştirilmesini başladıktan sonra değiştirebilirsiniz.  
  
 İçinde projenizi oluşturduktan sonra hedeflerini değiştirmek istiyorsanız **Çözüm Gezgini**, taşınabilir sınıf kitaplığı projeniz (çözümü değil) için kısayol menüsünü açın ve ardından **özellikleri** . Proje özellikleri sayfasında **Kitaplığı** projeniz şu anda hedefler sekmesi platformları gösterir.  
  
 ![Proje Özellikleri](../../../docs/standard/cross-platform/media/portablelibrary-projectproperties.png "PortableLibrary_ProjectProperties")  
Visual Studio 2013 güncelleştirme 2 için taşınabilir sınıf kitaplığı özellik sayfası  
  
 Ekleme veya kaldırma hedefleri için seçin **değişiklik** düğmesini seçin ve uygun onay kutularını temizleyin.  
  
 Hedefleri değiştirdiğinizde, projenizin geliştirmek için kullanabileceğiniz API'ler seçiminizi eşleşecek şekilde değişir. Visual Studio değiştirme hedefleri sonucunda ortaya çıkabilecek uyarıları ve hataları bildirir.  
  
 Taşınabilirlik değerlendirmek istiyorsanız, önce derlemelerinizin Visual Studio'da değişiklik yapmak, kullanabilirsiniz [.NET Portability Analyzer](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b).  
  
 Menü seçeneklerini, kullanmakta olduğunuz Visual Studio sürümüne bağlı olarak değişir.  
  
 ![Hedefi Değiştir](../../../docs/standard/cross-platform/media/portablelibrary.png "PortableLibrary_")  
Visual Studio 2012'de değişiklik hedefleri iletişim kutusu  
  
<a name="features"></a>   
## <a name="supported-features"></a>Desteklenen özellikler  
 Mevcut platformlar ve sürümlerde hangi özelliklerin desteklendiği aşağıdaki tabloda gösterilmektedir. Bazı durumlarda, Microsoft destek NuGet Paket sürümü ile eklemiştir ve bu not. .NET Framework NuGet paketleri hakkında daha fazla bilgi için bkz. [.NET Framework ve bant dışı yayınlar](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md).  
  
|Özellik|.NET Framework|.NET Framework|.NET Framework|Windows Mağazası|Windows Mağazası|Windows Phone Mağazası|Windows Phone Silverlight|Windows Phone Silverlight|Windows Phone Silverlight|Silverlight|Silverlight|Xbox 360|  
|-------------|--------------------|--------------------|--------------------|-------------------|-------------------|-------------------------|-------------------------------|-------------------------------|-------------------------------|-----------------|-----------------|--------------|  
||**4**|**4.0.3**|**4.5**|**8**|**8.1**|**8.1**|**7.5**|**8**|**8.1**|**4**|**5**||  
|Çekirdek kitaplıkları|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|  
|Zaman uyumsuz desteği|➊|➊|✓|✓|✓|✓|➊|➊|✓|➊|➊||  
|Sıkıştırma|||✓|✓|✓|✓||➋|➋||||  
|Veri açıklamaları||✓|✓|✓|✓|||||✓|✓||  
|Dynamic anahtar sözcüğü|✓|✓|✓|✓|✓|||||✓|✓||  
|HTTPClient|➌|➌|✓|✓|✓|✓|➌|➌|➌|➌|➌||  
|IQueryable|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|Dil ile Tümleşik Sorgu (LINQ)|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|Yönetilen Genişletilebilirlik ağ (MEF)|✓|✓|✓|✓|✓|||||✓|✓||  
|Ağ Sınıf Kütüphanesi (ASK)|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|Seri hale getirme (veri anlaşması, XML ve JSON)|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|System.Numerics|✓|✓|✓|✓|✓|||||✓|✓||  
|Görünüm Model (MVVM)|||✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|Windows Communication Foundation (WCF)|✓|✓|✓|✓|✓||✓|✓|✓|✓|✓||  
|Windows çalışma zamanı API'ları|||||✓|✓|||||||  
|Windows.UI.xaml|||||✓|✓|||||||  
|XLINQ||✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|  
  
 ➊ Gerektirir [Microsoft Async](https://www.nuget.org/packages/Microsoft.Bcl.Async/) paket  
 ➋ Gerektirir [Microsoft Compression](https://www.nuget.org/packages/Microsoft.Bcl.Compression) paket  
 ➌ Gerektirir [Microsoft HTTP istemcisi kitaplıkları](https://www.nuget.org/packages/Microsoft.Net.Http) paket  
  
> [!WARNING]
>  Başvuru hataları karşılaşabilirsiniz [Microsoft Compression](https://www.nuget.org/packages/Microsoft.Bcl.Compression) ve [Microsoft HTTP istemcisi kitaplıkları](https://www.nuget.org/packages/Microsoft.Net.Http) bir Windows Phone Silverlight 8.1 uygulaması tarafından kullanılan bir taşınabilir kitaplık paketleri. Daha fazla bilgi için [Platform uyumluluğu ve Windows Phone Silverlight 8.1 uygulamaları için önemli değişiklikler](https://docs.microsoft.com/previous-versions/windows/apps/dn642084(v=vs.105)).  
  
<a name="members"></a>   
## <a name="supported-types-and-members"></a>Desteklenen türler ve Üyeler  
 Türler ve taşınabilir sınıf kitaplığı projesinde kullanılabilir üyeler çeşitli uyumluluk unsurları tarafından zorlanır:  
  
-   Bunlar, seçtiğiniz hedef arasında paylaşılabilir olmalıdır.  
  
-   Bu hedefler arasında benzer şekilde davranmalıdır.  
  
-   Kaldırılma için aday olmamalıdır.  
  
-   Özellikle destekleyici üyeler taşınabilir olmadığında bunlar taşınabilir ortamda anlamlı olmalıdırlar.  
  
 Örneğin, yalnızca Windows 8.1 ve Windows Phone 8.1 hedeflediğinizde taşınabilir sınıf kitaplığı UI ilgili türleri içerir. Ayrıca, taşınabilir sınıf kitaplığı sunulmasıyla önce yayımlanan bu platformları (örneğin, Xbox, .NET Framework 4 ve Windows Phone 7) hedeflediğinizde kısıtlamalarla karşılaşabilirsiniz. .NET Framework paketleri bazı eski bu platformlar için taşınabilir sınıf kitaplığı desteği geliştirir NuGet aracılığıyla serbest bırakır. Daha fazla bilgi ve NuGet paketleri listesi için bkz: [.NET Framework ve bant dışı yayınlar](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md).  
  
 Üye taşınabilir sınıf kitaplığı ve seçili hedeflerinizi destekleniyorsa, projenizdeki ıntellisense'te görünür. Ayrıca, taşınabilir sınıf kitaplığı simgesi ![taşınabilir kitaplığı tarafından desteklenen](../../../docs/standard/cross-platform/media/portablelibrary-referenceicon.png "PortableLibrary_ReferenceIcon") üyeleri tablolarında yer [.NET Framework sınıf kitaplığı](https://msdn.microsoft.com/library/mt472912.aspx) yanındaki desteklenen üyeleri. Örneğin, aşağıdaki üyeleri tablo gösteren <xref:System.String.Chars%2A> özelliğinde <xref:System.String> sınıfı, taşınabilir Sınıf Kitaplığı'nda desteklenir:  
  
 ![Desteklenen üye simgesi](../../../docs/standard/cross-platform/media/plibsupportedmemberlist.png "PlibSupportedMemberList")  
Taşınabilir sınıf kitaplığı simgesi  
  
 Ayrıca bakabilirsiniz **sürüm bilgisi** taşınabilir sınıf kitaplığı projesi, bir tür veya üye desteklenip desteklenmediğini belirten bir not için bir başvuru konusu bölümünü:  
  
 ![Taşınabilir kitaplık sürüm bilgilerini](../../../docs/standard/cross-platform/media/plibversioninformation.png "PlibVersionInformation")  
Sürüm bilgileri örneği  
  
 Bununla birlikte, bir API taşınabilir Sınıf Kitaplığı'nda desteklenmiyor olabilir, ancak API kullanıp kullanamayacağını bağlıdır hedeflerde, unutmayın seçin.  
  
<a name="API_diff"></a>   
## <a name="api-differences-in-the-portable-class-library"></a>Taşınabilir Sınıf kitaplığındaki API farklılıkları  
 Bütün platformlar tarafından desteklenen taşınabilir sınıf kitaplığı derlemeleri uyumlu hale getirmek için bazı üyeler biraz taşınabilir Sınıf Kitaplığı'nda değiştirildi.  
  
<a name="using"></a>   
## <a name="using-the-portable-class-library"></a>Taşınabilir Sınıf Kitaplığı Kullanma  
 Taşınabilir sınıf kitaplığı projenizi derledikten sonra sadece bunu diğer projelerden başvuruda. Erişmek istediğiniz sınıfları içeren projeyi veya belirli derlemeleri projeye ekleyebilirsiniz.  
  
 Bir taşınabilir sınıf kitaplığı derleme gerekli sürümü başvuran bir uygulamayı çalıştırmak için (veya üzeri) hedeflenen platformun bilgisayarınızda yüklü olması gerekir. Visual Studio tüm gerekli framework'leri içerdiğinden, uygulamayı geliştirirken kullandığınız bilgisayarda daha fazla değişiklik gerekmeden uygulamayı çalıştırabilirsiniz.  
  
### <a name="deploying-a-windows-store-or-windows-phone-app"></a>Bir Windows Store veya Windows Phone uygulaması dağıtma  
 Bir Windows mağazası veya Windows Phone uygulaması oluşturduğunuzda bir taşınabilir sınıf kitaplığı derleme başvuran, uygulamayı dağıtmak için ihtiyacınız olan her şey uygulama paketine dahildir ve başka bir adım gereklidir.  
  
### <a name="deploying-a-net-framework-app"></a>Dağıtımı bir .NET Framework uygulaması  
 Taşınabilir sınıf kitaplığı derlemesine başvuran bir .NET Framework uygulamasını dağıtırken, bir bağımlılık '.NET Framework'ün doğru versiyonundaki belirtmeniz gerekir. Bu bağımlılığı belirterek, gerekli sürümün uygulamanızla birlikte yüklü olup olmadığını garantiye almış olursunuz. Daha sonra bilgisayarda .NET Framework 4 ile olmalıdır ya da .NET Framework 4 hedefleyen bir [güncelleştirme](https://www.microsoft.com/download/details.aspx?id=3556), .NET Framework 4 veya .NET Framework 4.5 için 4.0.3 güncellemesi.  
  
-   ClickOnce dağıtımı ile bir bağımlılık oluşturmak için: içinde **Çözüm Gezgini**, yayımlamak istediğiniz proje için proje düğümünü seçin. (Taşınabilir sınıf kitaplığı projesine başvuran proje budur.) Menü çubuğunda, **proje**, **özellikleri**ve ardından **Yayımla** sekmesi. Üzerinde **Yayımla** sayfasında **önkoşulları**. Önkoşul olarak gerekli .NET Framework sürümünü (ya da .NET Framework 4 güncellemesini) seçin.  
  
-   Bir kurulum projesi ile bir bağımlılık oluşturmak için: içinde **Çözüm Gezgini**, Kurulum projesini seçin. Menü çubuğunda, **proje**, **özellikleri**, **önkoşulları**. Önkoşul olarak gerekli .NET Framework sürümünü seçin.  
  
 .NET Framework uygulamalarını dağıtmak hakkında daha fazla bilgi için bkz. [geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md).  
  
### <a name="deploying-a-silverlight-based-app"></a>Silverlight tabanlı bir uygulama dağıtma  
 Taşınabilir sınıf kitaplığı derleme başvurmuş Silverlight tabanlı bir uygulamayı dağıttığınızda, uygulama için gerekli minimum çalışma zamanının sürümü, hedeflenen sürümle eşleşen emin olmanız gerekir. Silverlight 4'ü hedefliyorsanız, sürüm 4.0.60129.0 veya sonraki bir sürümü olmalıdır. Dahil ederek sürümü ayarladığınız `<param name="minRuntimeVersion" value="4.0.60129.0" />` gibi Silverlight tabanlı uygulamanın bulunduğu Web sayfasındaki:  
  
```xaml  
<div id="silverlightControlHost">  
    <object data="data:application/x-silverlight-2,"   
           type="application/x-silverlight-2" width="100%" height="100%">  
    <param name="source" value="ClientBin/SilverlightApplication.xap"/>  
    <param name="onError" value="onSilverlightError" />  
    <param name="background" value="white" />  
    <param name="minRuntimeVersion" value="4.0.60129.0" />  
    <param name="autoUpgrade" value="true" />  
    <a href="https://www.microsoft.com/getsilverlight/get-started/install/"   
             style="text-decoration:none">  
      <img src=http://download.microsoft.com/download/5/1/6/5165823D-1D79-4871-8AC2-42DDDB94A5C2/PNGs/SLMedallion_ENU.png  
             alt="Get Microsoft Silverlight" style="border-style:none"/>  
    </a>  
  </object>  
   <iframe id="_sl_historyFrame"   
              style="visibility:hidden;height:0px;width:0px;border:0px">  
   </iframe>  
</div>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [MVVM ile Taşınabilir Sınıf Kitaplığı Kullanma](../../../docs/standard/cross-platform/using-portable-class-library-with-model-view-view-model.md)  
- [Çoklu Platformları Hedefleyen Kitaplıklar için Uygulama Kaynakları](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md)  
- [.NET taşınabilirlik Çözümleyicisi](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)  
- [Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
- [Dağıtım](../../../docs/framework/deployment/net-framework-applications.md)
