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
ms.openlocfilehash: e846f45b55ac09d6ce6af4f3223c3bdba1dc83ba
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506015"
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>Birden Çok Platformu Hedefleyen Kitaplıklar için Uygulama Kaynakları
.NET Framework kullanabilirsiniz [taşınabilir sınıf kitaplığı](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) proje türü sınıf kitaplıklarınızdaki kaynakların birden çok platformdan erişilebildiğinden emin olmak için. Bu proje türü ve .NET Framework sınıf kitaplığının taşınabilir alt küme hedefleyen Visual Studio 2012'de kullanılabilir. Taşınabilir sınıf kitaplığı kullanarak sağlar kitaplığınızı erişilip erişilemediğini Masaüstü uygulamaları, Silverlight uygulamaları, Windows Phone uygulamaları ve [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 Taşınabilir sınıf kitaplığı projesi yalnızca çok sınırlı bir alt türlerini yapar <xref:System.Resources> ad alanı, uygulamanızın, ancak için kullanılabilir kullanmanıza izin <xref:System.Resources.ResourceManager> kaynakları almak için sınıf. Ancak, Visual Studio kullanarak bir uygulama oluşturuyorsanız kullanmak yerine Visual Studio tarafından oluşturulan türü kesin belirlenmiş sarıcı kullanmalısınız <xref:System.Resources.ResourceManager> doğrudan sınıf.

 Visual Studio'da türü kesin belirlenmiş bir sarmalayıcı oluşturmak için ana kaynak dosyasının ayarlamak **erişim değiştiricisi** Visual Studio Resource Designer'da içinde **genel**. Böylece, türü ksin belirlenmiş ResourceManager sarmalayıcısını içeren bir [resourceFileName].designer.cs veya [resourceFileName].designer.vb dosyası oluşturulur . Türü kesin belirlenmiş kaynak sarıcı kullanılması hakkında daha fazla bilgi için "Oluşturma bir türü kesin belirlenmiş kaynak sınıfı" bölümüne bakın [Resgen.exe (kaynak dosya oluşturucu)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) konu.

## <a name="resource-manager-in-the-portable-class-library"></a>Resource Manager'da taşınabilir sınıf kitaplığı
 Bir taşınabilir sınıf kitaplığı projesinde, tüm kaynaklara erişim tarafından işlenir <xref:System.Resources.ResourceManager> sınıfı. Çünkü türlerini <xref:System.Resources> ad gibi <xref:System.Resources.ResourceReader> ve <xref:System.Resources.ResourceSet>, olan taşınabilir sınıf kitaplığı projesi erişilebilir değil, bunlar kaynaklara erişmek için kullanılamaz.

 Taşınabilir sınıf kitaplığı projesi dört içerir <xref:System.Resources.ResourceManager> üyeleri aşağıdaki tabloda listelenen. Bu Kurucular ve yöntemler oluşturmak etkinleştirdiğiniz bir <xref:System.Resources.ResourceManager> nesne ve dize kaynakları almayı.

|`ResourceManager` Üyesi|Açıklama|
|------------------------------|-----------------|
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|Oluşturur bir <xref:System.Resources.ResourceManager> belirtilen derleme içinde bulunan adlandırılmış bir kaynak dosyasına erişmek için örneği.|
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|Oluşturur bir <xref:System.Resources.ResourceManager> belirtilen türe karşılık gelen bir örneği.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|Geçerli kültür için adlandırılmış bir kaynağı alır.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|Belirtilen kültüre ait olan bir adlandırılmış kaynağı alır.|

 Diğer dışlama <xref:System.Resources.ResourceManager> üyelerinden nesneler, dize olmayan verileri ve görüntüleri seri taşınabilir sınıf kitaplığı anlamına gelir, bir kaynak dosyadan alınamaz. Taşınabilir Sınıf Kitaplığı'ndan kaynakları kullanmak için tüm nesne verilerini dize formunda depolamanız gerekir. Örneğin, sayısal değerleri dizelere dönüştürerek kaynak dosyasında depolayabilir ve bunları alabilir ve ardından bunları geri sayılara sayısal veri tiplerinin dönüştürme `Parse` veya `TryParse` yöntemi. Çağırarak görüntüleri veya diğer ikili verileri bir dize gösterimine dönüştürebilirsiniz <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> yöntemi ve onları bir bayt dizisi çağırarak geri yükleme <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType> yöntemi.

