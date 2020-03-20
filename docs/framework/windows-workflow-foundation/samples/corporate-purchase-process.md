---
title: Şirket Satın Alma İşlemi
ms.date: 03/30/2017
ms.assetid: a5e57336-4290-41ea-936d-435593d97055
ms.openlocfilehash: 93cfc3546fc312f046c4a5e1dd63dfb357f143c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182867"
---
# <a name="corporate-purchase-process"></a>Şirket Satın Alma İşlemi
Bu örnek, otomatik en iyi teklif seçimi ile çok temel bir Teklif İsteği (RFP) tabanlı satın alma işleminin nasıl oluşturulacak olduğunu gösterir. İşlemi <xref:System.Activities.Statements.Parallel>temsil <xref:System.Activities.Statements.ParallelForEach%601>eden <xref:System.Activities.Statements.ForEach%601> bir iş akışı oluşturmak için özel bir etkinliği ve özel etkinliği birleştirir.

 Bu örnek, işlemle farklı katılımcılar (özgün istektecisi veya belirli bir satıcı olarak) etkileşime izin veren ASP.NET bir istemci uygulaması içerir.

## <a name="requirements"></a>Gereksinimler

- Görsel Stüdyo 2012.

- [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].

## <a name="demonstrates"></a>Gösteriler

- Özel etkinlikler.

- Faaliyetlerin bileşimi.

- Yer im -leri.

- Kalıcılık.

- Şematize sebat.

- Izleme.

- Izleme.

- Farklı [!INCLUDE[wf1](../../../../includes/wf1-md.md)] istemcilerde barındırma (ASP.NET Web uygulamaları ve WinForms uygulamaları).

> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\PurchaseProcess`  
  
## <a name="description-of-the-process"></a>Sürecin Açıklaması  
 Bu örnek, genel bir şirket için satıcılardan teklif toplamak için bir Windows İş Akışı Temeli (WF) programının uygulanmasını gösterir.  
  
1. X şirketinin bir çalışanı bir Teklif İsteği (RFP) oluşturur.  
  
    1. RFP başlığında ve açıklamasında çalışan türleri.  
  
    2. Çalışan, teklif sunmak için davet etmek istedikleri satıcıları seçer.  
  
2. Çalışan teklifi gönderir.  
  
    1. İş akışının bir örneği oluşturulur.  
  
    2. İş akışı, tüm satıcıların tekliflerini göndermesini bekliyor.  
  
3. Tüm teklifler alındıktan sonra, iş akışı alınan tüm teklifleri yineler ve en iyisini seçer.  
  
    1. Her satıcının bir itibarı vardır (bu örnek itibar listesini VendorRepository.cs olarak depolar).  
  
    2. Teklifin toplam değeri (Satıcı tarafından yazılan değer) * (Satıcının kayıtlı itibarı) / 100 tarafından belirlenir.  
  
4. Orijinal istekte bulundurucu tüm gönderilen teklifleri görebilir. En iyi teklif raporda özel bir bölümde sunulur.  
  
## <a name="process-definition"></a>İşlem Tanımı  
 Örneğin temel mantığı, her <xref:System.Activities.Statements.ParallelForEach%601> satıcıdan gelen teklifleri bekleyen (yer işareti oluşturan özel bir etkinlik kullanarak) ve satıcı teklifini RFP <xref:System.Activities.Statements.InvokeMethod> (bir etkinlik kullanarak) olarak kaydeden bir etkinlik kullanır.  
  
 Örnek daha sonra, düzeltilmiş değeri `RfpRepository`(bir <xref:System.Activities.Statements.Assign> etkinlik ve <xref:System.Activities.Expressions> etkinlik kullanarak) hesaplayarak, alınan tüm teklifleri yineler ve ayarlanan değer önceki en iyi tekliften daha <xref:System.Activities.Statements.If> iyiyse, yeni değeri en iyi teklif (kullanarak ve <xref:System.Activities.Statements.Assign> etkinlikler) olarak atar.  
  
## <a name="projects-in-this-sample"></a>Bu Örnekteki Projeler  
 Bu örnek aşağıdaki projeleri içerir.  
  
|Project|Açıklama|  
|-------------|-----------------|  
|Common|İşlem içinde kullanılan varlık nesneleri (Teklif İsteği, Satıcı ve Satıcı Teklifi).|  
|WfDefinition|Satınalma işlemi iş akışının örneklerini oluşturmak ve kullanmak için istemci uygulamaları tarafından kullanılan işlemin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] (program olarak) ve ana bilgisayar ()`PurchaseProcessHost`tanımı.|  
|Webclient|Kullanıcıların satın alma işleminin örneklerini oluşturmasına ve bu sürece katılmasını sağlayan ASP.NET istemci uygulaması. İş akışı altyapısıyla etkileşimkurmak için özel olarak oluşturulmuş bir ana bilgisayar kullanır.|  
|WinFormsClient|Kullanıcıların satın alma işleminin örneklerini oluşturmasına ve katılmasına olanak tanıyan bir Windows Forms istemci uygulaması. İş akışı altyapısıyla etkileşimkurmak için özel olarak oluşturulmuş bir ana bilgisayar kullanır.|  
  
### <a name="wfdefinition"></a>WfDefinition  
 Aşağıdaki tablo, WfDefinition projesindeki en önemli dosyaların açıklamasını içerir.  
  
|Dosya|Açıklama|  
|----------|-----------------|  
|IPurchaseProcessHost.cs|İş akışının ana bilgisayarı için arayüz.|  
|PurchaseProcessHost.cs|İş akışı için bir ana bilgisayar uygulaması. Ana bilgisayar iş akışı çalışma zamanının ayrıntılarını özetler ve iş akışı örneklerini yüklemek, `PurchaseProcess` çalıştırmak ve bunlarla etkileşimde bulunan tüm istemci uygulamalarında kullanılır.|  
|PurchaseProcessWorkflow.cs|Satınalma Süreci iş akışının tanımını içeren bir <xref:System.Activities.Activity>etkinlik (türetilmiştir).<br /><br /> Etkinlik kitaplığından <xref:System.Activities.Activity> [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] varolan özel etkinlikleri ve etkinlikleri birleştirerek işlevsellik ten türeyen etkinlikler. Bu etkinlikleri bir araya getirmek, özel işlevsellik oluşturmanın en temel yoludur.|  
|WaitForVendorProposal.cs|Bu özel etkinlik, <xref:System.Activities.NativeActivity> teklifi gönderirken satıcı tarafından daha sonra devam ettirilmesi gereken adlandırılmış bir yer imi oluşturur.<br /><br /> Türeyen etkinlikler <xref:System.Activities.NativeActivity>, bu tür, <xref:System.Activities.CodeActivity>geçersiz bırakarak <xref:System.Activities.NativeActivity.Execute%2A>zorunlu işlevsellik oluşturmak, ama aynı zamanda <xref:System.Activities.ActivityContext> `Execute` yönteme geçirilen alır aracılığıyla iş akışı çalışma süresinin tüm işlevselliği erişebilirsin. Bu bağlamda, alt etkinlikleri zamanlama ve iptal etme, kalıcı olmayan bölgeler (çalışma zamanının atomik hareketler gibi iş akışı verilerini sürdürmediği <xref:System.Activities.Bookmark> yürütme blokları) ve nesneler (duraklatılmış iş akışlarını devam ettirme işlemleri) için destek bulunur.|  
|TrackingParticipant.cs|Tüm <xref:System.Activities.Tracking.TrackingParticipant> izleme olaylarını alan ve bunları bir metin dosyasına kaydeden a.<br /><br /> İzleme katılımcıları, iş akışı örneğine Uzantı olarak eklenir.|  
|XmlWorkflowInstanceStore.cs|İş <xref:System.Runtime.DurableInstancing.InstanceStore> akışı uygulamalarını XML dosyalarına kaydeden bir özel.|  
|XmlPersistenceParticipant.cs|Bir <xref:System.Activities.Persistence.PersistenceParticipant> XML dosyasına teklif isteği örneği kaydeden bir özel.|  
|AsyncResult.cs / CompletedAsyncResult.cs|Kalıcılık bileşenlerinde asenkron deseni uygulamak için yardımcı sınıflar.|  
  
### <a name="common"></a>Common  
 Aşağıdaki tabloortak projedeki en önemli sınıfların açıklamasını içerir.  
  
|Sınıf|Açıklama|  
|-----------|-----------------|  
|Satıcı|Teklif İsteği'nde teklif gönderen satıcı.|  
|İstek Önerisi|Teklif talebi (RFP), satıcıların belirli bir mal veya hizmetle ilgili öneriler sunmaları için bir davettir.|  
|Satıcı Önerisi|Bir satıcı tarafından somut bir RFP'ye gönderilen bir öneri.|  
|SatıcıRepository|Satıcıların deposu. Bu uygulama, Satıcı örnekleri ve bu örnekleri açığa çıkarmak için yöntemlerin bellek içi bir koleksiyon içerir.|  
|RfpRepozitory|Teklif Taleplerinin deposu. Bu uygulama, şematize kalıcılık tarafından oluşturulan Teklif İstekleri XML dosyasını sorgulamak için XML Linq kullanır içerir. |  
|IOHelper|Bu sınıf, G/Ç ile ilgili tüm sorunları (klasörler, yollar vb.) işler.|  
  
### <a name="web-client"></a>Web İstemcisi  
 Aşağıdaki tablo, Web İstemci projesindeki en önemli Web sayfalarının açıklamasını içerir.  
  
|Dosya|Açıklama|  
|-|-|  
|CreateRfp.aspx|Yeni bir Teklif İsteği oluşturur ve gönderir.|  
|Default.aspx|Tüm etkin ve tamamlanmış Teklif İsteklerini gösterir.|  
|GetVendorProposal.aspx|Somut bir Teklif Talebi bir satıcıdan bir teklif alır. Bu sayfa yalnızca satıcılar tarafından kullanılır.|  
|ShowRfp.aspx|Teklif Talebi yle ilgili tüm bilgileri (alınan teklifler, tarihler, değerler ve diğer bilgiler) gösterin. Bu sayfa yalnızca Teklif İsteği'nin yaratıcısı tarafından kullanılır.|  
  
### <a name="winforms-client"></a>WinForms İstemci  
 Aşağıdaki tablo, Form kazan projesindeki en önemli formların açıklamasını içerir.  
  
|Form|Açıklama|  
|-|-|  
|Yeni Rfp|Yeni bir Teklif İsteği oluşturur ve gönderir.|  
|ShowProposals|Tüm etkin ve bitmiş Teklif İsteklerini gösterin. **Not:**  Teklif İsteği'ni oluşturduktan veya değiştirdikten sonra bu ekranda değişiklikleri görmek için UI'deki **Yenile** düğmesini tıklatmanız gerekebilir.|  
|Teklif Gönder|Somut bir Teklif Talebi'nde bir satıcıdan teklif alın. Bu pencere yalnızca satıcılar tarafından kullanılır.|  
|GörünümRfp|Teklif Talebi yle ilgili tüm bilgileri (alınan teklifler, tarihler, değerler ve diğer bilgiler) gösterin. Bu pencere yalnızca Teklif İsteği'nin yaratıcısı tarafından kullanılır.|  
  
### <a name="persistence-files"></a>Kalıcılık Dosyaları  
 Aşağıdaki tablo, kalıcılık sağlayıcısı (`XmlPersistenceProvider`) tarafından oluşturulan dosyaların geçerli sistemin geçici klasörünün (kullanarak) <xref:System.IO.Path.GetTempPath%2A>yolunda bulunduğunu gösterir. İzleme dosyası geçerli yürütme yolunda oluşturulur.  
  
|Dosya Adı|Açıklama|Yol|  
|-|-|-|  
|rfps.xml|Tüm etkin ve bitmiş Teklif İstekleri ile XML dosyası.|<xref:System.IO.Path.GetTempPath%2A>|  
|[instanceid]|Bu dosya, bir iş akışı örneği yle ilgili tüm bilgileri içerir.<br /><br /> Bu dosya şematize kalıcılık uygulaması (XmlPersistenceProvider persistenceKatılımcı) tarafından oluşturulur.|<xref:System.IO.Path.GetTempPath%2A>|  
|[instanceId].tracking|Somut bir örnek içinde meydana gelen tüm olayları içeren bir metin dosyası.<br /><br /> Bu dosya TrackingParticipant tarafından oluşturulur.|<xref:System.IO.Path.GetTempPath%2A>|  
|Satın AlmaProcess.Tracing.TraceLog.txt|App.config veya Web.config dosyalarındaki yapılandırma parametrelerini temel alarak iş akışı tarafından oluşturulan izleme dosyası.|Geçerli yürütme yolu|  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1. Visual Studio 2010'u kullanarak PurchaseProcess.sln çözüm dosyasını açın.  
  
2. Web İstemci projesini yürütmek için **Çözüm Gezgini'ni** açın ve **Web İstemci** projesini sağ tıklatın. **Başlangıç Projesi olarak Ayarla'yı**seçin.  
  
3. WinForms İstemci projesini yürütmek için **Solution Explorer'ı** açın ve **WinForms İstemci** projesini sağ tıklatın. **Başlangıç Projesi olarak Ayarla'yı**seçin.  
  
4. Çözümü oluşturmak için CTRL+SHIFT+B tuşuna basın.  
  
5. Çözümü çalıştırmak için CTRL+F5 tuşuna basın.  
  
### <a name="web-client-options"></a>Web İstemci Seçenekleri  
  
- **Yeni bir RFP Oluşturma**: Yeni bir Teklif İsteği (RFP) oluşturur ve Satınalma Süreci iş akışını başlatır.  
  
- **Yenileme**: Ana penceredeki Etkin ve Bitmiş RFP'lerin listesini yeniler.  
  
- **Görünüm**: Varolan bir RFP'nin içeriğini gösterir. Satıcılar tekliflerini sunabilir (davet edilirse veya RFP tamamlanmadıysa).  
  
- Görünüm As: Kullanıcı, etkin RFP'ler ızgarasında Görünüm'de istenen katılımcıyı açılan kutu **olarak** seçerek farklı kimlikler kullanarak RFP'ye erişebilir.  
  
### <a name="winforms-client-options"></a>WinForms İstemci Seçenekleri  
  
- **RFP Oluştur**: Yeni bir Teklif İsteği (RFP) oluşturur ve Satınalma Süreci iş akışını başlatır.  
  
- **Yenileme**: Ana penceredeki Etkin ve Bitmiş RFP'lerin listesini yeniler.  
  
- **RFP'yi Görüntüle**: Varolan bir RFP'nin içeriğini gösterir. Satıcılar tekliflerini sunabilir (davet edilirse veya RFP tamamlanmadıysa)  
  
- **As'a Bağlan**: Kullanıcı, etkin RFP ızgarasında Görünüm'de istenen katılımcıyı açılan kutu **olarak** seçerek farklı kimlikler kullanarak RFP'ye erişebilir.
