---
title: Güvenilir Güvenlik Profili
ms.date: 03/30/2017
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
ms.openlocfilehash: ee94dc5be2c50f9e383a42d435996b2fd35df4a4
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716497"
---
# <a name="reliable-secure-profile"></a>Güvenilir Güvenlik Profili
Bu örnek, WCF ve [güvenilir güvenli profilin](https://go.microsoft.com/fwlink/?LinkId=178140) (rsp) nasıl oluşturulacağını gösterir. Bu örnek, güvenilir mesajlaşma ile birlikte oluşturabileceğiniz bir [bağlantı oluşturma](https://go.microsoft.com/fwlink/?LinkId=178141) kanalının uygulanmasını ve isteğe bağlı olarak RSP belirtimine dayalı güvenilir bir güvenli bağlama oluşturmak için güvenli bir kanal oluşturmayı gösterir.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a>Tartışma  
 Bu örnekte, güvenilir bir zaman uyumsuz çift yönlü ileti değişimi senaryosu gösterilmektedir. Hizmetin çift yönlü bir anlaşması vardır ve istemci çift yönlü geri çağırma sözleşmesini uygular. İstemci, ayrı bir bağlantıda bir yanıt beklenildiği bir hizmete istek başlatır. İstek iletisi güvenilir bir şekilde gönderilir. İstemci sonunda bir dinleme uç noktası açmak istemiyor. Bu nedenle, hizmetin yanıtı bu ' bağlantı oluştur ' isteğinin arka kanalına geri göndermek için ' bağlantı oluştur ' isteklerini bu hizmette yoklar. Bu örnek, istemci bir dinleme uç noktası (ve güvenlik duvarı özel durumu oluşturma) olmadan HTTP üzerinden güvenli bir güvenilir çift yönlü iletişimin nasıl yapılacağını gösterir.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. **ReliableSecureProfile** çözümünü açın.  
  
2. **Çözüm Gezgini**' de **hizmet** projesine sağ tıklayın, **Hata Ayıkla**' yı seçin, bağlam menüsünden **Yeni örnek Başlat** ' ı seçin. Bu, hizmet ana bilgisayarını başlatır.  
  
3. **Çözüm Gezgini**' de **istemci** projesine sağ tıklayın, **Hata Ayıkla**' yı seçin, bağlam menüsünden **Yeni örnek Başlat** ' ı seçin. Bu, istemciyi başlatır.  
  
4. İstemci konsolu penceresinde istemde herhangi bir dizeyi yazın ve ENTER ' a tıklayın. Bu, giriş dizesini hizmete gönderir ve bu dizenin bir karmasını hesaplar.  
  
5. İstemci konsolu penceresinde sonucu görüntülemek için, hizmet çift yönlü geri çağırma sözleşmesi işlemini geri aradığında istemci penceresinde sonucu görüntüleyin. Hizmette, verilerin işlenmesi için uzun süredir çalışan bir işlemin benzetimini yapmak üzere bilerek bir gecikme vardır.  
  
6. HTTP trafiğini izleme (Ağ İzleyicisi, Fiddler vb. gibi çevrimiçi ağ izleme araçlarından herhangi biri tarafından), istemci ile hizmet arasında güvenilir güvenli profille gösterildiği gibi bir iletişim sırasının ve istemcinin nasıl hizmeti ' bağlantı oluştur ' istekleri ile yoklar. Hizmet işlenen yanıtı geri göndermeye hazırsa, sonuçları geri göndermek için son ' bağlantı oluştur ' isteğinin arka kanalını kullanır.  
  
7. Hizmeti kapatmak için hizmet konsolu penceresinde ENTER tuşuna basın. İstemcisini kapatmak için istemci konsolu penceresinde ENTER tuşuna basın.
