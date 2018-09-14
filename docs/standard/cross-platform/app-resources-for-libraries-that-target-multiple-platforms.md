---
title: Birden Çok Platformu Hedefleyen Kitaplıklar için Uygulama Kaynakları
ms.date: 07/18/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- multiple platforms, resources for
- resources [.NET Framework]
- .NET Framework, resources when targeting multiple platforms
- resources, for multiple platforms
- targeting multiple platforms, resources for
ms.assetid: 72c76f0b-7255-4576-9261-3587f949669c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a6c589a393ccfb5610a19776af6e33e4046bf5d3
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45569286"
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>Birden Çok Platformu Hedefleyen Kitaplıklar için Uygulama Kaynakları
.NET Framework kullanabilirsiniz [taşınabilir sınıf kitaplığı](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) proje türü sınıf kitaplıklarınızdaki kaynakların birden çok platformdan erişilebildiğinden emin olmak için. Bu proje türü kullanılabilir [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] ve .NET Framework sınıf kitaplığının taşınabilir alt küme hedefler. Kullanarak bir [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] kitaplığınızı erişilip erişilemediğini Masaüstü uygulamaları, Silverlight uygulamaları, Windows Phone uygulamaları sağlar ve [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar.  

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]
  
 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] Proje yalnızca çok sınırlı bir alt türlerini yapar <xref:System.Resources> ad alanı, uygulamanızın, ancak için kullanılabilir kullanmanıza izin <xref:System.Resources.ResourceManager> kaynakları almak için sınıf. Ancak, Visual Studio kullanarak bir uygulama oluşturuyorsanız kullanmak yerine Visual Studio tarafından oluşturulan türü kesin belirlenmiş sarıcı kullanmalısınız <xref:System.Resources.ResourceManager> doğrudan sınıf.  
  
 Visual Studio'da türü kesin belirlenmiş bir sarmalayıcı oluşturmak için ana kaynak dosyasının ayarlamak **erişim değiştiricisi** Visual Studio Resource Designer'da içinde **genel**. Böylece, türü ksin belirlenmiş ResourceManager sarmalayıcısını içeren bir [resourceFileName].designer.cs veya [resourceFileName].designer.vb dosyası oluşturulur . Türü kesin belirlenmiş kaynak sarıcı kullanılması hakkında daha fazla bilgi için "Oluşturma bir türü kesin belirlenmiş kaynak sınıfı" bölümüne bakın [Resgen.exe (kaynak dosya oluşturucu)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) konu.  
  
## <a name="resource-manager-in-the-includenetportableincludesnet-portable-mdmd"></a>Kaynak Yöneticisi'nde [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]  
 İçinde bir [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] proje, tüm kaynaklara erişim tarafından işlenir <xref:System.Resources.ResourceManager> sınıfı. Çünkü türlerini <xref:System.Resources> ad gibi <xref:System.Resources.ResourceReader> ve <xref:System.Resources.ResourceSet>, erişilemez bir [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] proje, kaynaklara erişmek için kullanılamaz.  
  
 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] Proje içeren dört <xref:System.Resources.ResourceManager> üyeleri aşağıdaki tabloda listelenen. Bu Kurucular ve yöntemler oluşturmak etkinleştirdiğiniz bir <xref:System.Resources.ResourceManager> nesne ve dize kaynakları almayı.  
  
