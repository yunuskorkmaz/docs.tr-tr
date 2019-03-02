---
title: .NET uygulamalarında kaynakları
ms.date: 07/25/2018
helpviewer_keywords:
  - 'deploying applications [.NET Framework], resources'
  - 'deploying applications [.NET Core], resources'
  - application resources
  - resource files
  - satellite assemblies
  - localization
  - packaging application resources
  - localizing resources
ms.assetid: 8ad495d4-2941-40cf-bf64-e82e85825890
author: rpetrusha
ms.author: ronpet
---
# <a name="resources-in-net-apps"></a>.NET uygulamalarında kaynakları
Üretim kalitesindeki neredeyse tüm uygulamaların kaynakları kullanması gerekir. Bir kaynak, mantıksal olarak bir uygulamayla dağıtılan yürütülemez herhangi bir veridir. Bir kaynak, bir uygulamada hata iletileri veya kullanıcı arabiriminin bir parçası olarak görüntülenebilir. Kaynaklar ve kalıcı nesneler formlar, dizeler, görüntüler dahil olmak üzere çeşitli verileri içerebilir. (Kalıcı nesneleri bir kaynak dosyasına yazmak için, nesnelerin seri hale getirilebilir olması gerekir.) Verilerinizi bir kaynak dosyasında depolamak bütün uygulamanızı yeniden derlemeden bu verileri değiştirmenize olanak tanır. Ayrıca verileri tek bir konumda depolamanızı sağlar ve çoklu konumlarda depolanan sabit kodlanmış verilerin kullanılması gereğini ortadan kaldırır.  
  
 .NET Framework ve .NET Core oluşturulması ve yerelleştirilmesi kaynakları için kapsamlı destek sağlar. Ayrıca, .NET, paketleme ve dağıtma yerelleştirilmiş kaynakları için basit bir modeli destekler.  
  
 ASP.net'deki kaynaklar hakkında daha fazla bilgi için bkz. [ASP.NET Web sayfası kaynaklarına genel bakış](https://docs.microsoft.com/previous-versions/aspnet/ms227427(v=vs.100)).  
  
## <a name="creating-and-localizing-resources"></a>Kaynakları Oluşturma ve Yerelleştirme  

