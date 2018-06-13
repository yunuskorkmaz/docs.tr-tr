---
title: Masaüstü Uygulamalarındaki Kaynaklar
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- application resources
- resource files
- satellite assemblies
- localization
- packaging application resources
- localizing resources
ms.assetid: 8ad495d4-2941-40cf-bf64-e82e85825890
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 023099adeeebf21b7dba631bde75332524eb0cc3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399263"
---
# <a name="resources-in-desktop-apps"></a>Masaüstü Uygulamalarındaki Kaynaklar
Üretim kalitesindeki neredeyse tüm uygulamaların kaynakları kullanması gerekir. Bir kaynak, mantıksal olarak bir uygulamayla dağıtılan yürütülemez herhangi bir veridir. Bir kaynak, bir uygulamada hata iletileri veya kullanıcı arabiriminin bir parçası olarak görüntülenebilir. Kaynaklar ve nesneleri kalıcı forms dizeleri, görüntüleri dahil olmak üzere, çeşitli veri içerebilir. (Kalıcı nesneleri bir kaynak dosyasına yazmak için, nesnelerin seri hale getirilebilir olması gerekir.) Verilerinizi bir kaynak dosyasında depolamak bütün uygulamanızı yeniden derlemeden bu verileri değiştirmenize olanak tanır. Ayrıca verileri tek bir konumda depolamanızı sağlar ve çoklu konumlarda depolanan sabit kodlanmış verilerin kullanılması gereğini ortadan kaldırır.  
  
 .NET Framework, masaüstü uygulamalarında kaynakların oluşturulması ve yerelleştirilmesi için kapsamlı destek sağlar. Ayrıca .NET Framework, masaüstü uygulamalarında kaynakların oluşturulması ve yerelleştirilmesi için basit bir model sağlar.  
  
 ASP.NET kaynaklar hakkında daha fazla bilgi için bkz: [ASP.NET Web sayfası kaynaklarına genel bakış](http://msdn.microsoft.com/library/0936b3b2-9e6e-4abe-9c06-364efef9dbbd) Internet Explorer Geliştirici Merkezi'nde.  
  
 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları, masaüstü uygulamalarından farklı bir kaynak modeli kullanır ve kaynaklarını tek bir paket kaynak dizini (PRI) dosyasında depolar. Kaynaklar hakkında bilgi için [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları bkz [oluşturma ve Windows mağazası uygulamalarında kaynakları alma](http://go.microsoft.com/fwlink/p/?LinkId=241674) Windows geliştirme Merkezi'ndeki.  
  
## <a name="creating-and-localizing-resources"></a>Kaynakları Oluşturma ve Yerelleştirme  
 Yerelleştirilmemiş bir uygulamada, özellikle aksi takdirde kaynak koddaki birden fazla konumda sabit kodlanmış olabilen dizeler için kaynak dosyalarını uygulama verilerinin bir deposu olarak kullanabilirsiniz. Genellikle, kaynaklar metin (.txt) veya XML (.resx) dosyaları olarak oluşturup [Resgen.exe (kaynak dosya oluşturucu)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) ikili .resources dosyalarıyla derlemek için. Bu dosyalar, bir dil derleyicisi tarafından uygulamanın yürütülebilir dosyası içine gömülebilir. Kaynakları oluşturma hakkında daha fazla bilgi için bkz: [oluşturma kaynak dosyaları](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  
  
 Aynı zamanda uygulamalarınızın kaynaklarını belirli kültürler için yerelleştirebilirsiniz. Bu, uygulamalarınızın yerelleştirilmiş (çevrilmiş) sürümlerini oluşturmanıza olanak sağlar. Yerelleştirilmiş kaynakları kullanan bir uygulama geliştirdiğinizde, kaynakları uygun kaynaklar mevcut olmadığında nötr veya geri dönüş kültürü olarak hizmet veren bir kültür belirtirsiniz. Genel olarak, nötr kültürün kaynakları uygulamanın yürütülebilir dosyasında depolanır. Yerelleştirilmiş tek kaynaklar için kalan kaynaklar tek başına uydu derlemeleri içinde depolanır. Daha fazla bilgi için bkz: [uydu derlemeleri oluşturma](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md).  
  
## <a name="packaging-and-deploying-resources"></a>Paketleme ve Dağıtma Kaynakları  
 Yerelleştirilmiş uygulama kaynaklarında dağıttığınız [uydu derlemeleri](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md). Bir uydu derlemesi, tek bir kültüre ait kaynakları içerir; herhangi bir uygulama kodu içermez. Uydu derleme dağıtım modelinde, bir varsayılan derlemesi olan (genellikle ana derleme) ve uygulamanın desteklediği her bir kültür için bir uydu derlemesi olan bir uygulama oluşturun. Uydu derlemeleri ana derlemenin parçası olmadığından, uygulamanın ana derlemesini değiştirmeden belirli bir kültüre karşılık gelen kaynakları kolay bir şekilde değiştirebilir veya güncelleştirebilirsiniz.  
  
 Uygulamanızın varsayılan kaynak derlemesini hangi kaynakların oluşturacağını dikkatli bir şekilde belirleyin. Ana derlemenin bir parçası olduğundan, bunda yapılacak herhangi bir değişiklik, ana derlemeyi değiştirmenizi gerektirecektir. Varsayılan kaynak belirtmezseniz, bir özel durum ne zaman oluşturulur [kaynak geri dönüş işlemi](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) bulmak çalışır. İyi tasarlanmış bir uygulamada kaynakların kullanılması hiçbir zaman özel bir durum oluşturmamalıdır.  
  
 Daha fazla bilgi için bkz: [paketleme ve dağıtma kaynakları](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) makalesi.  
  
## <a name="retrieving-resources"></a>Kaynakları Alma  
 Çalışma zamanında bir uygulama, <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> özelliği tarafından belirtilen kültürü temel alan, iş parçacığını düzeyinde uygun yerelleştirilmiş kaynakları yükler. Bu özellik değeri aşağıdaki şekilde türetilir:  
  
-   Yerelleştirilmiş kültürü temsil eden bir <xref:System.Globalization.CultureInfo> nesnesini doğrudan <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> özelliğine atayarak.  
  
-   Eğer bir kültür açıkça atanmamışsa, <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> özelliğinden varsayılan iş parçacığı UI kültürünü alarak.  
  
-   Eğer varsayılan iş parçacığı UI kültürü açıkça atanmışsa, Windows `GetUserDefaultUILanguage` işlevini çağırarak yerel bilgisayardaki geçerli kullanıcının kültürünü alarak.  
  
 Geçerli UI kültürünün nasıl ayarlandığı hakkında daha fazla bilgi için <xref:System.Globalization.CultureInfo> ve <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> başvuru sayfalarına bakın.  
  
 Ardından, <xref:System.Resources.ResourceManager?displayProperty=nameWithType> sınıfını kullanarak geçerli UI kültürünün veya belirli bir kültürün kaynaklarını alabilirsiniz. <xref:System.Resources.ResourceManager> sınıfının, en yaygın olarak masaüstü uygulamalarındaki kaynakları almak için kullanılmasına rağmen <xref:System.Resources?displayProperty=nameWithType> ad alanı, kaynakları almak için kullanabileceğiniz ek türleri içerir. Bu güncelleştirmeler şunlardır:  
  
-   Bir derlemede gömülü olan veya bir tek başına ikili .resources dosyasında depolanan kaynakları numaralandırmanızı sağlayan <xref:System.Resources.ResourceReader> sınıfı. Çalışma zamanında kullanılabilir olan kaynakların tam adını bilmediğinizde bu yararlı olur.  
  
-   Kaynakları bir XML (.resx) dosyasından almanızı sağlayan <xref:System.Resources.ResXResourceReader> sınıfı.  
  
-   Geri dönüş kurallarını gözlemlemeden belirli bir kültüre ait kaynakları almanızı sağlayan <xref:System.Resources.ResourceSet> sınıfı. Kaynaklar bir derlemede veya bir tek başına ikili .resources dosyasında depolanabilir. Kaynakları başka bir kaynaktan almak için aynı zamanda <xref:System.Resources.IResourceReader> sınıfını kullanmanızı sağlayan bir <xref:System.Resources.ResourceSet> uygulaması geliştirebilirsiniz.  
  
-   Bir XML kaynak dosyasındaki tüm öğeleri belleğe almanızı sağlayan <xref:System.Resources.ResXResourceSet> sınıfı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Globalization.CultureInfo>  
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>  
 [Uygulama Temelleri](../../../docs/standard/application-essentials.md)  
 [Kaynak Dosyaları Oluşturma](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)  
 [Kaynakları Paketleme ve Dağıtma](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [Uydu Derlemeleri Oluşturma](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)  
 [Kaynakları Alma](../../../docs/framework/resources/retrieving-resources-in-desktop-apps.md)
