---
title: HTTP Doğrulama Kanalı
ms.date: 03/30/2017
ms.assetid: 469f3056-5ef2-4753-8acf-b574d23d83cf
ms.openlocfilehash: c56b2fbe9d0bac3143ee7d234fd36a75f7b8071c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502838"
---
# <a name="http-acknowledgement-channel"></a>HTTP Doğrulama Kanalı
HTTP doğrulama kanalı tek yönlü Mesajlaşma düzeni, onaylayabilir veya gelen iletileri reddetmek bir hizmet veren otomatik olarak bir bildirim alındığında göndermek yerine değişiklikleri katmanlı bir kanal örneğidir. İleti işleme, iş düzeyi garantisi yapabilirsiniz kadar HTTP doğrulama kanalı gecikme bildirim hizmete de sağlar.  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.ServiceModel.Channels.ReceiveContext>, Katmanlı kanal örnek (HTTP doğrulama kanalı).  
  
## <a name="discussion"></a>Tartışma  
 HTTP doğrulama kanalı uygulayan <xref:System.ServiceModel.Channels.ReceiveContext> Gecikmeli bildirim ile tek yönlü bir desenle HTTP istek-yanıt Mesajlaşma düzeni yeniden şekillendirmek için. Bu yeni desenini kullanarak, bir hizmet ileti işleme ileti işleme tamamlanana veya bir hata iletisi biçiminde bir HTTP istemci gönderebilirsiniz kadar istemci engellenmeden bir HTTP Tamam durum kodu 200 biçiminde bir bildirim göndererek emin olabilirsiniz İç sunucu hatası durum kodu 500. Örneğin, bir hizmet bir sıraya bir ileti yazdıktan sonra bir bildirim göndermek ve iletisini zaman uyumsuz olarak işleme devam. Bir bildirim hizmetinden alınan kadar her ileti yeniden göndermeden, bu senaryoda, bir istemci kendi iletileri en az bir kez hizmeti tarafından işlenen gösterilmeyeceği. Bir hizmeti hızlı zaman uyumsuz ileti işleme garantileri, herhangi bir iletisi HTTP üzerinden işleme gerektiriyorsa, Not sonra <xref:System.ServiceModel.Channels.OneWayBindingElement> daha uygun bir seçimdir.  
  
 <xref:System.ServiceModel.Channels.ReceiveContext> iletinin ileti hizmeti işleme alınacak belirlenir yerinde tutarken için kullanılır. Bir hizmeti başarıyla ileti işleme yeteneği üzerinde tam çağrılarak gösterilen <xref:System.ServiceModel.Channels.ReceiveContext> gönderdiği Tamam HTTP durum kodu ve hizmet iletisi olup olmadığını işleyebilir nesne çağırarak belirtilir <xref:System.ServiceModel.Channels.ReceiveContext>'s `Abandon` yöntemini <xref:System.ServiceModel.Channels.ReceiveContext> bir HTTP iç sunucu hatası durum kodu gönderir nesnesi.  
  
 Bu örnekte, bir çalışan kimliği göndererek işleme bilgileri istemci istekleri Hizmet uç alınan çalışan kimliği 50'den büyükse hizmeti bir HTTP durum kodu 500 (Dahili Sunucu hatası) istemciye geri gönderir, aksi takdirde bu işlem başarıyla yapılabilir ve bir HTTP durum kodu 200 (gönderir varsayılır Başarılı) istemciye.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Açık [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yönetici ayrıcalıklarına sahip.  
  
2.  Açık **HttpAckChannel** çözümü.  
  
3.  Yeni bir örneğini Başlat **hizmet** sağ tıklayarak projede Proje **Çözüm Gezgini**, seçerek **hata ayıklama**, **başlangıç yeni örnek** ve bağlam menüsünden.  
  
4.  Yeni bir örneğini Başlat **istemci** sağ tıklayarak projede Proje **Çözüm Gezgini**, seçerek **hata ayıklama**, ve **başlangıç yeni örnek** ve bağlam menüsünden.  
  
5.  Hizmet başladıktan sonra hizmete bir ileti göndermek istemci izin vermek için istemci penceresinde ENTER tuşuna basın.  
  
6.  İlk iletinin hizmette işlenir ve bir HTTP Tamam durum kodu istemciye geri gönderir.  
  
7.  İkinci bir ileti başarısız olur ve bir HTTP iç sunucu hatası durum kodu oluşturan istemciye, gönderen bir <xref:System.ServiceModel.CommunicationException> istemci üzerinde.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpAckChannel`
