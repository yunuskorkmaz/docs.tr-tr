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
ms.openlocfilehash: 6db8f5914a325a276872ff804f679f8b3e0745a0
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653931"
---
# <a name="retrieving-resources-in-desktop-apps"></a>Masaüstü Uygulamalarında Kaynakları Alma
.NET Framework masaüstü uygulamalarında yerelleştirilmiş kaynaklar ile çalışırken, ideal olarak kaynaklar için varsayılan veya bağımsız kültür ile ana derleme paketi ve her bir dil veya uygulamanızın desteklediği kültür için bir ayrı uydu derleme oluşturma gerekir. Ardından <xref:System.Resources.ResourceManager> adlandırılmış kaynaklara erişmek için sonraki bölümde açıklandığı gibi sınıf. Kaynaklarınızı ana derlemeyi ve uydu derlemeler içinde değil eklemek isterseniz da ikili .resources dosyalarına doğrudan bölümünde açıklandığı gibi erişebilirsiniz [.resources dosyalarındaki kaynaklar alınıyor](#from_file) daha sonra bu makale.  İçindeki kaynakları almak için [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar, [oluşturma ve Windows Store uygulamalarında kaynakları alma](https://go.microsoft.com/fwlink/p/?LinkID=241674) Windows geliştirme Merkezi'nde.  
  
<a name="from_assembly"></a>   
## <a name="retrieving-resources-from-assemblies"></a>Derlemelerden kaynakları alma  
 <xref:System.Resources.ResourceManager> Sınıfı, çalışma zamanında kaynaklara erişim sağlar. Kullandığınız <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> dize kaynakları almak için yöntemi ve <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType> veya <xref:System.Resources.ResourceManager.GetStream%2A?displayProperty=nameWithType> dize olmayan kaynaklar almak için yöntemi. Her yöntemin iki aşırı yüklemesi vardır:  
  
-   Aşırı yükleme, tek bir parametre kaynağın adını içeren bir dizedir. Yöntemi, o kaynak için geçerli iş parçacığı kültürünü almayı dener. Daha fazla bilgi için <xref:System.Resources.ResourceManager.GetString%28System.String%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%29>, ve <xref:System.Resources.ResourceManager.GetStream%28System.String%29> yöntemleri.  
  
-   İki parametreleri olan bir aşırı yüklemeyi: bir kaynağın adını içeren dize ve bir <xref:System.Globalization.CultureInfo> olan kaynak alınacak kültürü temsil eden nesne. Bir kaynak için kültür bulunamıyor ayarlarsanız, kaynak yöneticisi uygun bir kaynağı almak için geri dönüş kurallarını kullanır. Daha fazla bilgi için <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>, ve <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> yöntemleri.  
  
 Kaynak Yöneticisi, uygulamanın kültüre özgü kaynaklar nasıl alacağını denetlemek için kaynak geri dönüş işlemi kullanır. "Kaynak geri dönüş işlemi" bölümünde daha fazla bilgi için bkz. [kaynakları paketleme ve dağıtma](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md). Örnekleme hakkında bilgi için bir <xref:System.Resources.ResourceManager> nesne, "ResourceManager nesnesini örnekleme" bölümüne bakın <xref:System.Resources.ResourceManager> sınıf konusuna.  
  
### <a name="retrieving-string-data-an-example"></a>Dize verileri alınıyor: Bir Örnek  
 Aşağıdaki örnek çağrıları <xref:System.Resources.ResourceManager.GetString%28System.String%29> geçerli UI kültürünün dize kaynaklarını almak için yöntemi. İngilizce (ABD) kültürü için bir bağımsız dize kaynağını ve yerelleştirilmiş kaynaklar Fransızca (Fransa) ve Rusça (Rusya) kültürleri için içerir. Aşağıdaki İngilizce (ABD) kaynak Strings.txt adlı dosyasıdır:  
  
```  
TimeHeader=The current time is  
```  
  
 Fransızca (Fransa) kaynaktır Strings.fr adındaki bir dosyada-FR.txt:  
  
```  
TimeHeader=L'heure actuelle est  
```  
  
 Rusça (Rusya) Strings.ru RU txt adındaki bir dosyada kaynağıdır:  
  
```  
TimeHeader=Текущее время —  
```  
  
 C# sürümü için GetString.vb ve kod Visual Basic sürümünü GetString.cs adındaki bir dosyaya, bu örnek, kaynak kodu dört kültür adını içeren dize dizisi tanımlar: kendisi için kaynakları kullanılabilir üç kültürler ve İspanyolca (İspanya) kültür. Beş kez rastgele yürüten bir döngü bu kültürler birini seçer ve buna atayan <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> ve <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> özellikleri. Ardından <xref:System.Resources.ResourceManager.GetString%28System.String%29> birlikte günün saatini gösteren yerelleştirilmiş dizeyi almak için yöntemi.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstring.cs#3)]
 [!code-vb[Conceptual.Resources.Retrieving#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstring.vb#3)]  
  
 Aşağıdaki toplu (.bat) dosyası, örnek derler ve uygun dizinler uydu derlemeleri üretir. Komutlar C# dili ve derleyici için sağlanır. Visual Basic için değiştirme `csc` için `vbc`, değiştirip `GetString.cs` için `GetString.vb`.  
  
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
  
 Geçerli UI kültürünün İspanyolca (İspanya) olduğunda, örneğin İngilizce dil kaynakları, İspanyolca dil kaynakları kullanılamaz ve örneğin varsayılan kültürü İngilizce olduğundan görüntüler unutmayın.  
  
### <a name="retrieving-object-data-two-examples"></a>Nesne verileri alınıyor: İki örnek  
 Kullanabileceğiniz <xref:System.Resources.ResourceManager.GetObject%2A> ve <xref:System.Resources.ResourceManager.GetStream%2A> nesne verilerini almak için yöntemler. Bu, basit veri türleri, seri hale getirilebilir nesneleri ve (örneğin, resim) ikili biçimde depolanmış nesneleri içerir.  
  
 Aşağıdaki örnekte <xref:System.Resources.ResourceManager.GetStream%28System.String%29> yönteminin bir uygulamada kullanılan bir bit eşlem almak için giriş penceresini açma. Aşağıdaki kaynak kodu adındaki bir dosyaya CreateResources.cs (C# için) veya CreateResources.vb (Visual Basic için) seri hale getirilmiş görüntüsünü içeren .resx dosyası oluşturur. Bu durumda, görüntünün SplashScreen.jpg adlı bir dosya yüklenir; kendi görüntünüzü yerine dosya adını değiştirebilirsiniz.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/createresources.cs#4)]
 [!code-vb[Conceptual.Resources.Retrieving#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/createresources.vb#4)]  
  
 Aşağıdaki kod kaynağı alır ve görüntüler görüntüde bir <xref:System.Windows.Forms.PictureBox> denetimi.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstream.cs#5)]
 [!code-vb[Conceptual.Resources.Retrieving#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstream.vb#5)]  
  
 C# örneği oluşturmak için aşağıdaki toplu iş dosyası kullanabilirsiniz. Visual Basic için değiştirme `csc` için `vbc`, kaynak kod dosyasının uzantısı değiştirip `.cs` için `.vb`.  
  
```  
csc CreateResources.cs  
CreateResources  
  
resgen AppResources.resx  
  
csc GetStream.cs -resource:AppResources.resources  
```  
  
 Aşağıdaki örnekte <xref:System.Resources.ResourceManager.GetObject%28System.String%29?displayProperty=nameWithType> yöntemi özel bir nesne seri durumdan çıkarılacak. Örnek adlı aşağıdaki yapısını tanımlayan UIElements.cs (Visual Basic için UIElements.vb) adlı bir kaynak kodu dosyası içerir `PersonTable`. Bu yapı, tablo sütunları yerelleştirilmiş adlarını görüntüler genel bir tablo görüntüleme yordamı tarafından kullanılmak üzere tasarlanmıştır. Unutmayın `PersonTable` yapısı ile işaretlenmiş <xref:System.SerializableAttribute> özniteliği.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example.cs#6)]
 [!code-vb[Conceptual.Resources.Retrieving#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#6)]  
  
 Adlı bir dosyaya aşağıdaki kodu CreateResources.cs (Visual Basic için CreateResources.vb) depolayan bir tablo başlığı UIResources.resx adlı bir XML kaynak dosyası oluşturur ve bir `PersonTable` için yerelleştirilmiş bir uygulama için bilgi içeren nesne İngilizce dili.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example1.cs#7)]
 [!code-vb[Conceptual.Resources.Retrieving#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#7)]  
  
 Bir kaynak kod dosyasında aşağıdaki kodu GetObject.cs (GetObject.vb) adlı ardından kaynakları alır ve bunları konsola görüntüler.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example2.cs#8)]
 [!code-vb[Conceptual.Resources.Retrieving#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example2.vb#8)]  
  
 Derlemeler ve gerekli kaynak dosyası oluşturun ve aşağıdaki toplu iş dosyasını çalıştırarak uygulamayı çalıştırın. Kullanmalısınız `/r` UIElements.dll başvurusuyla Resgen.exe hakkında bilgi erişebilmeleri sağlamak seçeneği `PersonTable` yapısı. C# kullanıyorsanız değiştirin `vbc` derleyici adıyla `csc`ve yerine `.vb` uzantısıyla `.cs`.  
  
```  
vbc -t:library UIElements.vb  
vbc CreateResources.vb -r:UIElements.dll  
CreateResources  
  
resgen UIResources.resx  -r:UIElements.dll  
vbc GetObject.vb -r:UIElements.dll -resource:UIResources.resources  
  
GetObject.exe  
```  
  
## <a name="versioning-support-for-satellite-assemblies"></a>Uydu derlemeler için sürüm oluşturma desteği  
 Varsayılan olarak, zaman <xref:System.Resources.ResourceManager> nesne istenen kaynaklara alır, ana derlemenin sürüm numarası aynı sürüm numarasına sahip uydu derlemeleri için görünür. Bir uygulamayı dağıttıktan sonra ana derlemeye veya belirli kaynak uydu derlemeleri güncelleştirmek isteyebilirsiniz. .NET Framework ana derlemeyi ve uydu derlemeleri sürüm oluşturma için destek sağlar.  
  
 <xref:System.Resources.SatelliteContractVersionAttribute> Özniteliği için bir ana derleme sürüm oluşturma desteği sağlar. Bir uygulamanın ana derlemesini üzerinde bu öznitelik belirtmemeye, güncelleştirme ve kendi uydu derlemeleri güncelleştirmeden bir ana derlemeye yeniden dağıtma sağlar. Ana derleme güncelleştirdikten sonra ana derlemenin sürüm numarasını Artır ancak uydu sözleşme sürüm numarasını değiştirmeden bırakın. Kaynak Yöneticisi istenen kaynaklara aldığında, bu özniteliği tarafından belirtilen uydu derleme sürümünü yükler.  
  
 Yayımcı ilkesi derlemeleri uydu derlemeler için sürüm oluşturma desteği. Güncelleştirme ve ana derleme güncelleştirmeden bir uydu derleme yeniden dağıtın. Uydu derlemesi güncelleştirdikten sonra sürüm numarasını Artır ve yayımcı ilke derlemesi ile gönderin. Yayımcı ilke derlemesi içinde yeni bir uydu bütünleştirilmiş kodunuzda geriye dönük olarak uyumlu olduğunu belirtmek, önceki bir sürümüne sahip. Kaynak Yöneticisi'ni kullanacaksınız <xref:System.Resources.SatelliteContractVersionAttribute> uydu derlemesini, ancak bütünleştirilmiş kod yükleyicisi sürümünü belirlemek için öznitelik bir yayımcı ilkesi tarafından belirtilen uydu derleme sürümü bağlanma. Yayımcı ilke derlemesi hakkında daha fazla bilgi için bkz. [Yayımcı ilkesi dosyası oluşturma](../../../docs/framework/configure-apps/how-to-create-a-publisher-policy.md).  
  
 Tam derleme sürümü oluşturma desteğini etkinleştirmek için tanımlayıcı adlı derlemeler dağıtmanızı öneririz [genel derleme önbelleği](../../../docs/framework/app-domains/gac.md) ve güçlü adlar uygulama dizininde olmayan derlemeleri dağıtın. Tanımlayıcı adlı derlemeleri uygulama dizininde dağıtmak istiyorsanız, bir uydu derleme sürüm numarası, derleme güncelleştirdiğinizde artırmak mümkün olmayacaktır. Bunun yerine, burada mevcut kodu güncelleştirilmiş kod ile değiştirin ve aynı sürüm numarasını Koru bir yerinde güncelleştirme gerçekleştirmeniz gerekir. Örneğin, tam olarak belirtilen derleme adı ile bir uydu derlemesine 1.0.0.0 sürümüne güncelleştirmek istiyorsanız "myApp.resources, sürüm 1.0.0.0, Culture = de, PublicKeyToken = b03f5f11d50a3a =", olan güncelleştirilmiş myApp.resources.dll ile üzerine aynı, tam olarak belirtilen derleme adı ile derlenmiş "myApp.resources, sürüm 1.0.0.0, Culture = de, PublicKeyToken = b03f5f11d50a3a =". Uydu derleme dosyalarına yerinde güncelleştirmeleri kullanarak bir uydu derleme sürümünü doğru bir şekilde belirlemek uygulama zorlaştırır olduğunu unutmayın.  
  
 Derleme sürüm oluşturma hakkında daha fazla bilgi için bkz. [derleme sürümlendirme](../../../docs/framework/app-domains/assembly-versioning.md) ve [çalışma zamanı derlemeleri nasıl konumlandırır](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
<a name="from_file"></a>   
## <a name="retrieving-resources-from-resources-files"></a>.Resources dosyalarını kaynakları alma  
 Kaynakları uydu derlemelerinde dağıtma kullanmayı tercih ederseniz kullanmaya devam edebilirsiniz bir <xref:System.Resources.ResourceManager> erişim kaynaklara nesneden .resources dosyaları doğrudan. Bunu yapmak için .resources dosyaları doğru dağıtmanız gerekir. Kullanmanız <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%2A?displayProperty=nameWithType> örneklemek için yöntemi bir <xref:System.Resources.ResourceManager> nesne ve tek başına .resources dosyalarını içeren dizini belirtin.  
  
### <a name="deploying-resources-files"></a>.Resources dosyalarını dağıtma  
 Bir uygulama derleme ve uydu derlemeler içinde .resources dosyaları eklediğinizde, her bir uydu derlemesini, aynı dosya adına sahip ancak uydu bütünleştirilmiş kodun kültürü yansıtan bir alt dizinine yerleştirilir. Buna karşılık, .resources dosyaları doğrudan kaynaklara erişirken tek bir dizinde, genellikle uygulama dizininin bir alt .resources dosyaları yerleştirebilirsiniz. Uygulamanın varsayılan .resources dosyasının adı (örneğin, strings.resources) kültürü herhangi bir gösterge ile yalnızca bir kök adı oluşur. Kaynaklar için her bir yerelleştirilmiş kültür adı (örneğin, strings.ja.resources veya strings.de-DE.resources) kültürü tarafından izlenen kök adı oluşan bir dosyada depolanır. 
 
 Aşağıdaki çizimde gösterildiği dizin yapısında kaynak dosyaları nerede yerleştirilmelidir. Ayrıca adlandırma kuralları için .resource dosyaları sağlar.  

 ![Uygulamanız için ana dizin gösteren şekil.](./media/retrieving-resources-in-desktop-apps/resource-application-directory.gif)  
  
### <a name="using-the-resource-manager"></a>Kaynak Yöneticisi'ni kullanma  
 Kaynaklarınızı oluşturduktan sonra bunları uygun dizine yerleştirilir, oluşturun bir <xref:System.Resources.ResourceManager> çağırarak kaynakları kullanmak için nesne <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%28System.String%2CSystem.String%2CSystem.Type%29> yöntemi. İlk parametre (örneğin önceki bölümde "dize" olacaktır) uygulamanın varsayılan .resources dosyasının kök adı belirtir. İkinci parametre (önceki örnek "Kaynaklar") kaynakların konumunu belirtir. Üçüncü parametre belirtir <xref:System.Resources.ResourceSet> kullanılacak uygulama. Üçüncü parametre ise `null`, varsayılan çalışma zamanı <xref:System.Resources.ResourceSet> kullanılır.  
  
> [!NOTE]
>  Tek başına .resources dosyaları kullanarak ASP.NET uygulamaları dağıtmayın. Bu, kilitleme sorunları ve sonu XCOPY dağıtımının neden olabilir. ASP.NET kaynakları uydu derlemelerinde dağıtmanızı öneririz. Daha fazla bilgi için [ASP.NET Web sayfası kaynaklarına genel bakış](https://docs.microsoft.com/previous-versions/aspnet/ms227427(v=vs.100)).  
  
 Örneği sonra <xref:System.Resources.ResourceManager> nesnesi, kullandığınız <xref:System.Resources.ResourceManager.GetString%2A>, <xref:System.Resources.ResourceManager.GetObject%2A>, ve <xref:System.Resources.ResourceManager.GetStream%2A> kaynakları almak için daha önce bahsedildiği gibi yöntemleri. Ancak, .resources dosyaları doğrudan kaynaklarından alınmasını derlemelerden gömülü kaynaklar alınmasını farklıdır. .Resources dosyaları, kaynakları alırken <xref:System.Resources.ResourceManager.GetString%28System.String%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%29>, ve <xref:System.Resources.ResourceManager.GetStream%28System.String%29> yöntemleri daima geçerli kültüre bakılmaksızın varsayılan kültürün kaynakları alır. Her iki uygulamanın geçerli kültürün veya belirli bir kültürün kaynaklarını almak için çağırmalıdır <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>, veya <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> yöntemi ve kaynaklarını alınacak olan kültürü belirtin. Geçerli kültürün kaynakları almak için değerini belirtin. <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özelliği olarak `culture` bağımsız değişken. Resource manager kaynaklarını alamıyorsa `culture`, uygun kaynakları almak için standart kaynak geri dönüş kurallarını kullanır.  
  
### <a name="an-example"></a>Bir Örnek  
 Aşağıdaki örnek, kaynak yöneticisi kaynaklar doğrudan .resources dosyaları nasıl alacağını gösterir. Örneğin İngilizce (Amerika Birleşik Devletleri), Fransızca (Fransa) ve Rusça (Rusya) kültürleri için üç metin tabanlı kaynak dosyalardan oluşur. İngilizce (Amerika Birleşik Devletleri), örneğin varsayılan kültürdür. Kaynaklarını Strings.txt adlı aşağıdaki dosya depolanır:  
  
```  
Greeting=Hello  
Prompt=What is your name?  
```  
  
 Fransızca (Fransa) kültürü için kaynaklar Strings.fr adlı aşağıdaki dosyasında depolanan-FR.txt:  
  
```  
Greeting=Bon jour  
Prompt=Comment vous appelez-vous?  
```  
  
 Rusça (Rusya) kültürü için kaynaklar Strings.ru adlı aşağıdaki dosyasında depolanan-RU.txt:  
  
```  
Greeting=Здравствуйте  
Prompt=Как вас зовут?  
```  
  
 Örnek kaynak kodu verilmiştir. Örnek <xref:System.Globalization.CultureInfo> nesneleri İngilizce (Amerika Birleşik Devletleri), İngilizce (Kanada), Fransızca (Fransa) ve Rusça (Rusya) kültürleri için ve her geçerli kültürü yapar. <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> Yöntemi ardından sağladığı değeri <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özelliği olarak `culture` uygun bir kültüre özgü kaynakları almak için bağımsız değişken.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example3.cs#9)]
 [!code-vb[Conceptual.Resources.Retrieving#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example3.vb#9)]  
  
 Örnek C# sürümü aşağıdaki toplu iş dosyası çalıştırılarak derleyebilirsiniz. Visual Basic kullanıyorsanız değiştirin `csc` ile `vbc`ve yerine `.cs` uzantısıyla `.vb`.  
  
```  
Md Resources  
Resgen Strings.txt Resources\Strings.resources  
Resgen Strings.fr-FR.txt Resources\Strings.fr-FR.resources  
Resgen Strings.ru-RU.txt Resources\Strings.ru-RU.resources  
  
csc Example.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Resources.ResourceManager>
- [Masaüstü Uygulamalarındaki Kaynaklar](../../../docs/framework/resources/index.md)
- [Kaynakları Paketleme ve Dağıtma](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Oluşturma ve Windows Store uygulamalarında kaynakları alma](https://go.microsoft.com/fwlink/p/?LinkID=241674)
