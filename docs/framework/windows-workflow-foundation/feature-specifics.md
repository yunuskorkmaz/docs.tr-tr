---
title: Windows Workflow Foundation Özellik Ayrıntıları
ms.date: 03/30/2017
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
ms.openlocfilehash: 11bde5edea44f09ef1a5658cdf0e20ec1349c84b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182917"
---
# <a name="windows-workflow-foundation-feature-specifics"></a>Windows Workflow Foundation Özellik Ayrıntıları

.NET Framework 4, Windows İş Akışı Temeli'ne bir dizi özellik ekler. Bu belge, bir dizi yeni özelliği açıklar ve yararlı olabileceksenaryolar hakkında ayrıntılı bilgi verir.

## <a name="messaging-activities"></a>Mesajlaşma Etkinlikleri

İleti etkinlikleri ,<xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply>iş <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply>akışınızdan WCF iletileri göndermek ve almak için kullanılır. <xref:System.ServiceModel.Activities.Receive>ve <xref:System.ServiceModel.Activities.SendReply> etkinlikler, standart WCF web hizmetleri gibi WSDL aracılığıyla ortaya çıkarılan bir Windows Communication Foundation (WCF) hizmet işlemi oluşturmak için kullanılır. <xref:System.ServiceModel.Activities.Send>ve <xref:System.ServiceModel.Activities.ReceiveReply> wcf <xref:System.ServiceModel.ChannelFactory>benzer bir web hizmeti tüketmek için kullanılır ; Önceden yapılandırılmış etkinlikler oluşturan İş Akışı Kuruluşu için bir **Hizmet Başvurusu Ekle** deneyimi de vardır.

### <a name="getting-started-with-messaging-activities"></a>Mesajlaşma Etkinliklerine Başlarken

- Visual Studio 2012'de bir WCF İş Akışı Hizmeti Uygulaması projesi oluşturun. Bir <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> ve çift tuval üzerine yerleştirilir.

- Projeye sağ tıklayın ve **Hizmet Başvurusu Ekle'yi**seçin. Varolan bir web hizmeti WSDL'yi işaret edin ve **Tamam'ı**tıklatın. Araç kutunuzda oluşturulan etkinlikleri (kullanılarak <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply>ve ) göstermek için projenizi oluşturun.

- [İş akışı hizmetleri dokümantasyonu](../wcf/feature-details/workflow-services.md)

### <a name="messaging-activities-example-scenario"></a>Mesajlaşma Etkinlikleri Örnek Senaryo

Bir `BestPriceFinder` servis, belirli bir rota için en iyi bilet fiyatını bulmak için birden fazla havayolu servisini çağırır. Bu senaryoyu uygulamak, fiyat isteğini almak, fiyatları arka uç hizmetlerinden almak ve fiyat isteğini en iyi fiyatla yanıtlamak için ileti etkinliklerini kullanmanız gerekir. Ayrıca, en iyi fiyatı hesaplamak için iş mantığı oluşturmak için diğer out-of-box faaliyetleri kullanmanız gerekir.

## <a name="workflowservicehost"></a>İş AkışıServiceHost

Birden <xref:System.ServiceModel.WorkflowServiceHost> çok örneği, yapılandırmayı ve WCF iletisini destekleyen kutu dan sıcağı sıcağısı (iş akışlarının barındırılmak üzere ileti kullanması gerekmese de). Ayrıca, bir dizi hizmet davranışı aracılığıyla kalıcılık, izleme ve örnek denetimiyle de tümleşir. WCF's <xref:System.ServiceModel.ServiceHost>gibi, <xref:System.ServiceModel.WorkflowServiceHost> bir konsol / WinForms / WPF uygulaması veya Windows hizmeti, ya da web barındırılan (.xamlx dosyası olarak) IIS veya WAS kendi kendine barındırılan olabilir.

### <a name="getting-started-with-workflow-service-host"></a>İş Akışı Servis Host'uyla Başlarken

