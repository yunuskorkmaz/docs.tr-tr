---
title: HTTP Doğrulama Kanalı
ms.date: 03/30/2017
ms.assetid: 469f3056-5ef2-4753-8acf-b574d23d83cf
ms.openlocfilehash: d83f3aa590471aa3d83b8f7bd1464ec1e6e106fc
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43559549"
---
# <a name="http-acknowledgement-channel"></a>HTTP Doğrulama Kanalı
HTTP doğrulama kanalı, tek yönlü Mesajlaşma modeli, Onayla veya Reddet gelen iletiler için bir hizmet verme otomatik olarak bir bildirim alındığında göndermek yerine değişen katmanlı bir kanal örneğidir. İletinin işlenmesi iş düzeyinde garantisi yapabilirsiniz kadar HTTP doğrulama kanalı gecikme bildirim hizmetine de sağlar.  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.ServiceModel.Channels.ReceiveContext>, Katmanlı kanal örnek (HTTP doğrulama kanalı).  
  
## <a name="discussion"></a>Tartışma  
 HTTP doğrulama kanalı uygulayan <xref:System.ServiceModel.Channels.ReceiveContext> HTTP istek-yanıt Mesajlaşma modeli Gecikmeli bildirim tek yönlü bir desenle şekillendirmek için. Bu yeni deseni kullanarak bir hizmet ileti işleme ileti işleme tamamlanana veya bir hata iletisi biçiminde bir HTTP istemci gönderebilirsiniz kadar istemciyi engellemeden bir HTTP Tamam durum kodu 200 biçiminde bir bildirim göndererek emin olabilirsiniz İç sunucu hatası durum kodu 500. Örneğin, bir hizmet kuyruğa bir ileti yazdıktan sonra bir bildirim gönderin ve sonra zaman uyumsuz ileti işleme devam edin. Hizmetten bir bildirim aldığı kadar her ileti yeniden gönderilen, bu senaryoda, bir istemci iletileri en az bir kez hizmeti tarafından işlenen toplam yararlandığından emin. Bir hizmeti hızlı zaman uyumsuz ileti işleme garantileri, herhangi bir ileti HTTP üzerinden işleme gerektiriyorsa, Not sonra <xref:System.ServiceModel.Channels.OneWayBindingElement> daha uygun bir seçimdir.  
  
 <xref:System.ServiceModel.Channels.ReceiveContext> iletinin ileti hizmeti işleme olup olmadığını belirlenir yerinde tutarak için kullanılır. Tam çağrı yaparak başarıyla iletiyi işlemek için bir hizmet özelliği gösterilir <xref:System.ServiceModel.Channels.ReceiveContext> bir HTTP Tamam durum kodu ve hizmet ileti olup olmadığını işleyebilir gönderen nesne çağırarak belirtilir <xref:System.ServiceModel.Channels.ReceiveContext>'s `Abandon` metodunda <xref:System.ServiceModel.Channels.ReceiveContext> gönderen bir HTTP iç sunucu hatası durum kodu nesnesi.  
  
 Bu örnekte, istemci bir çalışan kimliği göndererek işleme bilgi ister Hizmet uç alınan çalışan kimliği 50'den büyükse hizmeti bir HTTP durum kodunu 500 (iç sunucu hatası) istemciye geri gönderir, aksi takdirde, işleme başarıyla yapılabilir ve bir HTTP durum kodu 200 (gönderdiği varsayılır Başarılı) istemciye.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Açık [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yönetici ayrıcalıklarına sahip.  
  
2.  Açık **HttpAckChannel** çözüm.  
  
3.  Yeni bir örneğini Başlat **hizmet** projeye sağ tıklayarak proje **Çözüm Gezgini**, seçerek **hata ayıklama**, **yeni örnek Başlat** bağlam menüsünden.  
  
4.  Yeni bir örneğini Başlat **istemci** projeye sağ tıklayarak proje **Çözüm Gezgini**, seçerek **hata ayıklama**, ve **yeni örnek Başlat** bağlam menüsünden.  
  
5.  Hizmet başlatıldıktan sonra istemci hizmete ileti göndermek için istemci penceresinde ENTER tuşuna basın.  
  
6.  İlk iletinin hizmette işlenir ve bir HTTP Tamam durumu kodu istemciye geri gönderir.  
  
7.  İkinci bir ileti başarısız olur ve bir HTTP iç sunucu hatası durum kodu oluşturan istemciye, gönderir bir <xref:System.ServiceModel.CommunicationException> istemci üzerinde.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpAckChannel`
