---
title: Şirket Satın Alma İşlemi
ms.date: 03/30/2017
ms.assetid: a5e57336-4290-41ea-936d-435593d97055
ms.openlocfilehash: eaf77fc8b1697d0e337d8c4823ca2184cb9c545c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665932"
---
# <a name="corporate-purchase-process"></a>Şirket Satın Alma İşlemi
Bu örnek çok basit bir istek teklifleri (RFP) tabanlı satın alma işlemi için en iyi otomatik öneri seçimiyle oluşturma işlemini gösterir. Bunu birleştirir <xref:System.Activities.Statements.Parallel>, <xref:System.Activities.Statements.ParallelForEach%601>, ve <xref:System.Activities.Statements.ForEach%601> ve işlemini temsil eden bir iş akışı oluşturmak için özel bir etkinlik.

 Bu örnek içeren bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] farklı katılımcı (olarak, özgün istek sahibine veya belirli bir satıcının) işlemiyle etkileşim sağlayan istemci uygulaması.

## <a name="requirements"></a>Gereksinimler

- Visual Studio 2012.

- [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].

## <a name="demonstrates"></a>Gösteriler

- Özel etkinlikler.

- Etkinlik oluşturma.

- Yer işaretleri.

- Kalıcılık.

- Şema Kalıcılık.

- İzleme.

- İzleme.

