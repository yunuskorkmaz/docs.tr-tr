---
title: Masaüstü Uygulamalarında Kaynakları Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- resource files, packaging
- application resources, packaging
- localization
- versioning satellite assemblies
- retrieving localized resources
- application resources, deploying
- packaging application resources
- versioning resources
- translating resources into languages
- localizing resources
ms.assetid: eca16922-1c46-4f68-aefe-e7a12283641f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40eec7c03de616b22ae7b20c56cd5a05237ec759
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="retrieving-resources-in-desktop-apps"></a>Masaüstü Uygulamalarında Kaynakları Alma
.NET Framework masaüstü uygulamalarında yerelleştirilmiş kaynaklar ile çalışırken, ideal olarak varsayılan veya bağımsız kültür için kaynakları ana bütünleştirilmiş kod ile paketini ve her dil veya uygulamanızın destekleyen kültür için ayrı uydu derlemesi oluşturmanız. Daha sonra <xref:System.Resources.ResourceManager> sınıfı adlandırılmış kaynaklara erişmek için sonraki bölümde açıklandığı gibi. Ana derleme ve uydu derlemelerini kaynaklarınızı katıştırmak değil seçerseniz, ayrıca ikili .resources dosyaları doğrudan, bölümünde açıklandığı gibi erişebilirsiniz [.resources dosyaları alma kaynaklardan](#from_file) daha sonra bu makale.  Kaynaklarında almak için [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları bkz [oluşturma ve Windows mağazası uygulamalarında kaynakları alma](http://go.microsoft.com/fwlink/p/?LinkID=241674) Windows geliştirme Merkezi'ndeki.  
  
<a name="from_assembly"></a>   
## <a name="retrieving-resources-from-assemblies"></a>Derlemelerden kaynakları alma  
 <xref:System.Resources.ResourceManager> Sınıfı, çalışma zamanında kaynaklara erişim sağlar. Kullandığınız <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> dize kaynaklarını almak için yöntemini ve <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType> veya <xref:System.Resources.ResourceManager.GetStream%2A?displayProperty=nameWithType> dize olmayan kaynakları alma yöntemi. Her yöntemin iki aşırı vardır:  
  
-   Bir aşırı, tek bir parametre kaynağın adını içeren bir dizedir. Yöntemi, bu kaynak için geçerli iş parçacığı kültürünü almaya çalışır. Daha fazla bilgi için bkz: <xref:System.Resources.ResourceManager.GetString%28System.String%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%29>, ve <xref:System.Resources.ResourceManager.GetStream%28System.String%29> yöntemleri.  
  
-   İki parametreye sahip bir aşırı: bir kaynağın adını içeren dize ve bir <xref:System.Globalization.CultureInfo> olan kaynaktır alınacak kültür temsil eden nesne. Bir kaynak kültür bulunamıyor ayarlarsanız, Kaynak Yöneticisi'ni uygun kaynak almak için geri dönüş kuralları kullanır. Daha fazla bilgi için bkz: <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>, ve <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> yöntemleri.  
  
 Kaynak Yöneticisi kaynak geri dönüş işlemi uygulama kültüre özgü kaynakları nasıl alacağını denetlemek için kullanır. Daha fazla bilgi için "Kaynak geri dönüş işlemi" bölümüne bakın [paketleme ve dağıtma kaynakları](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md). Örnek oluşturma hakkında bilgi için bir <xref:System.Resources.ResourceManager> nesne, "ResourceManager nesnesi örnek oluşturma" bölümüne bakın <xref:System.Resources.ResourceManager> sınıfı konu.  
  
### <a name="retrieving-string-data-an-example"></a>Alma dizesi verileri: Bir örnek  
 Aşağıdaki örnek çağrıları <xref:System.Resources.ResourceManager.GetString%28System.String%29> geçerli UI kültürü dize kaynaklarını alma yöntemi. Bu ve bir nötr dize kaynak İngilizce (ABD) kültür için yerelleştirilen kaynaklar Fransızca (Fransa) ve Rusça (Rusya) kültürler için içerir. Aşağıdaki İngilizce (ABD) kaynak Strings.txt adlı dosyasıdır:  
  
```  
TimeHeader=The current time is  
```  
  
 Fransızca (Fransa) kaynaktır Strings.fr adındaki bir dosyada-FR.txt:  
  
```  
TimeHeader=L'heure actuelle est  
```  
  
 Rusça (Rusya) kaynak Strings.ru RU txt adlı dosyasıdır:  
  
```  
TimeHeader=Текущее время —  
```  
  
 C# sürümü için kod ve GetString.vb Visual Basic sürümü için GetString.cs adlı bir dosya olduğundan, bu örnek için kaynak kodunu dört kültürler adını içeren bir dize dizisi tanımlar: kendisi için kaynakları kullanılabilir üç kültürler ve İspanyolca (İspanya) kültür. Beş kez rastgele yürüten bir döngü bu kültürler birini seçer ve atar <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> ve <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> özellikleri. Daha sonra çağırır <xref:System.Resources.ResourceManager.GetString%28System.String%29> saati ile birlikte görüntüler yerelleştirilmiş dize alma yöntemi.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstring.cs#3)]
 [!code-vb[Conceptual.Resources.Retrieving#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstring.vb#3)]  
  
 Aşağıdaki toplu iş (.bat) dosyası örnek derler ve uydu derlemelerini uygun dizinler oluşturur. Komutları, derleyici ve C# dili için sağlanır. Visual Basic for değiştirme `csc` için `vbc`, değiştirip `GetString.cs` için `GetString.vb`.  
  
```  
resgen strings.txt  
csc GetString.cs -resource:strings.resources  
  
resgen strings.fr-FR.txt  
md fr-FR  
al -embed:strings.fr-FR.resources -culture:fr-FR -out:fr-FR\GetString.resources.dll  
  
resgen strings.ru-RU.txt  
md ru-RU  
al -embed:strings.ru-RU.resources -culture:ru-RU -out:ru-RU\GetString.resources.dll  
```  
  
 Geçerli UI kültürü İspanyolca (İspanya) olduğunda, örnek İspanyolca dil kaynaklar kullanılamıyor ve İngilizce örneğin varsayılan kültürü olduğundan İngilizcesi kaynaklarını görüntüler unutmayın.  
  
### <a name="retrieving-object-data-two-examples"></a>Nesne verileri: İki örnek  
 Kullanabileceğiniz <xref:System.Resources.ResourceManager.GetObject%2A> ve <xref:System.Resources.ResourceManager.GetStream%2A> nesne verilerini almak için yöntemleri. Bu, temel veri türleri, seri hale getirilebilir nesneler ve ikili biçimde (örneğin, görüntüleri için) depolanan nesneleri içerir.  
  
 Aşağıdaki örnek kullanır <xref:System.Resources.ResourceManager.GetStream%28System.String%29> bir uygulamada kullanılan bir bit eşlem alma yöntemi giriş penceresini açma. Aşağıdaki kaynak kodu adlı bir dosyaya CreateResources.cs (C# için) veya CreateResources.vb (Visual Basic için) seri hale getirilmiş görüntüsünü içeren .resx dosyası oluşturur. Bu durumda, görüntü SplashScreen.jpg adlı dosyadan yüklenir; kendi görüntünüzü yerine dosya adını değiştirebilirsiniz.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/createresources.cs#4)]
 [!code-vb[Conceptual.Resources.Retrieving#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/createresources.vb#4)]  
  
 Aşağıdaki kod kaynak alır ve görüntüde görüntüler bir <xref:System.Windows.Forms.PictureBox> denetim.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstream.cs#5)]
 [!code-vb[Conceptual.Resources.Retrieving#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstream.vb#5)]  
  
 C# örnek oluşturmak için aşağıdaki toplu iş dosyası kullanabilirsiniz. Visual Basic for değiştirme `csc` için `vbc`, kaynak kod dosyasının uzantısı değiştirip `.cs` için `.vb`.  
  
```  
csc CreateResources.cs  
CreateResources  
  
resgen AppResources.resx  
  
csc GetStream.cs -resource:AppResources.resources  
```  
  
 Aşağıdaki örnek kullanır <xref:System.Resources.ResourceManager.GetObject%28System.String%29?displayProperty=nameWithType> özel bir nesne seri durumdan yöntemi. Örnek adlı aşağıdaki yapısını tanımlar UIElements.cs (Visual Basic UIElements.vb) adlı bir kaynak kodu dosyasının içerir `PersonTable`. Bu yapı, tablo sütunları yerelleştirilmiş adlarını görüntüler genel tablosu görüntü yordamı tarafından kullanılmak üzere tasarlanmıştır. Unutmayın `PersonTable` yapısı ile işaretlenmiş <xref:System.SerializableAttribute> özniteliği.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example.cs#6)]
 [!code-vb[Conceptual.Resources.Retrieving#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#6)]  
  
 Aşağıdaki kod adlı dosyadan CreateResources.cs (Visual Basic CreateResources.vb) tablo başlığı depolar UIResources.resx adlı bir XML kaynak dosyası oluşturur ve bir `PersonTable` için yerelleştirilmiş bir uygulama için bilgileri içeren nesne İngilizce dili.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example1.cs#7)]
 [!code-vb[Conceptual.Resources.Retrieving#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#7)]  
  
 Kaynak kodu dosyasına aşağıdaki kodu GetObject.cs (GetObject.vb) adlı sonra kaynakları alır ve bunları konsola görüntüler.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example2.cs#8)]
 [!code-vb[Conceptual.Resources.Retrieving#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example2.vb#8)]  
  
 Derlemeler ve gerekli kaynak dosyası oluşturun ve aşağıdaki toplu iş dosyası yürüterek uygulamayı çalıştırın. Kullanmalısınız `/r` böylece hakkında bilgi erişebilir Resgen.exe UIElements.dll başvuru sağlamanız için seçeneği `PersonTable` yapısı. C# kullanıyorsanız Değiştir `vbc` derleyici adıyla `csc`ve yerine `.vb` uzantısıyla `.cs`.  
  
```  
vbc -t:library UIElements.vb  
vbc CreateResources.vb -r:UIElements.dll  
CreateResources  
  
resgen UIResources.resx  -r:UIElements.dll  
vbc GetObject.vb -r:UIElements.dll -resource:UIResources.resources  
  
GetObject.exe  
```  
  
## <a name="versioning-support-for-satellite-assemblies"></a>Uydu derlemeleri için sürüm oluşturma desteği  
 Varsayılan olarak, zaman <xref:System.Resources.ResourceManager> nesnesi alır. İstenen kaynaklar, ana derleme sürüm numarası aynı sürüm numarasına sahip için uydu derlemelerini görünüyor. Uygulamayı dağıttıktan sonra ana derleme ya da belirli kaynak uydu derlemelerini güncelleştirmek isteyebilirsiniz. Ana derleme ve uydu derlemelerini .NET Framework sürüm oluşturma için destek sağlar.  
  
 <xref:System.Resources.SatelliteContractVersionAttribute> Özniteliği için bir ana derleme sürümü oluşturma desteği sağlar. Bu öznitelik bir uygulamanın ana derlemede belirtme güncelleştirmek ve ana derleme uydu derlemelerini güncelleştirmeden yeniden dağıtmanızı sağlar. Ana derleme güncelleştirdikten sonra ana derlemenin sürüm numarasını Artır ancak değişmeden uydu sözleşmesi sürüm numarasını bırakın. Kaynak Yöneticisi'ni istenen kaynakları alır. Bu özniteliği tarafından belirtilen uydu derleme sürümünü yükler.  
  
 Yayımcı ilkesi derlemeler uydu derlemelerini sürüm oluşturma için destek sağlar. Güncelleştirme ve ana derleme güncelleştirmeden uydu derlemesi yeniden dağıtın. Uydu derlemesi güncelleştirdikten sonra alt sürüm numarasını Artır ve yayımcı ilke derlemesi ile birlikte. Yayımcı ilke derlemesi, yeni bir uydu derleme geriye dönük olarak uyumlu olduğunu belirtmek, önceki sürümü. Kaynak Yöneticisi'ni kullanacaksınız <xref:System.Resources.SatelliteContractVersionAttribute> özniteliğini uydu derlemesi ancak derleme yükleyicisi sürümünü belirlemek için yayımcı ilkesi tarafından belirtilen uydu derleme sürümü bağlanma. Yayımcı ilke derlemesi hakkında daha fazla bilgi için bkz: [bir yayımcı ilkesi dosyası oluşturma](../../../docs/framework/configure-apps/how-to-create-a-publisher-policy.md).  
  
 Tam derleme sürümü oluşturma desteğini etkinleştirmek için tanımlayıcı adlı derlemeler dağıtmanızı öneririz [genel derleme önbelleği](../../../docs/framework/app-domains/gac.md) ve tanımlayıcı adlar uygulama dizininde yok derlemeleri dağıtma. Tanımlayıcı adlı derlemeler uygulama dizinindeki dağıtmak istiyorsanız, derleme güncelleştirdiğinizde uydu derlemenin sürüm numarasını Artır mümkün olmaz. Bunun yerine, burada var olan kodu güncelleştirilmiş kod ile değiştirin ve aynı sürüm numarasını Koru yerinde güncelleştirmesini uygulamanız gerekir. Belirtilen derlemenin tam ada sahip bir uydu derleme 1.0.0.0 sürümünü güncelleştirmek isterseniz, örneğin, "myApp.resources, sürüm 1.0.0.0, kültür = de, PublicKeyToken = b03f5f11d50a3a =", bırakıldı güncelleştirilmiş myApp.resources.dll ile üzerine ile aynı, tam olarak belirtilen derleme adı derlenmiş "myApp.resources, sürüm 1.0.0.0, kültür = de, PublicKeyToken = b03f5f11d50a3a =". Uydu derleme dosyalarına yerinde güncelleştirmeleri kullanarak bir uygulamayı doğru şekilde bir uydu derleme sürümünü belirlemek için zorlaştırır olduğunu unutmayın.  
  
 Derleme sürümü oluşturma hakkında daha fazla bilgi için bkz: [derleme sürümü oluşturma](../../../docs/framework/app-domains/assembly-versioning.md) ve [nasıl çalışma zamanı bulur derlemeleri](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
<a name="from_file"></a>   
## <a name="retrieving-resources-from-resources-files"></a>.Resources dosyaları kaynakları alma  
 Uydu derlemeleri kaynaklarında dağıtma seçerseniz, kullanmaya devam edebilirsiniz bir <xref:System.Resources.ResourceManager> .resources kaynaklara erişmek için nesnesinden dosyaları doğrudan. Bunu yapmak için .resources dosyaları doğru dağıtmanız gerekir. Kullandığınız sonra <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%2A?displayProperty=nameWithType> yöntemi örneği oluşturmak için bir <xref:System.Resources.ResourceManager> nesne ve tek başına .resources dosyaları içeren dizini belirtin.  
  
### <a name="deploying-resources-files"></a>.Resources dosyaları dağıtma  
 .Resources dosyaları uygulaması derleme ve uydu derlemelerini katıştırma her uydu derlemesi aynı dosya adına sahiptir, ancak uydu derlemenin kültürü yansıtan bir alt dizinde yerleştirilir. Buna karşılık, .resources dosyaları doğrudan kaynaklara erişirken, genellikle uygulama dizininin bir alt gibi tek bir dizin içinde tüm .resources dosyaları yerleştirebilirsiniz. Uygulamanın varsayılan .resources dosyasının adı yalnızca, bir kök adı (örneğin, strings.resources) kültürü hiçbir belirtisi oluşur. Her yerelleştirilmiş kültür için kaynaklar (örneğin, strings.ja.resources veya strings.de DE.resources) kültür tarafından izlenen kök adı adı oluşan bir dosyada depolanır. Kaynak dosyaları dizin yapısında nerede bulunmalıdır aşağıdaki şekilde gösterilmiştir.  
  
 ![Uygulamanız için ana dizin](../../../docs/framework/resources/media/resappdir.gif "resappdir")  
Dizin yapısını ve .resources dosyaları için adlandırma kuralları  
  
### <a name="using-the-resource-manager"></a>Kaynak Yöneticisi'ni kullanma  
 Kaynaklarınızın oluşturdunuz ve bunları uygun dizine yerleştirilen, oluşturduktan sonra bir <xref:System.Resources.ResourceManager> çağırarak kaynakları kullanmak için nesne <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%28System.String%2CSystem.String%2CSystem.Type%29> yöntemi. İlk parametre (önceki bölümde örneğin "dize" olur) uygulamanın varsayılan .resources dosyası kök adını belirtir. İkinci parametre (önceki örnek "Kaynaklar") kaynakların konumunu belirtir. Üçüncü parametre belirtir <xref:System.Resources.ResourceSet> uygulaması kullanın. Üçüncü parametre ise `null`, varsayılan çalışma zamanı <xref:System.Resources.ResourceSet> kullanılır.  
  
> [!NOTE]
>  Tek başına .resources dosyaları kullanarak ASP.NET uygulamaları dağıtmayın. Bu, kilitleme sorunlar ve sonları XCOPY dağıtımı neden olabilir. Uydu derlemeleri ASP.NET kaynaklarında dağıtmanızı öneririz. Daha fazla bilgi için bkz: [ASP.NET Web sayfası kaynaklarına genel bakış](http://msdn.microsoft.com/library/0936b3b2-9e6e-4abe-9c06-364efef9dbbd).  
  
 Örneği sonra <xref:System.Resources.ResourceManager> nesnesi, kullandığınız <xref:System.Resources.ResourceManager.GetString%2A>, <xref:System.Resources.ResourceManager.GetObject%2A>, ve <xref:System.Resources.ResourceManager.GetStream%2A> kaynakları almak için daha önce bahsedildiği gibi yöntemleri. Ancak, .resources dosyaları doğrudan kaynaklardan alınmasını derlemelerden katıştırılmış kaynakları alma farklıdır. .Resources dosyaları, kaynakları aldığınızda <xref:System.Resources.ResourceManager.GetString%28System.String%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%29>, ve <xref:System.Resources.ResourceManager.GetStream%28System.String%29> yöntemleri varsayılan kültürün kaynaklarının geçerli kültürü bağımsız olarak daima alır. Her iki uygulamanın geçerli kültür ya da belirli bir kültür kaynakları almak için çağırmalısınız <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>, veya <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> yöntemi ve kaynakları alınacak kültür belirtin. Geçerli kültür kaynakları almak için değerini belirtin <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özelliği olarak `culture` bağımsız değişkeni. Resource manager kaynaklarını alamıyorsa `culture`, uygun kaynakları almak için standart kaynak geri dönüş kuralları kullanır.  
  
### <a name="an-example"></a>Bir Örnek  
 Aşağıdaki örnek resource manager kaynakları doğrudan .resources dosyaları nasıl alacağını gösterilmektedir. Örnek İngilizce (ABD), Fransızca (Fransa) ve Rusça (Rusya) kültürler için üç metin tabanlı kaynak dosyaları içerir. İngilizce (ABD), örneğin varsayılan kültürdür. Kaynaklarını Strings.txt adlı aşağıdaki dosyada depolanır:  
  
```  
Greeting=Hello  
Prompt=What is your name?  
```  
  
 Fransızca (Fransa) kültür için kaynaklar Strings.fr adlı aşağıdaki dosyasında depolanan-FR.txt:  
  
```  
Greeting=Bon jour  
Prompt=Comment vous appelez-vous?  
```  
  
 Rusça (Rusya) kültür için kaynaklar Strings.ru adlı aşağıdaki dosyasında depolanan-RU.txt:  
  
```  
Greeting=Здравствуйте  
Prompt=Как вас зовут?  
```  
  
 Örneğin kaynak kodu verilmiştir. Örnek başlatır <xref:System.Globalization.CultureInfo> nesneleri İngilizce (ABD), İngilizce (Kanada), Fransızca (Fransa) ve Rusça (Rusya) kültürler için ve her geçerli kültürü yapar. <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> Yöntemi sonra sağladığı değeri <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özelliği olarak `culture` uygun kültüre özgü kaynakları almak için bağımsız değişken.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example3.cs#9)]
 [!code-vb[Conceptual.Resources.Retrieving#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example3.vb#9)]  
  
 C# sürümü örnek aşağıdaki toplu iş dosyasını çalıştırarak derleyebilirsiniz. Visual Basic kullanıyorsanız, yerini `csc` ile `vbc`ve yerine `.cs` uzantısıyla `.vb`.  
  
```  
Md Resources  
Resgen Strings.txt Resources\Strings.resources  
Resgen Strings.fr-FR.txt Resources\Strings.fr-FR.resources  
Resgen Strings.ru-RU.txt Resources\Strings.ru-RU.resources  
  
csc Example.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Resources.ResourceManager>  
 [Masaüstü Uygulamalarındaki Kaynaklar](../../../docs/framework/resources/index.md)  
 [Kaynakları Paketleme ve Dağıtma](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Oluşturma ve Windows mağazası uygulamalarında kaynakları alma](http://go.microsoft.com/fwlink/p/?LinkID=241674)
