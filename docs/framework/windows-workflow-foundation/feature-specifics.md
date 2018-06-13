---
title: Windows Workflow Foundation özelliğini özellikleri
ms.date: 03/30/2017
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
ms.openlocfilehash: 0f9bc81609379414ce022499e20791073d259cdc
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809868"
---
# <a name="windows-workflow-foundation-feature-specifics"></a>Windows Workflow Foundation özelliğini özellikleri
[!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] bir dizi özellik Windows Workflow Foundation ekler. Bu belge yeni özelliklerini açıklar ve içinde bunlar yararlı olabilecek senaryoları hakkında ayrıntılar sağlar.  
  
## <a name="messaging-activities"></a>Mesajlaşma Etkinlikleri  
 Mesajlaşma etkinlikleri (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.ReceiveReply>) iş akışından WCF ileti alıp göndermek için kullanılır.  <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikleri, yalnızca standart WCF web Hizmetleri gibi WSDL kullanıma sunulan bir Windows Communication Foundation (WCF) hizmet işlemi oluşturmak için kullanılır.  <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> WCF için benzer bir web hizmeti kullanmak için kullanılan <xref:System.ServiceModel.ChannelFactory>; bir **hizmet Başvurusu Ekle** deneyimi mevcut da Workflow Foundation için önceden yapılandırılmış etkinliklerini oluşturur.  
  
### <a name="getting-started-with-messaging-activities"></a>Mesajlaşma etkinlikleri ile çalışmaya başlama  
  
-   İçinde [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], bir WCF iş akışı hizmeti uygulaması projesi oluşturun. A <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> çifti, tuvalde yerleştirilir.  
  
-   Sağ tıklatın ve proje **hizmet Başvurusu Ekle**.  Bir web hizmetiniz için WSDL'ın üzerine gelin ve tıklatın **Tamam**.  Oluşturulan etkinlikleri göstermek için projenizi derleme (kullanılarak uygulanan <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply>), araç çubuğundaki.  
  
