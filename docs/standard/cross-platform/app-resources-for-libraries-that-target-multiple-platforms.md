---
title: Birden Çok Platformu Hedefleyen Kitaplıklar için Uygulama Kaynakları
ms.date: 03/30/2017
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
ms.openlocfilehash: f4682b9ffcb0edb4e54c427968c3d40c0de134d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578228"
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>Birden Çok Platformu Hedefleyen Kitaplıklar için Uygulama Kaynakları
.NET Framework kullanabilirsiniz [taşınabilir sınıf kitaplığı](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) proje türü sınıf kitaplıkları kaynaklarında birden çok platformlarından erişilebildiğinden emin olun. Bu proje türü kullanılabilir [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] ve .NET Framework sınıf kitaplığı taşınabilir alt hedefler. Kullanarak bir [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] kitaplığınızın erişilip erişilemediğini Masaüstü uygulamaları, Silverlight uygulamaları, Windows Phone uygulamaları sağlar ve [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar.  
  
 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] Proje yapar yalnızca çok sınırlı bir alt türlerini <xref:System.Resources> ad alanı, uygulamanızın, ancak için kullanılabilir kullanmanıza izin <xref:System.Resources.ResourceManager> kaynakları almak için sınıf. Ancak, Visual Studio kullanarak bir uygulama oluşturuyorsanız, kullanmak yerine Visual Studio tarafından oluşturulan kesin türü belirtilmiş sarmalayıcı kullanmanız gereken <xref:System.Resources.ResourceManager> doğrudan sınıfı.  
  
 Visual Studio'da kesin türü belirtilmiş bir sarmalayıcı oluşturmak için ana kaynak dosyası ayarlamak **erişim değiştiricisi** Visual Studio kaynak Tasarımcısı'nda **ortak**. Böylece, türü ksin belirlenmiş ResourceManager sarmalayıcısını içeren bir [resourceFileName].designer.cs veya [resourceFileName].designer.vb dosyası oluşturulur . Kesin türü belirtilmiş kaynak sarmalayıcı kullanma hakkında daha fazla bilgi için "Oluşturma bir kesin türü belirtilmiş kaynak sınıfı" bölümüne bakın [Resgen.exe (kaynak dosya oluşturucu)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) konu.  
  
## <a name="resource-manager-in-the-includenetportableincludesnet-portable-mdmd"></a>Kaynak Yöneticisi'nde [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]  
 İçinde bir [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] proje, tüm kaynaklara erişimi tarafından işlenir <xref:System.Resources.ResourceManager> sınıfı. Çünkü türlerini <xref:System.Resources> ad alanı, gibi <xref:System.Resources.ResourceReader> ve <xref:System.Resources.ResourceSet>, erişilebilir olmayan bir [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] proje, kaynaklara erişmek için kullanılamaz.  
  
 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] Proje içeriyor dört <xref:System.Resources.ResourceManager> üyeleri aşağıdaki tabloda listelenen. Bu oluşturucular ve yöntemleri örneği sağlayan bir <xref:System.Resources.ResourceManager> nesne ve dize kaynaklarını alır.  
  