- Visual Studio 2010'da bir WCF İş Akışı Hizmeti Uygulaması projesi <xref:System.ServiceModel.WorkflowServiceHost> oluşturun: bu proje bir web barındırma ortamında kullanılmak üzere kurulacak.

- İleti olmayan bir iş akışını barındırmak için, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> bir iletiye dayalı örneği oluşturacak bir özel ekleyin.

- İş akışı örnekleri kontrol edilebilir (örn. askıya alınmış veya <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> sonlandırıldı) bir a ekleyerek <xref:System.ServiceModel.WorkflowServiceHost> ve sonra bir <xref:System.ServiceModel.Activities.WorkflowControlClient>.

- Örnekler için <xref:System.ServiceModel.WorkflowServiceHost> aşağıdaki bölümlerde bulunabilir:

  - [Yürütme](./samples/execution.md)

  - Uygulama: [Askıya Alınan Örnek Yönetimi](./samples/suspended-instance-management.md)

- [Hosting İş Akışı hizmetlerine genel bakış](../wcf/feature-details/hosting-workflow-services-overview.md)

### <a name="workflowservicehost-scenario"></a>İş AkışıServiceHost Senaryo

Bir BestPriceFinder hizmeti belirli bir rota için en iyi bilet fiyatını bulmak için birden fazla havayolu hizmetleri çağırır. Bu senaryoyu uygulamak, iş akışını 'da <xref:System.ServiceModel.WorkflowServiceHost>barındırmanızı gerektirir. Ayrıca, fiyat isteğini almak, fiyatları arka uç servislerinden almak ve fiyat isteğini en iyi fiyatla yanıtlamak için ileti etkinliklerini de kullanır.

## <a name="correlation"></a>Bağıntı

Korelasyon iki şeyden biridir:

- İletileri bir araya gruplandırmanın bir yolu; diğer bir şey, istek iletisi ile yanıtı arasındaki ilişkidir.

- Bir veri parçasını bir hizmet örneğiyle eşlemenin bir yolu

### <a name="getting-started"></a>Başlarken

- Korelasyona başlamak için Visual Studio'da yeni bir proje oluşturun. Türünde <xref:System.ServiceModel.Activities.CorrelationHandle>bir değişken oluşturun.

- İletileri gruplandırmak için kullanılan korelasyon örneği, iletileri bir araya getiren İstek-Yanıt korelasyondur.

  - Bir <xref:System.ServiceModel.Activities.Receive> etkinlikte, <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> özelliği tıklatın ve <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> yukarıdaki ilk adımda oluşturulan Korelasyon Kolu'nu kullanarak ekleyin.

  - Sağ <xref:System.ServiceModel.Activities.SendReply> tıklayarak <xref:System.ServiceModel.Activities.Receive> ve "SendReply Oluştur"u tıklatarak etkinlik oluşturun. Etkinlikten sonra iş akışınıza <xref:System.ServiceModel.Activities.Receive> yapıştırın.

- Bir veri parçasını bir hizmet örneğiyle eşlemenin bir örneği, bir veri parçasını (örneğin, sipariş kimliği) belirli bir iş akışı örneğiyle eşleyen içerik tabanlı korelasyondur.

  - Herhangi bir ileti etkinliğinde, `CorrelationInitializers` özelliği tıklatın <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> ve <xref:System.ServiceModel.Activities.CorrelationHandle> yukarıda oluşturulan değişkeni kullanarak bir ekleyin. Açılan menüden iletide (örn. OrderID) istenen özelliği çift tıklatın. `CorrelatesWith` Özelliği yukarıda kullanılan <xref:System.ServiceModel.Activities.CorrelationHandle> değişkene ayarlayın.

- [Korelasyon Kavramsal Dokümantasyon](../wcf/feature-details/correlation.md)

### <a name="correlation-scenario"></a>Korelasyon Senaryosu

