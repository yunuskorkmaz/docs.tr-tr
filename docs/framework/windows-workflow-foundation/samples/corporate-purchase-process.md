---
title: "Şirket satın alma işlemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5e57336-4290-41ea-936d-435593d97055
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ea3814fe187fb721771b6ce09a5fa0ff95558852
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corporate-purchase-process"></a>Şirket satın alma işlemi
Bu örnek ile otomatik en iyi Teklif seçimi tekliflerinin temel Projeyi satın alma işlemi çok basit bir istek oluşturulacağını gösterir. Bunu birleştirir <xref:System.Activities.Statements.Parallel>, <xref:System.Activities.Statements.ParallelForEach%601>, ve <xref:System.Activities.Statements.ForEach%601> ve işlemini temsil eden bir iş akışı oluşturmak için özel bir etkinlik.  
  
 Bu örnek içeren bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] (olarak, özgün istek sahibi veya belirli bir satıcının) farklı katılımcı olarak işlemle etkileşim sağlayan istemci uygulaması.  
  
## <a name="requirements"></a>Gereksinimler  
  
-   [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
-   [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
## <a name="demonstrates"></a>Gösteriler  
  
-   Özel etkinlikler.  
  
-   Birleşim etkinlikler.  
  
-   Yer işaretleri.  
  
-   Kalıcılık.  
  
-   Şema haline getirilmiş Kalıcılık.  
  
-   İzleme.  
  
-   İzleme.  
  
-   Barındırma [!INCLUDE[wf1](../../../../includes/wf1-md.md)] farklı istemcileri ([!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web uygulamaları ve WinForms uygulamaları).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\PurchaseProcess`  
  
## <a name="description-of-the-process"></a>İşleminin açıklaması  
 Bu örnek uygulaması gösteren bir [!INCLUDE[wf](../../../../includes/wf-md.md)] genel bir şirket için satıcılardan teklifleri toplamak için program.  
  
1.  Şirket x bir çalışan bir istek teklifi Projeyi için oluşturur.  
  
    1.  RFP başlığı ve açıklamayı çalışan türler.  
  
    2.  Çalışan teklifleri göndermek için davet etmek istediği satıcılar seçer.  
  
2.  Çalışan teklif gönderir.  
  
    1.  İş akışı örneği oluşturulur.  
  
    2.  İş akışı kendi teklifleri göndermek tüm satıcılar için bekliyor.  
  
3.  Tüm teklifleri alındıktan sonra iş akışı tüm alınan teklifleri tekrarlanan ve en iyisi seçer.  
  
    1.  Her satıcının (Bu örnek saygınlığı listenin içinde VendorRepository.cs depoladığı yer) itibar sahiptir.  
  
    2.  Teklif toplam değeri (satıcı tarafından yazdığınız değer) tarafından belirlenen * (satıcı saygınlığı kayıtlı) / 100.  
  
4.  Özgün istek sahibinin gönderilen tüm teklifleri görebilirsiniz. En iyi teklif özel rapor bölümünde sunulur.  
  
## <a name="process-definition"></a>İşlem tanımı  
 Örnek çekirdek mantığını kullanır bir <xref:System.Activities.Statements.ParallelForEach%601> (yer işareti oluşturur özel bir aktivite kullanarak), her satıcının teklifleri bekler etkinliği ve bir RFP satıcı teklifi kaydeder (kullanarak bir <xref:System.Activities.Statements.InvokeMethod> etkinlik).  
  
 Örnek sonra tüm depolanan alınan teklifleri dolaşır `RfpRepository`, ayarlanan değer hesaplama (kullanarak bir <xref:System.Activities.Statements.Assign> etkinlik ve <xref:System.Activities.Expressions> etkinlikleri), ve ayarlanan değer önceki en iyi teklif iyi ise Yeni değer olarak en iyi teklif atar (kullanarak <xref:System.Activities.Statements.If> ve <xref:System.Activities.Statements.Assign> etkinlikleri).  
  
## <a name="projects-in-this-sample"></a>Bu örnek proje  
 Bu örnek aşağıdaki projeleri içerir.  
  
|Project|Açıklama|  
|-------------|-----------------|  
|Ortak|(İstek teklifi, satıcı ve satıcı teklifi) işlemi içinde kullanılan varlık nesnesi.|  
|WfDefinition|İşlem tanımını (olarak bir [!INCLUDE[wf1](../../../../includes/wf1-md.md)] program) ve ana bilgisayar (`PurchaseProcessHost`) oluşturma ve satın alma işlemi iş akışı örneği kullanmak için istemci uygulamaları tarafından kullanılır.|  
|WebClient|Bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] istemci uygulaması, kullanıcıların oluşturun ve satın alma işlemini durumlarda katılmasına olanak sağlar. İş akışı altyapısı ile etkileşim kurmak için özel olarak oluşturulmuş bir ana bilgisayar kullanır.|  
|WinFormsClient|Oluşturma ve satın alma işlemini durumlarda katılmak kullanıcılara bir Windows Forms istemci uygulaması. İş akışı altyapısı ile etkileşim kurmak için özel olarak oluşturulmuş bir ana bilgisayar kullanır.|  
  
### <a name="wfdefinition"></a>WfDefinition  
 Aşağıdaki tabloda en önemli WfDefinition proje dosyalarında açıklamasını içerir.  
  
|Dosya|Açıklama|  
|----------|-----------------|  
|IPurchaseProcessHost.cs|İş akışı ana bilgisayar için arabirim.|  
|PurchaseProcessHost.cs|İş akışı için bir ana bilgisayar uygulaması. Ana bilgisayar iş akışı çalışma zamanı ayrıntılarını soyutlar ve tüm istemci uygulamaları yüklemek için çalıştırmak ve etkileşim için kullanılan `PurchaseProcess` iş akışı örnekleri.|  
|PurchaseProcessWorkflow.cs|Satın alma işlemi iş akışı tanımını içeren bir etkinlik (türetilen <xref:System.Activities.Activity>).<br /><br /> Öğesinden türetilen etkinlikleri <xref:System.Activities.Activity> varolan özel birleştirerek işlevselliği oluşturan etkinlikler ve etkinlikten [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] etkinlik kitaplığı. Bu etkinlikler birleştirme, özel işlevsellik oluşturmak için en temel bir yoludur.|  
|WaitForVendorProposal.cs|Bu özel etkinlik türetilen <xref:System.Activities.NativeActivity> ve daha sonra bir satıcı tarafından teklif gönderirken devam ettirilebilir gerekir adlandırılmış bir yer işareti oluşturur.<br /><br /> Öğesinden türetilen etkinlikleri <xref:System.Activities.NativeActivity>, ister öğesinden türetilen o <xref:System.Activities.CodeActivity>, kesinlik temelli işlevselliğe kılarak oluşturmak <xref:System.Activities.NativeActivity.Execute%2A>, ancak aynı zamanda tüm iş akışı çalışma zamanı işlevselliğini erişimi <xref:System.Activities.ActivityContext> alır içine aktarılan `Execute` yöntemi. Bu bağlamda zamanlamak için desteğe sahiptir ve ayarlama etkinlikleri, Hayır kalıcı alt iptal etme (sırasında çalışma zamanı kalmayan iş akışının veri gibi atomik işlemlerin içinden yürütme engeller) bölgeleri ve <xref:System.Activities.Bookmark> nesneleri (işleç için sürdürme iş akışları duraklatıldı).|  
|TrackingParticipant.cs|A <xref:System.Activities.Tracking.TrackingParticipant> tüm izleme olaylarını alır ve bunları bir metin dosyasına kaydeder.<br /><br /> İzleme katılımcıları iş akışı örneğine uzantıları olarak eklenir.|  
|XmlWorkflowInstanceStore.cs|Özel bir <xref:System.Runtime.DurableInstancing.InstanceStore> iş akışı uygulamaları XML dosyalarına kaydeder.|  
|XmlPersistenceParticipant.cs|Özel bir <xref:System.Activities.Persistence.PersistenceParticipant> , istek teklifiyle ilgili örneği bir XML dosyasına kaydeder.|  
|AsyncResult.cs / CompletedAsyncResult.cs|Kalıcılık bileşenlerinde zaman uyumsuz desen uygulamak için yardımcı sınıfları.|  
  
### <a name="common"></a>Ortak  
 Aşağıdaki tabloda ortak proje en önemli sınıflarda açıklamasını içerir.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|Satıcı|Teklifleri için bir istek tekliflerini gönderen bir satıcı.|  
|RequestForProposal|Bir istek teklifleri (RFP) için belirli Emtia veya hizmet teklifleri göndermek üzere satıcılar için bir davet ' dir.|  
|VendorProposal|Somut RFP bir satıcı tarafından gönderilen bir teklif.|  
|VendorRepository|Satıcılar deposu. Bu uygulama, satıcı ve bu örnekleri gösterme yöntemleri örnekleri bir bellek içi koleksiyonunu içerir.|  
|RfpRepository|İstek teklifleri için depo. Bu uygulama kullanımlar içeren LINQ-XML istekleri XML dosyası şema haline getirilmiş Kalıcılık tarafından oluşturulan teklifi için sorgulanamıyor. Bu sınıf uygulayan [System.Runtime.Persistence.IDataViewMapper](https://msdn.microsoft.com/library/system.runtime.persistence.idataviewmapper(v=vs.110).aspx).|  
|IOHelper|Bu sınıf işler tüm g/Ç ile ilgili sorunları (klasörler, yolları ve benzeri.)|  
  
### <a name="web-client"></a>Web İstemcisi  
 Aşağıdaki tabloda en önemli Web sayfaları Web istemcisi projesinde açıklamasını içerir.  
  
|Dosya|Açıklama|  
|-|-|  
|CreateRfp.aspx|Oluşturur ve önerileri için yeni bir istek gönderir.|  
|Default.aspx|Tüm etkin ve tamamlanmış istekleri teklifleri için gösterir.|  
|GetVendorProposal.aspx|Bir teklif somut isteğinde bir satıcıdan önerileri alır. Bu sayfa yalnızca satıcıları tarafından kullanılır.|  
|ShowRfp.aspx|Bir istek teklifleri (alınan teklifleri, tarihler, değerler ve diğer bilgileri) için ilgili tüm bilgileri gösterir. Bu sayfa yalnızca teklifi isteği oluşturucusu tarafından kullanılır.|  
  
### <a name="winforms-client"></a>WinForms istemci  
 Aşağıdaki tabloda Win Forms proje en önemli formlarında açıklamasını içerir.  
  
|Form|Açıklama|  
|-|-|  
|NewRfp|Oluşturur ve önerileri için yeni bir istek gönderir.|  
|ShowProposals|Tüm etkin ve tamamlanmış istekleri teklifleri için gösterir. **Not:** seçeneğini gerekebilir **yenileme** oluşturmak veya Teklif talebi değiştirdikten sonra o ekranı değişiklikleri görmek için kullanıcı arabiriminde düğmesi.|  
|SubmitProposal|Bir teklif somut isteğinde bir satıcıdan tekliflerini alın. Bu pencere, yalnızca satıcıları tarafından kullanılır.|  
|ViewRfp|Bir istek teklifleri (alınan teklifleri, tarihler, değerler ve diğer bilgileri) için ilgili tüm bilgileri gösterir. Bu pencere, yalnızca teklifleri için istek oluşturucusu tarafından kullanılır.|  
  
### <a name="persistence-files"></a>Kalıcılık dosyaları  
 Aşağıdaki tabloda Kalıcılık sağlayıcı tarafından oluşturulan dosyalar gösterir (`XmlPersistenceProvider`) geçerli sistemin geçici klasörü yolunda bulunur (kullanarak <xref:System.IO.Path.GetTempPath%2A>). İzleme dosyası geçerli yürütme yolunda oluşturulur.  
  
|Dosya Adı|Açıklama|Yol|  
|-|-|-|  
|rfps.XML|Tüm etkin ve tamamlanmış istekleri olan XML dosyası teklifleri için.|<xref:System.IO.Path.GetTempPath%2A>|  
|[InstanceId]|Bu dosya bir iş akışı örneği ilgili tüm bilgileri içerir.<br /><br /> Bu dosya, şema haline getirilmiş Kalıcılık uygulaması (PersistenceParticipant XmlPersistenceProvider içinde) tarafından oluşturulur.|<xref:System.IO.Path.GetTempPath%2A>|  
|[InstanceId] .tracking|Bir metin dosyası somut örneği içinde gerçekleşen tüm olaylar ile.<br /><br /> Bu dosya TrackingParticipant tarafından oluşturulur.|<xref:System.IO.Path.GetTempPath%2A>|  
|PurchaseProcess.Tracing.TraceLog.txt|App.config veya Web.config dosyalarında yapılandırma parametreleri temel iş akışı tarafından oluşturulan izleme dosyası.|Geçerli yürütme yolu|  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], PurchaseProcess.sln çözüm dosyasını açın.  
  
2.  Web istemcisi proje yürütmek için açık **Çözüm Gezgini** ve sağ **Web istemcisi** projesi. Seçin **başlangıç projesi olarak ayarla**.  
  
3.  WinForms istemci projesi yürütmek için açık **Çözüm Gezgini** ve sağ **WinForms istemci** projesi. Seçin **başlangıç projesi olarak ayarla**.  
  
4.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
5.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
### <a name="web-client-options"></a>Web istemci seçenekleri  
  
-   **Yeni bir RFP oluşturmak**: yeni bir istek tekliflerini Projeyi için oluşturur ve satın alma işlemi iş akışını başlatır.  
  
-   **Yenileme**: etkin ve tamamlandı RFPs ana penceresinde listesini yeniler.  
  
-   **Görünüm**: varolan bir RFP içeriğini gösterir. Satıcılar kendi teklifleri gönder (davet varsa veya RFP bitmeyen).  
  
-   Görünüm olarak: İstenen Katılımcısı seçerek kullanarak farklı kimlikleri RFP kullanıcının erişebildiği **olarak görüntülemek** birleşik giriş kutusu etkin RFPs kılavuzunda.  
  
### <a name="winforms-client-options"></a>WinForms istemci seçenekleri  
  
-   **RFP oluşturmak**: yeni bir istek tekliflerini Projeyi için oluşturur ve satın alma işlemi iş akışını başlatır.  
  
-   **Yenileme**: etkin ve tamamlandı RFPs ana penceresinde listesini yeniler.  
  
-   **Görüntüleme RFP**: varolan bir RFP içeriğini gösterir. Satıcılar kendi teklifleri gönder (davet varsa veya RFP bitmeyen)  
  
-   **Connect olarak**: kullanıcının istenen Katılımcısı seçerek kullanarak farklı kimlikleri RFP erişebildiği **olarak görüntülemek** birleşik giriş kutusu etkin RFPs kılavuzunda.  
  
## <a name="see-also"></a>Ayrıca Bkz.
