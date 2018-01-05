---
title: "Dış Ruleset Araç Seti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a306d283-a031-475e-aa01-9ae86e7adcb0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fbac6bf8be169aca8ad61c69b8d024f44928d8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="external-ruleset-toolkit"></a>Dış Ruleset Araç Seti
Bir iş akışı uygulama içinde kuralları kullanıldığında, normalde derlemenin parçası kurallardır. Bazı senaryolarda, böylece yeniden oluşturma ve dağıtma iş akışı derlemesi güncelleştirilebilir ayrı olarak derlemesinden RuleSets korumak isteyebilirsiniz. Bu örnek, yönetme ve bir veritabanında RuleSets düzenlemek ve çalışma zamanında bir iş akışı bu RuleSets erişmek sağlar. Bu otomatik olarak RuleSet değişikliklerin uygulanması çalışan iş akışı örnekleri sağlar.  
  
 Dış RuleSet Araç Seti örnek, yönetme ve bir veritabanı RuleSet sürümlerde düzenlemek için kullanabileceğiniz bir Windows Forms tabanlı aracı içerir. Bir etkinliği ve bir ana bilgisayar hizmeti, bu kurallar yürütmek de içerir.  
  
> [!NOTE]
>  Bu örnek gerektirir [Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkId=96181).  
  
 [!INCLUDE[vsprvsext](../../../../includes/vsprvsext-md.md)]Windows Workflow Foundation (WF) bir parçası olarak RuleSet Düzenleyicisi sağlar. Bu Düzenleyici'yi tıklatarak başlatabilirsiniz `Policy` bir iş akışı; etkinliğinde tanımlı RuleSet nesnesi iş akışı ile ilişkilendirilmiş .rules dosyasına serileştiren (bir `Policy` etkinlik RuleSet örnek iş akışı karşı çalışır). İş akışı projeyi derlerken .rules dosyanın derleme bir kaynak olarak derlenir.  
  
 Bu örnek INCLUDE bileşenler:  
  
-   Düzenle ve veritabanındaki RuleSet sürümlerini yönetmek için kullanabileceğiniz bir RuleSet grafik kullanıcı arabirimi aracıdır.  
  
-   Ana uygulamanın yapılandırılır ve RuleSets veritabanından erişir RuleSet hizmeti.  
  
