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
ms.openlocfilehash: 17795db2cdec419a31fe862793c88506f9535ff9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180457"
---
# <a name="retrieving-resources-in-desktop-apps"></a>Masaüstü Uygulamalarında Kaynakları Alma

.NET Framework masaüstü uygulamalarında yerelleştirilmiş kaynaklarla çalışırken, varsayılan veya nötr kültür kaynaklarını ana derlemeyle düzenli olarak paketlemeli ve uygulamanızın desteklediği her dil veya kültür için ayrı bir uydu derlemesi oluşturmalısınız. Daha sonra adlandırılmış kaynaklara <xref:System.Resources.ResourceManager> erişmek için bir sonraki bölümde açıklandığı gibi sınıfı kullanabilirsiniz. Kaynaklarınızı ana derlemeye ve uydu derlemelerine gömmemeyi seçerseniz, bu makalenin ilerleyen bölümlerinde [açıkolduğu](#from_file) gibi ikili .kaynaklar dosyalarına da doğrudan erişebilirsiniz.  Windows 8.x Store uygulamalarındaki kaynakları almak için Windows [Mağazası uygulamalarında kaynak oluşturma ve alma](https://docs.microsoft.com/previous-versions/windows/apps/hh694557(v=vs.140))hakkında bkz.  
  
<a name="from_assembly"></a>
## <a name="retrieving-resources-from-assemblies"></a>Derlemelerden Kaynak Alma  
 Sınıf, <xref:System.Resources.ResourceManager> çalışma zamanında kaynaklara erişim sağlar. Dize <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> kaynaklarını almak için yöntemi <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType> <xref:System.Resources.ResourceManager.GetStream%2A?displayProperty=nameWithType> ve dize olmayan kaynakları almak için veya yöntemi kullanırsınız. Her yöntemin iki aşırı yüklemesi vardır:  
  
- Tek parametresi kaynağın adını içeren bir dize olan aşırı yük. Yöntem, geçerli iş parçacığı kültürü için bu kaynağı almaya çalışır. Daha fazla bilgi <xref:System.Resources.ResourceManager.GetString%28System.String%29>için <xref:System.Resources.ResourceManager.GetObject%28System.String%29>, <xref:System.Resources.ResourceManager.GetStream%28System.String%29> , ve yöntemleri bakın.  
  
- İki parametreye sahip bir aşırı yükleme: kaynağın adını <xref:System.Globalization.CultureInfo> içeren bir dize ve kaynağı alınacak kültürü temsil eden bir nesne. Bu kültür için bir kaynak kümesi bulunamazsa, kaynak yöneticisi uygun bir kaynak almak için geri dönüş kurallarını kullanır. Daha fazla bilgi <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>için <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> , ve yöntemleri bakın.  
  
 Kaynak yöneticisi, uygulamanın kültüre özgü kaynakları nasıl aldığını denetlemek için kaynak geri dönüş işlemini kullanır. Daha fazla bilgi için, Kaynakları Paketleme ve Dağıtma'daki "Kaynak Geri Dönüş Süreci" [bölümüne](packaging-and-deploying-resources-in-desktop-apps.md)bakın. Bir <xref:System.Resources.ResourceManager> nesneyi anlık olarak kullanma hakkında bilgi için sınıf konusundaki "ResourceManager <xref:System.Resources.ResourceManager> Nesnesini Anında Kullanma" bölümüne bakın.  
  
### <a name="retrieving-string-data-an-example"></a>String Veri Alma: Bir Örnek  
 Aşağıdaki örnekte, <xref:System.Resources.ResourceManager.GetString%28System.String%29> geçerli UI kültürünün dize kaynaklarını alma yöntemi ni çağırır. İngilizce (Amerika Birleşik Devletleri) kültürü ve Fransız (Fransa) ve Rus (Rusya) kültürleri için yerelleştirilmiş kaynaklar için tarafsız bir dize kaynağı içerir. Aşağıdaki İngilizce (ABD) kaynağı Strings.txt adlı bir dosyada dır:  
  
```text
TimeHeader=The current time is  
```  
  
 Fransızca (Fransa) kaynağı Strings.fr-FR.txt adlı bir dosyada dır:  
  
```text
TimeHeader=L'heure actuelle est  
```  
  
 Rus (Rusya) kaynağı Strings.ru-RU-txt adlı bir dosyada dır:  
  
```text
TimeHeader=Текущее время —  
```  
  
 Bu örneğin kaynak kodu, kodun C# sürümü için GetString.cs adlı bir dosyada ve Visual Basic sürümü için GetString.vb adlı bir dosyada, dört kültürün adını içeren bir dize dizisini tanımlar: kaynakların bulunduğu üç kültür ve İspanyolca (İspanya) kültürü. Beş kez rasgele yürüten bir döngü bu kültürlerden birini seçer <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> ve <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> onu ve özelliklerine atar. Daha sonra, <xref:System.Resources.ResourceManager.GetString%28System.String%29> günün saati ile birlikte görüntülediği yerelleştirilmiş dizeyi almak için yöntemi çağırır.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstring.cs#3)]
 [!code-vb[Conceptual.Resources.Retrieving#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstring.vb#3)]  
  
 Aşağıdaki toplu iş (.bat) dosyası örneği derler ve uygun dizinlerde uydu derlemeleri oluşturur. Komutlar C# dili ve derleyicisi için sağlanır. Visual Basic için, `vbc`''' olarak değiştirin `csc` ve ' `GetString.cs` ' `GetString.vb`  
  
```console
resgen strings.txt  
csc GetString.cs -resource:strings.resources  
  
resgen strings.fr-FR.txt  
md fr-FR  
al -embed:strings.fr-FR.resources -culture:fr-FR -out:fr-FR\GetString.resources.dll  
  
resgen strings.ru-RU.txt  
md ru-RU  
al -embed:strings.ru-RU.resources -culture:ru-RU -out:ru-RU\GetString.resources.dll  
```  
  
 Geçerli UI kültürü İspanyolca (İspanya) olduğunda, İspanyolca dil kaynakları kullanılamadığından ve İngilizce örneğin varsayılan kültürü olduğundan, örneğin İngilizce dil kaynaklarını görüntülediğine unutmayın.  
  
### <a name="retrieving-object-data-two-examples"></a>Nesne Verilerini Alma: İki Örnek  
 Nesne verilerini <xref:System.Resources.ResourceManager.GetObject%2A> almak <xref:System.Resources.ResourceManager.GetStream%2A> için yöntemleri kullanabilirsiniz. Bu, ilkel veri türlerini, serileştirilebilir nesneleri ve ikili biçimde depolanan nesneleri (görüntüler gibi) içerir.  
  
 Aşağıdaki örnek, <xref:System.Resources.ResourceManager.GetStream%28System.String%29> bir uygulamanın açılış sıçrama penceresinde kullanılan bir bit eşlemi almak için yöntemi kullanır. CreateResources.cs (C#için) veya CreateResources.vb (Visual Basic için) adlı bir dosyadaki aşağıdaki kaynak kodu, serileştirilmiş görüntüyü içeren bir .resx dosyası oluşturur. Bu durumda, görüntü SplashScreen.jpg adlı bir dosyadan yüklenir; kendi resminizi değiştirmek için dosya adını değiştirebilirsiniz.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/createresources.cs#4)]
 [!code-vb[Conceptual.Resources.Retrieving#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/createresources.vb#4)]  
  
 Aşağıdaki kod kaynağı alır ve görüntüyü denetimde <xref:System.Windows.Forms.PictureBox> görüntüler.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstream.cs#5)]
 [!code-vb[Conceptual.Resources.Retrieving#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstream.vb#5)]  
  
 C# örneğini oluşturmak için aşağıdaki toplu iş dosyasını kullanabilirsiniz. Visual Basic için `csc` `vbc`kaynak kod dosyasının uzantısını ' `.cs` `.vb`'' olarak değiştirin ve '' olarak değiştirin  
  
```console
csc CreateResources.cs  
CreateResources  
  
resgen AppResources.resx  
  
csc GetStream.cs -resource:AppResources.resources  
```  
  
 Aşağıdaki örnek, <xref:System.Resources.ResourceManager.GetObject%28System.String%29?displayProperty=nameWithType> özel bir nesneyi deserialize etmek için yöntemi kullanır. Örnek, UIElements.cs adlı bir kaynak kodu dosyası içerir (Visual Basic için UIElements.vb) adlı `PersonTable`aşağıdaki yapıyı tanımlar. Bu yapı, tablo sütunlarının yerelleştirilmiş adlarını görüntüleyen genel bir tablo görüntüleme yordamı tarafından kullanılmak üzere tasarlanmıştır. Yapının `PersonTable` öznitelik ile <xref:System.SerializableAttribute> işaretlendiğini unutmayın.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example.cs#6)]
 [!code-vb[Conceptual.Resources.Retrieving#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#6)]  
  
 CreateResources.cs adlı bir dosyadan (Visual Basic için CreateResources.vb) aşağıdaki kod, tablo başlığı nı ve İngilizce dili `PersonTable` için yerelleştirilmiş bir uygulama için bilgi içeren bir nesne depolayan UIResources.resx adlı bir XML kaynak dosyası oluşturur.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example1.cs#7)]
 [!code-vb[Conceptual.Resources.Retrieving#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#7)]  
  
 GetObject.cs (GetObject.vb) adlı bir kaynak kodu dosyasında aşağıdaki kod kaynakları alır ve konsola görüntüler.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example2.cs#8)]
 [!code-vb[Conceptual.Resources.Retrieving#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example2.vb#8)]  
  
 Gerekli kaynak dosyasını ve derlemelerini oluşturabilir ve aşağıdaki toplu iş dosyasını çalıştırarak uygulamayı çalıştırabilirsiniz. Yapı hakkındaki `/r` bilgilere erişebilmek için Resgen.exe'ye UIElements.dll'ye bir başvuru sağlama seçeneğini kullanmanız gerekir. `PersonTable` C# kullanıyorsanız, `vbc` derleyici adını `csc`' ile değiştirin `.vb` ve `.cs`uzantıyı ' ile değiştirin.  
  
```console
vbc -t:library UIElements.vb  
vbc CreateResources.vb -r:UIElements.dll  
CreateResources  
  
resgen UIResources.resx  -r:UIElements.dll  
vbc GetObject.vb -r:UIElements.dll -resource:UIResources.resources  
  
GetObject.exe  
```  
  
## <a name="versioning-support-for-satellite-assemblies"></a>Uydu Montajları için Sürüm Desteği  
 Varsayılan olarak, <xref:System.Resources.ResourceManager> nesne istenen kaynakları aldığında, ana derlemenin sürüm numarasıyla eşleşen sürüm numaralarına sahip uydu derlemelerini arar. Bir uygulamayı dağıttıktan sonra, ana derlemeyi veya belirli kaynak uydu derlemelerini güncelleştirmek isteyebilirsiniz. .NET Framework, ana montaj ve uydu derlemelerinin sürümü için destek sağlar.  
  
 Öznitelik, <xref:System.Resources.SatelliteContractVersionAttribute> bir ana derleme için sürüm desteği sağlar. Bu özniteliği bir uygulamanın ana montajında belirtmek, uydu derlemelerini güncelleştirmeden bir ana derlemeyi güncelleştirmenize ve yeniden dağıtmanıza olanak tanır. Ana derlemeyi güncelledikten sonra, ana derlemenin sürüm numarasını artım, ancak uydu sözleşme sürüm numarasını değiştirmeden bırakın. Kaynak yöneticisi istenen kaynakları aldığında, bu öznitelik tarafından belirtilen uydu derleme sürümünü yükler.  
  
 Yayıncı ilke derlemeleri uydu derlemelerinin sürümü için destek sağlar. Ana derlemeyi güncelleştirmeden uydu derlemesini güncelleyebilir ve yeniden dağıtabilirsiniz. Uydu montajını güncelledikten sonra, sürüm numarasını artım ve bir yayımcı ilke derlemesi ile sevk edin. Yayımcı ilke derlemesinde, yeni uydu derlemenizin önceki sürümüyle geriye dönük uyumlu olduğunu belirtin. Kaynak yöneticisi uydu <xref:System.Resources.SatelliteContractVersionAttribute> derlemesinin sürümünü belirlemek için özniteliği kullanır, ancak montaj yükleyiciyayım ilkesi tarafından belirtilen uydu montaj sürümüne bağlanır. Yayımcı ilke derlemeleri hakkında daha fazla bilgi için [bkz.](../configure-apps/how-to-create-a-publisher-policy.md)  
  
 Tam montaj sürüm desteğini etkinleştirmek için, [genel derleme önbelleğinde](../app-domains/gac.md) güçlü adlandırılmış derlemeler dağıtmanızı ve uygulama dizininde güçlü adları olmayan derlemeleri dağıtmanızı öneririz. Uygulama dizininde güçlü adlandırılmış derlemeler dağıtmak istiyorsanız, derlemeyi güncelleştirdiğinizde uydu derlemesinin sürüm numarasını artımayı mümkün olmazsınız. Bunun yerine, varolan kodu güncelleştirilmiş kodla değiştirip aynı sürüm numarasını koruduğunuz yerinde bir güncelleştirme gerçekleştirmeniz gerekir. Örneğin, uydu assemblyin 1.0.0.0 sürümünü tam olarak belirtilen montaj adı "myApp.resources, Version=1.0.0.0, Culture=de, PublicKeyToken=b03f5f11d50a3a" ile güncellemek istiyorsanız, güncellenmiş myApp.resources.dll ile üzerine yazmak aynı, tam olarak belirtilen montaj adı "myApp.resources, Version=1.0.0.0, Culture=de, PublicKeyToken=b03f5f11d50a3a" ile derlenmiştir. Uydu derleme dosyalarındaki yerinde güncelleştirmeleri kullanmanın, bir uygulamanın uydu derlemesinin sürümünü doğru bir şekilde belirlemesini zorlaştırdığını unutmayın.  
  
 Derleme sürümü hakkında daha fazla bilgi için [Montaj Sürümü](../../standard/assembly/versioning.md) ve Çalışma [Zamanı Derlemeleri Nasıl Bulur'a](../deployment/how-the-runtime-locates-assemblies.md)bakın.  
  
<a name="from_file"></a>
## <a name="retrieving-resources-from-resources-files"></a>.resources Dosyalarından Kaynak Alma  
 Kaynakları uydu derlemelerine dağıtmamayı seçerseniz, kaynaklara <xref:System.Resources.ResourceManager> doğrudan .kaynaklar dosyalarından erişmek için bir nesne kullanmaya devam edebilirsiniz. Bunu yapmak için .resources dosyalarını doğru dağıtmanız gerekir. Ardından, nesneyi <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%2A?displayProperty=nameWithType> <xref:System.Resources.ResourceManager> anında anımsamak ve bağımsız .kaynaklar dosyalarını içeren dizin belirtmek için yöntemi kullanırsınız.  
  
### <a name="deploying-resources-files"></a>.resources Dosyalarını dağıtma  
 .resources dosyalarını bir uygulama derlemesine ve uydu derlemelerine katıştırdığınızda, her uydu derlemesi aynı dosya adıvardır, ancak uydu derlemesinin kültürünü yansıtan bir alt dizine yerleştirilir. Bunun aksine, .kaynaklar dosyalarından kaynaklara doğrudan erişdiğinizde, tüm .resources dosyalarını genellikle uygulama dizininin bir alt dizini olan tek bir dizine yerleştirebilirsiniz. Uygulamanın varsayılan .resources dosyasının adı yalnızca bir kök adından oluşur ve kültürüne dair hiçbir belirti göstermez (örneğin, strings.resources). Her yerelleştirilmiş kültürün kaynakları, adı kültür tarafından izlenen kök adından oluşan bir dosyada depolanır (örneğin, strings.ja.resources veya strings.de-DE.resources).

 Aşağıdaki resimde kaynak dosyalarının dizin yapısında nerede bulunması gerektiği gösterilmektedir. Ayrıca .kaynak dosyaları için adlandırma kuralları verir.  

 ![Uygulamanızın ana dizinini gösteren çizim.](./media/retrieving-resources-in-desktop-apps/resource-application-directory.gif)  
  
### <a name="using-the-resource-manager"></a>Kaynak Yöneticisini Kullanma  
 Kaynaklarınızı oluşturduktan ve bunları uygun dizine yerleştirdikten <xref:System.Resources.ResourceManager> sonra, <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%28System.String%2CSystem.String%2CSystem.Type%29> yöntemi çağırarak kaynakları kullanmak için bir nesne oluşturursunuz. İlk parametre, uygulamanın varsayılan .resources dosyasının kök adını belirtir (bu önceki bölümdeki örnek için "dizeleri" olacaktır). İkinci parametre kaynakların konumunu belirtir ("Önceki örnek için Kaynaklar"). Üçüncü parametre, <xref:System.Resources.ResourceSet> kullanılacak uygulamayı belirtir. Üçüncü parametre `null`ise, varsayılan çalışma <xref:System.Resources.ResourceSet> süresi kullanılır.  
  
> [!NOTE]
> Tek başına .resources dosyalarını kullanarak ASP.NET uygulamaları dağıtmayın. Bu kilitleme sorunlarına neden olabilir ve XCOPY dağıtım tatili. ASP.NET kaynakları uydu meclislerine dağıtmanızı öneririz. Daha fazla bilgi için [Web Sayfası Kaynaklarına Genel Bakış ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/ms227427(v=vs.100))sayfasına bakın.  
  
 <xref:System.Resources.ResourceManager> Nesneyi anında yaptıktan sonra, kaynakları <xref:System.Resources.ResourceManager.GetString%2A>almak <xref:System.Resources.ResourceManager.GetObject%2A>için <xref:System.Resources.ResourceManager.GetStream%2A> daha önce tartışıldığı gibi , ve yöntemleri kullanırsınız. Ancak, kaynakların doğrudan .resources dosyalarından alınması, katışılmış kaynakların derlemelerden alınmasından farklıdır. .resources dosyalarından kaynak <xref:System.Resources.ResourceManager.GetString%28System.String%29>aldığınızda, <xref:System.Resources.ResourceManager.GetObject%28System.String%29>,, ve <xref:System.Resources.ResourceManager.GetStream%28System.String%29> yöntemler her zaman geçerli kültürden bağımsız olarak varsayılan kültürün kaynaklarını alır. Uygulamanın geçerli kültürünün veya belirli bir kültürün kaynaklarını almak için <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>, <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> veya yöntemi aramanız ve kaynakları alınacak kültürü belirtmeniz gerekir. Geçerli kültürün kaynaklarını almak için, bağımsız değişken <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> olarak `culture` özelliğin değerini belirtin. Kaynak yöneticisi kaynakları `culture`alamıyorsa, uygun kaynakları almak için standart kaynak geri dönüş kurallarını kullanır.  
  
### <a name="an-example"></a>Bir Örnek  
 Aşağıdaki örnekte, kaynak yöneticisinin kaynakları doğrudan .resources dosyalarından nasıl aldığı gösterilebilir. Örnek, İngilizce (ABD), Fransızca (Fransa) ve Rus (Rusya) kültürleri için metin tabanlı üç kaynak dosyasından oluşur. İngilizce (ABD) örneğin varsayılan kültürüdür. Kaynakları Strings.txt adlı aşağıdaki dosyada depolanır:  
  
```text
Greeting=Hello  
Prompt=What is your name?  
```  
  
 Fransız (Fransa) kültürü için kaynaklar Strings.fr-FR.txt adlı aşağıdaki dosyada saklanır:  
  
```text
Greeting=Bon jour  
Prompt=Comment vous appelez-vous?  
```  
  
 Rus (Rusya) kültürü için kaynaklar Strings.ru-RU.txt adlı aşağıdaki dosyada saklanır:  
  
```text
Greeting=Здравствуйте  
Prompt=Как вас зовут?  
```  
  
 Aşağıdaki örnek için kaynak kodudur. Örnek, İngilizce (ABD), İngilizce (Kanada), Fransızca (Fransa) ve Rus (Rusya) kültürleri için <xref:System.Globalization.CultureInfo> nesneleri anlık olarak alır ve her birinin geçerli kültürünü yapar. Yöntem <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> daha sonra uygun <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> kültüre `culture` özgü kaynakları almak için bağımsız değişken olarak özelliğin değerini sağlar.  
  
 [!code-csharp[Conceptual.Resources.Retrieving#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example3.cs#9)]
 [!code-vb[Conceptual.Resources.Retrieving#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example3.vb#9)]  
  
 Aşağıdaki toplu iş dosyasını çalıştırarak örneğin C# sürümünü derleyebilirsiniz. Visual `csc` Basic kullanıyorsanız, uzantıyı `vbc` `.cs` `.vb`değiştirin ve uzantıyı değiştirin.  
  
```console
Md Resources  
Resgen Strings.txt Resources\Strings.resources  
Resgen Strings.fr-FR.txt Resources\Strings.fr-FR.resources  
Resgen Strings.ru-RU.txt Resources\Strings.ru-RU.resources  
  
csc Example.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Resources.ResourceManager>
- [Masaüstü Uygulamalarında Kaynaklar](index.md)
- [Kaynakları Paketleme ve Dağıtma](packaging-and-deploying-resources-in-desktop-apps.md)
- [Çalışma Zamanının Derlemelerin Konumunu Bulması](../deployment/how-the-runtime-locates-assemblies.md)
- [Windows Mağazası uygulamalarında kaynak oluşturma ve alma](https://docs.microsoft.com/previous-versions/windows/apps/hh694557(v=vs.140))
