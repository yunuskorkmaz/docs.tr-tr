---
title: Windows Workflow Foundation Özellik Ayrıntıları
ms.date: 03/30/2017
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
ms.openlocfilehash: 197b2e0d6586e001a4970cf8cb3f8e6b2a372af2
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936790"
---
# <a name="windows-workflow-foundation-feature-specifics"></a>Windows Workflow Foundation Özellik Ayrıntıları

.NET Framework 4, Windows Workflow Foundation bir dizi özellik ekler. Bu belge, yeni özelliklerin bir sayısını açıklar ve yararlı olabilecek senaryolar hakkındaki ayrıntıları verir.

## <a name="messaging-activities"></a>Mesajlaşma Etkinlikleri

İleti etkinlikleri (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.ReceiveReply>) iş akışınızdan WCF iletileri göndermek ve almak için kullanılır. <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikleri, yalnızca standart WCF Web Hizmetleri gibi WSDL aracılığıyla sunulan bir Windows Communication Foundation (WCF) hizmet işlemi oluşturmak için kullanılır. <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply>, WCF <xref:System.ServiceModel.ChannelFactory>benzer bir Web hizmetini tüketmek için kullanılır; Workflow Foundation için önceden yapılandırılmış etkinlikler üreten bir **hizmet başvurusu Ekle** deneyimi de mevcuttur.

### <a name="getting-started-with-messaging-activities"></a>Mesajlaşma etkinliklerine Başlarken

- Visual Studio 2012 ' de bir WCF Iş akışı hizmeti uygulama projesi oluşturun. <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> çifti Tuvalinize yerleştirilecek.

- Projeye sağ tıklayın ve **hizmet başvurusu Ekle**' yi seçin. Var olan bir Web hizmeti WSDL 'sinin üzerine gelin ve **Tamam**' a tıklayın. Araç kutusunda oluşturulan Etkinlikleri (<xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply>kullanılarak uygulanan) göstermek için projenizi derleyin.

- [İş akışı Hizmetleri belgeleri](../wcf/feature-details/workflow-services.md)

### <a name="messaging-activities-example-scenario"></a>Mesajlaşma etkinlikleri örnek senaryosu

Bir `BestPriceFinder` hizmeti, belirli bir rota için en iyi bilet fiyatını bulmak üzere birden çok hava yolu hizmetine çağrı yapılır. Bu senaryonun uygulanması, Fiyat isteğini almak, arka uç hizmetlerinden fiyatları almak ve fiyat talebini en iyi fiyatla yanıtlamak için ileti etkinliklerini kullanmanızı gerektirir. Ayrıca, en iyi fiyatı hesaplamak için iş mantığını oluşturmak üzere diğer hazır etkinlikler kullanmanızı da gerektirir.

## <a name="workflowservicehost"></a>WorkflowServiceHost

<xref:System.ServiceModel.WorkflowServiceHost>, birden çok örneği, yapılandırmayı ve WCF iletilerini destekleyen, kullanıma hazır olan iş akışı ana bilgisayarı olur (ancak iş akışlarının barındırılmak için mesajlaşma kullanması gerekmez). Ayrıca, bir dizi hizmet davranışı aracılığıyla Kalıcılık, izleme ve örnek denetimiyle tümleştirilir. WCF 'nin <xref:System.ServiceModel.ServiceHost>benzer şekilde, <xref:System.ServiceModel.WorkflowServiceHost>, IIS ya da bir konsol/WinForms/WPF uygulamasında veya Windows hizmetinde veya Web 'de barındırılan (bir. xamlx dosyası olarak) IIS veya WAS içinde şirket içinde barınabilir.

### <a name="getting-started-with-workflow-service-host"></a>Iş akışı hizmet ana bilgisayarı ile çalışmaya başlama

- Visual Studio 2010 ' de bir WCF Iş akışı hizmeti uygulama projesi oluşturun: Bu proje, bir Web ana bilgisayar ortamında <xref:System.ServiceModel.WorkflowServiceHost> kullanacak şekilde ayarlanacak.

