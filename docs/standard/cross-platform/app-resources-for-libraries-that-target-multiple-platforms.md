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
ms.openlocfilehash: a2d02a8ebe5e2611db3bc284bb022470ff77f601
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290363"
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>Birden Çok Platformu Hedefleyen Kitaplıklar için Uygulama Kaynakları
Sınıf kitaplıklarınızdaki kaynaklara birden çok platformdan erişilebildiğinden emin olmak için .NET Framework [taşınabilir sınıf kitaplığı](cross-platform-development-with-the-portable-class-library.md) proje türünü kullanabilirsiniz. Bu proje türü, Visual Studio 2012 ' de kullanılabilir ve .NET Framework sınıfı kitaplığının taşınabilir alt kümesini hedefler. Taşınabilir sınıf kitaplığı kullanmak, kitaplığınıza masaüstü uygulamaları, Silverlight uygulamaları, Windows Phone uygulamaları ve Windows 8. x Mağazası uygulamaları üzerinden erişilebilmesini sağlar.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 Taşınabilir sınıf kitaplığı projesi, yalnızca uygulamanızın kullanabildiği ad alanındaki türlerin çok sınırlı bir alt kümesini oluşturur <xref:System.Resources> , ancak <xref:System.Resources.ResourceManager> kaynakları almak için sınıfı kullanmanıza izin verir. Ancak, Visual Studio 'Yu kullanarak bir uygulama oluşturuyorsanız, sınıfı doğrudan kullanmak yerine Visual Studio tarafından oluşturulan türü kesin belirlenmiş sarmalayıcı kullanmanız gerekir <xref:System.Resources.ResourceManager> .

 Visual Studio 'da türü kesin belirlenmiş bir sarmalayıcı oluşturmak için, Visual Studio kaynak tasarımcısında ana kaynak dosyasının **erişim değiştiricisini** **Public**olarak ayarlayın. Böylece, türü ksin belirlenmiş ResourceManager sarmalayıcısını içeren bir [resourceFileName].designer.cs veya [resourceFileName].designer.vb dosyası oluşturulur . Türü kesin belirlenmiş kaynak sarmalayıcı kullanımı hakkında daha fazla bilgi için, [Resgen. exe (kaynak dosya Oluşturucu)](../../framework/tools/resgen-exe-resource-file-generator.md) konusunun "türü kesin belirlenmiş kaynak sınıfı oluşturma" bölümüne bakın.

## <a name="resource-manager-in-the-portable-class-library"></a>Taşınabilir Sınıf kitaplığındaki Kaynak Yöneticisi
 Taşınabilir bir sınıf kitaplığı projesinde, kaynaklara tüm erişim sınıf tarafından işlenir <xref:System.Resources.ResourceManager> . <xref:System.Resources>Ve gibi ad alanındaki türlere <xref:System.Resources.ResourceReader> <xref:System.Resources.ResourceSet> taşınabilir bir sınıf kitaplığı projesinden erişilemediğinden, bu kişiler kaynaklara erişmek için kullanılamaz.

 Taşınabilir sınıf kitaplığı projesi, <xref:System.Resources.ResourceManager> Aşağıdaki tabloda listelenen dört üyeyi içerir. Bu oluşturucular ve yöntemler bir <xref:System.Resources.ResourceManager> nesne örneği oluşturup dize kaynaklarını almanızı sağlar.

|`ResourceManager`üyesidir|Description|
|------------------------------|-----------------|
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|<xref:System.Resources.ResourceManager>Belirtilen derlemede bulunan adlandırılmış kaynak dosyasına erişmek için bir örnek oluşturur.|
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|<xref:System.Resources.ResourceManager>Belirtilen türe karşılık gelen bir örnek oluşturur.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|Geçerli kültür için adlandırılmış bir kaynağı alır.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|Belirtilen kültüre ait olan bir adlandırılmış kaynağı alır.|

 <xref:System.Resources.ResourceManager>Taşınabilir sınıf kitaplığından diğer üyelerin dışlamasıdır, serileştirilmiş nesneler, dize olmayan veriler ve görüntülerin bir kaynak dosyasından alınamadığı anlamına gelir. Taşınabilir bir sınıf kitaplığındaki kaynakları kullanmak için tüm nesne verilerini dize biçiminde depolamanız gerekir. Örneğin, sayısal değerleri dizelere dönüştürerek bir kaynak dosyasında saklayabilir ve bunları alabilir ve ardından sayısal veri türünün veya yöntemini kullanarak bunları sayıya geri dönüştürebilirsiniz `Parse` `TryParse` . Metodu çağırarak resimleri veya diğer ikili verileri bir dize gösterimine dönüştürebilirsiniz <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> ve yöntemini çağırarak bir bayt dizisine geri yükleyebilirsiniz <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType> .

