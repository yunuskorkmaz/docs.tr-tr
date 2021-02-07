---
description: 'Daha fazla bilgi edinin: güvenilir güvenli profil'
title: Güvenilir Güvenlik Profili
ms.date: 03/30/2017
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
ms.openlocfilehash: 6e9552b3a6e715f6eac6742f89b2e70a34f926a6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703828"
---
# <a name="reliable-secure-profile"></a>Güvenilir Güvenlik Profili

Bu örnek, WCF ve [güvenilir güvenli profilin (rsp)](http://www.ws-i.org/Profiles/ReliableSecureProfile-1.0.html)nasıl oluşturulacağını gösterir. Bu örnek, güvenilir mesajlaşma ile birlikte oluşturabileceğiniz ve isteğe bağlı olarak RSP belirtimine dayalı güvenilir bir güvenli bağlama oluşturmak için güvenli bir kanal olan bir [bağlantı oluşturma](http://docs.oasis-open.org/ws-rx/wsmc/200702/wsmc-1.0-spec-cs-01.pdf) kanalının uygulanmasını gösterir.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
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
  
6. HTTP trafiğini izleme (Ağ İzleyicisi, Fiddler vb. gibi çevrimiçi ağ izleme araçlarından herhangi biri tarafından), istemci ile hizmet arasında güvenilir güvenli profille gösterildiği gibi ve istemcinin hizmeti ' bağlantı oluştur ' istekleri ile nasıl yokladığı hakkında bir iletişim dizisi olduğunu gösterir. Hizmet işlenen yanıtı geri göndermeye hazırsa, sonuçları geri göndermek için son ' bağlantı oluştur ' isteğinin arka kanalını kullanır.  
  
7. Hizmeti kapatmak için hizmet konsolu penceresinde ENTER tuşuna basın. İstemcisini kapatmak için istemci konsolu penceresinde ENTER tuşuna basın.