- Mesajlaşma olmayan bir iş akışını barındırmak için, bir iletiye göre örneği oluşturacak özel bir <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> ekleyin.

- Bir <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> <xref:System.ServiceModel.WorkflowServiceHost> ve ardından bir <xref:System.ServiceModel.Activities.WorkflowControlClient>kullanarak iş akışı örnekleri denetlenebilir (örn. askıya alınmış veya sonlandırılmış).

- <xref:System.ServiceModel.WorkflowServiceHost> örnekleri aşağıdaki bölümlerde bulunabilir:

  - [Yürütme](./samples/execution.md)

  - Uygulama: [askıya alınmış örnek yönetimi](./samples/suspended-instance-management.md)

- [Barındırma Iş akışı hizmetlerine genel bakış](../wcf/feature-details/hosting-workflow-services-overview.md)

### <a name="workflowservicehost-scenario"></a>WorkflowServiceHost senaryosu

En iyi şekilde bir pricefinder hizmeti, belirli bir rota için en iyi bilet fiyatını bulmak üzere birden çok hava yolu hizmetine çağrı yapılır. Bu senaryonun uygulanması, <xref:System.ServiceModel.WorkflowServiceHost>iş akışını barındırmanıza gerek duyar. Ayrıca, Fiyat isteğini almak, arka uç hizmetlerinden fiyatları almak ve fiyat isteğini en iyi fiyatla yanıtlamak için ileti etkinliklerini de kullanabilirsiniz.

## <a name="correlation"></a>Bağıntı

Bağıntı iki işlemlerden biridir:

- İletileri birlikte gruplandırmanın bir yolu; diğer bir deyişle, bir istek iletisi ve yanıtı arasındaki ilişki.

- Bir veri parçasını bir hizmet örneğine eşlemenin bir yolu

### <a name="getting-started"></a>Başlarken

- Bağıntı ile çalışmaya başlamak için, Visual Studio 'da yeni bir proje oluşturun. <xref:System.ServiceModel.Activities.CorrelationHandle>türünde bir değişken oluşturun.

- İletileri birlikte gruplamak için kullanılan bağıntı örneği, iletileri birlikte gruplandıran bir Istek-Yanıt Bağıntısı olur.

  - <xref:System.ServiceModel.Activities.Receive> etkinliğinde, <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> özelliğine tıklayın ve yukarıdaki ilk adımda oluşturulan CorrelationHandle 'ı kullanarak bir <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> ekleyin.

  - <xref:System.ServiceModel.Activities.Receive> sağ tıklayıp "SendReply oluştur" seçeneğine tıklayarak <xref:System.ServiceModel.Activities.SendReply> etkinlik oluşturun. <xref:System.ServiceModel.Activities.Receive> etkinliğinden sonra iş akışınıza yapıştırın.

- Bir veri parçasını bir hizmet örneğine eşlemeye örnek olarak, bir veri parçasını (örneğin, bir sipariş KIMLIĞI) belirli bir iş akışı örneğine eşleyen içerik tabanlı bağıntı bulunur.

  - Herhangi bir mesajlaşma etkinliğinde `CorrelationInitializers` özelliğine tıklayın ve yukarıda oluşturulan <xref:System.ServiceModel.Activities.CorrelationHandle> değişkenini kullanarak bir <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> ekleyin. Açılan menüden, iletide istenen özelliğe (örn. OrderID) çift tıklayın. `CorrelatesWith` özelliğini yukarıda kullanılan <xref:System.ServiceModel.Activities.CorrelationHandle> değişkenine ayarlayın.

- [Bağıntı kavramsal belgeleri](../wcf/feature-details/correlation.md)

### <a name="correlation-scenario"></a>Bağıntı senaryosu

Yeni sipariş oluşturma ve işlemdeki mevcut siparişlerin güncelleştirilmesi için bir sipariş işleme iş akışı kullanılır. Bu senaryonun uygulanması, iş akışını <xref:System.ServiceModel.WorkflowServiceHost> ' de barındırmanıza ve mesajlaşma etkinliklerini kullanmanıza gerek duyar. Ayrıca güncelleştirmelerin doğru iş akışında yapıldığından emin olmak için `orderId` göre bağıntı gerektirir.