## <a name="the-portable-class-library-and-windows-store-apps"></a>Taşınabilir sınıf kitaplığı ve Windows Mağazası uygulamaları
 Taşınabilir sınıf kitaplığı projeleri, daha sonra. resources dosyalarına derlenen ve derleme zamanında ana derlemeye veya uydu Derlemeleriyle gömülü olan. resx dosyalarında kaynakları depolar. Diğer yandan Windows 8. x Mağazası uygulamaları, kaynakların. resw dosyalarında depolanmasını gerektirir ve bu, daha sonra tek bir paket kaynak dizini (PRı) dosyasında derlenir. Ancak, uyumsuz dosya biçimlerine rağmen, taşınabilir sınıf kitaplığınız bir Windows 8. x mağaza uygulamasında çalışacaktır.

 Sınıf kitaplığınızı bir Windows 8. x Mağazası uygulamasından kullanmak için, Windows Mağazası uygulama projenizde buna bir başvuru ekleyin. Visual Studio, derlemeden kaynakları bir. resw dosyasına saydam bir şekilde ayıklayıp Windows Çalışma Zamanı kaynak ayıklayabileceği bir PRı dosyası oluşturmak için kullanır. Çalışma zamanında Windows Çalışma Zamanı, kodu taşınabilir sınıf kitaplığınızda yürütür, ancak taşınabilir sınıf kitaplığınızın kaynaklarını PRı dosyasından alır.

 Taşınabilir sınıf kitaplığı projeniz yerelleştirilmiş kaynaklar içeriyorsa, bunları masaüstü uygulamasındaki bir kitaplıkta olduğu gibi dağıtmak için hub ve bağlı bileşen modelini kullanırsınız. Ana kaynak dosyanızı ve Windows 8. x Mağazası uygulamanızda yerelleştirilmiş kaynak dosyalarını kullanmak için ana derlemeye bir başvuru eklersiniz. Derleme zamanında, Visual Studio kaynakları, ana kaynak dosyasından ve yerelleştirilmiş herhangi bir kaynak dosyasından ayrı .resw dosyalarına aktarır. Daha sonra. resw dosyalarını, Windows Çalışma Zamanı çalışma zamanında eriştiği tek bir PRı dosyasına derler.

<a name="NonLoc"></a>
## <a name="example-non-localized-portable-class-library"></a>Örnek: yerelleştirilmemiş taşınabilir sınıf kitaplığı
 Aşağıdaki basit, yerelleştirilmemiş taşınabilir sınıf kitaplığı örneği, sütunların adlarını depolamak ve tablo verileri için ayrılacak karakter sayısını belirlemede kaynakları kullanır. Bu örnek, aşağıdaki tabloda listelenen dize kaynakları depolamak için LibResources.resx adlı bir dosya kullanır.

|Kaynak adı|Kaynak değeri|
|-------------------|--------------------|
|Doğma|Doğum Tarihi|
|Doğum Uzunluğu|12|
|İşe Alma|İşe Giriş Tarihi|
|İşe Alma Uzunluğu|12|
|ID|ID|
|KİMLİK.Uzunluğu|12|
|Name|Name|
|Ad Uzunluğu|25|
|Başlık|Personel Veritabanı|

 Aşağıdaki kod, `UILibrary` `resources` Dosya Için **erişim değiştiricisi** **Public**olarak değiştirildiğinde, Visual Studio tarafından oluşturulan Kaynak Yöneticisi sarmalayıcı kullanan bir sınıfı tanımlar. UILibrary sınıfı, dize verilerini gerektiği gibi ayrıştırır. . Sınıfının `MyCompany.Employees` ad alanında olduğunu unutmayın.

 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]

 Aşağıdaki kodda, `UILibrary` sınıfının ve kaynaklarına konsol modundaki bir uygulamadan nasıl erişilebileceği gösterilmektedir. Konsol uygulaması projesine eklenmek üzere Uııbrary. dll ' ye bir başvuru gerektirir.

 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]

 Aşağıdaki kod, `UILibrary` sınıfının ve kaynaklarının bir Windows 8. x mağaza uygulamasından nasıl erişilebilir olduğunu gösterir. Windows Mağazası uygulama projesine eklenmek üzere Uııbrary. dll ' ye bir başvuru gerektirir.

 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]

## <a name="example-localized-portable-class-library"></a>Örnek: yerelleştirilmiş taşınabilir sınıf kitaplığı
 Aşağıdaki yerelleştirilmiş taşınabilir sınıf kitaplığı örneği, Fransızca (Fransa) ve Ingilizce (Birleşik Devletler) kültürlerin kaynaklarını içerir. Ingilizce (Birleşik Devletler) kültürü uygulamanın varsayılan kültürüdür; kaynakları, [önceki bölümdeki](app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc)tabloda gösterilir. Fransızca (Fransa) kültürü için kaynaklar dosyası LibResources.fr-FR.resx olarak adlandırılmıştır ve aşağıdaki tabloda listelenen dize kaynaklarından oluşur. Sınıfının kaynak kodu, `UILibrary` önceki bölümde gösterilenle aynıdır.

|Kaynak adı|Kaynak değeri|
|-------------------|--------------------|
|Doğma|Doğum Tarihi|
|Doğum Uzunluğu|20|
|İşe Alma|İşe Giriş Tarihi|
|İşe Alma Uzunluğu|16|
|ID|ID|
|Name|Ad|
|Başlık|Çalışanlar veritabanı|

 Aşağıdaki kodda, `UILibrary` sınıfının ve kaynaklarına konsol modundaki bir uygulamadan nasıl erişilebileceği gösterilmektedir. Konsol uygulaması projesine eklenmek üzere Uııbrary. dll ' ye bir başvuru gerektirir.

 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]

 Aşağıdaki kod, `UILibrary` sınıfının ve kaynaklarının bir Windows 8. x mağaza uygulamasından nasıl erişilebilir olduğunu gösterir. Windows Mağazası uygulama projesine eklenmek üzere Uııbrary. dll ' ye bir başvuru gerektirir. `ApplicationLanguages.PrimaryLanguageOverride`Uygulamanın tercih edilen dilini Fransızca olarak ayarlamak için static özelliğini kullanır.

 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Resources.ResourceManager>
- [Masaüstü uygulamalarındaki kaynaklar](../../framework/resources/index.md)
- [Kaynakları Paketleme ve Dağıtma](../../framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