|`ResourceManager` Üyesi|Açıklama|  
|------------------------------|-----------------|  
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|Oluşturur bir <xref:System.Resources.ResourceManager> belirtilen derleme içinde bulunan adlandırılmış bir kaynak dosyasına erişmek için örneği.|  
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|Oluşturur bir <xref:System.Resources.ResourceManager> belirtilen türe karşılık gelen bir örneği.|  
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|Geçerli kültür için adlandırılmış bir kaynağı alır.|  
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|Belirtilen kültüre ait olan bir adlandırılmış kaynağı alır.|  
  
 Diğer dışlama <xref:System.Resources.ResourceManager> üyelerinden [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] nesneler, dize olmayan verileri ve görüntüleri seri anlamına gelir, bir kaynak dosyadan alınamaz. Kaynaklarını kullanmak için bir [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], tüm nesne verilerini dize formunda depolamanız gerekir. Örneğin, sayısal değerleri dizelere dönüştürerek kaynak dosyasında depolayabilir ve bunları alabilir ve ardından bunları geri sayılara sayısal veri tiplerinin dönüştürme `Parse` veya `TryParse` yöntemi. Çağırarak görüntüleri veya diğer ikili verileri bir dize gösterimine dönüştürebilirsiniz <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> yöntemi ve onları bir bayt dizisi çağırarak geri yükleme <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="the-includenetportableincludesnet-portable-mdmd-and-windows-store-apps"></a>[!INCLUDE[net_portable](../../../includes/net-portable-md.md)] Ve Windows Store uygulamaları  
 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projeleri ardından .resources dosyalarına derlenir ve ana derlemeye veya uydu derlemelerini derleme zamanında katıştırılmış .resx dosyaları, kaynakları depolar. [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar, diğer taraftan, ardından bir tek bir paket kaynak dizini (PRI) dosyasına derlenir .resw dosyalarında depolanan kaynakları gerektirir. Ancak, uyumsuz dosya biçimlerine rağmen [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] çalışacaktır bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama.  
  
 Sınıf Kitaplığı'ndan kullanmak üzere bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama, Windows Store uygulaması projenize bir başvuru ekleyin. Visual Studio şeffaf bir şekilde kaynakları bir .resw dosyasına derlemenizi ayıklamak ve onu bir PRI dosyası oluşturmak için kullanabilirsiniz [!INCLUDE[wrt](../../../includes/wrt-md.md)] kaynakları ayıklayabilir. Çalışma zamanında [!INCLUDE[wrt](../../../includes/wrt-md.md)] kodu yürütür, [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], ancak, taşınabilir Sınıf Kitaplığı'nızın kaynaklarını PRI dosyasından alır.  
  
 Varsa, [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projeniz yerelleştirilmiş kaynakları içeriyorsa, masaüstü uygulamasındaki bir kitaplık için yaptığınız gibi bunları dağıtmak için hub-and-spoke modelini kullanın. Ana kaynak dosyanızı ve tüm tüketmeye içinde yerelleştirilmiş kaynak dosyalarını, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama, ana derlemeye bir başvuru ekleyin. Derleme zamanında, Visual Studio kaynakları, ana kaynak dosyasından ve yerelleştirilmiş herhangi bir kaynak dosyasından ayrı .resw dosyalarına aktarır. Ardından derler bir tek PRI dosyası [!INCLUDE[wrt](../../../includes/wrt-md.md)] çalışma zamanında.  
  
<a name="NonLoc"></a>   
## <a name="example-non-localized-includenetportableincludesnet-portable-mdmd"></a>Örnek: Yerelleştirilmemiş [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]  
 Aşağıdaki basit, yerelleştirilmemiş [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] sütunların adlarını saklar ve sekmeli veri için rezerve edilecek karakter sayısını belirlemek için örnek kaynakları kullanır. Bu örnek, aşağıdaki tabloda listelenen dize kaynakları depolamak için LibResources.resx adlı bir dosya kullanır.  
  
|Kaynak adı|Kaynak değeri|  
|-------------------|--------------------|  
|Doğma|Doğum Tarihi|  
|Doğum Uzunluğu|12|  
|İşe Alma|İşe Giriş Tarihi|  
|İşe Alma Uzunluğu|12|  
|Kimlik|Kimlik|  
|KİMLİK.Uzunluğu|12|  
|Ad|Ad|  
|Ad Uzunluğu|25|  
|Başlık|Personel Veritabanı|  
  
 Aşağıdaki kodu tanımlayan bir `UILibrary` adlı Kaynak Yöneticisi sarmalayıcısını kullanan sınıf `resources` Visual Studio tarafından oluşturulan olduğunda **erişim değiştiricisi** dosya değiştirildiğinde **genel** . UILibrary sınıfı, dize verilerini gerektiği gibi ayrıştırır. biçimindeki telefon numarasıdır. Ders başlıyor Not `MyCompany.Employees` ad alanı.  
  
 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]  
  
 Aşağıdaki kod gösterir nasıl `UILibrary` sınıfı ve kaynaklarının, konsol modu uygulamasından erişilebilir. Konsol uygulaması projesine eklemek için bir UILIbrary.dll başvurusu gerektirir.  
  
 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]  
  
 Aşağıdaki kod gösterir nasıl `UILibrary` sınıfı ve kaynaklarının erişilebilir bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama. Windows Mağazası uygulama projesine eklenmesi için UILIbrary.dll 'e bir başvuru gerektirir.  
  
 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]  
  
## <a name="example-localized-includenetportableincludesnet-portable-mdmd"></a>Örnek: yerelleştirilmiş [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]  
 Aşağıdaki yerelleştirilmiş [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] Fransızca (Fransa) ve İngilizce (ABD) kültürleri için örnek kaynakları içerir. İngilizce (ABD) kültürü uygulamanın varsayılan kültürüdür; kaynaklarını tablosunda gösterilen [önceki bölümde](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc). Fransızca (Fransa) kültürü için kaynaklar dosyası LibResources.fr-FR.resx olarak adlandırılmıştır ve aşağıdaki tabloda listelenen dize kaynaklarından oluşur. Kaynak kodu `UILibrary` sınıfı, önceki bölümde gösterilenle aynı.  
  
|Kaynak adı|Kaynak değeri|  
|-------------------|--------------------|  
|Doğma|Doğum Tarihi|  
|Doğum Uzunluğu|20|  
|İşe Alma|İşe Giriş Tarihi|  
|İşe Alma Uzunluğu|16|  
|Kimlik|Kimlik|  
|Ad|Ad|  
|Başlık|Çalışanlar veritabanı|  
  
 Aşağıdaki kod gösterir nasıl `UILibrary` sınıfı ve kaynaklarının, konsol modu uygulamasından erişilebilir. Konsol uygulaması projesine eklemek için bir UILIbrary.dll başvurusu gerektirir.  
  
 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]  
  
 Aşağıdaki kod gösterir nasıl `UILibrary` sınıfı ve kaynaklarının erişilebilir bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama. Windows Mağazası uygulama projesine eklenmesi için UILIbrary.dll 'e bir başvuru gerektirir. Statik kullanan `ApplicationLanguages.PrimaryLanguageOverride` özelliği ayarlamak için tercih edilen dilini Fransızca için.  
  
 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Resources.ResourceManager>  
- [Masaüstü Uygulamalarındaki Kaynaklar](../../../docs/framework/resources/index.md)  
- [Kaynakları Paketleme ve Dağıtma](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