## <a name="the-portable-class-library-and-windows-store-apps"></a>Windows Store uygulamaları ve taşınabilir sınıf kitaplığı
 Taşınabilir sınıf kitaplığı projeleri ardından .resources dosyalarına derlenir ve ana derlemeye veya uydu derlemelerini derleme zamanında katıştırılmış .resx dosyaları, kaynakları depolar. [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar, diğer taraftan, ardından bir tek bir paket kaynak dizini (PRI) dosyasına derlenir .resw dosyalarında depolanan kaynakları gerektirir. Uyumsuz dosya biçimlerine rağmen taşınabilir sınıf kitaplığı çalışacaktır ancak bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama.

 Sınıf Kitaplığı'ndan kullanmak üzere bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama, Windows Store uygulaması projenize bir başvuru ekleyin. Visual Studio şeffaf bir şekilde kaynakları bir .resw dosyasına derlemenizi ayıklamak ve Windows çalışma zamanı kaynakları ayıklayabilir bir PRI dosyası oluşturmak için kullanın. Çalışma zamanında Windows çalışma zamanı taşınabilir sınıf kitaplığı kodu yürütür, ancak, taşınabilir Sınıf Kitaplığı'nızın kaynaklarını PRI dosyasından alır.

 Taşınabilir sınıf kitaplığı projeniz yerelleştirilmiş kaynakları içeriyorsa, masaüstü uygulamasındaki bir kitaplık için yaptığınız gibi bunları dağıtmak için hub-and-spoke modelini kullanın. Ana kaynak dosyanızı ve tüm tüketmeye içinde yerelleştirilmiş kaynak dosyalarını, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama, ana derlemeye bir başvuru ekleyin. Derleme zamanında, Visual Studio kaynakları, ana kaynak dosyasından ve yerelleştirilmiş herhangi bir kaynak dosyasından ayrı .resw dosyalarına aktarır. Ardından, çalışma zamanında Windows çalışma zamanı erişen bir tek PRI dosyası içine .resw dosyaları derler.

<a name="NonLoc"></a>
## <a name="example-non-localized-portable-class-library"></a>Örnek: Yerelleştirilmemiş taşınabilir sınıf kitaplığı
 Aşağıdaki basit, yerelleştirilmemiş taşınabilir sınıf kitaplığı örnek, sütunların adlarını saklar ve sekmeli veri için rezerve edilecek karakter sayısını belirlemek için kaynakları kullanır. Bu örnek, aşağıdaki tabloda listelenen dize kaynakları depolamak için LibResources.resx adlı bir dosya kullanır.

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

 Aşağıdaki kod gösterir nasıl `UILibrary` sınıfı ve kaynaklarının, konsol modu uygulamasından erişilebilir. Bu, bir konsol uygulaması projesine eklemek için bir Uılıbrary.dll başvurusu gerektirir.

 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]

 Aşağıdaki kod gösterir nasıl `UILibrary` sınıfı ve kaynaklarının erişilebilir bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama. Windows Store uygulaması proje için bir Uılıbrary.dll başvurusu gerektirir.

 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]

## <a name="example-localized-portable-class-library"></a>Örnek: Yerelleştirilmiş taşınabilir sınıf kitaplığı
 Fransızca (Fransa) ve İngilizce (ABD) kültürleri için aşağıdaki yerelleştirilmiş taşınabilir sınıf kitaplığı örnek kaynakları içerir. İngilizce (ABD) kültürü uygulamanın varsayılan kültürüdür; kaynaklarını tablosunda gösterilen [önceki bölümde](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc). Fransızca (Fransa) kültürü için kaynaklar dosyası LibResources.fr-FR.resx olarak adlandırılmıştır ve aşağıdaki tabloda listelenen dize kaynaklarından oluşur. Kaynak kodu `UILibrary` sınıfı, önceki bölümde gösterilenle aynı.

|Kaynak adı|Kaynak değeri|
|-------------------|--------------------|
|Doğma|Doğum Tarihi|
|Doğum Uzunluğu|20|
|İşe Alma|İşe Giriş Tarihi|
|İşe Alma Uzunluğu|16|
|Kimlik|Kimlik|
|Ad|Ad|
|Başlık|Çalışanlar veritabanı|

 Aşağıdaki kod gösterir nasıl `UILibrary` sınıfı ve kaynaklarının, konsol modu uygulamasından erişilebilir. Bu, bir konsol uygulaması projesine eklemek için bir Uılıbrary.dll başvurusu gerektirir.

 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]

 Aşağıdaki kod gösterir nasıl `UILibrary` sınıfı ve kaynaklarının erişilebilir bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama. Windows Store uygulaması proje için bir Uılıbrary.dll başvurusu gerektirir. Statik kullanan `ApplicationLanguages.PrimaryLanguageOverride` özelliği ayarlamak için tercih edilen dilini Fransızca için.

 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Resources.ResourceManager>
- [Masaüstü Uygulamalarındaki Kaynaklar](../../../docs/framework/resources/index.md)
- [Kaynakları Paketleme ve Dağıtma](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