## <a name="simplified-configuration"></a>Basitleştirilmiş Yapılandırma

WCF yapılandırma şeması karmaşıktır ve kullanıcılara birçok özellik bulmak için çok zor olan özellikler sağlar. [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], WCF kullanıcılarının hizmetlerini aşağıdaki özelliklerle yapılandırmasına yardımcı olmaya odaklandık:

- Açık hizmet başına yapılandırma gereksinimi kaldırılıyor. Hizmetiniz için herhangi bir \<Hizmeti > öğesi yapılandırmazsanız ve hizmetiniz program aracılığıyla herhangi bir uç nokta tanımlamıyorsa, hizmetinize, hizmet temel adresi başına ve hizmetiniz tarafından uygulanan sözleşmeye göre otomatik olarak bir uç nokta kümesi eklenir.

- Kullanıcının WCF bağlamaları ve davranışları için, açık yapılandırma olmayan hizmetlere uygulanacak varsayılan değerleri tanımlamasını sağlar.

- Standart uç noktalar, bir veya daha fazla uç nokta özelliği (adres, bağlama ve anlaşma) için sabit değerlere sahip ve özel özellikleri tanımlamaya izin veren yeniden kullanılabilir, önceden yapılandırılmış uç noktaları tanımlar.

- Son olarak <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>, WCF istemci yapılandırmasının merkezi yönetimini yapmanıza olanak sağlar. bu sayede, uygulamanın etki alanı yükleme zamanından sonra yapılandırmanın seçildiği veya değiştiği senaryolarda faydalıdır.

### <a name="getting-started"></a>Başlarken