- Barındırma [!INCLUDE[wf1](../../../../includes/wf1-md.md)] farklı istemcileri ([!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web uygulamaları ve WinForms uygulamaları).

> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\PurchaseProcess`  
  
## <a name="description-of-the-process"></a>İşlem açıklaması  
 Bu örnek, genel bir şirket için satıcılardan tekliflerini toplamak için bir Windows Workflow Foundation (WF) programı uygulanışı gösterilmektedir.  
  
1. Şirket x bir çalışan bir istek teklifi (RFP) oluşturur.  
  
    1. Çalışan türü RFP başlık ve açıklama.  
  
    2. Çalışan tekliflerini göndermek için davet etmek istediği satıcıları seçer.  
  
2. Çalışan teklif gönderir.  
  
    1. İş akışı örneği oluşturulur.  
  
    2. İş akışı, teklifler göndermek tüm satıcılar için bekliyor.  
  
3. Tüm teklifleri alındıktan sonra iş akışı alınan tüm teklifleri yinelenir ve en iyisi seçer.  
  
    1. Her bir satıcı, (Bu örnekte saygınlığı liste içinde VendorRepository.cs depolar) bir üretme ününe sahip.  
  
    2. Teklif toplam değeri (satıcı tarafından yazdığınız değer) tarafından belirlenir * (satıcı saygınlığı kaydedildiği) / 100.  
  
4. Özgün istek sahibine gönderilen tüm teklifleri görebilirsiniz. Özel bir rapor bölümünde en iyi teklifi sunulur.  
  
## <a name="process-definition"></a>İşlem tanımı  
 Örnek çekirdek mantığını kullanır bir <xref:System.Activities.Statements.ParallelForEach%601> teklifler (bir yer işareti oluşturur ve özel bir etkinlik kullanılarak), her satıcının bekler etkinlik ve satıcı teklifi bir RFP kaydeder (kullanarak bir <xref:System.Activities.Statements.InvokeMethod> etkinliği).  
  
 Örnek daha sonra tüm depolanan alınan teklifler gezinir `RfpRepository`, ayarlanan değer hesaplama (kullanarak bir <xref:System.Activities.Statements.Assign> etkinlik ve <xref:System.Activities.Expressions> etkinlikler), ve ayarlanan değer, önceki en iyi teklif iyidir en iyi öneri olarak yeni değeri atar (kullanarak <xref:System.Activities.Statements.If> ve <xref:System.Activities.Statements.Assign> etkinlikler).  
  
## <a name="projects-in-this-sample"></a>Bu örnekte projeleri  
 Bu örnek aşağıdaki projeleri içerir.  
  
|Project|Açıklama|  
|-------------|-----------------|  
|Common|' % S'işlemi (istek teklifi, satıcı ve satıcı teklifi) içinde kullanılan varlık nesnesi.|  
|WfDefinition|İşlem tanımı (olarak bir [!INCLUDE[wf1](../../../../includes/wf1-md.md)] programı) ve ana bilgisayar (`PurchaseProcessHost`) oluşturma ve satın alma işlemi iş akışı örneği kullanmak için istemci uygulamaları tarafından kullanılır.|  
|WebClient|Bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] oluşturmak ve satın alma işlemi durumlarda katılmak kullanıcılara istemci uygulaması. Özel olarak oluşturulmuş bir konak, bir iş akışı altyapısı ile etkileşim kurmak için kullanır.|  
|WinFormsClient|Kullanıcılara oluşturmak ve satın alma işlemi durumlarda katılmak bir Windows Forms istemci uygulaması. Özel olarak oluşturulmuş bir konak, bir iş akışı altyapısı ile etkileşim kurmak için kullanır.|  
  
### <a name="wfdefinition"></a>WfDefinition  
 Aşağıdaki tabloda en önemli WfDefinition proje dosyalarında açıklamasını içerir.  
  
|Dosya|Açıklama|  
|----------|-----------------|  
|IPurchaseProcessHost.cs|İş akışı ana bilgisayarı için arabirim.|  
|PurchaseProcessHost.cs|İş akışı için bir ana bilgisayar uygulaması. Konak iş akışı çalışma zamanı ilişkin ayrıntıları özetleyen ve tüm istemci uygulamaları yüklemek için çalıştırın ve etkileşim için kullanılan `PurchaseProcess` iş akışı örnekleri.|  
|PurchaseProcessWorkflow.cs|Satın alma işlemi iş akışının tanımını içeren bir etkinlik (türetilen <xref:System.Activities.Activity>).<br /><br /> Öğesinden türetilen etkinlikleri <xref:System.Activities.Activity> işlevselliği varolan özel birleştirerek oluşturan etkinlikler ve etkinlikler [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] etkinlik kitaplığı. Bu etkinlikler derleyerek, özel işlevler oluşturmak için en temel bir yoludur.|  
|WaitForVendorProposal.cs|Bu özel etkinlik türetildiği <xref:System.Activities.NativeActivity> ve daha sonra bir satıcı tarafından teklif gönderirken hata ayıklanan devam adlandırılmış bir yer işareti oluşturur.<br /><br /> Öğesinden türetilen etkinlikleri <xref:System.Activities.NativeActivity>, ister, türetilen <xref:System.Activities.CodeActivity>, geçersiz kılarak kesinlik temelli işlevi oluşturma <xref:System.Activities.NativeActivity.Execute%2A>, ancak tüm işlevleri iş akışı çalışma zamanı erişimi de <xref:System.Activities.ActivityContext> alır yöntemlere geçirilen `Execute` yöntemi. Bu bağlam zamanlamak için destek içerir ve bölgeleri (yürütme blokları boyunca çalışma zamanı kalıcı iş akışının veri gibi atomik işlemler dahilinde), etkinlikleri, ayarlama Hayır kalıcı alt iptal ediliyor ve <xref:System.Activities.Bookmark> nesneleri (tutamaçları sürdürme iş akışları duraklatıldı).|  
|TrackingParticipant.cs|A <xref:System.Activities.Tracking.TrackingParticipant> tüm izleme olaylarını alır ve bunları bir metin dosyasına kaydeder.<br /><br /> İzleme katılımcıları iş akışı örneğinin uzantıları olarak eklenir.|  
|XmlWorkflowInstanceStore.cs|Özel bir <xref:System.Runtime.DurableInstancing.InstanceStore> , XML dosyaları için iş akışı uygulamaları kaydeder.|  
|XmlPersistenceParticipant.cs|Özel bir <xref:System.Activities.Persistence.PersistenceParticipant> , istek teklifiyle ilgili bir örneği bir XML dosyasına kaydeder.|  
|AsyncResult.cs / CompletedAsyncResult.cs|Kalıcılık bileşenlerinde zaman uyumsuz desen uygulamak için yardımcı sınıfları.|  
  
### <a name="common"></a>Common  
 Aşağıdaki tabloda, ortak proje en önemli sınıflarda açıklamasını içerir.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|Satıcı|Bir satıcı teklifleri için bir istek teklifleri gönderir.|  
|RequestForProposal|Teklifleri (RFP) için bir özel ticari veya hizmet tekliflerini göndermek satıcıları için davetiye isteğidir.|  
|VendorProposal|Somut RFP bir satıcı tarafından gönderilen bir teklif.|  
|VendorRepository|Satıcıların deposu. Bu uygulama, satıcı ve bu örnekleri gösterme yöntemleri örnekleri bir bellek içi koleksiyonu içerir.|  
|RfpRepository|İstek teklifleri için depo. Bu uygulama kullanımları içeren LINQ to XML şema Kalıcılık tarafından oluşturulan teklifi XML dosyasını istekleri sorgulamak için. |  
|IOHelper|Bu sınıf işler tüm miyim/Ç ile ilgili sorunlar (klasörleri, yollar ve benzeri.)|  
  
### <a name="web-client"></a>Web İstemcisi  
 Aşağıdaki tabloda, en önemli Web sayfaları Web istemci projesindeki açıklamasını içerir.  
  
|Dosya|Açıklama|  
|-|-|  
|CreateRfp.aspx|Oluşturur ve teklifleri için yeni bir istek gönderir.|  
|Default.aspx|Tüm etkin ve tamamlanmış istekler için önerileri gösterir.|  
|GetVendorProposal.aspx|Bir teklif somut isteğinde bir satıcının önerileri alır. Bu sayfa yalnızca satıcıları tarafından kullanılır.|  
|ShowRfp.aspx|Bir istek teklifleri (alınan teklifleri, tarihler, değerleri ve diğer bilgileri) için ilgili tüm bilgileri gösterir. Bu sayfa yalnızca teklifi isteğin oluşturucusu tarafından kullanılır.|  
  
### <a name="winforms-client"></a>WinForms istemci  
 Aşağıdaki tabloda, Win form projenin en önemli formlarında açıklamasını içerir.  
  
|Form|Açıklama|  
|-|-|  
|NewRfp|Oluşturur ve teklifleri için yeni bir istek gönderir.|  
|ShowProposals|Tüm etkin ve tamamlanan isteklerin teklifleri için gösterilir. **Not:**  Tıklaymanız gerekebilir **Yenile** oluşturduğunuzda veya bir istek teklifi için sonra bu ekrandaki değişiklikleri görmek için kullanıcı arabiriminde düğmesi.|  
|SubmitProposal|Bir teklif somut isteğinde bir satıcının önerileri alın. Bu pencere, yalnızca satıcıları tarafından kullanılır.|  
|ViewRfp|Bir istek teklifleri (alınan teklifleri, tarihler, değerleri ve diğer bilgileri) için ilgili tüm bilgileri gösterir. Bu pencere, yalnızca önerileri isteğin oluşturucusu tarafından kullanılır.|  
  
### <a name="persistence-files"></a>Kalıcılık dosyaları  
 Aşağıdaki tablo kalıcı bir sağlayıcı tarafından oluşturulan dosyalar gösterir (`XmlPersistenceProvider`) geçerli sistemin geçici klasör yolunda yer alır (kullanarak <xref:System.IO.Path.GetTempPath%2A>). Geçerli yürütme yolu izleme dosyası oluşturulur.  
  
|Dosya Adı|Açıklama|Yol|  
|-|-|-|  
|rfps.XML|Teklifleri için tüm etkin ve tamamlanmış istekleri olan XML dosyası.|<xref:System.IO.Path.GetTempPath%2A>|  
|[InstanceId]|Bu dosya, bir iş akışı örneği ilgili tüm bilgileri içerir.<br /><br /> Bu dosya, şema Kalıcılık uygulaması (PersistenceParticipant XmlPersistenceProvider içinde) tarafından oluşturulur.|<xref:System.IO.Path.GetTempPath%2A>|  
|[InstanceId] .tracking|Somut bir örneği içinde gerçekleşen tüm olayları içeren bir metin dosyası.<br /><br /> Bu dosya TrackingParticipant tarafından oluşturulur.|<xref:System.IO.Path.GetTempPath%2A>|  
|PurchaseProcess.Tracing.TraceLog.txt|App.config veya Web.config dosyalarında yapılandırma parametreleri temel iş akışı tarafından oluşturulan izleme dosyası.|Geçerli yürütme yolu|  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1. Visual Studio 2010 kullanarak PurchaseProcess.sln çözüm dosyasını açın.  
  
2. Web istemcisi projesi yürütmek için açık **Çözüm Gezgini** sağ tıklayın ve **Web istemcisi** proje. Seçin **başlangıç projesi olarak ayarla**.  
  
3. WinForms istemci projesi yürütmek için açık **Çözüm Gezgini** sağ tıklayın ve **WinForms istemci** proje. Seçin **başlangıç projesi olarak ayarla**.  
  
4. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
5. Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
### <a name="web-client-options"></a>Web istemci seçenekleri  
  
- **Yeni bir RFP oluşturma**: Yeni bir istek teklifleri (RFP) oluşturur ve satın alma işlemi iş akışı başlatır.  
  
- **Yenileme**: Etkin ve ana penceresinde tamamlanmış RFPs listesini yeniler.  
  
- **Görünüm**: Mevcut bir RFP içeriğini gösterir. Satıcılar, kendi önerileri gönderebildiği (davet varsa veya RFP bitmeyen).  
  
- Farklı görüntüle: Kullanıcının istenen Katılımcısı seçerek farklı kimliklerle RFP erişebildiği **olarak görüntülemek** birleşik giriş kutusu etkin RFPs kılavuzunda.  
  
### <a name="winforms-client-options"></a>WinForms istemci seçenekleri  
  
- **RFP oluşturma**: Yeni bir istek teklifleri (RFP) oluşturur ve satın alma işlemi iş akışı başlatır.  
  
- **Yenileme**: Etkin ve ana penceresinde tamamlanmış RFPs listesini yeniler.  
  
- **Görüntüleme RFP**: Mevcut bir RFP içeriğini gösterir. Satıcılar, kendi önerileri gönderebildiği (davet varsa veya RFP bitmeyen)  
  
- **Farklı Bağlan**: Kullanıcının istenen Katılımcısı seçerek farklı kimliklerle RFP erişebildiği **olarak görüntülemek** birleşik giriş kutusu etkin RFPs kılavuzunda.