Yerelleştirilmemiş bir uygulamada, özellikle aksi takdirde kaynak koddaki birden fazla konumda sabit kodlanmış olabilen dizeler için kaynak dosyalarını uygulama verilerinin bir deposu olarak kullanabilirsiniz. En yaygın olarak, kaynakları metin (.txt) veya XML (.resx) dosyaları olarak oluşturun ve kullanın [Resgen.exe (kaynak dosya oluşturucu)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) bunları ikili .resources dosyalarına derlemek için. Bu dosyalar, bir dil derleyicisi tarafından uygulamanın yürütülebilir dosyası içine gömülebilir. Kaynak oluşturma hakkında daha fazla bilgi için bkz. [Creating Resource Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  

Aynı zamanda uygulamalarınızın kaynaklarını belirli kültürler için yerelleştirebilirsiniz. Bu, uygulamalarınızın yerelleştirilmiş (çevrilmiş) sürümlerini oluşturmanıza olanak sağlar. Yerelleştirilmiş kaynakları kullanan bir uygulama geliştirdiğinizde, kaynakları uygun kaynaklar mevcut olmadığında nötr veya geri dönüş kültürü olarak hizmet veren bir kültür belirtirsiniz. Genel olarak, nötr kültürün kaynakları uygulamanın yürütülebilir dosyasında depolanır. Yerelleştirilmiş tek kaynaklar için kalan kaynaklar tek başına uydu derlemeleri içinde depolanır. Daha fazla bilgi için [uydu derlemeleri oluşturma](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md).  
  
## <a name="packaging-and-deploying-resources"></a>Paketleme ve Dağıtma Kaynakları  
 Yerelleştirilmiş uygulama kaynaklarını dağıtma [uydu bütünleştirilmiş kodlar](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md). Bir uydu derlemesi, tek bir kültüre ait kaynakları içerir; herhangi bir uygulama kodu içermez. Uydu derleme dağıtım modelinde, bir varsayılan derlemesi olan (genellikle ana derleme) ve uygulamanın desteklediği her bir kültür için bir uydu derlemesi olan bir uygulama oluşturun. Uydu derlemeleri ana derlemenin parçası olmadığından, uygulamanın ana derlemesini değiştirmeden belirli bir kültüre karşılık gelen kaynakları kolay bir şekilde değiştirebilir veya güncelleştirebilirsiniz.  
  
 Uygulamanızın varsayılan kaynak derlemesini hangi kaynakların oluşturacağını dikkatli bir şekilde belirleyin. Ana derlemenin bir parçası olduğundan, bunda yapılacak herhangi bir değişiklik, ana derlemeyi değiştirmenizi gerektirecektir. Varsayılan bir kaynak belirtmezseniz, bir özel durum oluşturulur [kaynak geri dönüş işlemi](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) onu bulmaya çalışır. İyi tasarlanmış bir uygulamada kaynakların kullanılması hiçbir zaman özel bir durum oluşturmamalıdır.  
  
 Daha fazla bilgi için [kaynakları paketleme ve dağıtma](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) makalesi.  
  
## <a name="retrieving-resources"></a>Kaynakları Alma  
 Çalışma zamanında bir uygulama, <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> özelliği tarafından belirtilen kültürü temel alan, iş parçacığını düzeyinde uygun yerelleştirilmiş kaynakları yükler. Bu özellik değeri aşağıdaki şekilde türetilir:  
  
-   Yerelleştirilmiş kültürü temsil eden bir <xref:System.Globalization.CultureInfo> nesnesini doğrudan <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> özelliğine atayarak.  
  
-   Eğer bir kültür açıkça atanmamışsa, <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> özelliğinden varsayılan iş parçacığı UI kültürünü alarak.  
  
-   Varsayılan iş parçacığı UI kültürü açıkça, yerel bilgisayardaki geçerli kullanıcının kültürünü alarak atanmamışsa. Windows üzerinde çalışan .NET uygulamalarını bunu Windows çağırarak [ `GetUserDefaultUILanguage` ](/windows/desktop/api/winnls/nf-winnls-getuserdefaultuilanguage) işlevi.  
  
 Geçerli UI kültürünün nasıl ayarlandığı hakkında daha fazla bilgi için <xref:System.Globalization.CultureInfo> ve <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> başvuru sayfalarına bakın.  
  
 Ardından, <xref:System.Resources.ResourceManager?displayProperty=nameWithType> sınıfını kullanarak geçerli UI kültürünün veya belirli bir kültürün kaynaklarını alabilirsiniz. Ancak <xref:System.Resources.ResourceManager> sınıfı, kaynakları almak için en yaygın olarak kullanılır <xref:System.Resources?displayProperty=nameWithType> ad alanı, kaynakları almak için kullanabileceğiniz ek türleri içerir. Bu güncelleştirmeler şunlardır:  
  
-   Bir derlemede gömülü olan veya bir tek başına ikili .resources dosyasında depolanan kaynakları numaralandırmanızı sağlayan <xref:System.Resources.ResourceReader> sınıfı. Çalışma zamanında kullanılabilir olan kaynakların tam adını bilmediğinizde bu yararlı olur.  
  
-   Kaynakları bir XML (.resx) dosyasından almanızı sağlayan <xref:System.Resources.ResXResourceReader> sınıfı.  
  
-   Geri dönüş kurallarını gözlemlemeden belirli bir kültüre ait kaynakları almanızı sağlayan <xref:System.Resources.ResourceSet> sınıfı. Kaynaklar bir derlemede veya bir tek başına ikili .resources dosyasında depolanabilir. Kaynakları başka bir kaynaktan almak için aynı zamanda <xref:System.Resources.IResourceReader> sınıfını kullanmanızı sağlayan bir <xref:System.Resources.ResourceSet> uygulaması geliştirebilirsiniz.  
  
-   Bir XML kaynak dosyasındaki tüm öğeleri belleğe almanızı sağlayan <xref:System.Resources.ResXResourceSet> sınıfı.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Globalization.CultureInfo>
- <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>
- [Uygulama Temelleri](../../../docs/standard/application-essentials.md)
- [Kaynak Dosyaları Oluşturma](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)
- [Kaynakları Paketleme ve Dağıtma](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Uydu Derlemeleri Oluşturma](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [Kaynakları Alma](../../../docs/framework/resources/retrieving-resources-in-desktop-apps.md)