-   Bir `ExternalPolicy` RuleSet hizmetinden bir RuleSet ister ve RuleSet karşı iş akışının çalıştığı etkinliği.  
  
 Şekil 1'de bileşenlerin etkileşimi gösterilmektedir. Aşağıdaki bölümlerde, her bileşen açıklanmaktadır.  
  
 ![Dış RuleSet örnek kavramsal genel bakış](../../../../docs/framework/windows-workflow-foundation/samples/media/rulesettoolkitsampleoverview.gif "RuleSetToolkitSampleOverview")  
  
 Şekil 1: Örnek genel bakış  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ExternalRuleSetToolKit`  
  
## <a name="ruleset-tool"></a>RuleSet aracı  
 RuleSet aracı ekran görüntüsü, Şekil 2'de gösterilir. Gelen **kural deposu** menüsünde kullanılabilir RuleSets veritabanından yükleyin ve değiştirilmiş RuleSets geri depoya kaydedin. Uygulama yapılandırma dosyası RuleSet veritabanı için veritabanı bağlantı dizesi sağlar. Aracı'nı başlattığınızda yapılandırılmış veritabanından otomatik olarak RuleSets yükler.  
  
 ![Dış RuleSet Toolket örnek çıktı](../../../../docs/framework/windows-workflow-foundation/samples/media/rulesetbrowser.gif "RuleSetBrowser")  
  
 Şekil 2: RuleSet tarayıcı  
  
 RuleSet Aracı'nı (aracı kilitleme veya diğer yapılandırma sürüm oluşturma yeteneği ek yönetim özellikleri sağlar) birden çok sürümü depolamak ve aynı anda korumak sağlayarak RuleSets, birincil ve ikincil sürüm numaralarını uygular. Aracı'nı kullanarak yeni RuleSet sürümleri oluşturun veya varolan sürümlerini silin. Tıkladığınızda **yeni**, aracı yeni bir RuleSet adı oluşturur ve sürüm 1.0 uygular. Bir sürümünü kopyaladığınızda, aracı kapsanan kuralları dahil olmak üzere seçili RuleSet sürümünün bir kopyasını oluşturur ve yeni ve benzersiz sürüm numaraları atar. Bu sürüm numaralarını varolan RuleSets sürüm numaralarını temel alır. Formdaki ilişkili alanlarını kullanarak RuleSet adı ve sürüm numaralarını değiştirebilirsiniz.  
  
 Tıkladığınızda **kurallarını Düzenle**, Şekil 3'te gösterildiği gibi RuleSet Düzenleyicisi'ni başlatır.  
  
 ![Dış RuleSet Araç Seti örnek çıktı](../../../../docs/framework/windows-workflow-foundation/samples/media/ruleseteditor.gif "RuleSetEditor")  
  
 Şekil 3: RuleSet Düzenleyicisi  
  
 Bir Windows Workflow Foundation parçası olan Düzenleyicisi iletişim kutusu yeniden barındırma budur [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] eklentisi. IntelliSense desteği dahil olmak üzere aynı işlevselliği sağlar. Kurallar, aracı kümesinde ile ilişkili hedef türü (örneğin, bir iş akışı) karşı yazılan; tıkladığınızda **Gözat** ana aracı iletişim kutusunda, **türündeki iş akışı Seçici** Şekil 4'te gösterildiği gibi iletişim kutusu görüntülenir.  
  
 ![İş akışı &#47; Türü seçimi](../../../../docs/framework/windows-workflow-foundation/samples/media/71f08d57-e8f2-499e-8151-ece2cbdcabfd.gif "71f08d57-e8f2-499e-8151-ece2cbdcabfd")  
  
 Şekil 4: Türündeki iş akışı Seçici  
  
 Kullanabileceğiniz **türündeki iş akışı Seçici** iletişim bütünleştirilmiş ve bu derleme içinde belirli bir tür belirtin. Bu tür göre kuralları yazılan (çalıştırın ve) hedef türüdür. Çoğu durumda, bir iş akışı veya başka bir etkinlik türü hedef türü ise. Ancak, bir RuleSet herhangi bir .NET türü karşı çalıştırabilirsiniz.  
  
 Derleme dosyasını ve türü yoluna `name are stored with the` veritabanı kümesinde, böylece zaman RuleSet veritabanından alınır aracı çalışır hedef türü otomatik olarak yüklenecek.  
  
 Tıkladığınızda **Tamam** içinde **türündeki iş akışı Seçici** iletişim kutusunda, seçili türü hedef türü kurallar tarafından başvurulan tüm üyeleri olduğundan emin olmak için RuleSet karşı doğrular. Hataları gösterilmiştir bir **doğrulama hataları** iletişim (bkz. Şekil 5). Tıklayın veya hataları rağmen değişiklikle devam seçebilirsiniz **iptal**. Gelen **Araçları** tıklayabilirsiniz menüsünde ana aracı iletişim kutusunda, **doğrulama** hedef etkinlik karşı RuleSet sürüm yeniden doğrulamak için.  
  
 ![Doğrulama hataları dış RuleSet örnekten](../../../../docs/framework/windows-workflow-foundation/samples/media/validationerrorsruleset.png "ValidationErrorsRuleSet")  
  
 Şekil 5: Doğrulama hataları  
  
 Gelen **veri** menü aracında içeri ve dışarı aktarma RuleSets. Tıkladığınızda **alma**, bir dosya Seçici iletişim kutusu görüntülenirse, .rules dosya seçin. Bu olabilir veya bir dosya başlangıçta içinde oluşturulabilir değil [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]. .Rules dosyası seri hale getirilmiş bir içermelidir `RuleDefinitions` koşulları koleksiyonu ve RuleSets koleksiyonunu içeren örneği. Aracı koşulları koleksiyonu kullanmaz, ancak kullanmak `RuleDefinitions` etkileşime izin vermek için .rules biçimi [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] ortamı.  
  
 .Rules dosyayı seçtikten sonra bir **RuleSet Seçici** iletişim kutusu görüntülenir (Şekil 6'ya bakın). İçeri aktarmak istediğiniz dosyadan RuleSets seçmek için iletişim kutusunu kullanabilirsiniz (varsayılan tüm RuleSets belirtir). Kendi sürüm WF projedeki derlemesinin sürümü ile aynı olduğundan .rules dosyasında RuleSets sürüm numaralarını sahip değilsiniz. İçeri aktarma işlemi sırasında Aracı'nı (hangi içeri aktardıktan sonra değiştirebilirsiniz) sonraki kullanılabilir ana sürüm numarası otomatik olarak atar; atanan sürüm numaralarını görebilirsiniz **RuleSet Seçici** listesi.  
  
 Bunu aktarır her RuleSet için .rules dosyasının (varsa) konumu altında klasörüne ilişkili türünden bulmak için aracı denemeleri temel kümesinde kullanılan üyeler. Aracı birden çok eşleşen türleri bulursa, .rules dosya adı ve tür adı arasında bir eşleşme dayanan bir türü seçmek çalışır (örneğin, `Workflow1` türü için Workflow1.rules karşılık gelir). Birden çok eşleşme yoksa, türü seçmeniz istenir. Eşleşen bir derleme veya tür bulmak bu otomatik kimlik mekanizması başarısız olduysa tıklayabilirsiniz içeri aktardıktan sonra **Gözat** ilişkili türü gitmek için ana aracı iletişim.  
  
 ![RuleSet Seçici](../../../../docs/framework/windows-workflow-foundation/samples/media/rulesetselector.gif "RuleSetSelector")  
  
 Şekil 6: RuleSet Seçici  
  
 Tıkladığınızda **veri dışa aktarma** ana aracı menüsünden **RuleSet Seçici** verilmeli veritabanından RuleSets belirlemek iletişim kutusu yeniden görüntülenir. Tıkladığınızda **Tamam**, **dosyayı Kaydet** iletişim kutusu görüntülenirse, sonuçta elde edilen .rules dosyasının konumunu ve adını belirtebilirsiniz. .Rules dosya sürümü bilgilerini içermediğinden, yalnızca belirli bir RuleSet ada sahip bir RuleSet sürüm seçebilirsiniz.  
  
## <a name="policyfromservice-activity"></a>PolicyFromService etkinliği  
 Kodunu `PolicyFromService` etkinliktir kolay. Benzer çalışır `Policy` etkinlik sağlanan WF ile ancak hedef RuleSet .rules dosyasından alma yerine RuleSet örneği elde etmek için bir ana bilgisayar hizmeti çağırır. Daha sonra RuleSet karşı kök iş akışı etkinliği örneği çalıştırır.  
  
 Etkinlik bir iş akışında kullanmak için bir başvuru ekleyin `PolicyActivities` ve `RuleSetService` iş akışı projenizden derlemeler. Araç Kutusu'na etkinlik ekleme Tartışması için bu konunun sonundaki yordamına bakın.  
  
 Etkinlik akışınıza yerleştirme sonra çalıştırılacak RuleSet'in adı sağlamanız gerekir. Değişmez değer adı girin veya bir iş akışı değişken ya da başka bir etkinliğin özelliği için bağlama. İsteğe bağlı olarak, çalışması gereken belirli RuleSet için sürüm numaraları girebilirsiniz. Varsayılan değer 0 birincil ve ikincil sürüm numaraları için değiştirmeden bırakırsanız, veritabanındaki en son sürüm numarasını etkinlik için otomatik olarak sağlanır.  
  
## <a name="ruleset-service"></a>RuleSet hizmeti  
 Hizmet, belirtilen RuleSet sürümü veritabanından alma ve arama etkinlik döndürme sorumludur. Birincil ve ikincil sürüm değerleri geçirilen, daha önce açıklandığı gibi `GetRuleSet` çağrısı, her iki 0 hizmet en son sürümünü alır. Bu noktada, yoktur RuleSet tanımları veya örnekleri önbelleğe alma; benzer şekilde, RuleSet sürümleri "Sürüyor RuleSets ayırmak için dağıtılan" olarak işaretlemek için hiçbir özellik yok.  
  
 Hizmet tarafından erişilebilmesi için veritabanı ana bilgisayarında bir uygulama yapılandırma dosyası kullanarak yapılandırılması gerekir.  
  
#### <a name="to-run-the-tool"></a>Aracı çalıştırmak için  
  
1.  Aracı ve hizmeti tarafından kullanılan RuleSet tablo ayarlar klasörü Setup.sql dosyasını içerir. SQL Express kuralları veritabanı oluşturmak ve RuleSet tablosu ayarlamanız için Setup.cmd toplu iş dosyasını çalıştırabilirsiniz.  
  
2.  Toplu iş dosyasını veya Setup.sql düzenleyin ve SQL Express kullanmamak veya tablo dışında bir veritabanında yerleştirmek üzere belirtirseniz `Rules`, RuleSet aracında uygulama yapılandırma dosyaları ve `UsageSample` projeleri düzenlenmesi gerekir ile aynı bilgi.  
  
3.  Setup.sql betiği çalıştırdıktan sonra oluşturabilirsiniz `ExternalRuleSetToolkit` çözüm ve ardından başlatma RuleSet aracı ExternalRuleSetTool projeden.  
  
4.  `RuleSetToolkitUsageSample` Sıralı iş akışı konsol uygulaması çözümü örnek iş akışı içerir. İş akışı oluşan bir `PolicyFromService` etkinliği ve iki değişken `orderValue` ve `discount`, hedef RuleSet çalıştığı karşı.  
  
5.  Örnek kullanmak için derleme `RuleSetToolkitUsageSample` çözümü. RuleSet aracı ana menüden, ardından **veri alma** ve RuleSetToolkitUsageSample klasöründeki DiscountRuleSet.rules dosyasını in üzerine gelin. Tıklatın **kural depolama tasarrufu** alınan RuleSet veritabanına kaydetmek için menü seçeneği.  
  
6.  Çünkü `PolicyActivities` derlemesi örnek iş akışı projeden başvurulan `PolicyFromService` etkinlik iş akışı içinde görüntülenir. Bu ancak, araç kutusunda varsayılan olarak görünmez. Araç kutusuna eklemek için aşağıdakileri yapın:  
  
    -   Araç kutusunu sağ tıklatın ve seçin **öğeleri Seç** (Bu işlem biraz zaman alabilir).  
  
    -   Zaman **araç kutusu öğelerini Seç** iletişim görüntülendikten sonra **etkinlikleri** sekmesi.  
  
    -   Gözat `PolicyActivities` derlemede `ExternalRuleSetToolkit` çözümü ve tıklatın **açık**.  
  
    -   Emin `PolicyFromService` etkinlik seçildiğinde, **araç kutusu öğelerini Seç** iletişim ve ardından **Tamam**.  
  
    -   Etkinlik araç kutusunda görüntülenmelidir şimdi **RuleSetToolkitUsageSample bileşenleri** kategorisi.  
  
7.  RuleSet hizmet Program.cs içinde şu deyimi kullanarak konsol uygulama konağı üzerinde zaten yapılandırılmış.  
  
    ```  
    workflowRuntime.AddService(new RuleSetService());  
    ```  
  
8.  Hizmet ana bilgisayarında bir yapılandırma dosyası kullanarak da yapılandırabilirsiniz; Ayrıntılar için SDK belgelerine bakın.  
  
9. Uygulama yapılandırma dosyası hizmeti tarafından kullanılan veritabanı için bağlantı dizesini belirtmek için iş akışı projesinde eklenir. Bu RuleSet tablo içeren bir veritabanına işaret eden RuleSet aracı tarafından kullanılan aynı bağlantı dizesi olması gerekir.  
  
10. Şimdi Çalıştır `RuleSetToolkitUsageSample` proje başka bir iş akışı konsol uygulaması gibi. F5 veya Ctrl + F5 içinde basın [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] veya RuleSetToolkitUsageSample.exe dosyasını doğrudan çalıştırın.  
  
    > [!NOTE]
    >  Aracın kullanımı örnek derleme yüklediğinden RuleSet aracı kullanım örnek derlenir kapatmanız gerekir.