Yeni sipariş oluşturma işlemini işlemek ve devam eden varolan siparişleri güncelleştirmek için sipariş işleme iş akışı kullanılır. Bu senaryoyu uygulamak, iş akışını barındırmanızı <xref:System.ServiceModel.WorkflowServiceHost> ve ileti etkinliklerini kullanmanızgerekir. Ayrıca, güncelleştirmelerin doğru `orderId` iş akışına yapıldığından emin olmak için bağlı olarak korelasyon gerektirir.

## <a name="simplified-configuration"></a>Basitleştirilmiş Yapılandırma

WCF yapılandırma şeması karmaşıktır ve kullanıcılara bulunması zor birçok özellik sağlar. WCF [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]kullanıcılarının hizmetlerini aşağıdaki özelliklerle yapılandırmalarına yardımcı olmak için:

- Açık hizmet başına yapılandırma gereksinimini kaldırma. Hizmetiniz için herhangi \<bir hizmet> öğesini yapılandırmazsanız ve hizmetiniz programlı olarak herhangi bir bitiş noktası tanımlamazsa, hizmet adresinizbaşına bir tane ve hizmetiniz tarafından uygulanan sözleşme başına bir dizi uç nokta otomatik olarak eklenir.

- Kullanıcının WCF bağlamaları ve açık yapılandırması olmayan hizmetlere uygulanacak davranışlar için varsayılan değerleri tanımlamasını sağlar.

- Standart uç noktaları, bitiş noktası özelliklerinden biri veya daha fazlası için sabit değerlere sahip olan yeniden kullanılabilir önceden yapılandırılmış uç noktaları tanımlar ve özel özelliklerin tanımlanmasına izin verir.

- Son olarak, uygulama etki alanı yükleme süresinden sonra yapılandırmanın seçildiği veya değiştirildiği senaryolarda yararlı olan WCF istemci yapılandırmasının merkezi yönetimini yapmanıza <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> olanak tanır.

### <a name="getting-started"></a>Başlarken

