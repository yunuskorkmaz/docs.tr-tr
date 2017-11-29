---
title: "Taşınabilir Sınıf Kitaplığı ile Platformlar Arası Geliştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
caps.latest.revision: "95"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 697842906772c190c67e2f6ec1a4eb255229f289
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>Taşınabilir Sınıf Kitaplığı ile Platformlar Arası Geliştirme
Visual Studio'da .NET Framework taşınabilir sınıf kitaplığı proje türü, platformlar arası uygulamalar ve Microsoft platformları için kitaplıkları hızla ve kolayca oluşturmanıza yardımcı olur.  
  
 Taşınabilir sınıf kitaplıkları, saat ve geliştirme ve sınama kodu maliyetleri azaltmanıza yardımcı olabilir. Windows ve Windows Phone gibi birden çok platformu hedefleyen uygulamalardan bu derlemeler başvuru ve bu proje türü yazma ve taşınabilir .NET Framework derlemeleri oluşturmak için kullanın.  
  
 Visual Studio'da bir taşınabilir sınıf kitaplığı projesi oluşturun ve onu geliştirmeye başlayın bile sonra hedef platformlar değiştirebilirsiniz. Visual Studio, kodunuzda yapmanız gereken değişiklikleri belirlemenize yardımcı olur, yeni derlemeler kitaplıkla derlenir.  
  
 Bu makalede, Visual Studio'da uygulama geliştirme anlatılmaktadır, ancak Microsoft uygulamaları ve Xamarin gibi diğer araçları kitaplıklarıyla geliştirmek için kullanabileceğiniz taşınabilir sınıf kitaplığı başvuru derlemeleri de sağlar. Tüm .NET Framework tabanlı çalışma zamanında Microsoft dışı platformlarda bu uygulamaları ve kitaplıkları kullanabilirsiniz. Başvuru bütünleştirilmiş kodları hakkında daha fazla bilgi için blog girişine bakın [taşınabilir sınıf kitaplığı (PCL) tüm platformlarda artık kullanılabilir](http://blogs.msdn.com/b/dotnet/archive/2013/10/14/portable-class-library-pcl-now-available-on-all-platforms.aspx). Derlemeleri indirmek için bkz: [Microsoft .NET taşınabilir kitaplığı başvuru derlemeleri](http://www.microsoft.com/download/details.aspx?id=40727) Microsoft Download Center'da. Xamarin ile derlemeleri kullanma hakkında daha fazla bilgi için blog girişine bakın [PCL ve .NET NuGet için Xamarin şu anda etkin kitaplıkları](http://blogs.msdn.com/b/dotnet/archive/2013/11/13/pcl-and-net-nuget-libraries-are-now-enabled-for-xamarin.aspx).  
  
 Visual Studio ile taşınabilir sınıf kitaplığı geliştirmenize yardımcı olması için şablonlar sağlar. Visual Studio sürümünü kullanmakta olduğunuz bağlı olarak, kullanılabilir şablonlar ve menüleri bu makalede açıklanan kullanılanlardan farklı olabilir.  
  
> [!WARNING]
>  [Visual Studio 2013 güncelleştirme 2](http://go.microsoft.com/fwlink/p/?LinkId=393658) taşınabilir sınıf kitaplığı şablonları için güncelleştirmeleri içerir. Visual Studio ve aynı bilgisayarda yüklü Visual Studio 2013 önceki bir sürümü varsa ve ardından güncelleştirme 2, değişiklikleri yükleyin **hedef Framework** seçenekler her iki sürümünün de Visual Studio için uygulanır.  
  
 Bu konuda:  
  
 [Visual Studio desteği](#vs_support)  
 [Taşınabilir sınıf kitaplığı proje oluşturma](#create_pcl)  
 [Hedef seçenekleri](#platforms)  
 [Hedefleri değiştirme](#change_targets)  
 [Desteklenen özellikler](#features)  
 [Desteklenen türler ve üyeleri](#members)  
 [Taşınabilir Sınıf Kitaplığı'nda API farklılıkları](#API_diff)  
 [Taşınabilir sınıf kitaplığı kullanma](#using)  
  
<a name="vs_support"></a>   
## <a name="visual-studio-support"></a>Visual Studio desteği  
 Taşınabilir sınıf kitaplığı için Visual Studio desteği kullanmakta olduğunuz Visual Studio sürümüne bağlıdır. Bazı durumlarda, ihtiyaç duyduğunuz her şeyi gerekir ve diğer durumlarda, ek öğelere yüklemek aşağıdaki tabloda gösterildiği gibi gerekir.  
  
|Visual Studio SKU|Taşınabilir sınıf kitaplığı oluşturmak için destek|  
|-----------------------|---------------------------------------------------|  
|Visual Studio 2010 Professional, Premium veya Ultimate|Evet, yüklediğinizde [taşınabilir kitaplık Araçları](http://go.microsoft.com/fwlink/?LinkId=210823).|  
|Visual Studio Express 2010 sürümleri|Hayır.|  
|Visual Studio 2012 Professional, Premium veya Ultimate|Evet. Telefon desteği için yükleme [Windows Phone SDK 8.0](http://go.microsoft.com/fwlink/?LinkId=265772).|  
|Visual Studio Express 2012 sürümleri|Hayır.|  
|Visual Studio 2013 Professional, Premium veya Ultimate|Evet. Windows Phone 8.1 desteği yükleme [Visual Studio 2013 güncelleştirme 2](http://go.microsoft.com/fwlink/p/?LinkId=393658).|  
|Windows için Visual Studio Express 2013|Evet, yüklediğinizde [Visual Studio Express en son sürümünü](http://go.microsoft.com/fwlink/p/?LinkId=394629), güncelleştirme 2 içerir veya ekleyin [Visual Studio 2013 güncelleştirme 2](http://go.microsoft.com/fwlink/p/?LinkId=393658).|  
  
<a name="create_pcl"></a>   
## <a name="creating-a-portable-class-library-project"></a>Taşınabilir sınıf kitaplığı proje oluşturma  
 Taşınabilir sınıf kitaplığı oluşturmak için Visual Studio'da sağlanan şablonlarından birini kullanmanız gerekir. Yeni bir proje oluşturun ve **yeni proje** iletişim kutusunda **şablonları**(C# veya Visual Basic) hedef dilinizi seçin ve hedeflemek istediğiniz platformları birini seçin. Sonraki adımda ek platformları seçebilirsiniz.  
  
 Visual Studio 2013 güncelleştirme 2'de seçtiğiniz **sınıf kitaplığı (taşınabilir)** seçilen dil ve taşınabilir sınıf kitaplığı oluşturmak için platform için şablon. Bu şablon aşağıdaki platformları için görürsünüz:  
  
-   Mağazası uygulamaları  
  
-   Windows Masaüstü  
  
-   Silverlight  
  
 Bir kitaplık hedef Windows Phone 8.1 ve Windows 8.1 için C# ' ta oluşturmak istiyorsanız, seçebileceğiniz **depolamak uygulamaları**ve ardından **sınıf kitaplığı (Evrensel uygulamaları için taşınabilir)**.  
  
 ![Mağaza uygulamaları için taşınabilir sınıf kitaplığı](../../../docs/standard/cross-platform/media/storeuniversalpcl.png "StoreUniversalPCL")  
  
 Bu şablon, hedefleri olarak Windows 8.1 ve Windows Phone 8.1 otomatik olarak seçer. Yalnızca Windows Phone 8.1 veya Windows 8.1 hedefleyen bir kitaplık oluşturursanız, Hedef platformlar değiştirin ve platformlar daha sonra ekleyebilirsiniz.  
  
 Visual Studio 2012 veya güncelleştirme 2 olmadan Visual Studio 2013 kullanıyorsanız, yeni bir proje oluşturun ve seçin **taşınabilir sınıf kitaplığı** şablonu Visual C# veya Visual Basic altında.  
  
 ![Select taşınabilir kitaplığı projesi](../../../docs/standard/cross-platform/media/portablelibrary-start.png "PortableLibrary_start")  
  
 **Taşınabilir sınıf kitaplığı eklemek** iletişim kutusu belirir ve ek platformları seçebilirsiniz. İletişim kutusunda seçtiğiniz hedeflerini temel alarak uyumluluğu uyarı verir.  
  
 ![Değişiklik hedef çerçeveler iletişim VS2013 için](../../../docs/standard/cross-platform/media/clr-pcl-changeframeworks.png "CLR_PCL_ChangeFrameworks")  
Visual Studio 2013 güncelleştirme 2 için taşınabilir sınıf kitaplığı iletişim kutusu ekleme  
  
 Olup, Visual Studio 2012 veya Visual Studio 2013 kullanıyorsanız bağımsız olarak, bir taşınabilir sınıf kitaplığı proje oluşturduğunuzda ya da proje özelliklerini projesi oluşturduktan sonra hedef platformlar değiştirmek için kullanabileceğiniz platformları seçebilirsiniz.  
  
<a name="platforms"></a>   
## <a name="target-options"></a>Hedef seçenekleri  
 Taşınabilir sınıf kitaplığı proje oluşturduğunuzda, işletim sistemi ve .NET Framework sürümünü hedeflemek istediğinizi seçebilirsiniz. Visual Studio 2013 kullanıyorsanız ve güncelleştirme 2 yüklediğiniz veya daha sonra seçebileceğiniz **sınıf kitaplığı (Evrensel uygulamaları için taşınabilir)** Windows 8.1 ve Windows Phone 8. 1'i hedefleyen taşınabilir sınıf kitaplığı oluşturmak için şablon. Aşağıdaki tabloda kullanılabilir hedefler kullanmakta olduğunuz Visual Studio sürümüne bağlı olarak gösterir.  
  
|Hedef seçeneği|Visual Studio 2012|Visual Studio 2013|Visual Studio 2013 güncelleştirme 2 veya sonrası|  
|-|-|-|-|  
|.NET Framework|-.NET framework 4 ve üzeri<br /><br /> -.NET framework 4.0.3 ve üstü<br /><br /> -.NET framework 4.5|-.NET framework 4 ve üzeri<br /><br /> -.NET framework 4.0.3 ve üstü<br /><br /> -.NET framework 4.5 ve üzeri<br /><br /> -.NET framework 4.5.1|-.NET framework 4<br /><br /> -.NET framework 4.0.3<br /><br /> -.NET framework 4.5<br /><br /> -.NET framework 4.5.1|  
|Windows Phone|-Windows Phone 7 ve üzeri<br /><br /> -Windows Phone 7.5 ve üzeri<br /><br /> -Windows Phone 8|-Windows Phone 8|-Windows Phone Silverlight 8<br /><br /> -Windows Phone Silverlight 8.1<br /><br /> Windows çalışma zamanı ve XAML desteği seçin:<br /><br /> -Windows Phone 8.1|  
|Windows Mağazası|-Windows mağazası uygulamaları için .NET|-Windows mağazası uygulamaları (Windows 8) ve üzeri<br /><br /> -Windows mağazası uygulamaları (Windows 8.1)|-Windows 8<br /><br /> -Windows 8.1|  
|-Silverlight|-Silverlight 4 ve üzeri<br /><br /> -Silverlight 5|-Silverlight 5|-Silverlight 5|  
|Xbox|-Xbox 360|Yok|Yok|  
  
<a name="change_targets"></a>   
## <a name="changing-targets"></a>Hedefleri değiştirme  
 Taşınabilir sınıf kitaplığı şablonu seçme, varsayılan platformları sizin için seçilir, ancak bu varsayılan değişir Visual Studio sürümüne bağlı olarak yüklediğiniz ve hangi hedefleri, daha önce seçtiğiniz. Taşınabilir sınıf kitaplığı oluşturduğunuzda veya bir taşınabilir sınıf kitaplığı geliştirilmesini başladıktan sonra platformları değiştirebilirsiniz.  
  
 İçinde projeniz oluşturduktan sonra hedefleri değiştirmek istiyorsanız **Çözüm Gezgini**taşınabilir sınıf kitaplığı projenizin (çözümü değil) için kısayol menüsünü açın ve ardından **özellikleri** . Proje özellikleri sayfasında **Kitaplığı** sekmesi, proje şu anda hedefler platformları gösterir.  
  
 ![Proje Özellikleri](../../../docs/standard/cross-platform/media/portablelibrary-projectproperties.png "PortableLibrary_ProjectProperties")  
Visual Studio 2013 güncelleştirme 2 için taşınabilir sınıf kitaplığı özellik sayfası  
  
 Eklemek veya hedefleri kaldırmak istediğiniz **değişiklik** düğmesine tıklayın, seçin ve uygun onay kutularını temizleyin.  
  
 Hedefleri değiştirdiğinizde, projenizi geliştirmek için kullanılabilen API'leri seçiminizi eşleşecek şekilde değiştirilecek. Visual Studio değiştirme hedefleri sonucu olarak ortaya çıkabilecek uyarıları ve hataları raporlar.  
  
 Taşınabilirlik değerlendirmek istiyorsanız, önce derlemelerin Visual Studio'da değişiklik, kullanabileceğiniz [.NET taşınabilirlik Çözümleyicisi](http://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b).  
  
 Menü seçeneklerini kullanmakta olduğunuz Visual Studio sürümüne bağlı olarak değişir.  
  
 ![Değişiklik hedef](../../../docs/standard/cross-platform/media/portablelibrary.png "PortableLibrary_")  
Visual Studio 2012'de değişiklik hedefleri iletişim kutusu  
  
<a name="features"></a>   
## <a name="supported-features"></a>Desteklenen özellikler  
 Mevcut platformlar ve sürümlerde hangi özelliklerin desteklendiği aşağıdaki tabloda gösterilmektedir. Bazı durumlarda, Microsoft destek bir NuGet paketi sürümü ile eklenmiş ve bu not. .NET Framework NuGet paketleri hakkında daha fazla bilgi için bkz: [.NET Framework ve bant dışı sürümler](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md).  
  
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
|Seri hale getirme (veri sözleşmesi, XML ve JSON)|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|System.Numerics|✓|✓|✓|✓|✓|||||✓|✓||  
|Görünüm modelleri (MVVM)|||✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|Windows Communication Foundation (WCF)|✓|✓|✓|✓|✓||✓|✓|✓|✓|✓||  
|Windows çalışma zamanı API'leri|||||✓|✓|||||||  
|Windows.UI.XAML|||||✓|✓|||||||  
|XLINQ||✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|  
  
 ➊ Gerektirir [Microsoft Async](https://www.nuget.org/packages/Microsoft.Bcl.Async/) paketi  
 ➋ Gerektirir [Microsoft Compression](https://www.nuget.org/packages/Microsoft.Bcl.Compression) paketi  
 ➌ Gerektirir [Microsoft HTTP istemci kitaplıkları](http://www.nuget.org/packages/Microsoft.Net.Http) paketi  
  
> [!WARNING]
>  Başvuru zaman hatalarla karşılaşabilir [Microsoft Compression](https://www.nuget.org/packages/Microsoft.Bcl.Compression) ve [Microsoft HTTP istemci kitaplıkları](http://www.nuget.org/packages/Microsoft.Net.Http) bir Windows Phone Silverlight 8.1 uygulama tarafından kullanılan bir taşınabilir kitaplıktan paketler. Daha fazla bilgi için bkz: [Platform uyumluluğu ve Windows Phone Silverlight 8.1 uygulamaları için önemli değişiklikler](http://go.microsoft.com/fwlink/p/?LinkId=394744).  
  
<a name="members"></a>   
## <a name="supported-types-and-members"></a>Desteklenen türler ve üyeleri  
 Tür ve taşınabilir Sınıf Kitaplığı projelerinde kullanılabilir üyelerinin çeşitli uyumluluk faktörler tarafından zorlanır:  
  
-   Bunlar, seçtiğiniz hedefleri arasında paylaşılan gerekir.  
  
-   Bu hedefler benzer şekilde davranır gerekir.  
  
-   Kaldırılma için aday olmamalıdır.  
  
-   Özellikle destekleyici üyeler taşınabilir olmadığında bunlar taşınabilir ortamda anlamlı olmalıdırlar.  
  
 Örneğin, yalnızca Windows 8.1 ve Windows Phone 8.1 hedeflediğinizde taşınabilir sınıf kitaplığı UI ilgili türler içerir. Ayrıca, taşınabilir sınıf kitaplığı giriş önce yayımlanan platformları (örneğin, Xbox, .NET Framework 4 ve Windows Phone 7) hedefliyorsanız sınırlamaları karşılaşabilirsiniz. .NET Framework paketler bazı eski bu platformlar için taşınabilir sınıf kitaplığı desteği artırır NuGet aracılığıyla yayımlar. Daha fazla bilgi ve NuGet paketleri listesi için bkz: [.NET Framework ve bant dışı sürümler](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md).  
  
 Üye taşınabilir Sınıf Kitaplığı'nda ve seçili hedeflerinizi destekleniyorsa, IntelliSense projenizde görünür. Ayrıca, taşınabilir sınıf kitaplığı simgesi ![taşınabilir kitaplığı tarafından desteklenen](../../../docs/standard/cross-platform/media/portablelibrary-referenceicon.png "PortableLibrary_ReferenceIcon") üyeleri tablolarda görünür [.NET Framework sınıf kitaplığı](http://go.microsoft.com/fwlink/?LinkId=211358) yanındaki üyeleri desteklenir. Örneğin, aşağıdaki üyeleri tablo gösterir <xref:System.String.Chars%2A> özelliğinde <xref:System.String> sınıfı taşınabilir Sınıf Kitaplığı'nda desteklenir:  
  
 ![Desteklenen üye simgesi](../../../docs/standard/cross-platform/media/plibsupportedmemberlist.png "PlibSupportedMemberList")  
Taşınabilir sınıf kitaplığı simgesi  
  
 Ayrıca bakabilirsiniz **sürüm bilgilerini** bir tür veya üye taşınabilir sınıf kitaplığı projesinde desteklendiğini belirten bir not yönelik bir başvuru konusu bölümünü:  
  
 ![Taşınabilir Kitaplığı sürüm bilgilerini](../../../docs/standard/cross-platform/media/plibversioninformation.png "PlibVersionInformation")  
Sürüm bilgileri örneği  
  
 Bununla birlikte, bir API taşınabilir Sınıf Kitaplığı'nda desteklenmiyor olabilir, ancak API kullanıp kullanmayacağınızı bağlıdır hedeflerde, unutmayın seçin.  
  
<a name="API_diff"></a>   
## <a name="api-differences-in-the-portable-class-library"></a>Taşınabilir Sınıf Kitaplığı'nda API farklılıkları  
 Taşınabilir sınıf kitaplığı derlemeleri tüm desteklenen platformlarda uyumlu hale getirmek için bazı üyeler biraz taşınabilir Sınıf Kitaplığı'nda değiştirildi.  
  
<a name="using"></a>   
## <a name="using-the-portable-class-library"></a>Taşınabilir Sınıf Kitaplığı Kullanma  
 Taşınabilir sınıf kitaplığı proje oluşturduktan sonra yalnızca bu diğer projelerden başvuru. Erişmek istediğiniz sınıfları içeren projeyi veya belirli derlemeleri projeye ekleyebilirsiniz.  
  
 Gerekli sürümü bir taşınabilir sınıf kitaplığı derlemeye başvuran bir uygulamayı çalıştırmak için (veya üstü) Hedeflenen platformlar bilgisayarınızda yüklü olmalıdır. Visual Studio tüm gerekli çerçeveleri içerdiğinden, uygulama geliştirmek için kullanılan bilgisayarda daha fazla değişiklik olmadan uygulamayı çalıştırabilirsiniz.  
  
### <a name="deploying-a-windows-store-or-windows-phone-app"></a>Windows mağazası veya Windows Phone uygulama dağıtımı  
 Bir Windows mağazası veya Windows Phone Uygulama oluşturduğunuzda, taşınabilir sınıf kitaplığı bütünleştirilmiş koduna başvuruyor, uygulamayı dağıtmak için gereken her şeyi uygulama paketinde bulunan ve başka bir adım gereklidir.  
  
### <a name="deploying-a-net-framework-app"></a>Dağıtımı bir .NET Framework uygulama  
 Taşınabilir sınıf kitaplığı derlemeye başvuran bir .NET Framework uygulama dağıttığınızda, .NET Framework'ün doğru sürümünde bir bağımlılık belirtmeniz gerekir. Bu bağımlılığı belirterek, gerekli sürümün uygulamanızla birlikte yüklü olup olmadığını garantiye almış olursunuz. .NET Framework 4 hedef ya da daha sonra bilgisayarda .NET Framework 4 ile olmalıdır bir [güncelleştirme](http://go.microsoft.com/fwlink/?LinkId=210824), .NET Framework 4 veya .NET Framework 4.5 yüklü 4.0.3 güncelleştirin.  
  
-   ClickOnce dağıtımı ile bir bağımlılık oluşturmak için: içinde **Çözüm Gezgini**, yayımlamak istediğiniz proje için proje düğümünü seçin. (Taşınabilir sınıf kitaplığı proje başvuru proje budur.) Menü çubuğunda seçin **proje**, **özellikleri**ve ardından **Yayımla** sekmesi. Üzerinde **Yayımla** sayfasında, **Önkoşullar**. Önkoşul olarak gerekli .NET Framework sürümünü (ya da .NET Framework 4 güncellemesini) seçin.  
  
-   Kurulum projesi ile bir bağımlılık oluşturmak için: içinde **Çözüm Gezgini**, Kurulum projesini seçin. Menü çubuğunda seçin **proje**, **özellikleri**, **Önkoşullar**. Önkoşul olarak gerekli .NET Framework sürümünü seçin.  
  
 .NET Framework uygulamaları dağıtma hakkında daha fazla bilgi için bkz: [geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md).  
  
### <a name="deploying-a-silverlight-based-app"></a>Silverlight tabanlı bir uygulamanın dağıtımı  
 Taşınabilir sınıf kitaplığı bütünleştirilmiş koduna başvuruyor Silverlight tabanlı bir uygulama dağıttığınızda, uygulama için gerekli en düşük çalışma zamanı sürümü, hedeflenen eşleştiğinden emin olmalısınız. Silverlight 4'ü hedefliyorsanız, sürüm 4.0.60129.0 veya sonraki bir sürümü olmalıdır. Ekleyerek sürümü Ayarla `<param name="minRuntimeVersion" value="4.0.60129.0" />` Silverlight tabanlı uygulama gibi barındıran Web sayfasındaki:  
  
```xaml  
<div id="silverlightControlHost">  
    <object data="data:application/x-silverlight-2,"   
           type="application/x-silverlight-2" width="100%" height="100%">  
    <param name="source" value="ClientBin/SilverlightApplication.xap"/>  
    <param name="onError" value="onSilverlightError" />  
    <param name="background" value="white" />  
    <param name="minRuntimeVersion" value="4.0.60129.0" />  
    <param name="autoUpgrade" value="true" />  
    <a href="http://go.microsoft.com/fwlink/?LinkID=149156&v=4.0.50826.0"   
             style="text-decoration:none">  
      <img src=http://go.microsoft.com/fwlink/?LinkId=161376  
             alt="Get Microsoft Silverlight" style="border-style:none"/>  
    </a>  
  </object>  
   <iframe id="_sl_historyFrame"   
              style="visibility:hidden;height:0px;width:0px;border:0px">  
   </iframe>  
</div>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MVVM ile taşınabilir sınıf kitaplığı kullanma](../../../docs/standard/cross-platform/using-portable-class-library-with-model-view-view-model.md)  
 [Birden çok platformu hedefleyen kitaplıklar için uygulama kaynakları](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md)  
 [.NET taşınabilirlik Çözümleyicisi](http://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)  
 [Windows mağazası uygulamaları ve Windows çalışma zamanı için .NET framework desteği](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
 [Dağıtım](../../../docs/framework/deployment/net-framework-applications.md)
