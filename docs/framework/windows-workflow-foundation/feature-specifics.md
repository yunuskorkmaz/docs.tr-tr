---
title: Windows Workflow Foundation özellik ayrıntıları
ms.date: 03/30/2017
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
ms.openlocfilehash: b18c6dd76762f4495ac475cd3dfa4e1995733b59
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44140885"
---
# <a name="windows-workflow-foundation-feature-specifics"></a>Windows Workflow Foundation özellik ayrıntıları
[!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] Windows Workflow Foundation için bir dizi özellik ekler. Bu belge, bir dizi yeni özellik açıklar ve bunlar yararlı olabilecek senaryoları hakkında ayrıntılar sağlar.  
  
## <a name="messaging-activities"></a>Mesajlaşma Etkinlikleri  
 Mesajlaşma etkinlikleri (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.ReceiveReply>) akışınızdan WCF iletileri almak ve göndermek için kullanılır.  <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikleri, yalnızca standart WCF web Hizmetleri gibi WSDL kullanıma sunulan bir Windows Communication Foundation (WCF) hizmet işlemi oluşturmak için kullanılır.  <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> bir WCF için benzer bir web hizmetini kullanma için kullanılan <xref:System.ServiceModel.ChannelFactory>; bir **hizmet Başvurusu Ekle** deneyimi de mevcut Workflow Foundation için önceden yapılandırılmış etkinlikleri oluşturur.  
  
### <a name="getting-started-with-messaging-activities"></a>Mesajlaşma etkinlikleri ile çalışmaya başlama  
  
-   İçinde [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], bir WCF iş akışı hizmeti uygulaması projesi oluşturun. A <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> çifti tuvalinizde yerleştirilir.  
  
-   Sağ tıklatın ve proje **hizmet Başvurusu Ekle**.  Bir web hizmetiniz için WSDL'ın üzerine gelin ve tıklayın **Tamam**.  Oluşturulan etkinlikleri göstermek için projenizi derleyin (kullanılarak uygulanan <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply>), araç çubuğundaki.  
  