- [WCF 4.0 Için Geliştirici Kılavuzu](https://docs.microsoft.com/previous-versions/dotnet/articles/ee354381(v=msdn.10))

- [Yapılandırma Kanal Fabrikası](xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601)

- [Standart Bitiş Noktası Öğesi](xref:System.ServiceModel.Configuration.StandardEndpointElement)

- [.NET Framework 4'teki hizmet yapılandırma sı](https://docs.microsoft.com/archive/blogs/endpoint/service-configuration-improvements-in-net-4)

- [.NET 4'te Sık Karşılaşılan Kullanıcı Hatası: WF/WCF Hizmet Yapılandırma Adının Yanlış YazDisi](https://docs.microsoft.com/archive/blogs/endpoint/common-user-mistake-in-net-4-mistyping-the-wfwcf-service-configuration-name)

### <a name="simplified-configuration-scenarios"></a>Basitleştirilmiş Yapılandırma Senaryoları

- Deneyimli bir ASMX geliştiricisi WCF kullanmaya başlamak istiyor. Ancak, WCF yol çok karmaşık görünüyor! Yapılandırma dosyasına yazmam gereken tüm bu bilgiler nedir? .NET 4'te, yapılandırma dosyasının hiç olmamasına bile karar verebilirsiniz.

- Varolan bir WCF hizmetleri kümesini yapılandırmak ve sürdürmek çok zordur. Yapılandırma dosyası, dokunmak için son derece tehlikeli xml kodu satırları binlerce vardır. Bu kod miktarını daha yönetilebilir bir şeye düşürmek için yardım gerekir.

## <a name="data-contract-resolver"></a>Veri Sözleşmesi Çözümleyicisi

.NET 3.5'te, bilinen türlerin tasarımında birkaç sınırlama vardı:

- Bilinen türleri dinamik olarak eklemek, serileştirme veya deserialization sırasında, mümkün değildi.

- Serializers bilinmeyen xsi ile başa çıkamadı:türü bilgi.

- Kullanıcıların, örneğin, kablodaki bir serileştirme örneğinin boyutunu küçültmek için, kabloda görünmesini istedikleri xsi:type'ı belirtmeleri mümkün değildi.

[DataContractResolver](../wcf/samples/datacontractresolver.md) bu sorunları .NET 4.5'te çözer.

### <a name="getting-started"></a>Başlarken

- [Veri Sözleşmesi Çözümleyici API belgeleri](xref:System.Runtime.Serialization.DataContractResolver)

- [Veri Sözleşmesi Çözümleyicisi Tanıtımı](https://docs.microsoft.com/archive/blogs/youssefm/configuring-known-types-dynamically-introducing-the-datacontractresolver)

- Örnekleri:

  - [DataContractResolver](../wcf/samples/datacontractresolver.md)

  - [KnownAssemblyAttribute](../wcf/samples/knownassemblyattribute.md)

### <a name="data-contract-resolver-scenarios"></a>Veri Sözleşmesi Çözümleyici Senaryoları

- Bir hizmette onlarca <xref:System.Runtime.Serialization.KnownTypeAttribute> nesne bildirmek zorunda kalmamak.

- XML lekeboyutunu azaltır.

## <a name="flowchart"></a>Akış Çizelgesi

Akış şeması, etki alanı sorunlarını görsel olarak temsil eden iyi bilinen bir paradigmadır. .NET 4'te sunduğumuz yeni bir kontrol akışı stilidir. Flowchart'ın temel bir özelliği, herhangi bir zamanda yalnızca bir etkinliğin yürütülmesidir. Akış şemaları döngüleri ve alternatif sonuçları ifade edebilir, ancak birden çok düğümün eşzamanlı yürütülmesini doğal olarak ifade edemez.

### <a name="getting-started"></a>Başlarken

- Visual Studio 2012'de bir iş akışı konsolu uygulaması oluşturun. İş akışı tasarımcısına bir Akış Şeması ekleyin.

- Akış şeması özelliği aşağıdaki sınıfları kullanır:

  - <xref:System.Activities.Statements.Flowchart>

  - <xref:System.Activities.Statements.FlowNode>

  - <xref:System.Activities.Statements.FlowDecision>

  - <xref:System.Activities.Statements.FlowStep>

  - <xref:System.Activities.Statements.FlowSwitch%601>

- Örnekleri:

  - [TryCatch Kullanarak Akış Çizelgesi Etkinliğine Hata İşleme](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

  - [İşe Alma İşlemi](./samples/hiring-process.md)

- Tasarımcı Dokümantasyon:

  - [Flowchart Etkinlik Tasarımcıları](/visualstudio/workflow-designer/flowchart-activity-designers)

### <a name="flowchart-scenarios"></a>Akış Şeması Senaryoları

Bir akış şeması etkinliği bir tahmin oyunu uygulamak için kullanılabilir. Tahmin oyunu çok basittir: bilgisayar rastgele bir sayı seçer ve oyuncu bu sayıyı tahmin etmek zorundadır. Oyuncu her tahmin gönderdiğinde, bilgisayar onlara bir ipucu gösterir (örneğin" daha düşük bir sayı deneyin"). Oyuncu numarayı 7 denemeden daha kısa bir sürede bulursa, bilgisayardan özel bir tebrik alır. Bu oyun aşağıdaki usul faaliyetlerinin bir kombinasyonu ile uygulanabilir:

- <xref:System.Activities.Statements.Sequence>

- <xref:System.Activities.Statements.While>

- <xref:System.Activities.Statements.Switch%601>

- <xref:System.Activities.Statements.TryCatch>

- <xref:System.Activities.Statements.Assign%601>

- <xref:System.Activities.Statements.If>

## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a>Yordam saletkinlikleri (Sıra, If, ForEach, Switch, Atama, DoWhile, While)

Yordamsal etkinlikler, programcılara tanıdık kavramları kullanarak sıralı denetim akışını modellemek için bir mekanizma sağlar. Bu etkinlikler geleneksel olarak yapılandırılmış programlama dili yapılarını sağlar ve uygun olduğunda C# ve Visual Basic gibi ortak yordam dilleriyle dil eşitliği sağlar.

### <a name="getting-started"></a>Başlarken

- Visual Studio 2012'de bir iş akışı konsolu uygulaması oluşturun. İş akışı tasarımcısına yordamsal etkinlikler ekleyin.

- Örnekleri:

  - [İşe Alma İşlemi](./samples/hiring-process.md)

  - [Şirket Satın Alma İşlemi](./samples/corporate-purchase-process.md)

- Tasarımcı Dokümantasyon:

  - [Parallel Etkinlik Tasarımcısı](/visualstudio/workflow-designer/parallel-activity-designer)

  - [ParallelForEach\<T> Etkinlik Tasarımcısı](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)

### <a name="procedural-activity-scenarios"></a>Yordam Etkinlik Senaryoları

- <xref:System.Activities.Statements.Parallel>: Intranet belge yönetim sisteminde belge onay iş akışı vardır. Belgelerin intranet'te yayınlanmadan önce çeşitli departmanlarda bulunan kişiler tarafından onaylanması gerekir. Onaylar için belirlenmiş bir emir yoktur; belge "onay beklemede" aşamasındayken herhangi bir zamanda oluşabilir. Bir kullanıcı gözden geçirilmeüzere bir belge gönderdiğinde, belgenin doğrudan yöneticisi, intranet yöneticisi ve dahili iletişim yöneticisi tarafından onaylanması gerekir.

- <xref:System.Activities.Statements.ParallelForEach%601>: Bir WF uygulaması büyük bir şirket içinde kurumsal satın yönetir. Şirket kuralları, herhangi bir satın alma işlemini planlamadan önce üç farklı satıcının değerlemesinin gerekli olduğunu belirtir. Satın alma bölümünden bir çalışan, şirketin satıcı listesinden üç satıcı seçer. Bu satıcılar seçildikten ve bilgilendirildikten sonra, şirket ekonomik önerilerini bekleyecektir. Teklifler herhangi bir sırada gelebilir. WF bu senaryoyu uygulamak için, satıcıların bizim toplama yoluyla yinelemek ve ekonomik önerilerini sormak bir <xref:System.Activities.Statements.ParallelForEach%601> kullanın. Tüm teklifler toplandıktan sonra, en iyi teklif seçilir ve görüntülenir.

## <a name="invokemethod"></a>InvokeMethod

Etkinlik, <xref:System.Activities.Statements.InvokeMethod> kapsamdaki nesnelerde veya türlerde ortak yöntemlerin çağırılamasına olanak tanır. Parametre dizileri (parametre dizileri dahil) ve genel yöntemlerle örnek ve statik yöntemleri çağıran destekler. Ayrıca, yöntemin eşzamanlı ve eş senkronize olarak yürütülmesine de olanak tanır.

### <a name="getting-started"></a>Başlarken

- Visual Studio 2012'de bir iş akışı konsolu uygulaması oluşturun. İş <xref:System.Activities.Statements.InvokeMethod> akışı tasarımcısına bir etkinlik ekleyin ve üzerinde statik ve örnek yöntemleri yapılandırın.

- Tasarımcı Dokümantasyonu: [InvokeMethod Etkinlik Tasarımcısı](/visualstudio/workflow-designer/invokemethod-activity-designer)

### <a name="invokemethod-scenarios"></a>InvokeMethod Senaryoları

- Kapsamdaki bir nesnedeki yöntemin çağrılması gerekir. Örneğin, bir değerin bir sözlüke eklenmesi gerekir. Sözlük örneğinin Ekle yöntemi çağrılır ve anahtar ve değer sağlanır.

- Eski bir CLR nesnesi üzerinde bir yöntemin çağrılması gerekir. İş akışı yürütme <xref:System.Activities.Statements.InvokeMethod> sırasında kapsamda ysa, bu eski sınıfa çağrıyı sarmak için özel bir etkinlik oluşturmak yerine kullanılabilir.

## <a name="error-handling-activities"></a>Hata işleme etkinlikleri

Etkinlik, <xref:System.Activities.Statements.TryCatch> bir dizi içi sahipli etkinlik (C# ve Visual Basic'teki Try/Catch yapısına benzer) yürütülmesi sırasında oluşan özel durumları yakalamak için bir mekanizma sağlar. <xref:System.Activities.Statements.TryCatch>iş akışı düzeyinde özel durum işleme sağlar. İşlenmemiş bir özel durum atıldığında, iş akışı iptal edilir ve Son olarak blok yürütülmez. Bu davranış C# ile tutarlıdır.

### <a name="getting-started"></a>Başlarken

- Visual Studio 2012'de bir iş akışı konsolu uygulaması oluşturun. İş <xref:System.Activities.Statements.TryCatch> akışı tasarımcısına bir etkinlik ekleyin.

- Örnek: [TryCatch kullanarak Bir Flowchart Etkinliğinde Hata İşleme](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

- Tasarımcı Belgeleri: [Hata İşleme Etkinlik Tasarımcıları](/visualstudio/workflow-designer/error-handling-activity-designers)

### <a name="error-handling-scenarios"></a>Hata işleme senaryoları

Bir dizi etkinlik yürütülmesi ve bir hata oluştuğunda belirli bir mantığın yürütülmesi gerekir. Bu hata işleme mantığı sırasında hata kurtarılamaz bulunursa, özel durum yeniden atılır ve üst etkinlik (veya ana bilgisayar) sorunla ilgilenecektir.

## <a name="pick-activity"></a>Etkinliği seçme

Etkinlik <xref:System.Activities.Statements.Pick> WF olay tabanlı kontrol akışı modelleme sağlar. <xref:System.Activities.Statements.Pick>her dal, çalıştırmadan önce belirli bir olayın gerçekleşmesini beklediği birçok dal içerir. Bu kurulumda, <xref:System.Activities.Statements.Pick> Etkinlik'in dinlediği olaylar kümesinden yalnızca birini yürüteceği a'ya <xref:System.Activities.Statements.Switch%601> benzer bir şekilde hareket eder. Her dal olay odaklıdır ve oluşan olay önce ilgili dalı çalıştırılır. Diğer tüm şubeler etkinlikleri iptal eder ve dinlemeyi durdurur.

### <a name="getting-started"></a>Başlarken

- Visual Studio 2012'de bir iş akışı konsolu uygulaması oluşturun. İş <xref:System.Activities.Statements.Pick> akışı tasarımcısına bir etkinlik ekleyin.

- Örnek: [Çekme Etkinliğini Kullanma](./samples/using-the-pick-activity.md)

- Tasarımcı belgeleri: [Etkinlik Tasarımcısı seçin](/visualstudio/workflow-designer/pick-activity-designer)

### <a name="pick-scenario"></a>Senaryo Yu Seçin

Giriş için bir kullanıcıdan istenmesi gerekir. Normal koşullar altında, geliştirici bir kullanıcının girişi için istem gibi <xref:System.Console.ReadLine%2A> bir yöntem çağrısı kullanır. Bu kurulumla ilgili sorun, programın kullanıcı bir şey girene kadar beklemesidir. Bu senaryoda, engelleme etkinliğini kaldırmak için bir zaman arası gerekir. Sık karşılaşılan bir senaryo, belirli bir süre içinde tamamlanması gereken bir görevdir. Engelleme etkinliğini zamanlama, Çekme'nin çok fazla değer eklediği bir senaryodur.

## <a name="wcf-routing-service"></a>WCF Yönlendirme Hizmeti

Yönlendirme Hizmeti, WCF iletilerinin müşterileriniz ve hizmetleriniz arasında nasıl aktığını denetlemenize olanak tanıyan genel bir yazılım Yönlendiricisi olarak tasarlanmıştır. Yönlendirme Hizmeti, müşterilerinizi hizmetlerinizden ayırmanızı sağlar ve bu da size destek olabileceğiniz yapılandırmalar ve hizmetlerinizi nasıl barındırabileceğinizi düşünürken sahip olduğunuz esneklik açısından çok daha fazla özgürlük sağlar. .NET 3.5'te müşteriler ve hizmetler sıkıca birleştirilmiş; bir müşteri konuşmak için gereken tüm hizmetleri ve nerede bulunduğunu bilmek zorunda kaldı. Buna ek olarak, .NET Framework 3.5'teki WCF'nin aşağıdaki sınırlamaları vardı:

- Hata işleme karmaşıktı, çünkü bu mantık istemciye sabit kodlanmış olması gerekiyordu.

- İstemciler ve hizmetler her zaman aynı bağlamaları kullanmak zorunda kaldı.

- Hizmetler nadiren iyi faktöre edildi: istemcinin birden çok hizmet arasında seçim yapmak zorunda kalmaktansa, her şeyi uygulayan bir hizmetle konuşması daha kolaydır.

.NET 4'teki yönlendirme hizmeti, bu sorunların çözülmesini kolaylaştırmak için tasarlanmıştır. Yeni yönlendirme hizmeti aşağıdaki özelliklere sahiptir:

1. İçerime dayalı yönlendirme<xref:System.ServiceModel.Dispatcher.MessageFilter> ( nesneler nereye gönderilmesi gerektiğini belirlemek için bir iletiyi inceler.)

2. Protokol köprüleme (aktarım & iletisi)

3. Hata işleme (yönlendirici iletişim özel durumlarını yakalar ve yedekleme uç noktaları üzerinde başarısız olur)

4. Dinamik (bellekte) <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> güncelleştirme ve Yönlendirme Yapılandırması.

### <a name="getting-started"></a>Başlarken

1. Dokümantasyon: [Yönlendirme](../wcf/feature-details/routing.md)

2. Örnekler: [Routing Hizmetleri &#91;WCF Örnekleri&#93;](../wcf/samples/routing-services.md)

3. Blog: [Yönlendirme Kuralları!](https://docs.microsoft.com/archive/blogs/RoutingRules/)

### <a name="routing-scenarios"></a>Yönlendirme Senaryoları

Yönlendirme hizmeti aşağıdaki senaryolarda yararlıdır:

- İstemciler, bunların tümüne doğrudan hitap etmek zorunda kalmadan birden çok hizmetle konuşabilir.

- İstemciler, istemci isteğinde nereye yönlendireceklerini belirlemek için ek mantık gerçekleştirebilir

- İstemciyi yeniden düzenlemeden birden çok hizmet uygulamasına dönüştürün.

- İstemciler ve hizmetler farklı güvenlik ayarlarıyla farklı bağlamalar konuşabilir.

- İstemcilerin başarısızlığa veya hizmetlerin kullanılamamasına karşı daha sağlam olması etkinleştirilebilir.

## <a name="wcf-discovery"></a>WCF Keşfetme

WCF Discovery, uygulama altyapınıza bir bulma mekanizması dahil etmenizi sağlayan bir çerçeve teknolojisidir. Bunu, hizmetinizi bulunabilir hale getirmek ve müşterilerinizi hizmet aramak üzere yapılandırmak için kullanabilirsiniz. İstemcilerin artık uç noktayla kodlanmış olması gerekmez, bu da uygulamanızı daha sağlam ve hataya dayanıklı hale getirir. Discovery, uygulamanızda otomatik yapılandırma özellikleri oluşturmak için mükemmel bir platformdur.

Ürün, WS-Discovery standardının üzerine inşa edilmiştir. Birlikte çalışabilir, genişletilebilir ve genel olacak şekilde tasarlanmıştır. Ürün iki çalışma modunu destekler:

1. Yönetilen: ağda varolan hizmetler hakkında bilgili bir varlık varsa, istemciler doğrudan bilgi için sorgular. Bu Active Directory benzer.

2. Ad-hoc: istemcilerin hizmetleri bulmak için çok noktaya yayın iletileri kullandığı yer.

Ayrıca, keşif iletileri ağ protokolü agnostik vardır; mod gereksinimlerini destekleyen herhangi bir protokolün üzerinde kullanabilirsiniz. Örneğin, keşif çok noktaya yayın iletileri UDP kanalı veya çok noktaya yayın iletisini destekleyen başka bir ağ üzerinden gönderilebilir. Bu tasarım noktaları, özellik esnekliğiyle birleştiğinde, keşfi özellikle çözümünüze uyarlamanıza olanak sağlar.

### <a name="getting-started"></a>Başlarken

- Dokümantasyon: [WCF Discovery](../wcf/feature-details/wcf-discovery.md)

- Örnekler: [Discovery (Örnekler)](../wcf/samples/discovery-samples.md)

### <a name="discovery-scenarios"></a>Bulma Senaryoları

Bir geliştirici, hizmetimin ne zaman kullanılabilir olacağı bilinmediği için kod uç noktalarını sabit almak istemez. Bunun yerine, geliştirici çalışma zamanında bir hizmet seçmek istiyor. Uygulamadaki bileşenler arasında daha fazla ayrışma, sağlamlık ve otomatik yapılandırma gerekir.

## <a name="tracking"></a>İzleme

İş akışı izleme, iş akışı örneğinin yürütülmesine ilişkin öngörüsağlar. İzleme olayları iş akışı örneği düzeyindeki bir iş akışından ve iş akışı içindeki etkinlikler yürütüldüğünde yayılır. İzleme kayıtlarına abone olmak için iş akışı ana bilgisayara bir iş akışı izleme katılımcısının eklenmesi gerekir. İzleme kayıtları bir izleme profili kullanılarak filtrelenir. .NET Framework bir ETW (Windows için Olay İzleme) izleme katılımcısı sağlar ve machine.config dosyasına temel bir profil yüklenir.

### <a name="getting-started"></a>Başlarken

1. Visual Studio 2010'da bir WCF İş Akışı Hizmeti Uygulaması projesi oluşturun. Başlamak <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> için tuvalinizin üzerine a ve çift yerleştirilir.

2. Web.config'i açın ve profili olmayan bir ETW izleme davranışı ekleyin.

    1. Varsayılan profil kullanılır.

    2. Olay görüntüleyicisi açın ve aşağıdaki düğümde analitik kanalı etkinleştirin: **Olay Görüntüleyicisi**, **Uygulamalar ve Hizmetler Günlükleri**, **Microsoft**, **Windows**, **Uygulama Sunucusu-Uygulamalar**. **Analytic'e** sağ tıklayın ve **Günlüğü Etkinleştir'i**seçin.

    3. İş akışı hizmetini çalıştırın.

    4. Olay görüntüleyicisinde iş akışı izleme olaylarını gözlemleyin.

3. Örnekler: [İzleme](./samples/tracking.md)

4. Kavramsal dokümantasyon: [İş Akışı İzleme ve İzleme](workflow-tracking-and-tracing.md)

## <a name="sql-workflow-instance-store"></a>SQL İş Akışı Örnek Deposu

Örnek <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> deposunun SQL Server tabanlı uygulamasıdır. Bir örnek deposu, çalışan bir örneğin durumunu, bu örneği yüklemek ve devam ettirmek için gereken tüm verilerle birlikte depolar. Hizmet ana bilgisayarı, iş akışı devam ederse örnek mağazaya örnek durumu kaydetmesini bildirir ve bu örnek için bir ileti geldiğinde veya bir gecikme etkinliği sona erdiğinde örnek durumu yüklemesini bildirir.

### <a name="getting-started"></a>Başlarken

1. Visual Studio 2012'de, örtük veya açık <xref:System.Activities.Statements.Persist> bir etkinlik içeren bir İş Akışı oluşturun. <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Davranışı iş akışı hizmet ana bilgisayarınıza ekleyin. Bu kod veya uygulama yapılandırma dosyasında yapılabilir.

2. Örnekler: [Sebat](/previous-versions/dotnet/netframework-4.0/dd699769(v%3dvs.100))

3. Kavramsal dokümantasyon: [SQL İş Akışı Örnek Deposu.](sql-workflow-instance-store.md)
