---
title: Şirket Satın Alma İşlemi
ms.date: 03/30/2017
ms.assetid: a5e57336-4290-41ea-936d-435593d97055
ms.openlocfilehash: 95fa421ed44cf2d930fb4b80979d1b8bd9fda5ed
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715217"
---
# <a name="corporate-purchase-process"></a>Şirket Satın Alma İşlemi
Bu örnek, otomatik en iyi teklif seçimine sahip teklifler (RFP) tabanlı satın alma süreci için çok temel bir Istek oluşturmayı gösterir. İşlemi temsil eden bir iş akışı oluşturmak için <xref:System.Activities.Statements.Parallel>, <xref:System.Activities.Statements.ParallelForEach%601>ve <xref:System.Activities.Statements.ForEach%601> ve özel bir etkinliği birleştirir.

 Bu örnek, işlem ile farklı katılımcılar (özgün istek sahibi veya belirli bir satıcı olarak) ile etkileşime izin veren bir ASP.NET istemci uygulaması içerir.

## <a name="requirements"></a>Gereksinimler

- Visual Studio 2012.

- [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].

## <a name="demonstrates"></a>Gösterir

- Özel etkinlikler.

- Etkinliklerin oluşturulması.

- Leriniz.

- Kalıcılığı.

- Şema sürekliliği.

- İzleniyor.

- İzlerken.