|`ResourceManager` Üye|Açıklama|  
|------------------------------|-----------------|  
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|Oluşturur bir <xref:System.Resources.ResourceManager> belirtilen derlemesinde adlandırılmış kaynak dosyaya erişmek için örneği.|  
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|Oluşturur bir <xref:System.Resources.ResourceManager> belirtilen türüne karşılık gelen örnek.|  
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|Geçerli kültür için adlandırılmış bir kaynağı alır.|  
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|Belirtilen kültüre ait olan bir adlandırılmış kaynağı alır.|  
  
 Diğer dışlama <xref:System.Resources.ResourceManager> üyelerinden [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] nesneleri, dize olmayan veri ve görüntüleri serileştirilmiş anlamına gelir, bir kaynak dosyasından alınamıyor. Kaynaklardan kullanmak için bir [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], tüm nesne verilerini dize biçiminde depolamanız gerekir. Örneğin, dizeleri dönüştürme tarafından kaynak dosyası sayısal değerleri depolayabilir ve bunları alabilir ve ardından bunları geri sayılara sayısal veri türünün kullanarak dönüştürme `Parse` veya `TryParse` yöntemi. Çağırarak bir dize gösterimi görüntüleri veya diğer ikili veriler dönüştürebilirsiniz <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> yöntemi ve bunları bir bayt dizisi çağırarak geri yükleme <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="the-includenetportableincludesnet-portable-mdmd-and-windows-store-apps"></a>[!INCLUDE[net_portable](../../../includes/net-portable-md.md)] Ve Windows mağazası uygulamaları  
 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projeleri kaynakları sonra .resources dosyalarıyla derlenir ve ana derleme veya uydu derlemelerini derleme zamanında katıştırılmış .resx dosyaları depolayın. [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları, diğer yandan, tek bir paket kaynak dizini (PRI) dosyasına sonra derlenmiş .resw dosyaların depolanması için kaynaklar gerektirir. Ancak, uyumsuz dosya biçimleri rağmen [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] çalışıp çalışmayacağını bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama.  
  
 Sınıf Kitaplığı'ndan kullanmak için bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama, Windows mağazası uygulaması projenize kendisine bir başvuru ekleyin. Visual Studio saydam kaynakları derlemenizi .resw dosyasına ayıklamak ve kendisinden PRI dosyası oluşturmak için kullanmak [!INCLUDE[wrt](../../../includes/wrt-md.md)] kaynakları ayıklayabilirsiniz. Çalışma zamanında [!INCLUDE[wrt](../../../includes/wrt-md.md)] kodu çalıştırır, [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], ancak PRI dosyasından taşınabilir sınıf kitaplığınızın kaynakları alır.  
  
 Varsa, [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] proje yerelleştirilmiş kaynaklar içeriyor, hub ve bağlı bileşen modeli bir kitaplıkta bir masaüstü uygulaması için yaptığınız gibi bunları dağıtmak için kullanın. Ana kaynak dosyanızı ve tüm kullanmak için kaynak dosyalarını yerelleştirilmiş, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama, bir ana derlemesine başvuru ekleyin. Derleme zamanında, Visual Studio kaynakları, ana kaynak dosyasından ve yerelleştirilmiş herhangi bir kaynak dosyasından ayrı .resw dosyalarına aktarır. Ardından, dosya derlerken tek PRI .resw dosyalarına [!INCLUDE[wrt](../../../includes/wrt-md.md)] çalışma zamanında erişir.  
  
<a name="NonLoc"></a>   
## <a name="example-non-localized-includenetportableincludesnet-portable-mdmd"></a>Örnek: Yerelleştirilmemiş [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]  
 Aşağıdaki basit yerelleştirilmemiş [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] örnek kaynaklar sütunlarının adlarını depolamak ve tablo veri için ayrılacak karakter sayısını belirlemek için kullanır. Bu örnek, aşağıdaki tabloda listelenen dize kaynakları depolamak için LibResources.resx adlı bir dosya kullanır.  
  
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
  
 Aşağıdaki kod tanımlar bir `UILibrary` adlı Kaynak Yöneticisi'ni sarmalayıcı kullanan sınıfı `resources` Visual Studio tarafından oluşturulan zaman **erişim değiştiricisi** dosyası için değiştirilirse **ortak** . UILibrary sınıfı, dize verilerini gerektiği gibi ayrıştırır. biçimindeki telefon numarasıdır. İçinde sınıf olduğuna dikkat edin `MyCompany.Employees` ad alanı.  
  
 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]  
  
 Aşağıdaki kod gösterir nasıl `UILibrary` sınıfı ve kaynaklarına konsol modu uygulamadan erişilebilir. Konsol uygulaması projesine eklemek için bir UILIbrary.dll başvurusu gerektirir.  
  
 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]  
  
 Aşağıdaki kod gösterir nasıl `UILibrary` gelen sınıfı ve kaynaklarına erişilebilir bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama. Windows Mağazası uygulama projesine eklenmesi için UILIbrary.dll 'e bir başvuru gerektirir.  
  
 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]  
  
## <a name="example-localized-includenetportableincludesnet-portable-mdmd"></a>Örnek: yerelleştirilmiş [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]  
 Yerelleştirilmiş aşağıdaki [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] örnek Fransızca (Fransa) hem de İngilizce (ABD) kültürler için kaynakları içerir. İngilizce (ABD), uygulamanın varsayılan kültürü kültürdür; kaynaklarıyla tabloda gösterilen [önceki bölümde](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc). Fransızca (Fransa) kültürü için kaynaklar dosyası LibResources.fr-FR.resx olarak adlandırılmıştır ve aşağıdaki tabloda listelenen dize kaynaklarından oluşur. Kaynak kodu `UILibrary` sınıfı, önceki bölümde gösterilen aynı.  
  
|Kaynak adı|Kaynak değeri|  
|-------------------|--------------------|  
|Doğma|Doğum Tarihi|  
|Doğum Uzunluğu|20|  
|İşe Alma|İşe Giriş Tarihi|  
|İşe Alma Uzunluğu|16|  
|Kimlik|Kimlik|  
|Ad|Ad|  
|Başlık|Çalışanlar veritabanı|  
  
 Aşağıdaki kod gösterir nasıl `UILibrary` sınıfı ve kaynaklarına konsol modu uygulamadan erişilebilir. Konsol uygulaması projesine eklemek için bir UILIbrary.dll başvurusu gerektirir.  
  
 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]  
  
 Aşağıdaki kod gösterir nasıl `UILibrary` gelen sınıfı ve kaynaklarına erişilebilir bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama. Windows Mağazası uygulama projesine eklenmesi için UILIbrary.dll 'e bir başvuru gerektirir. Statik kullanan `ApplicationLanguages.PrimaryLanguageOverride` uygulama ayarlamak için özellik tercih edilen dili Fransızca.  
  
 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Resources.ResourceManager>  
 [Masaüstü Uygulamalarındaki Kaynaklar](../../../docs/framework/resources/index.md)  
 [Kaynakları Paketleme ve Dağıtma](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