-   Aşağıdaki bölümlerde bu etkinlikler için örnek bulunabilir:  
  
    -   Basic: [Hizmetleri](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Senaryolar: [Hizmetleri](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
-   [Kavramsal belgeler](http://go.microsoft.com/fwlink/?LinkId=204801)  
  
-   [Mesajlaşma etkinlikleri Tasarımcı belgeleri](http://go.microsoft.com/fwlink/?LinkId=204802)  
  
### <a name="messaging-activities-example-scenario"></a>Mesajlaşma etkinlikleri Örnek senaryo  
 A `BestPriceFinder` belirli bir rota için en iyi bilet fiyat bulmak için birden çok uçak hizmetlerine hizmetini çağırır.  Bu senaryoyu uygulamaya fiyat durdurmanız, Fiyatlar arka uç hizmetlerinden almak ve en iyi fiyat fiyat istekle yanıtlamak için ileti etkinlikleri kullanmanızı gerektirir.  Bu ayrıca diğer out-of-box etkinlikler en iyi fiyat hesaplanırken için iş mantığını oluşturmaya kullanmanızı gerektirir.  
  
## <a name="workflowservicehost"></a>WorkflowServiceHost  
 <xref:System.ServiceModel.WorkflowServiceHost> (İş akışları barındırılması için Mesajlaşma kullanmak için gerekli olmasa da) destekleyen birden çok örneği, yapılandırma ve WCF ileti out-of-box iş akışı ana bilgisayardır.  Ayrıca Kalıcılık, izleme ve bir dizi hizmet davranışları örneği denetimi ile tümleştirilir.  WCF'ın ' olduğu gibi <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.WorkflowServiceHost> bir WinForms/konsol/WPF uygulaması veya Windows hizmeti otomatik olarak barındırılan veya (.xamlx dosyası olarak) web barındırılan IIS veya WAS.  
  
### <a name="getting-started-with-workflow-service-host"></a>İş akışı hizmeti ana bilgisayarı ile çalışmaya başlama  
  
-   Visual Studio 2010'da bir WCF iş akışı hizmeti uygulaması projesi oluşturma: kullanmak için bu proje ayarlanacaktır <xref:System.ServiceModel.WorkflowServiceHost> bir web barındırma ortamında.  
  
-   İleti sistemi olmayan bir iş akışı barındırmak için özel bir ekleme <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> iletisini temel alarak örneği oluşturur.  
  
-   İş akışı örnekleri denetlenebilir (örneğin askıya alındı veya sonlandırıldı) ekleyerek bir <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> için <xref:System.ServiceModel.WorkflowServiceHost> ve ardından kullanarak bir <xref:System.ServiceModel.Activities.WorkflowControlClient>.  
  
-   İçin örnekleri <xref:System.ServiceModel.WorkflowServiceHost> aşağıdaki bölümlerde bulunabilir:  
  
    -   [Yürütme](../../../docs/framework/windows-workflow-foundation/samples/execution.md)  
  
    -   Basic: [Hizmetleri](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Senaryolar: [Hizmetleri](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Uygulama: [askıya örnek Yönetimi](../../../docs/framework/windows-workflow-foundation/samples/suspended-instance-management.md)  
  
-   [WorkflowServiceHost kavramsal belgeler](http://go.microsoft.com/fwlink/?LinkId=204807)  
  
### <a name="workflowservicehost-scenario"></a>WorkflowServiceHost senaryosu  
 Belirli bir rota için en iyi bilet fiyat bulmak için birden çok uçak hizmetlerine BestPriceFinder hizmet çağırır.  Bu senaryoyu uygulamaya duyar, iş akışında barındırmak <xref:System.ServiceModel.WorkflowServiceHost>.  Bu ayrıca, ileti etkinlikleri fiyat durdurmanız, Fiyatlar arka uç hizmetlerinden almak ve en iyi fiyat fiyat istekle yanıtlamak için kullanırsınız.  
  
## <a name="correlation"></a>Bağıntı  
 Bir bağıntı ikisinden biri:  
  
-   Bir yol birlikte gruplandırma iletilerinin; diğer bir deyişle, bir istek iletisi ve kendi yanıt arasındaki ilişki.  
  
-   Bir hizmet örneği için bir veri eşleme yöntemi  
  
### <a name="getting-started"></a>Başlarken  
  
-   Bağıntı ile çalışmaya başlamak için Visual Studio'da yeni bir proje oluşturun. Türünde bir değişken oluşturmak <xref:System.ServiceModel.Activities.CorrelationHandle>.  
  
-   Grup iletiler birlikte kullanılan bağıntı iletileri gruplandıran bir istek-yanıt bağıntısı örnektir.  
  
    -   Üzerinde bir <xref:System.ServiceModel.Activities.Receive> etkinliği tıklatın <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> özelliği ve ekleme bir <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> CorrelationHandle kullanarak Yukarıdaki ilk adımda oluşturduğunuz.  
  
    -   Create bir <xref:System.ServiceModel.Activities.SendReply> sağ tıklayarak etkinliği <xref:System.ServiceModel.Activities.Receive> "SendReply oluşturma" ye tıklayın. Sonra iş akışınızı yapıştırın <xref:System.ServiceModel.Activities.Receive> etkinlik.  
  
-   Bir hizmet örneği için bir veri eşleme belirli iş akışı örneği için bir veri (örneğin, bir siparişi kimliği) parçasını eşleştiren içerik tabanlı bağıntı örneğidir.  
  
    -   Herhangi bir ileti etkinliği üzerinde tıklayın `CorrelationInitializers` özelliği ve ekleme bir <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> kullanarak <xref:System.ServiceModel.Activities.CorrelationHandle> yukarıda oluşturduğunuz değişkeni. Aşağı açılır menüden (örneğin OrderID) ileti üzerinde istenen özelliği çift tıklayın. Ayarlama `CorrelatesWith` özelliğine <xref:System.ServiceModel.Activities.CorrelationHandle> yukarıda kullanılan değişkeni.  
  
-   Örnekler:  
  
    -   Basic: [Hizmetleri](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Senaryolar: [Hizmetleri](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   [Bağıntı kavramsal belgeler](http://go.microsoft.com/fwlink/?LinkId=204939)  
  
### <a name="correlation-scenario"></a>Bağıntı senaryosu  
 Bir sipariş işleme iş akışı, yeni sıra oluşturma ve işlemde varolan siparişleri güncelleştirme işlemek için kullanılır.  Bu senaryoyu uygulamaya duyar, iş akışında barındırmak <xref:System.ServiceModel.WorkflowServiceHost> ve mesajlaşma etkinlikleri kullanın.  Dayalı bağıntı gerektirecek `orderId` güncelleştirmeleri doğru iş akışına yapılır emin olmak için.  
  
## <a name="simplified-configuration"></a>Basitleştirilmiş Yapılandırma  
 WCF yapılandırma şeması karmaşıktır ve kullanıcıların çoğu ile özellikleri bulmak için sabit sağlar. İçinde [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], biz WCF kullanıcıların aşağıdaki özelliklerle hizmetlerini yapılandırmasına yardımcı odaklanmıştır:  
  
-   Açık hizmet başına yapılandırması kaldırılıyor. Herhangi bir yapılandırmazsanız \<hizmet > hizmetinizi ve hizmetiniz için öğeleri program aracılığıyla herhangi bir uç nokta tanımlayan değil, ardından uç noktalar kümesi otomatik olarak hizmetiniz bir sözleşme ve hizmeti temel adresi başına eklenir hizmetiniz tarafından uygulanır.  
  
-   WCF bağlamaları ve herhangi bir açık yapılandırma ile Hizmetleri uygulanacak davranışları için varsayılan değerleri tanımlamak kullanıcının sağlar.  
  
-   Standart uç noktaları, sabit bir veya daha fazla uç noktası özellikleri (adresi, bağlama ve Sözleşme) için değerleri ve özel özellikleri tanımlamaya izin yeniden kullanılabilir önceden yapılandırılmış uç tanımlayın.  
  
-   Son olarak, <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> WCF istemci yapılandırması, yapılandırma seçtikten veya uygulama etki alanı yükleme zamanını sonra değiştirilen senaryolarda yararlı Merkezi Yönetimi yapmanıza izin verir.  
  
### <a name="getting-started"></a>Başlarken  
  
-   [WCF 4.0 için bir Geliştirici Kılavuzu](http://go.microsoft.com/fwlink/?LinkId=204940)  
  
-   [Yapılandırma Kanal Fabrikası](http://go.microsoft.com/fwlink/?LinkId=204941)  
  
-   [Standart uç nokta öğesi](http://go.microsoft.com/fwlink/?LinkId=204942)  
  
-   [Hizmet yapılandırma yenilikleri .net Framework 4](http://go.microsoft.com/fwlink/?LinkId=204943)  
  
-   [.NET 4'te yaygın kullanıcı hata: WF/WCF hizmet yapılandırması adının yanlış yazmanız](http://go.microsoft.com/fwlink/?LinkId=204944)  
  
### <a name="simplified-configuration-scenarios"></a>Basitleştirilmiş yapılandırma senaryoları  
  
-   WCF'ı kullanmaya başlamak bir deneyimli ASMX Geliştirici istemektedir. Ancak, WCF çok karmaşık görünüyor! Bir yapılandırma dosyasında yazma gerekir bu bilgileri nedir? .NET 4'te bir yapılandırma dosyası hiç olmayacak şekilde bile karar verebilirsiniz.  
  
-   WCF hizmetlerini var olan bir dizi yapılandırmak ve korumak oldukça zor. Yapılandırma dosyası touch son derece tehlikeli XML kodunu satırlık binlerce vardır. Yardım daha kolay yönetilebilir bir şey için bu kodu miktarını azaltmak için gereklidir.  
  
## <a name="data-contract-resolver"></a>Veri sözleşmesi Çözücü  
 .NET 3. 5'da, bazı sınırlamaları bilinen türleri tasarımında vardı:  
  
-   Bilinen türler dinamik olarak ekleme, seri hale getirme veya seri durumdan çıkarma, sırasında mümkün değildi.  
  
-   Serileştiricileri bilinmeyen xsi: type bilgilerle ilgilenir değil.  
  
-   Kullanıcıların sahip görünmesi Kablo örneği için seri hale getirme örneği boyutu kablo küçültmek için istediğiniz hangi xsi: type belirtmek mümkün değildi.  
  
 [DataContractResolver](../../../docs/framework/wcf/samples/datacontractresolver.md) .NET 4.5, bu sorunları çözer.  
  
### <a name="getting-started"></a>Başlarken  
  
-   [Veri sözleşmesi Çözücü API belgeleri](http://go.microsoft.com/fwlink/?LinkId=204946)  
  
-   [Veri sözleşmesi Çözücü Tanıtımı](http://go.microsoft.com/fwlink/?LinkId=204947)  
  
-   Örnekler:  
  
    -   [DataContractResolver](../../../docs/framework/wcf/samples/datacontractresolver.md)  
  
    -   [KnownAssemblyAttribute](../../../docs/framework/wcf/samples/knownassemblyattribute.md)  
  
### <a name="data-contract-resolver-scenarios"></a>Veri sözleşmesi Çözücü senaryoları  
  
-   Onlarca bildirme gerek kalmadan önleme <xref:System.Runtime.Serialization.KnownTypeAttribute> hizmet nesneleri.  
  
-   XML Kabarcık boyutunu azaltma.  
  
## <a name="flowchart"></a>Akış Çizelgesi  
 Akış Çizelgesi, etki alanı sorunlarını görsel olarak sunmak üzere iyi bilinen bir örnektir. .NET 4'te Tanıtımı yeni bir denetim akışı stilini değil. Akış Çizelgesi özellik çekirdek herhangi bir anda yalnızca bir etkinlik yürütüldüğünden emin olur. Akış çizelgeleri döngüler ve alternatif sonuçları express, ancak yerel olarak birden çok düğümün eşzamanlı yürütülmesi express olamaz.  
  
### <a name="getting-started"></a>Başlarken  
  
-   İçinde [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], bir iş akışı konsol uygulaması oluşturun. Bir akış iş akışı Tasarımcısı'nda ekleyin.  
  
-   Akış özelliği aşağıdaki sınıflar kullanır:  
  
    -   <xref:System.Activities.Statements.Flowchart>  
  
    -   <xref:System.Activities.Statements.FlowNode>  
  
    -   <xref:System.Activities.Statements.FlowDecision>  
  
    -   <xref:System.Activities.Statements.FlowStep>  
  
    -   <xref:System.Activities.Statements.FlowSwitch%601>  
  
-   Örnekler:  
  
    -   [TryCatch Kullanarak Akış Çizelgesi Etkinliğine Hata İşleme](../../../docs/framework/windows-workflow-foundation/samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)  
  
    -   [FlowChart ve Pick Birleşimini Kullanan StateMachine Senaryosu](../../../docs/framework/windows-workflow-foundation/samples/statemachine-scenario-using-a-combination-of-flowchart-and-pick.md)  
  
    -   [İşe Alma İşlemi](../../../docs/framework/windows-workflow-foundation/samples/hiring-process.md)  
  
-   Tasarımcı belgeleri:  
  
    -   [Akış Çizelgesi Etkinlik Tasarımcıları](/visualstudio/workflow-designer/flowchart-activity-designers)  
  
### <a name="flowchart-scenarios"></a>Akış Çizelgesi senaryoları  
 Bir akış etkinliği tahmin eden oyun uygulamak için kullanılabilir. Tahmin eden oyun çok basittir: rastgele bir sayı bilgisayarı seçer ve bu sayıyı tahmin etmeye player sahiptir. Player her tahmin gönderdiğinde, bilgisayarın ona (yani "daha düşük bir sayı deneyin") ipucu gösterir. Player değerinden 7 girişimlerinde numarasını bulursa, kendisinin bilgisayardan özel congratulation alır. Aşağıdaki yordam etkinliklerin birlikte bu oyun uygulanabilir:  
  
-   <xref:System.Activities.Statements.Sequence>  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.TryCatch>  
  
-   <xref:System.Activities.Statements.Assign%601>  
  
-   <xref:System.Activities.Statements.If>  
  
## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a>Yordam etkinlikleri (sırası, IF, ForEach, anahtar, ata, DoWhile, sırada)  
 Yordam etkinlikleri programcıları kavramları kullanarak modeli Sıralı denetim akışı için bir mekanizma sağlar. Bu etkinlikler geleneksel yapısal programlama dil yapıları etkinleştirin ve uygun olduğunda dil eşlik gibi C# genel yordam dilleri sağlamak / vb  
  
### <a name="getting-started"></a>Başlarken  
  
-   İçinde [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], bir iş akışı konsol uygulaması oluşturun. Yordam etkinlikler iş akışı Tasarımcısı'nda ekleyin.  
  
-   Örnekler:  
  
    -   [İşe Alma İşlemi](../../../docs/framework/windows-workflow-foundation/samples/hiring-process.md)  
  
    -   [Şirket Satın Alma İşlemi](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md)  
  
-   Tasarımcı belgeleri:  
  
    -   [Parallel Etkinlik Tasarımcısı](/visualstudio/workflow-designer/parallel-activity-designer)  
  
    -   [ParallelForEach\<T > etkinlik Tasarımcısı](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)  
  
### <a name="procedural-activity-scenarios"></a>Yordam etkinliği senaryoları  
  
-   <xref:System.Activities.Statements.Parallel>: Bir intranet belge yönetim sistemi bir belge onayı iş akışı vardır. Belgeler intranet yayımlanabilmesi çeşitli Departmanlar kişiler tarafından onaylanması gerekir. Onayları için kurulmuş bir sıra değil; Belgenin "onay bekliyor" aşamasında olsa da herhangi bir zamanda ortaya çıkabilir. Bir kullanıcı bir belgeyi gözden geçirilmek gönderdiğinde doğrudan yöneticisinin, intranet Yöneticisi ve iç iletişim Yöneticisi tarafından onaylanması gerekir.  
  
-   <xref:System.Activities.Statements.ParallelForEach%601>: Bir WF uygulamanın Kurumsal satın büyük bir şirket içinde yönetir. Herhangi bir satın alma işlemi planlama önce üç farklı satıcılar valuations olduğunu gerekli Kurumsal kuralları dikte. Satın alma departmanından bir çalışan üç satıcılar şirketin satıcı listeden seçer. Bu satıcılardan seçili ve bildirim sonra şirket için ekonomik kendi tekliflerini bekleyin. Teklifler herhangi bir sırada gelebilir. Bu senaryo WF uygulamak için kullanırız bir <xref:System.Activities.Statements.ParallelForEach%601> , satıcıların bizim koleksiyonda yinelemek ve bunların ekonomik önerileri isteyin. Tüm teklifleri toplanan sonra en iyisi seçili ve görüntülenir.  
  
## <a name="invokemethod"></a>InvokeMethod  
 <xref:System.Activities.Statements.InvokeMethod> Etkinlik sağlayan genel yöntemler nesnelerde veya kapsam türleri çağırma. Bu örneği ve statik yöntemleri ile veya olmadan (parametre dizileri dahil) ve genel yöntemler çağırma destekler. Ayrıca, zaman uyumlu ve zaman uyumsuz olarak çalıştırma yöntemi sağlar.  
  
### <a name="getting-started"></a>Başlarken  
  
-   İçinde [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], bir iş akışı konsol uygulaması oluşturun. Ekleme bir <xref:System.Activities.Statements.InvokeMethod> etkinliği iş akışı Tasarımcısı'nda statik yapılandırmak ve örnek üzerindeki yöntemleri.  
  
-   Örnekler:  
  
    -   [InvokeMethod](../../../docs/framework/windows-workflow-foundation/samples/invokemethod.md)  
  
-   Tasarımcı belgelerine: [InvokeMethod etkinlik Tasarımcısı](/visualstudio/workflow-designer/invokemethod-activity-designer)  
  
### <a name="invokemethod-scenarios"></a>InvokeMethod senaryoları  
  
-   Kapsamındaki bir nesne bir yöntemin çağrılması gerekir. Örneğin, bir değer için Sözlük eklenmesi gerekir. Sözlük örneğinin ekleme yöntemi çağrılır ve anahtar ve değer sağlanır.  
  
-   Eski bir CLR nesnesi üzerinde çağrılacak bir yöntem gerekir. İş akışı yürütme sırasında kapsamları dahilinde olması durumunda bu eski sınıfı çağrısı sarmalamak için özel bir etkinlik oluşturmak yerine <xref:System.Activities.Statements.InvokeMethod> kullanılabilir.  
  
## <a name="error-handling-activities"></a>Hata işleme etkinlikleri  
 <xref:System.Activities.Statements.TryCatch> Etkinlik içerilen etkinlikleri (C# /VB Try/Catch yapı benzer) kümesi yürütülmesi sırasında oluşan özel durumları yakalama için bir mekanizma sağlar. <xref:System.Activities.Statements.TryCatch> özel durum işleme iş akışı düzeyinde sağlar. İşlenmeyen bir özel durum, iş akışı iptal edilir ve son blok yürütülen olmaz. Bu davranış, C# ile tutarlıdır.  
  
### <a name="getting-started"></a>Başlarken  
  
-   İçinde [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], bir iş akışı konsol uygulaması oluşturun. Ekleme bir <xref:System.Activities.Statements.TryCatch> etkinliği iş akışı Tasarımcısı'nda.  
  
-   Örnekler:  
  
    1.  [TryCatch Kullanarak Akış Çizelgesi Etkinliğine Hata İşleme](../../../docs/framework/windows-workflow-foundation/samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)  
  
    2.  [Yordam Etkinlikleri Kullanma](../../../docs/framework/windows-workflow-foundation/samples/using-procedural-activities.md)  
  
-   Tasarımcı belgelerine: [hata işleme etkinlik tasarımcıları](/visualstudio/workflow-designer/error-handling-activity-designers)  
  
### <a name="error-handling-scenarios"></a>Hata işleme senaryoları  
 Etkinlikleri kümesi yürütülmesi gerekiyor ve belirli mantığı hata oluştuğunda yürütülmesi gerekiyor. Bu hata mantığı işleme sırasında hata kurtarılamaz bulunursa, özel durum işlenemezse ve üst etkinlik (veya konak) sorun ilgilenecektir.  
  
## <a name="pick-activity"></a>Etkinlik seçin  
 <xref:System.Activities.Statements.Pick> İçinde WF modelleme olay tabanlı denetim akışı etkinliği sağlar. <xref:System.Activities.Statements.Pick> Burada her dal çalıştırmadan önce gerçekleşmesi belirli bir olay bekler birçok dal içerir. Bu kurulum içinde bir <xref:System.Activities.Statements.Pick> benzer şekilde davranır bir <xref:System.Activities.Statements.Switch%601> için hangi etkinlik dinleme olay kümesini yalnızca birini çalıştırır. Her dal güdümlü olayıdır ve ortaya çıkan olayın karşılık gelen şube ilk çalıştırır. Diğer tüm dalları iptal etmek ve olayları dinleme durdurun.  
  
### <a name="getting-started"></a>Başlarken  
  
-   İçinde [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], bir iş akışı konsol uygulaması oluşturun. Ekleme bir <xref:System.Activities.Statements.Pick> etkinliği iş akışı Tasarımcısı'nda.  
  
-   Örnek: [çekme etkinliğini kullanma](../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md)  
  
-   Tasarımcı belgelerine: [çekme etkinlik Tasarımcısı](/visualstudio/workflow-designer/pick-activity-designer)  
  
### <a name="pick-scenario"></a>Senaryo seçin  
 Bir kullanıcı için giriş sorulması gerekiyor. Normal koşullar altında Geliştirici gibi bir yöntem çağrısı kullanmak istediğiniz <xref:System.Console.ReadLine%2A> bir kullanıcı giriş için istemek için. Bu kurulum ile kullanıcı bir şey girene kadar program bekler sorunudur. Bu senaryoda, bir zaman aşımı engelleme etkinliğini engellemesini kaldırmak için gereklidir. Yaygın bir senaryo belirli bir süre içinde tamamlanması için bir görev gerektirir biridir. Engelleme etkinliğini aşımından Burada çekme değeri çok ekler bir senaryodur.  
  
## <a name="wcf-routing-service"></a>WCF yönlendirme hizmeti  
 Yönlendirme hizmeti, bir genel yazılım WCFmessages istemciler ve hizmetler arasında nasıl gerçekleştiğini denetlemek izin veren yönlendirici olacak şekilde tasarlanmıştır.  Yönlendirme hizmeti, hizmetlerinizi, istemcilerden ayırırsınız yapılandırmaları açısından çok özgürlüğü sağlar, destekleyebilir ve hizmetlerinizi barındırmak nasıl değerlendirirken sahip esnekliği sağlar.  .NET 3. 5'da, istemciler ve hizmetler sıkı şekilde bağlı; bir istemci tüm konuşun için gereken ve nerede bulunduğu hizmetleri hakkında bilmeniz gerekiyordu. Ayrıca, .net WCF Framework 3.5 vardı aşağıdaki sınırlamalar:  
  
-   Bu mantık istemciyi sabit kodlanmış olması gerekiyordu gibi hata işleme karmaşıktı.  
  
-   İstemcileri ve Hizmetleri her zaman aynı bağlamaları kullanmanız gerekiyordu.  
  
-   Hizmetleri nadiren iyi oluşturmak: her şeyi uygulayan bir hizmet konuşun istemcinin daha kolay denetlediğinden birden çok hizmetleri arasında seçim yapma.  
  
 .Net 4'te yönlendirme hizmeti, bu sorunları çözmek kolaylaştırmak için tasarlanmıştır. Yeni yönlendirme hizmeti aşağıdaki özelliklere sahiptir:  
  
1.  İçerik tabanlı yönlendirme (<xref:System.ServiceModel.Dispatcher.MessageFilter> nesneleri burada gönderilmelidir belirlemek için bir ileti inceleyin.)  
  
2.  Protokol (aktarım & ileti) köprü oluşturma  
  
3.  (Yönlendirici iletişimi özel durumları yakalar ve yedekleme Uç noktalara yöneltilir) hata işleme  
  
4.  (Bellekte) dinamik olarak güncelleştirilmesini <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> ve yönlendirme yapılandırması.  
  
### <a name="getting-started"></a>Başlarken  
  
1.  Belgeler: [yönlendirme](../../../docs/framework/wcf/feature-details/routing.md)  
  
2.  Örnekler: [yönlendirme hizmetleri &#91;WCF örnekleri&#93;](../../../docs/framework/wcf/samples/routing-services.md)  
  
3.  Blog: [yönlendirme kuralları!](http://go.microsoft.com/fwlink/?LinkId=204956)  
  
### <a name="routing-scenarios"></a>Yönlendirme Senaryoları  
 Yönlendirme hizmeti, aşağıdaki senaryolarda kullanışlıdır:  
  
-   İstemciler, tüm doğrudan adres gerek kalmadan birden fazla hizmet için iletişim kurabilirsiniz.  
  
-   İstemcileri ek mantık yönlendirmek nereye belirlemek için bir istemci isteği gerçekleştirebilirsiniz  
  
-   İstemci yeniden düzenleme olmadan bir istemci birden çok hizmet uygulamaları gerçekleştirir işlemleri parçalayın.  
  
-   İstemciler ve hizmetler farklı güvenlik ayarları farklı bağlamalarla konuşarak iletebilirsiniz.  
  
-   İstemci hatası veya hizmetleri kullanılamama karşı daha sağlam olması için etkinleştirilebilir.  
  
## <a name="wcf-discovery"></a>WCF Keşfetme  
 WCF bulma, bulma mekanizmasından uygulama altyapınıza eklemenizi sağlayan bir framework teknolojisidir. Hizmetinizi bulunabilmesini sağlamak için bunu kullanın ve Hizmetleri aramak için istemcileri yapılandırın. İstemciler artık sabit olması bitiş noktası ile kodlanmış, uygulama daha sağlam ve hataya dayanıklı hale gerekir. Bulma, uygulamanıza otomatik yapılandırma özellikleri oluşturmak için mükemmel bir platformdur.  
  
 Ürün üstünde WS-bulma standart yerleşik olarak bulunur. Birlikte çalışabilir, genişletilebilir ve genel olarak tasarlanmıştır. Ürün iki çalışma modunu destekler:  
  
1.  Yönetilen: söz konusu olduğunda bir varlık ağda varolan hizmetleri hakkında bilgi sahibi, istemciler, doğrudan bilgiler için Sorgulayabileceğiniz. Bu, Active Directory ile benzerdir.  
  
2.  Geçici: çok noktaya yayın iletileri istemcileri Hizmetleri bulmak için burada kullanın.  
  
 Ayrıca, bulma iletileri ağ protokolü bağımsızdır; bunları üstte modu gereksinimlerini destekleyen herhangi bir protokolünü kullanabilirsiniz. Örneğin, bulma çok noktaya yayın iletileri UDP kanal veya çok noktaya yayın iletileri destekleyen herhangi bir ağ gönderilebilir.  Bu özellik esnekliği çözümünüze özellikle bulma uyarlamak izin birleştirilmiş noktaları tasarlayın.  
  
### <a name="getting-started"></a>Başlarken  
  
-   Belgeler: [WCF bulma](../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
  
-   Örnekler: [keşif (örnekler)](../../../docs/framework/wcf/samples/discovery-samples.md)  
  
### <a name="discovery-scenarios"></a>Bulma senaryoları  
 My hizmetinin kullanılabilir olacağı zaman bilinmediğinden, geliştirici sabit kod Uç noktalara istememektedir. Bunun yerine, geliştirici çalışma zamanında bir hizmet seçin istiyor. Uygulama bileşenleri arasında daha fazla ayırma, sağlamlık ve otomatik yapılandırma gereklidir.  
  
## <a name="tracking"></a>İzleme  
 İzleme iş akışını bir iş akışı örneğini yürütmeyi bir anlayış sağlar.  İzleme olayları bir iş akışını iş akışı örneği düzeyinde ve iş akışındaki etkinliklerin yürüttüğünüzde gösterilen. Bir iş akışı izleme katılımcı kayıtları izleme için abone olmak için iş akışı ana bilgisayara eklenmesi gerekir. İzleme kayıtları izleme profili kullanılarak filtrelenir. .Net Framework (Windows için olay izleme) ETW İzleme katılımcı sağlar ve temel bir profil machine.config dosyasındaki yüklenir.  
  
### <a name="getting-started"></a>Başlarken  
  
1.  İçinde [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], bir WCF iş akışı hizmeti uygulaması projesi oluşturun. A <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> çifti başlatmak için tuval üzerinde yerleştirilir.  
  
2.  Web.config dosyasını açın ve profil davranışa izleme ETW ekleyin.  
  
    1.  Varsayılan profili kullanılır.  
  
    2.  Olay Görüntüleyicisi'ni açın ve aşağıdaki düğüm analitik kanalda etkinleştirin: **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows** , **Uygulama uygulamalarının**. Sağ **analitik** seçip **günlüğü etkinleştir**.  
  
    3.  İş akışı hizmeti çalıştırın.  
  
    4.  İş akışı Olay Görüntüleyicisi'nde izleme olayları gözlemektir.  
  
3.  Örnekler: [izleme](../../../docs/framework/windows-workflow-foundation/samples/tracking.md)  
  
4.  Kavramsal belgeler: [izleme ve izleme iş akışı](../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
  
## <a name="sql-workflow-instance-store"></a>SQL iş akışı örneği deposu  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Bir SQL Server tabanlı bir örnek deposuna uygulamasıdır. Bir örnek deposuna yükleyin ve o örneği sürdürmek gereken tüm verileri ile birlikte çalışan bir örneği durumunu saklar. Hizmet ana bilgisayarı, örneğin durumu iş akışını devam ederse ve bu örneği için bir ileti geldiğinde veya bir gecikme etkinlik süresi dolduğunda örnek durum yüklemek için örnek deposuna bildirir kaydetmek için örnek deposuna bildirir.  
  
### <a name="getting-started"></a>Başlarken  
  
1.  İçinde [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], örtük veya açık içeren bir iş akışı oluşturmak <xref:System.Activities.Statements.Persist> etkinlik. Ekleme <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> , iş akışı hizmeti ana bilgisayarı için davranış. Bu, kod veya uygulama yapılandırma dosyasında yapılabilir.  
  
2.  Örnekler: [kalıcılığı](../../../docs/framework/windows-workflow-foundation/samples/persistence.md)  
  
3.  Kavramsal belgeler: [SQL iş akışı örneği deposuna](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).