-   Aşağıdaki bölümlerde bu etkinlikler için örnekleri bulunabilir:  
  
    -   Temel: [Hizmetleri](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Senaryo: [Hizmetleri](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
-   [Kavramsal belgeler](https://go.microsoft.com/fwlink/?LinkId=204801)  
  
-   [Mesajlaşma etkinlikleri Tasarımcı belgeleri](https://go.microsoft.com/fwlink/?LinkId=204802)  
  
### <a name="messaging-activities-example-scenario"></a>Mesajlaşma etkinlikleri Örnek senaryo  
 A `BestPriceFinder` belirli bir rota için en iyi bilet fiyatı bulmak için birden çok Havayolu hizmetlerine hizmetini çağırır.  Bu senaryoyu uygulamaya fiyat durdurmanız, Fiyatlar arka uç hizmetlerinden almak ve en iyi fiyatı Fiyat isteği yanıtlamak için ileti etkinlikleri kullanmanızı gerektirir.  Bu ayrıca en iyi fiyatı hesaplama iş mantığı oluşturmak için diğer kullanıma hazır etkinlikleri kullanmanızı gerektirir.  
  
## <a name="workflowservicehost"></a>WorkflowServiceHost  
 <xref:System.ServiceModel.WorkflowServiceHost> (İş akışları barındırılması için Mesajlaşma kullanmak için gerekli olmasa da) destekleyen birden çok örneği, yapılandırma ve WCF ileti kullanıma hazır iş akışı ana bilgisayarı.  Ayrıca Kalıcılık, izleme ve hizmet davranışlarını bir dizi aracılığıyla örneği denetimi ile tümleştirilir.  WCF'ın ' olduğu gibi <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.WorkflowServiceHost> bir WinForms/konsol/WPF uygulaması veya Windows hizmeti, şirket içinde barındırılan veya (.xamlx dosyası) web barındırılan IIS veya WAS.  
  
### <a name="getting-started-with-workflow-service-host"></a>İş akışı hizmeti konağı ile çalışmaya başlama  
  
-   Visual Studio 2010'da bir WCF iş akışı hizmeti uygulaması projesi oluşturun: kullanmak için bu projeyi ayarlanır <xref:System.ServiceModel.WorkflowServiceHost> bir web barındırma ortamında.  
  
-   Mesajlaşma bir iş akışı barındırma için özel bir ekleme <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> iletisini temel alarak örneği oluşturur.  
  
-   İş akışı örnekleri denetlenebilir (örneğin askıya alınmış veya sonlandırıldı) ekleyerek bir <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> için <xref:System.ServiceModel.WorkflowServiceHost> kullanarak bir <xref:System.ServiceModel.Activities.WorkflowControlClient>.  
  
-   İçin örnek <xref:System.ServiceModel.WorkflowServiceHost> aşağıdaki bölümlerde bulunabilir:  
  
    -   [Yürütme](../../../docs/framework/windows-workflow-foundation/samples/execution.md)  
  
    -   Temel: [Hizmetleri](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Senaryo: [Hizmetleri](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Uygulama: [askıya alınmış örnek Yönetimi](../../../docs/framework/windows-workflow-foundation/samples/suspended-instance-management.md)  
  
-   [WorkflowServiceHost kavramsal belgeler](https://go.microsoft.com/fwlink/?LinkId=204807)  
  
### <a name="workflowservicehost-scenario"></a>WorkflowServiceHost senaryosu  
 Belirli bir rota için en iyi bilet fiyatı bulmak için birden çok Havayolu hizmetlerine BestPriceFinder hizmeti çağırır.  Bu senaryoyu uygulamaya içerseydi, iş akışında barındırmak <xref:System.ServiceModel.WorkflowServiceHost>.  Bu da fiyatı almak, Fiyatlar arka uç hizmetlerinden almak ve en iyi fiyatı Fiyat isteği yanıtlamak için ileti etkinlikleri kullanırsınız.  
  
## <a name="correlation"></a>Bağıntı  
 Bir bağıntı ikisinden biri:  
  
-   Bir şekilde birlikte gruplandırma iletilerinin; diğer bir deyişle, bir istek iletisi ve onun yanıtı arasındaki ilişki.  
  
-   Bir hizmet örneği için bir veri parçasını eşleme yöntemi  
  
### <a name="getting-started"></a>Başlarken  
  
-   Yurt içi hasıla ile çalışmaya başlamak için Visual Studio'da yeni bir proje oluşturun. Türünde bir değişken oluşturma <xref:System.ServiceModel.Activities.CorrelationHandle>.  
  
-   Grup iletileri birlikte kullanılan bağıntı iletileri gruplandıran bir istek-yanıt bağıntısı örneğidir.  
  
    -   Üzerinde bir <xref:System.ServiceModel.Activities.Receive> etkinliği tıklatın <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> özelliği ve ekleme bir <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> CorrelationHandle kullanarak Yukarıdaki ilk adımda oluşturduğunuz.  
  
    -   Oluşturma bir <xref:System.ServiceModel.Activities.SendReply> sağ tıklayarak etkinlik <xref:System.ServiceModel.Activities.Receive> ve "SendReply oluşturma". Sonra iş akışınızı yapıştırın <xref:System.ServiceModel.Activities.Receive> etkinlik.  
  
-   Bir hizmet örneği için bir veri parçasını eşleme örneği için belirli bir iş akışı örneği verileri (örneğin, bir sipariş kimliği) bir parçası eşleştiren içerik temelli bağıntı var.  
  
    -   Mesajlaşma tüm etkinliklerde tıklayarak `CorrelationInitializers` özelliği ve ekleme bir <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> kullanarak <xref:System.ServiceModel.Activities.CorrelationHandle> yukarıda oluşturulan değişken. ' % S'iletisi (örneğin, orderId) açılan menüsünden istenen özelliği çift tıklayın. Ayarlama `CorrelatesWith` özelliğini <xref:System.ServiceModel.Activities.CorrelationHandle> yukarıda kullanılan değişkeni.  
  
-   Örnekler:  
  
    -   Temel: [Hizmetleri](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Senaryo: [Hizmetleri](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   [Bağıntı kavramsal belgeler](https://go.microsoft.com/fwlink/?LinkId=204939)  
  
### <a name="correlation-scenario"></a>Bağıntı senaryosu  
 Bir sipariş işleme iş akışı, yeni sipariş oluşturulmasını ve işlemde olan mevcut siparişlerini güncelleştirme işlemek için kullanılır.  Bu senaryoyu uygulamaya içerseydi, iş akışında barındırmak <xref:System.ServiceModel.WorkflowServiceHost> ve mesajlaşma etkinlikleri kullanın.  Dayalı bağıntı gerektirecek `orderId` için güncelleştirmeleri doğru iş akışına yapıldığından emin olun.  
  
## <a name="simplified-configuration"></a>Basitleştirilmiş Yapılandırma  
 WCF yapılandırma şeması karmaşıktır ve kullanıcıların çoğu ile özellikleri bulmak için sabit sağlar. İçinde [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], biz WCF kullanıcılar aşağıdaki özelliklerle hizmetlerini yapılandırma sağlamaya odaklanmıştır:  
  
-   Açık hizmeti yapılandırma gereksinimini kaldırılıyor. Tüm yapılandırmazsanız \<hizmet > hizmetinizin ve hizmetiniz için öğeleri programlı olarak herhangi bir uç noktası tanımlamıyor ve ardından bir uç nokta kümesine hizmetinize bir sözleşme ve hizmeti temel adresi başına otomatik olarak eklenir hizmetiniz tarafından uygulanır.  
  
-   WCF bağlamaları ve herhangi bir açık yapılandırma ile Hizmetleri için uygulanan davranışları için varsayılan değerleri tanımlamak kullanıcı sağlar.  
  
-   Standart uç noktaları, sabit bir veya daha fazla uç noktası özellikleri (adresi, bağlama ve Sözleşme) için değerleri ve özel özellikleri tanımlamaya izin verir, yeniden kullanılabilir önceden yapılandırılmış uç tanımlayın.  
  
-   Son olarak, <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> WCF istemci yapılandırması, yapılandırma seçtikten veya uygulama etki alanı yükleme süresi sonra değiştirilen senaryolarda yararlı Merkezi Yönetimi gerçekleştirmenize izin verir.  
  
### <a name="getting-started"></a>Başlarken  
  
-   [WCF 4.0 için Geliştirici Kılavuzu](https://go.microsoft.com/fwlink/?LinkId=204940)  
  
-   [Yapılandırma Kanal Fabrikası](https://go.microsoft.com/fwlink/?LinkId=204941)  
  
-   [Standart uç nokta öğesi](https://go.microsoft.com/fwlink/?LinkId=204942)  
  
-   [Hizmet yapılandırma yenilikleri .net Framework 4](https://go.microsoft.com/fwlink/?LinkId=204943)  
  
-   [.NET 4'te kullanıcı sıkça: yanlış yazmanız WF/WCF hizmeti yapılandırma adı](https://go.microsoft.com/fwlink/?LinkId=204944)  
  
### <a name="simplified-configuration-scenarios"></a>Basitleştirilmiş yapılandırma senaryoları  
  
-   WCF kullanmaya başlamak bir deneyimli ASMX Geliştirici istiyor. Ancak, WCF çok karmaşık görünüyor! Bir yapılandırma dosyasında yazma gereken tüm bu bilgileri nedir? .NET 4'te bir yapılandırma dosyası hiç olmaması bile karar verebilirsiniz.  
  
-   WCF hizmetlerini var olan bir kümesi yapılandırmak ve korumak oldukça zor. Yapılandırma dosyasında XML kod satırlarının dokunması oldukça tehlikeli binlerce sahiptir. Yardım daha yönetilebilir bir şey için bu kod miktarını azaltmak için gereklidir.  
  
## <a name="data-contract-resolver"></a>Veri anlaşması çözümleyici  
 .NET 3. 5 ', bilinen türleri tasarım birkaç sınırlama vardı:  
  
-   Bilinen türleri dinamik olarak ekleme, serileştirme veya seri durumundan çıkarma sırasında mümkün değildi.  
  
-   Seri hale getiricileri genişletme bilinmeyen xsi: type bilgiyle uğraşmak değil.  
  
-   Örneğin, bir seri hale getirme örnek boyutu kablo küçültmek için kablo üzerinde görünür olmasını istediğiniz hangi xsi: type belirtmek kullanıcılar için mümkün değildi.  
  
 [DataContractResolver](../../../docs/framework/wcf/samples/datacontractresolver.md) .NET 4.5 içinde bu sorunları çözer.  
  
### <a name="getting-started"></a>Başlarken  
  
-   [Veri anlaşması çözümleyici API'si belgeleri](https://go.microsoft.com/fwlink/?LinkId=204946)  
  
-   [Veri sözleşmesi Çözücü ile tanışın](https://go.microsoft.com/fwlink/?LinkId=204947)  
  
-   Örnekler:  
  
    -   [DataContractResolver](../../../docs/framework/wcf/samples/datacontractresolver.md)  
  
    -   [KnownAssemblyAttribute](../../../docs/framework/wcf/samples/knownassemblyattribute.md)  
  
### <a name="data-contract-resolver-scenarios"></a>Veri anlaşması çözümleyici senaryoları  
  
-   Onlarca bildirme zorunda <xref:System.Runtime.Serialization.KnownTypeAttribute> hizmet nesneleri.  
  
-   XML Kabarcık boyutunu azaltır.  
  
## <a name="flowchart"></a>Akış Çizelgesi  
 Akış Çizelgesi, etki alanı sorunlarını görsel olarak göstermek için iyi bilinen bir örnektir. .NET 4'te kullanıma sunduğumuz yeni bir denetim akışı stili var. Bir çekirdek akış çizelgesi özellik, yalnızca bir etkinlik herhangi bir zamanda yürütülür ' dir. Akış çizelgeleri döngüleri ve diğer sonuçlar ifade edebilirsiniz, ancak birden çok düğüm eş zamanlı yürütme yerel olarak express olamaz.  
  
### <a name="getting-started"></a>Başlarken  
  
-   İçinde [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], bir iş akışı konsol uygulaması oluşturun. Bir akış çizelgesi iş akışı Tasarımcısı'nda ekleyin.  
  
-   Akış özelliğini aşağıdaki sınıflar kullanır:  
  
    -   <xref:System.Activities.Statements.Flowchart>  
  
    -   <xref:System.Activities.Statements.FlowNode>  
  
    -   <xref:System.Activities.Statements.FlowDecision>  
  
    -   <xref:System.Activities.Statements.FlowStep>  
  
    -   <xref:System.Activities.Statements.FlowSwitch%601>  
  
-   Örnekler:  
  
    -   [TryCatch Kullanarak Akış Çizelgesi Etkinliğine Hata İşleme](../../../docs/framework/windows-workflow-foundation/samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)  
  
    -   [FlowChart ve Pick Birleşimini Kullanan StateMachine Senaryosu](../../../docs/framework/windows-workflow-foundation/samples/statemachine-scenario-using-a-combination-of-flowchart-and-pick.md)  
  
    -   [İşe Alma İşlemi](../../../docs/framework/windows-workflow-foundation/samples/hiring-process.md)  
  
-   Tasarımcı belgeler:  
  
    -   [Akış Çizelgesi Etkinlik Tasarımcıları](/visualstudio/workflow-designer/flowchart-activity-designers)  
  
### <a name="flowchart-scenarios"></a>Akış senaryoları  
 Akış Çizelgesi etkinliğine tahmin eden bir oyun uygulamak için kullanılabilir. Tahmin eden oyun çok basittir: bilgisayar rastgele bir sayı seçer ve bu sayıyı tahmin oyuncusu içeriyor. Oyuncu her tahmin gönderdiğinde, bilgisayar kendisine (yani "daha düşük bir sayı deneyin") bir ipucu gösterilmektedir. Yürütücü numarası 7'den az girişimlerinde bulursa, o bilgisayardan özel congratulation alır. Bu oyunu aşağıdaki yordam etkinlikleri bir birleşimini uygulanabilir:  
  
-   <xref:System.Activities.Statements.Sequence>  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.TryCatch>  
  
-   <xref:System.Activities.Statements.Assign%601>  
  
-   <xref:System.Activities.Statements.If>  
  
## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a>Yordam etkinlikleri (sıralı, IF, ForEach, anahtar, atama, DoWhile, ancak)  
 Yordam etkinlikleri programcıları kavramları kullanarak model Sıralı denetim akışı için bir mekanizma sağlar. Bu etkinlikler geleneksel olarak yapılandırılmış programlama dili yapıları etkinleştirin ve uygun olduğunda, C# gibi genel yordam dilleri ile dil eşliğine sağlamak / VB.  
  
### <a name="getting-started"></a>Başlarken  
  
-   İçinde [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], bir iş akışı konsol uygulaması oluşturun. Yordam etkinlikleri iş akışı Tasarımcısı'nda ekleyin.  
  
-   Örnekler:  
  
    -   [İşe Alma İşlemi](../../../docs/framework/windows-workflow-foundation/samples/hiring-process.md)  
  
    -   [Şirket Satın Alma İşlemi](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md)  
  
-   Tasarımcı belgeler:  
  
    -   [Parallel Etkinlik Tasarımcısı](/visualstudio/workflow-designer/parallel-activity-designer)  
  
    -   [ParallelForEach\<T > etkinlik Tasarımcısı](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)  
  
### <a name="procedural-activity-scenarios"></a>Yordam etkinliği senaryoları  
  
-   <xref:System.Activities.Statements.Parallel>: Bir intranet belge yönetim sistemi bir belge onay iş akışı vardır. Belgeler intranet yayımlanmadan önce çeşitli Departmanlar kişiler tarafından onaylanması gerekir. Onaylar için yerleşik bir sipariş değildir; Belge "onay bekliyor" aşamasında olduğu sürece herhangi bir zamanda ortaya çıkabilir. Bir kullanıcı bir belgeyi gözden geçirme için gönderdiğinde doğrudan yöneticisinin, intranet yönetici ve dahili iletişim Yöneticisi tarafından onaylanması gerekir.  
  
-   <xref:System.Activities.Statements.ParallelForEach%601>Şirket satın büyük bir şirkette WF uygulama yönetir. Herhangi bir satın alma işlemi planlamadan önce üç farklı satıcıların sunduğu valuations olduğunu gerekli Kurumsal kuralları gerektirir. Satın alma departmanından bir çalışan üç satıcıları şirketin satıcı listeden seçer. Bu satıcılardan seçili ve bildirim sonra şirket için ekonomik, tekliflerini bekler. Teklifler herhangi bir sırada gelebilir. İçinde WF bu senaryoyu uygulamak için kullandığımız bir <xref:System.Activities.Statements.ParallelForEach%601> , satıcıları bizim toplulukta tekrarlama ve ekonomik kendi önerilerini isteyin. Tüm teklifler toplanan sonra en iyisi seçili ve görüntülenir.  
  
## <a name="invokemethod"></a>InvokeMethod  
 <xref:System.Activities.Statements.InvokeMethod> Etkinliği nesneler genel yöntemleri veya türleri kapsamındaki çağırma sağlar. Bu örnek ve statik yöntemler (parametre dizileri de dahil olmak üzere) parametrelerle veya parametresiz ve genel yöntemleri çağırma destekler. Ayrıca, zaman uyumlu ve zaman uyumsuz olarak çalıştırma yöntemi sağlar.  
  
### <a name="getting-started"></a>Başlarken  
  
-   İçinde [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], bir iş akışı konsol uygulaması oluşturun. Ekleme bir <xref:System.Activities.Statements.InvokeMethod> iş akışı tasarımcısında etkinlik statik yapılandırma ve örnek yöntemler üzerindeki.  
  
-   Örnekler:  
  
    -   [InvokeMethod](../../../docs/framework/windows-workflow-foundation/samples/invokemethod.md)  
  
-   Tasarımcı belgeler: [InvokeMethod etkinlik Tasarımcısı](/visualstudio/workflow-designer/invokemethod-activity-designer)  
  
### <a name="invokemethod-scenarios"></a>InvokeMethod senaryoları  
  
-   Bir nesne kapsam içinde bir yöntemde çağrılması gerekir. Örneğin, bir değer için bir sözlük eklenmesi gerekir. Sözlük örneğinin Ekle yöntemi çağrılır ve anahtar ve değer sağlanır.  
  
-   Eski bir CLR nesnesinde çağrılacak bir yöntem gerekir. İş akışı yürütme sırasında kapsamları dahilinde olması durumunda, eski o sınıfın çağrısını sarmalamak için özel bir etkinlik oluşturmak yerine <xref:System.Activities.Statements.InvokeMethod> kullanılabilir.  
  
## <a name="error-handling-activities"></a>Hata işleme etkinlik  
 <xref:System.Activities.Statements.TryCatch> Etkinlik içerilen etkinlikleri (C# /VB Try/Catch yapısında benzer) kümesi yürütülmesi sırasında oluşan özel durumları yakalama için bir mekanizma sağlar. <xref:System.Activities.Statements.TryCatch> özel durum işleme iş akışı düzeyinde sağlar. İş akışı, işlenmeyen bir özel durum oluştuğunda iptal edilir ve Finally bloğu yürütülmez olmaz. Bu davranış, C# ile tutarlıdır.  
  
### <a name="getting-started"></a>Başlarken  
  
-   İçinde [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], bir iş akışı konsol uygulaması oluşturun. Ekleme bir <xref:System.Activities.Statements.TryCatch> iş akışı tasarımcısında etkinlik.  
  
-   Örnekler:  
  
    1.  [TryCatch Kullanarak Akış Çizelgesi Etkinliğine Hata İşleme](../../../docs/framework/windows-workflow-foundation/samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)  
  
    2.  [Yordam Etkinlikleri Kullanma](../../../docs/framework/windows-workflow-foundation/samples/using-procedural-activities.md)  
  
-   Tasarımcı belgeler: [hata işleme etkinlik tasarımcıları](/visualstudio/workflow-designer/error-handling-activity-designers)  
  
### <a name="error-handling-scenarios"></a>Hata işleme senaryoları  
 Bir dizi etkinliği yürütülmesi gerekiyor ve belirli mantığı bir hata oluştuğunda yürütülmesi gerekiyor. Bu hata işleme mantığı sırasında hata kurtarılabilir olduğunu bulunursa, özel durum yeniden oluşturulabilir ve üst etkinliği (veya konak) sorun ilgilenecektir.  
  
## <a name="pick-activity"></a>Pick etkinliği  
 <xref:System.Activities.Statements.Pick> İçinde WF modelleme olay tabanlı denetim akış etkinliği sağlar. <xref:System.Activities.Statements.Pick> Burada her dal çalıştırmadan önce gerçekleşmesi belirli bir olay bekler fazla dal içerir. Bu kurulum içinde bir <xref:System.Activities.Statements.Pick> benzer şekilde davranan bir <xref:System.Activities.Statements.Switch%601> için hangi etkinlik, dinleme olay kümesini yalnızca birini çalıştırır. Olay temelli her daldır ve oluşan olayı karşılık gelen dal önce çalışır. Diğer tüm dallar iptal edin ve olayları dinleme durdurun.  
  
### <a name="getting-started"></a>Başlarken  
  
-   İçinde [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], bir iş akışı konsol uygulaması oluşturun. Ekleme bir <xref:System.Activities.Statements.Pick> iş akışı tasarımcısında etkinlik.  
  
-   Örnek: [Pick etkinliği kullanma](../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md)  
  
-   Tasarımcı belgeleri: [çekme etkinlik Tasarımcısı](/visualstudio/workflow-designer/pick-activity-designer)  
  
### <a name="pick-scenario"></a>Senaryo seçin  
 Bir kullanıcının giriş sorulması gerekir. Normal koşullar altında Geliştirici gibi bir yöntem çağrısının kullanacağınız <xref:System.Console.ReadLine%2A> bir kullanıcının girişinin için istemek için. Bu kurulum ile sorun, kullanıcının bir şey girene kadar program bekler olmasıdır. Bu senaryoda, bir zaman aşımı bir engelleyen etkinliği engelini kaldırmak için gereklidir. Sık karşılaşılan bir senaryodur belirli bir süre içinde tamamlanması için bir görev biridir. Zaman aşımının bir engelleyen etkinliği burada çekme değerli birçok ekler bir senaryodur.  
  
## <a name="wcf-routing-service"></a>WCF yönlendirme hizmeti  
 Yönlendirme hizmeti, bir genel yazılım nasıl WCFmessages, istemciler ve hizmetler arası akışını denetlemenizi sağlayan bir yönlendirici olacak şekilde tasarlanmıştır.  Yönlendirme hizmeti, hizmetlerinizi, istemcilerden ayırmak için yapılandırmaları açısından çok daha fazla özgürlük sağlayan, destekleyebilir ve hizmetlerinizi nasıl değerlendirirken sahip esnekliği sağlar.  .NET 3. 5 ', istemciler ve hizmetler sıkı şekilde bağlı; bir istemci, tüm hizmetleri bunun için iletişim kurmak için gereken ve burada bulunduğu hakkında bilmeniz gerekiyordu. Ayrıca, WCF'de .net Framework 3.5 olan aşağıdaki sınırlamalar:  
  
-   Bu mantık istemciyi sabit kodlanmış olması gerekiyordu karmaşık hata işleme kaydedildi.  
  
-   İstemcileri ve Hizmetleri her zaman aynı bağlamaları kullanmanız gerekiyordu.  
  
-   Hizmetleri nadiren de factored: her şeyi uygulayan bir hizmetinizle iletişim kurmasına istemcinin daha kolay denetlediğinden birden çok hizmetleri arasında seçim yapma.  
  
 .Net 4'te yönlendirme hizmeti, bu sorunları gidermek daha kolay hale getirmek için tasarlanmıştır. Yeni yönlendirme hizmeti aşağıdaki özelliklere sahiptir:  
  
1.  İçerik tabanlı yönlendirme (<xref:System.ServiceModel.Dispatcher.MessageFilter> nesneleri nereye gönderileceğini belirlemek için bir ileti inceleyin.)  
  
2.  (Aktarım & ileti) köprülemesi Protokolü  
  
3.  Hata işleme (yönlendirici iletişim özel durumu yakalar ve yedekleme Uç noktalara devreder)  
  
4.  (Bellekte) dinamik olarak güncelleştirilmesini <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> ve yönlendirmeyi yapılandırma.  
  
### <a name="getting-started"></a>Başlarken  
  
1.  Belgeler: [yönlendirme](../../../docs/framework/wcf/feature-details/routing.md)  
  
2.  Örnekler: [yönlendirme hizmetleri &#91;WCF örnekleri&#93;](../../../docs/framework/wcf/samples/routing-services.md)  
  
3.  Blog: [yönlendirme kuralları!](https://go.microsoft.com/fwlink/?LinkId=204956)  
  
### <a name="routing-scenarios"></a>Yönlendirme Senaryoları  
 Yönlendirme hizmeti, aşağıdaki senaryolarda kullanışlıdır:  
  
-   İstemciler, birden fazla hizmet için tüm doğrudan gidermek zorunda kalmadan konuşabilirsiniz.  
  
-   İstemciler bir istemci isteği yönlendirmek nereye belirlemek için ilave bir mantık gerçekleştirebilirsiniz  
  
-   İstemci yeniden düzenleme yapmadan bir istemci birden çok hizmet uygulamaları gerçekleştirir operations parçalara ayırın.  
  
-   İstemciler ve hizmetler farklı güvenlik ayarları farklı bağlamalarla konuşabilirsiniz.  
  
-   İstemciler, hata veya kullanım dışı kalması Hizmetleri karşı daha sağlam olması için etkinleştirilebilir.  
  
## <a name="wcf-discovery"></a>WCF Keşfetme  
 WCF bulma, uygulama altyapınızı bir keşif mekanizması eklemenizi sağlayan bir framework teknolojisidir. Hizmetinizi bulunabilmesini sağlamak için bunu kullanın ve Hizmetleri aramak için istemcileri yapılandırın. İstemciler artık zor uç nokta ile kodlanmış uygulama daha güçlü ve hataya dayanıklı hale gerekmez. Bulma, otomatik yapılandırma özelliklerini uygulamanıza oluşturmak için mükemmel bir platformdur.  
  
 Bir ürün üzerinde WS-bulma standart yerleşik olarak bulunur. Birlikte çalışabilir, genişletilebilir ve genel olacak şekilde tasarlanmıştır. Ürün iki çalışma modunu destekler:  
  
1.  Yönetilen: bulunduğu bir varlık ağda var olan hizmetleri hakkında bilgi sahibi, istemciler için bilgileri doğrudan sorgulayın. Bu, Active Directory ile benzerdir.  
  
2.  Geçici: çok noktaya yayın iletileri istemciler Hizmetleri bulmak için nereye kullanın.  
  
 Ayrıca, bulma iletileri ağ protokolü bağımsızdır; bunları üstte modu gereksinimlerini destekleyen herhangi bir protokolünü kullanabilirsiniz. Örneğin, bulma çok noktaya yayın iletileri, UDP kanal veya çok noktaya yayın iletileri destekleyen herhangi bir ağ gönderilebilir.  Bu bulma çözümünüz için özel olarak uyum sağlar özellik esnekliğiyle birlikte noktaları tasarlayın.  
  
### <a name="getting-started"></a>Başlarken  
  
-   Belgeler: [WCF bulma](../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
  
-   Örnekler: [keşif (örnekler)](../../../docs/framework/wcf/samples/discovery-samples.md)  
  
### <a name="discovery-scenarios"></a>Bulma senaryoları  
 Hizmetimi kullanılabilir olduğunda, bilinmeyen olduğundan bir geliştirici sabit kodu uç noktalarına istememektedir. Bunun yerine, geliştirici çalışma zamanında bir hizmet seçin ister. Daha fazla ayırma, sağlamlık ve otomatik yapılandırma, uygulama bileşenleri arasında gereklidir.  
  
## <a name="tracking"></a>İzleme  
 İş akışı izleme bir iş akışı örneği yürütülmesi hakkında Öngörüler sağlar.  Bir iş akışındaki etkinliklerin yürüttüğünüzde ve iş akışı örnek düzeyinde akışından yayılan izleme olayları. İş akışı izleme katılımcı abone izleme kayıtları için iş akışı ana bilgisayarı için eklenmesi gerekir. İzleme kayıtları bir izleme profili kullanılarak filtrelenir. .net Framework bir (olay izleme için Windows) ETW İzleme katılımcı sağlar ve temel profil machine.config dosyasında yüklenir.  
  
### <a name="getting-started"></a>Başlarken  
  
1.  İçinde [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], bir WCF iş akışı hizmeti uygulaması projesi oluşturun. A <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> çifti başlatmak için tuvalinizde yerleştirilir.  
  
2.  Web.config dosyasını açın ve bir ETW profil ile davranışını izleme ekleyin.  
  
    1.  Varsayılan profili kullanılır.  
  
    2.  Olay Görüntüleyicisi'ni açın ve şu düğümü analitik kanalda etkinleştirin: **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows** , **Uygulama uygulamalarının**. Sağ **analitik** seçip **günlüğü etkinleştir**.  
  
    3.  İş akışı hizmeti çalıştırın.  
  
    4.  İş akışı izleme olayları Olay Görüntüleyicisi'nde gözlemleyin.  
  
3.  Örnekler: [izleme](../../../docs/framework/windows-workflow-foundation/samples/tracking.md)  
  
4.  Kavramsal belgeler: [takip ve izleme iş akışı](../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
  
## <a name="sql-workflow-instance-store"></a>SQL iş akışı örneği Store  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Bir SQL Server tabanlı bir örnek deposuna uygulamasıdır. Bir örnek deposuna yüklemek ve bu örneğe sürdürmek gereken tüm verileri ile birlikte çalışan bir örneğinin durumunu depolar. Hizmet ana bilgisayarı, örnek durumu iş akışını devam ediyorsa ve bu örneği için bir ileti geldiğinde veya bir gecikme etkinlik süresi dolduğunda, örnek durumu yüklemek için örnek deposuna bildirir kaydetmek için örnek deposuna bildirir.  
  
### <a name="getting-started"></a>Başlarken  
  
1.  İçinde [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], kapalı veya açık içeren bir iş akışı oluşturmak <xref:System.Activities.Statements.Persist> etkinlik. Ekleme <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> davranışı, iş akışı hizmeti konağı için. Bu, kodda veya uygulama yapılandırma dosyasında yapılabilir.  
  
2.  Örnekler: [kalıcılığı](../../../docs/framework/windows-workflow-foundation/samples/persistence.md)  
  
3.  Kavramsal belgeler: [SQL iş akışı örneği Store](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).