- [Bir geliştiricinin WCF 4,0 Kılavuzu](https://docs.microsoft.com/previous-versions/dotnet/articles/ee354381(v=msdn.10))

- [Yapılandırma Kanal Fabrikası](xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601)

- [Standart uç nokta öğesi](xref:System.ServiceModel.Configuration.StandardEndpointElement)

- [.NET Framework 4 ' te hizmet yapılandırması geliştirmeleri](https://docs.microsoft.com/archive/blogs/endpoint/service-configuration-improvements-in-net-4)

- [.NET 4 ' te yaygın kullanıcı hatası: WF/WCF hizmeti yapılandırma adını yanlış yazma](https://docs.microsoft.com/archive/blogs/endpoint/common-user-mistake-in-net-4-mistyping-the-wfwcf-service-configuration-name)

### <a name="simplified-configuration-scenarios"></a>Basitleştirilmiş yapılandırma senaryoları

- Deneyimli bir ASMX geliştiricisi, WCF kullanmaya başlamak istiyor. Bununla birlikte, WCF çok karmaşık gibi görünüyor! Bir yapılandırma dosyasında yazma yapmam gereken tüm bilgiler nelerdir? .NET 4 ' te, hiç bir yapılandırma dosyasına sahip olmasanız da karar verebilirsiniz.

- Mevcut bir WCF Hizmetleri kümesinin yapılandırılması ve korunması çok zordur. Yapılandırma dosyasında, dokunma için son derece tehlikeli XML kodu binlerce satırı vardır. Bu kod miktarını daha yönetilebilir bir şekilde azaltmak için yardım gerekir.

## <a name="data-contract-resolver"></a>Veri sözleşme Çözümleyicisi

.NET 3,5 ' de, bilinen türlerin tasarımında bazı sınırlamalar vardı:

- Serileştirme veya seri durumundan çıkarma sırasında bilinen türleri dinamik olarak ekleme mümkün değildi.

- Serileştiriciler bilinmeyen xsi: Type bilgileriyle ilgilenmiyor.

- Kullanıcıların, tel üzerinde görünmesini istediğiniz xsi: Type türlerini belirtmesi mümkün değildi, örneğin, bir serileştirme örneğinin boyutunu daha küçük hale getirin.

[DataContractResolver](../wcf/samples/datacontractresolver.md) , .NET 4,5 'deki bu sorunları çözer.

### <a name="getting-started"></a>Başlarken

- [Veri sözleşme Çözümleyicisi API 'SI belgeleri](xref:System.Runtime.Serialization.DataContractResolver)

- [Veri sözleşmesi çözümleyicisine giriş](https://docs.microsoft.com/archive/blogs/youssefm/configuring-known-types-dynamically-introducing-the-datacontractresolver)

- Lerinizi

  - [DataContractResolver](../wcf/samples/datacontractresolver.md)

  - [KnownAssemblyAttribute](../wcf/samples/knownassemblyattribute.md)

### <a name="data-contract-resolver-scenarios"></a>Veri sözleşme Çözümleyicisi senaryoları

- Bir hizmette onlarca <xref:System.Runtime.Serialization.KnownTypeAttribute> nesne bildirmek zorunda kalmaktan kaçınıyoruz.

- XML Blobun boyutunu küçültme.

## <a name="flowchart"></a>Akış Çizelgesi

Akış çizelgesi, etki alanı sorunlarını görsel olarak temsil eden iyi bilinen bir paradigdır. .NET 4 ' te sunduğumuz yeni bir denetim akışı stilidir. Akış çizelgesinin çekirdek özelliği, belirli bir zamanda yalnızca bir etkinliğin yürütülmesi olur. Akış çizelgeleri döngüler ve alternatif sonuçlar ifade edebilir, ancak çoklu düğümlerin eşzamanlı olarak yürütülmesini yerel olarak ifade edemez.

### <a name="getting-started"></a>Başlarken

- Visual Studio 2012 ' de bir iş akışı konsol uygulaması oluşturun. İş akışı tasarımcısında bir akış çizelgesi ekleyin.

- Akış çizelgesi özelliği aşağıdaki sınıfları kullanır:

  - <xref:System.Activities.Statements.Flowchart>

  - <xref:System.Activities.Statements.FlowNode>

  - <xref:System.Activities.Statements.FlowDecision>

  - <xref:System.Activities.Statements.FlowStep>

  - <xref:System.Activities.Statements.FlowSwitch%601>

- Lerinizi

  - [TryCatch Kullanarak Akış Çizelgesi Etkinliğine Hata İşleme](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

  - [İşe Alma İşlemi](./samples/hiring-process.md)

- Tasarımcı belgeleri:

  - [Akış Çizelgesi Etkinlik Tasarımcıları](/visualstudio/workflow-designer/flowchart-activity-designers)

### <a name="flowchart-scenarios"></a>Akış çizelgesi senaryoları

Bir akış çizelgesi etkinliği tahmin eden bir oyun uygulamak için kullanılabilir. Tahmin etme oyunu çok basittir: bilgisayar rastgele bir sayı seçer ve oyuncunun bu sayıyı tahmin etmesi yeterlidir. Oyuncu her tahmin gönderdiğinde, bilgisayar bir ipucunu ("daha düşük bir sayı deneyin") gösterir. Oyuncu sayıyı 7 ' den az denemeden bulursa bilgisayardan özel bir kutlama alır. Bu oyun, aşağıdaki yordamsal etkinliklerin birleşimiyle uygulanabilir:

- <xref:System.Activities.Statements.Sequence>

- <xref:System.Activities.Statements.While>

- <xref:System.Activities.Statements.Switch%601>

- <xref:System.Activities.Statements.TryCatch>

- <xref:System.Activities.Statements.Assign%601>

- <xref:System.Activities.Statements.If>

## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a>Yordamsal Etkinlikler (sequence, IF, ForEach, Switch, Assign, DoWhile, while)

Yordamsal etkinlikler, programcılara tanıdık olan kavramları kullanarak sıralı denetim akışını modellemek için bir mekanizma sağlar. Bu etkinlikler geleneksel olarak C# yapılandırılmış programlama dili yapılarını etkinleştirir ve uygun olduğunda, ve Visual Basic gibi ortak yordamsal dillerle dil eşliği sağlar.

### <a name="getting-started"></a>Başlarken

- Visual Studio 2012 ' de bir iş akışı konsol uygulaması oluşturun. İş akışı tasarımcısında yordamsal etkinlikleri ekleyin.

- Lerinizi

  - [İşe Alma İşlemi](./samples/hiring-process.md)

  - [Şirket Satın Alma İşlemi](./samples/corporate-purchase-process.md)

- Tasarımcı belgeleri:

  - [Parallel Etkinlik Tasarımcısı](/visualstudio/workflow-designer/parallel-activity-designer)

  - [ParallelForEach\<T > etkinlik Tasarımcısı](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)

### <a name="procedural-activity-scenarios"></a>Yordamsal etkinlik senaryoları

- <xref:System.Activities.Statements.Parallel>: intranet belge yönetimi sisteminde bir belge onayı iş akışı vardır. Belgelerin intranette yayımlanabilmesi için birkaç departmandaki kişiler tarafından onaylanması gerekir. Onaylar için bir sıra oluşturulmamış; belge "onay bekleniyor" aşamasında olduğunda herhangi bir zamanda meydana gelebilir. Bir Kullanıcı gözden geçirme için bir belge gönderdiğinde doğrudan yönetici, intranet Yöneticisi ve dahili iletişim Yöneticisi tarafından onaylanmalıdır.

- <xref:System.Activities.Statements.ParallelForEach%601>: bir WF uygulaması büyük bir şirketteki Kurumsal satın alım işlemlerini yönetir. Kurumsal kurallar, herhangi bir satın alma işlemini planlamadan önce, üç farklı satıcının değerlemeleri gerektiğini belirler. Satın alma departmanından bir çalışan, şirketin satıcı listesinden üç satıcıyı seçer. Bu satıcılar seçildikten ve bilgilendirdikten sonra şirket ekonomik tekliflerini bekler. Teklifler herhangi bir sırada gelebilir. Bu senaryoyu WF 'de uygulamak için, satıcılarımız topladığımız ve ekonomik tekliflerini isteytiğimiz bir <xref:System.Activities.Statements.ParallelForEach%601> kullanırız. Tüm teklifler toplandıktan sonra, en iyi bir seçilir ve görüntülenir.

## <a name="invokemethod"></a>InvokeMethod

<xref:System.Activities.Statements.InvokeMethod> etkinliği, kapsamdaki nesnelerde veya türlerde ortak yöntemlerin yüklenmesine izin verir. Parametreleri (parametre dizileri dahil) ve genel yöntemleri olmayan ya da olmadan örnek ve statik yöntemlerin çağrılması desteklenir. Ayrıca, yöntemi eşzamanlı ve zaman uyumsuz olarak yürütmeye de olanak tanır.

### <a name="getting-started"></a>Başlarken

- Visual Studio 2012 ' de bir iş akışı konsol uygulaması oluşturun. İş akışı tasarımcısında bir <xref:System.Activities.Statements.InvokeMethod> etkinliği ekleyin ve üzerinde statik ve örnek yöntemlerini yapılandırın.

- Tasarımcı belgeleri: [InvokeMethod etkinlik Tasarımcısı](/visualstudio/workflow-designer/invokemethod-activity-designer)

### <a name="invokemethod-scenarios"></a>InvokeMethod senaryoları

- Kapsamdaki bir nesne içindeki bir yöntemin çağrılması gerekir. Örneğin, bir sözlüğe bir değer eklenmelidir. Sözlük örneğinin Add yöntemi çağrılır ve anahtar ve değer sağlanır.

- Bir yöntemin eski bir CLR nesnesinde çağrılması gerekir. Bu eski sınıfa çağrıyı kaydırmak için özel etkinlik oluşturmak yerine, iş akışı yürütmesi sırasında kapsam içinde ise <xref:System.Activities.Statements.InvokeMethod> kullanılabilir.

## <a name="error-handling-activities"></a>Etkinlikler işlenirken hata oluştu

<xref:System.Activities.Statements.TryCatch> etkinliği, İçerilen etkinliklerin bir kümesinin yürütülmesi sırasında oluşan özel durumları yakalamak için bir mekanizma sağlar (ve Visual Basic ' de C# try/catch yapısına benzer). <xref:System.Activities.Statements.TryCatch> iş akışı düzeyinde özel durum işleme sağlar. İşlenmeyen bir özel durum oluştuğunda, iş akışı iptal edilir ve finally bloğu yürütülmez. Bu davranış ile C#tutarlıdır.

### <a name="getting-started"></a>Başlarken

- Visual Studio 2012 ' de bir iş akışı konsol uygulaması oluşturun. İş akışı tasarımcısında <xref:System.Activities.Statements.TryCatch> etkinliği ekleyin.

- Örnek: [TryCatch kullanarak akış çizelgesi etkinliğinde hata işleme](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

- Tasarımcı belgeleri: [etkinlik tasarımcıları Işlenirken hata oluştu](/visualstudio/workflow-designer/error-handling-activity-designers)

### <a name="error-handling-scenarios"></a>Senaryolar işlenirken hata oluştu

Bir dizi etkinliğin yürütülmesi gerekir ve bir hata oluştuğunda belirli bir mantık yürütülmesi gerekir. Bu hata işleme mantığı sırasında hatanın kurtarılamaz olduğu, özel durumun yeniden oluşturulduğu ve üst etkinliğin (veya konağın) sorun ile ilgili olduğunu tespit eder.

## <a name="pick-activity"></a>Çekme etkinliği

<xref:System.Activities.Statements.Pick> etkinliği WF 'de olay tabanlı denetim akışı modelleme sağlar. <xref:System.Activities.Statements.Pick> her dalın çalıştırılmadan önce belirli bir olayın gerçekleşmesini beklediği birçok dal bulunur. Bu kurulumda <xref:System.Activities.Statements.Pick>, etkinliğin dinlediği olay kümesinden yalnızca birini yürütebileceği bir <xref:System.Activities.Statements.Switch%601> benzer şekilde davranır. Her dal olay odaklı ve oluşan olay, önce karşılık gelen dalı çalıştırır. Diğer tüm dallar olayları dinlemeyi iptal eder ve durdurur.

### <a name="getting-started"></a>Başlarken

- Visual Studio 2012 ' de bir iş akışı konsol uygulaması oluşturun. İş akışı tasarımcısında <xref:System.Activities.Statements.Pick> etkinliği ekleyin.

- Örnek: [çekme etkinliğini kullanma](./samples/using-the-pick-activity.md)

- Tasarımcı belgeleri: [etkinlik tasarımcısını Seç](/visualstudio/workflow-designer/pick-activity-designer)

### <a name="pick-scenario"></a>Seçim senaryosu

Kullanıcıdan giriş yapması istenir. Normal koşullarda geliştirici, bir kullanıcının girişini istemek için <xref:System.Console.ReadLine%2A> gibi bir yöntem çağrısı kullanır. Bu kurulumla ilgili sorun, programın Kullanıcı bir şeyi girene kadar beklediği şeydir. Bu senaryoda, engelleyici bir etkinliğin engelini kaldırmak için zaman aşımı gerekir. Yaygın bir senaryo, belirli bir süre içinde görevin tamamlanmasını gerektiren bir senaryodur. Engelleyici bir etkinliğin zaman aşımına uğraması, çekmenin çok miktarda değer eklediği bir senaryodur.

## <a name="wcf-routing-service"></a>WCF yönlendirme hizmeti

Yönlendirme hizmeti, WCF iletilerinin istemcileriniz ve hizmetleriniz arasında nasıl akmasını denetlemenizi sağlayan bir genel yazılım yönlendiricisi olacak şekilde tasarlanmıştır. Yönlendirme hizmeti, istemcilerinizi, desteklerinizin ve hizmetlerinizin nasıl barındırılacaklarını düşünürken sahip olduğunuz yapılandırmalara göre daha fazla serbestlik sağlayan hizmetlerinize göre ayırmanıza olanak tanır. .NET 3,5 ' de, istemciler ve hizmetler sıkı bir şekilde bağlanmış. bir istemcinin, iletişim kurmasını ve nerede bulunduğunu öğrenmek için gereken tüm hizmetler hakkında bilgi sahibi olması gerekiyordu. Ayrıca, .NET Framework 3,5 ' deki WCF aşağıdaki sınırlamalara sahiptir:

- Hata işleme, bu mantığın istemciye sabit kodlanmış olması gerektiği için karmaşıktır.

- İstemcilerin ve hizmetlerin her zaman aynı bağlamaları kullanması gerekiyordu.

- Hizmetler nadiren iyi bir şekilde, birden çok hizmet arasında seçim yapmak zorunda kalmadan, istemcinin her şeyi uygulayan bir hizmetle iletişim kurmasını kolaylaştırır.

.NET 4 ' teki yönlendirme hizmeti bu sorunların çözülmesine daha kolay hale getirmek için tasarlanmıştır. Yeni yönlendirme hizmeti aşağıdaki özelliklere sahiptir:

1. İçerik tabanlı yönlendirme (<xref:System.ServiceModel.Dispatcher.MessageFilter> nesneleri, gönderilmesi gereken yeri belirleyecek bir ileti inceler.)

2. Protokol köprüleme (aktarım & iletisi)

3. Hata işleme (yönlendirici iletişim özel durumlarını yakalar ve yedekleme uç noktalarına devreder)

4. <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> ve Yönlendirme yapılandırması için dinamik (bellekte) güncelleştirme.

### <a name="getting-started"></a>Başlarken

1. Belgeler: [yönlendirme](../wcf/feature-details/routing.md)

2. Örnekler: [Yönlendirme Hizmetleri &#91;WCF örnekleri&#93; ](../wcf/samples/routing-services.md)

3. Blog: [yönlendirme kuralları!](https://docs.microsoft.com/archive/blogs/RoutingRules/)

### <a name="routing-scenarios"></a>Yönlendirme Senaryoları

Yönlendirme hizmeti aşağıdaki senaryolarda yararlı olur:

- İstemciler, hepsi doğrudan ele almak zorunda kalmadan birden fazla hizmet ile iletişim kurabilir.

- İstemciler, bir istemci isteğinde nereden yönlendirileceğini öğrenmek için ek mantık gerçekleştirebilir

- İstemciyi yeniden düzenlemeye gerek kalmadan, bir istemcinin birden fazla hizmet uygulamasında gerçekleştirdiği işlemleri kaldırır.

- İstemciler ve hizmetler farklı güvenlik ayarlarına sahip farklı bağlamaları okuyabilirler.

- İstemciler, hata veya hizmetlerin KULLANILAMAMASINDAN daha sağlam olması için etkinleştirilebilir.

## <a name="wcf-discovery"></a>WCF Keşfetme

WCF bulma, uygulama altyapınıza bir bulma mekanizması eklemenize olanak tanıyan bir çerçeve teknolojisidir. Bunu, hizmetinizi bulunabilir hale getirmek ve istemcilerinizi Hizmetleri arayacak şekilde yapılandırmak için kullanabilirsiniz. İstemcilerin artık uç noktayla sabit olarak kodlanmış olması gerekmez, böylece uygulamanızın daha sağlam ve hataya dayanıklı olmasını sağlar. Bulma özelliği, uygulamanıza otomatik yapılandırma özellikleri oluşturmaya yönelik mükemmel bir platformdur.

Ürün, WS-Discovery standardının üzerine kurulmuştur. Birlikte çalışabilen, genişletilebilir ve genel olmak üzere tasarlanmıştır. Ürün iki işlem modunu destekler:

1. Yönetilen: ağ üzerinde mevcut hizmetler hakkında bilgili bir varlık olduğunda, istemcileri doğrudan bilgi için sorgular. Bu, Active Directory benzerdir.

2. Geçici: istemcilerin hizmetleri bulmak için çok noktaya yayın iletileri kullanması burada.

Ayrıca, bulma iletileri ağ protokolstik; Bunları, mod gereksinimlerini destekleyen herhangi bir protokolde kullanabilirsiniz. Örneğin, bulma çok noktaya yayın iletileri UDP kanalı veya çok noktaya yayın mesajlaşma 'yı destekleyen başka herhangi bir ağ üzerinden gönderilebilir. Özellik esnekliği ile birleştirilmiş bu tasarım noktaları, bulmayı özel olarak çözümünüze uyarlamanızı sağlar.

### <a name="getting-started"></a>Başlarken

- Belgeler: [WCF bulma](../wcf/feature-details/wcf-discovery.md)

- Örnekler: [bulgu (örnekler)](../wcf/samples/discovery-samples.md)

### <a name="discovery-scenarios"></a>Bulma senaryoları

Bir geliştirici, hizmetim kullanılabilir olduğunda bilinmediği için uç noktalara sabit kod eklemek istemiyor. Bunun yerine, geliştirici çalışma zamanında bir hizmet seçmek istiyor. Uygulamadaki bileşenler arasında daha fazla ayrılmış, sağlamlık ve otomatik yapılandırma gerekir.

## <a name="tracking"></a>İzleme

İş akışı izleme, bir iş akışı örneğinin yürütülmesi hakkında öngörüler sağlar. İzleme olayları iş akışı örneği düzeyindeki bir iş akışından ve iş akışı içindeki etkinliklerin yürütülmesi sırasında yayınlanır. Kayıt iş akışı izleme katılımcısının kayıtları izlemeye abone olmak için iş akışı ana bilgisayarına eklenmesi gerekir. İzleme kayıtları, bir izleme profili kullanılarak filtrelenmiştir. .NET Framework, ETW (Windows için olay Izleme) izleme katılımcısı sağlar ve Machine. config dosyasına temel bir profil yüklenir.

### <a name="getting-started"></a>Başlarken

1. Visual Studio 2010 ' de bir WCF Iş akışı hizmeti uygulama projesi oluşturun. <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> çifti, Tuvalinize başlamak için yerleştirilecek.

2. Web. config dosyasını açın ve profil olmadan bir ETW izleme davranışı ekleyin.

    1. Varsayılan profil kullanılır.

    2. Olay Görüntüleyicisi 'ni açın ve şu düğümdeki analitik kanalı etkinleştirin: **Olay Görüntüleyicisi**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama sunucusu-uygulamalar**. **Analitik** öğesine sağ tıklayın ve **günlüğü etkinleştir**' i seçin.

    3. İş akışı hizmetini çalıştırın.

    4. Olay Görüntüleyicisi 'nde iş akışı izleme olaylarını gözlemleyin.

3. Örnekler: [izleme](./samples/tracking.md)

4. Kavramsal belgeler: [Iş akışı izleme ve izleme](workflow-tracking-and-tracing.md)

## <a name="sql-workflow-instance-store"></a>SQL İş Akışı Örnek Deposu

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, örnek deposunun SQL Server tabanlı bir uygulamasıdır. Örnek deposu, çalışan bir örneğin durumunu, bu örneği yüklemek ve sürdürülmesi için gereken tüm verilerle birlikte depolar. Hizmet ana bilgisayarı, örnek deposuna iş akışı devam ederse örnek durumunu kaydetmesini söyler ve bu örneğe bir ileti geldiğinde ya da bir gecikme etkinliğinin süresinin dolacağını örnek deposuna yükler.

### <a name="getting-started"></a>Başlarken

1. Visual Studio 2012 ' de örtük veya açık bir <xref:System.Activities.Statements.Persist> etkinlik içeren bir Iş akışı oluşturun. <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> davranışını iş akışı hizmeti konağına ekleyin. Bu, kod veya uygulama yapılandırma dosyasında yapılabilir.

2. Örnekler: [Kalıcılık](/previous-versions/dotnet/netframework-4.0/dd699769(v%3dvs.100))

3. Kavramsal belgeler: [SQL Iş akışı örnek deposu](sql-workflow-instance-store.md).