- Farklı istemcilerde [!INCLUDE[wf1](../../../../includes/wf1-md.md)] barındırma (ASP.NET Web uygulamaları ve WinForms uygulamaları).

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\PurchaseProcess`  
  
## <a name="description-of-the-process"></a>Işlemin açıklaması  
 Bu örnek, bir genel şirket için satıcılardan teklif toplamak üzere Windows Workflow Foundation (WF) programının bir uygulamasını gösterir.  
  
1. Şirket X çalışanı bir teklif (RFP) Isteği oluşturur.  
  
    1. RFP başlığında ve açıklamasında çalışan türleri.  
  
    2. Çalışan, teklifleri göndermek için davet etmek istediği satıcıları seçer.  
  
2. Çalışan teklifi gönderir.  
  
    1. İş akışının bir örneği oluşturulur.  
  
    2. İş akışı tüm satıcıların tekliflerini göndermesini bekliyor.  
  
3. Tüm teklifler alındıktan sonra, iş akışı tüm alınan tekliflerle yinelenir ve en iyi olanı seçer.  
  
    1. Her satıcının bir saygınlığı vardır (Bu örnek, VendorRepository.cs içinde saygınlık listesini depolar).  
  
    2. Teklifin toplam değeri tarafından belirlenir (satıcı tarafından yazılan değer) * (satıcının kayıtlı saygınlığı)/100.  
  
4. Özgün istek sahibi gönderilen tüm teklifleri görebilir. En iyi teklif, raporun özel bir bölümünde sunulur.  
  
## <a name="process-definition"></a>İşlem tanımı  
 Örneğin Çekirdek mantığı her bir satıcıdan teklifleri bekleyen bir <xref:System.Activities.Statements.ParallelForEach%601> etkinlik kullanır (bir yer işareti oluşturan özel bir etkinlik kullanarak) ve satıcı teklifini bir RFP (<xref:System.Activities.Statements.InvokeMethod> etkinliği kullanarak) olarak kaydeder.  
  
 Örnek daha sonra, `RfpRepository`depolanan alınan tekliflerin tümünde yinelenir, düzeltilen değeri (bir <xref:System.Activities.Statements.Assign> etkinliği ve <xref:System.Activities.Expressions> etkinliklerini kullanarak) hesaplıyor ve ayarlanmış değer önceki en iyi tekliften daha iyidir, yeni değeri en iyi teklif olarak atar (<xref:System.Activities.Statements.If> ve <xref:System.Activities.Statements.Assign> etkinliklerini kullanarak).  
  
## <a name="projects-in-this-sample"></a>Bu örnekteki projeler  
 Bu örnek aşağıdaki projeleri içerir.  
  
|{1&gt;Proje (Project)&lt;1}|Açıklama|  
|-------------|-----------------|  
|Birçok|İşlem içinde kullanılan varlık nesneleri (teklif talebi, satıcı ve satıcı teklifi).|  
|WfDefinition|Satın alma işlemi iş akışının örneklerini oluşturmak ve kullanmak için istemci uygulamaları tarafından kullanılan işlemin tanımı ([!INCLUDE[wf1](../../../../includes/wf1-md.md)] program olarak) ve ana bilgisayar (`PurchaseProcessHost`).|  
|WebClient|Kullanıcıların satın alma sürecinin örneklerini oluşturmalarına ve bu örneklere katılmasına izin veren bir ASP.NET istemci uygulaması. İş akışı altyapısıyla etkileşim kurmak için özel oluşturulmuş bir konak kullanır.|  
|WinFormsClient|Kullanıcıların satın alma sürecinin örneklerini oluşturmalarına ve bu örneklere katılmasına izin veren bir Windows Forms istemci uygulaması. İş akışı altyapısıyla etkileşim kurmak için özel oluşturulmuş bir konak kullanır.|  
  
### <a name="wfdefinition"></a>WfDefinition  
 Aşağıdaki tabloda WfDefinition projesindeki en önemli dosyaların açıklaması yer almaktadır.  
  
|Dosya|Açıklama|  
|----------|-----------------|  
|IPurchaseProcessHost.cs|İş akışının ana bilgisayarı için arabirim.|  
|PurchaseProcessHost.cs|İş akışı için bir konak uygulama. Konak, iş akışı çalışma zamanının ayrıntılarını soyutlar ve `PurchaseProcess` iş akışı örnekleri yüklemek, çalıştırmak ve bunlarla etkileşim kurmak için tüm istemci uygulamalarında kullanılır.|  
|PurchaseProcessWorkflow.cs|Satın alma Işlemi iş akışının tanımını içeren bir etkinlik (<xref:System.Activities.Activity>türetilir).<br /><br /> [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] etkinlik kitaplığından var olan özel etkinlikleri ve etkinlikleri derleyerek <xref:System.Activities.Activity> oluşturma işlevlerinden türeten etkinlikler. Bu etkinlikleri montaj, özel işlevler oluşturmanın en temel yoludur.|  
|WaitForVendorProposal.cs|Bu özel etkinlik <xref:System.Activities.NativeActivity> türetilir ve teklif gönderilirken daha sonra bir satıcı tarafından sürdürülmesi gereken adlandırılmış bir yer işareti oluşturur.<br /><br /> <xref:System.Activities.CodeActivity>türeten türetilmiş olanlar gibi <xref:System.Activities.NativeActivity>' den türetilen etkinlikler, <xref:System.Activities.NativeActivity.Execute%2A>geçersiz kılarak zorunlu işlevler oluşturur, ancak aynı zamanda `Execute` yöntemine geçirilen <xref:System.Activities.ActivityContext> aracılığıyla iş akışı çalışma zamanının tüm işlevlerine erişime sahip olur. Bu bağlam, alt etkinlikleri zamanlama ve iptal etme desteği içerir. kalıcı olmayan bölgeler (çalışma zamanının Atomik işlemler içinde olduğu gibi iş akışının verilerini kalıcı olmadığı yürütme blokları) ve <xref:System.Activities.Bookmark> nesneleri (duraklatılmış iş akışlarına devam ettirmek için tutamaçlar).|  
|TrackingParticipant.cs|Tüm izleme olaylarını alan ve bunları bir metin dosyasına kaydeden bir <xref:System.Activities.Tracking.TrackingParticipant>.<br /><br /> İzleme katılımcıları, iş akışı örneğine uzantı olarak eklenir.|  
|XmlWorkflowInstanceStore.cs|İş akışı uygulamalarını XML dosyalarına kaydeden özel bir <xref:System.Runtime.DurableInstancing.InstanceStore>.|  
|XmlPersistenceParticipant.cs|Teklif için bir istek örneğini bir XML dosyasına kaydeden özel bir <xref:System.Activities.Persistence.PersistenceParticipant>.|  
|AsyncResult.cs/CompletedAsyncResult.cs|Kalıcılık bileşenlerinde zaman uyumsuz model uygulama yardımcı sınıfları.|  
  
### <a name="common"></a>Birçok  
 Aşağıdaki tabloda ortak projedeki en önemli sınıfların açıklaması yer almaktadır.  
  
|Sınıf|Açıklama|  
|-----------|-----------------|  
|Satıcı|Teklifler için bir Istek için teklifleri gönderen bir satıcı.|  
|Requestforteklifle|Teklifler için bir istek (RFP), satıcıların belirli bir emtia veya hizmete teklif göndermesine yönelik bir davetdir.|  
|Vendorteklifi|Bir satıcıdan somut RFP 'ye gönderilen teklif.|  
|VendorRepository|Satıcıların deposu. Bu uygulama, satıcı örneklerinin ve bu örnekleri ortaya çıkarmak için yöntemlerin bellek içi bir koleksiyonunu içerir.|  
|RfpRepository|Teklifler için Istek deposu. Bu uygulama, şema sürekliliği tarafından oluşturulan teklife yönelik Isteklerin XML dosyasını sorgulamak için LINQ to XML kullanır. |  
|IOHelper|Bu sınıf, tüm g/ç ile ilgili sorunları (klasörler, yollar vb.) işler.|  
  
### <a name="web-client"></a>Web İstemcisi  
 Aşağıdaki tabloda, Web Istemcisi projesindeki en önemli Web sayfalarının açıklaması yer almaktadır.  
  
|Dosya|Açıklama|  
|-|-|  
|CreateRfp. aspx|Teklifler için yeni bir Istek oluşturur ve gönderir.|  
|Default. aspx|Teklifler için tüm etkin ve tamamlanmış Istekleri gösterir.|  
|Getvendorteklife. aspx|Teklifler için somut bir Istekteki bir satıcıdan teklif alır. Bu sayfa yalnızca satıcılar tarafından kullanılır.|  
|ShowRfp. aspx|Teklifler için bir Istek (alınan teklifler, tarihler, değerler ve diğer bilgiler) hakkındaki tüm bilgileri gösterir. Bu sayfa yalnızca teklif Isteği Oluşturucu tarafından kullanılır.|  
  
### <a name="winforms-client"></a>WinForms Istemcisi  
 Aşağıdaki tabloda, Win Forms projesindeki en önemli formların açıklaması yer almaktadır.  
  
|Form|Açıklama|  
|-|-|  
|NewRfp|Teklifler için yeni bir Istek oluşturur ve gönderir.|  
|Showtekliflerin|Teklifler için tüm etkin ve tamamlanmış Istekleri gösterin. **Note:**  Teklif talebi oluşturduktan veya değiştirdikten sonra bu ekrandaki değişiklikleri görmek için Kullanıcı arabirimindeki **Yenile** düğmesine tıklamanız gerekebilir.|  
|Submitteklifle|Teklifler için somut bir Istekteki bir satıcıdan teklif alın. Bu pencere yalnızca satıcılar tarafından kullanılır.|  
|ViewRfp|Teklifler için bir Istek (alınan teklifler, tarihler, değerler ve diğer bilgiler) hakkındaki tüm bilgileri gösterir. Bu pencere yalnızca tekliflerin Isteği için Oluşturucu tarafından kullanılır.|  
  
### <a name="persistence-files"></a>Kalıcılık dosyaları  
 Aşağıdaki tabloda, kalıcılık sağlayıcısı tarafından oluşturulan dosyaların (`XmlPersistenceProvider`) geçerli sistemin geçici klasörünün yolunda (<xref:System.IO.Path.GetTempPath%2A>kullanılarak) bulunduğu gösterilmektedir. İzleme dosyası geçerli yürütme yolunda oluşturulur.  
  
|Dosya Adı|Açıklama|Yol|  
|-|-|-|  
|RFPs. xml|Teklifler için tüm etkin ve tamamlanmış Istekleri içeren XML dosyası.|<xref:System.IO.Path.GetTempPath%2A>|  
|InstanceId|Bu dosya, bir iş akışı örneğiyle ilgili tüm bilgileri içerir.<br /><br /> Bu dosya, şema sürekliliği uygulama (XmlPersistenceProvider içinde Persistencekatılımcı) tarafından oluşturulur.|<xref:System.IO.Path.GetTempPath%2A>|  
|[InstanceId]. izleme|Somut bir örnek içinde oluşan tüm olayları içeren bir metin dosyası.<br /><br /> Bu dosya Trackingkatılımcı tarafından oluşturulmuştur.|<xref:System.IO.Path.GetTempPath%2A>|  
|PurchaseProcess. Tracing. TraceLog. txt|App. config veya Web. config dosyalarındaki yapılandırma parametrelerine göre iş akışı tarafından oluşturulan izleme dosyası.|Geçerli yürütme yolu|  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1. Visual Studio 2010 kullanarak PurchaseProcess. sln çözüm dosyasını açın.  
  
2. Web Istemcisi projesini yürütmek için **Çözüm Gezgini** açın ve **Web istemcisi** projesine sağ tıklayın. **Başlangıç projesi olarak ayarla**' yı seçin.  
  
3. WinForms Istemci projesini yürütmek için **Çözüm Gezgini** açın ve **WinForms istemci** projesine sağ tıklayın. **Başlangıç projesi olarak ayarla**' yı seçin.  
  
4. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
5. Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
### <a name="web-client-options"></a>Web Istemcisi seçenekleri  
  
- **Yeni BIR RFP oluştur**: Teklifler (RFP) için yeni bir istek oluşturur ve bir satın alma işlemi iş akışı başlatır.  
  
- **Yenile**: Ana penceredeki etkin ve tamamlanmış RFPs listesini yeniler.  
  
- **Görüntüle**: var olan bir RFP içeriğini gösterir. Satıcılar, tekliflerini (davet edilen veya RFP bitmez) gönderebilir.  
  
- Farklı görüntüle: Kullanıcı, etkin RFPs **kılavuzundaki Birleşik giriş** kutusunda bulunan istediğiniz katılımcıyı seçerek, farklı kimlikler kullanarak RFP 'ye erişebilir.  
  
### <a name="winforms-client-options"></a>WinForms Istemci seçenekleri  
  
- **Oluşturma RFP**: Teklifler (RFP) için yeni bir istek oluşturur ve bir satın alma işlemi iş akışı başlatır.  
  
- **Yenile**: Ana penceredeki etkin ve tamamlanmış RFPs listesini yeniler.  
  
- **Görünümü RFP**: var olan bir RFP içeriğini gösterir. Satıcılar, tekliflerini (davet edilen veya RFP bitmez) gönderebilir  
  
- **Farklı Bağlan**: Kullanıcı, etkin RFPs **kılavuzundaki Birleşik giriş** kutusunda bulunan istediğiniz katılımcıyı seçerek, farklı kimlikler kullanarak RFP 'ye erişebilir.
