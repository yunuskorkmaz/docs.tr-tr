---
title: Güvenilir Güvenlik Profili
ms.date: 03/30/2017
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: dfdafbcdc461c80192e310a86d5bff50f0885283
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45998974"
---
# <a name="reliable-secure-profile"></a>Güvenilir Güvenlik Profili
Bu örnek WCF oluşturmak nasıl gösterir ve [güvenilir güvenli profili](https://go.microsoft.com/fwlink/?LinkId=178140) (RSP). Bu örnek uygulamasını gösterir. bir [bağlantı yap](https://go.microsoft.com/fwlink/?LinkId=178141) güvenilir Mesajlaşma ile birlikte ve isteğe bağlı olarak oluşan kanal güvenilir güvenli bir bağlama oluşturmak için güvenli bir kanal tabanlı RSP belirtimi.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, bir iki yönlü zaman uyumsuz ileti güvenilir exchange senaryosunu gösterir. Çift yönlü sözleşme hizmette olduğunu ve çift yönlü geri çağırma anlaşması istemci uygular. İstemci, ayrı bir bağlantı üzerinde beklenen bir yanıt için bir hizmet isteğine başlatır. İstek iletisi güvenilir bir şekilde gönderilir. İstemci, sonunda dinleyen bir uç nokta açmak istediğiniz değil. Bu nedenle, hizmeti ile arka kanal bu 'Bağlantı Yap' isteğinin yanıtı geri gönderilecek ilişkin 'Bağlantı Yap' isteklerin yoklar. Bu örnek, istemci dinleyen bir uç noktayı kullanıma sunmayı (ve güvenlik duvarı özel durumu oluşturulmadan), HTTP üzerinden güvenli güvenilir bir çift yönlü iletişim sağlamak nasıl gösterir.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Açık **ReliableSecureProfile** çözüm.  
  
2.  Sağ tıklayın **hizmet** projesi **Çözüm Gezgini**seçin **hata ayıklama**, **yeni örnek Başlat** bağlam menüsünden. Bu hizmet ana bilgisayar başlatır.  
  
3.  Sağ tıklayın **istemci** projesi **Çözüm Gezgini**seçin **hata ayıklama**, **yeni örnek Başlat** bağlam menüsünden. Bu, istemci başlatır.  
  
4.  Herhangi bir dize istemci konsol penceresinde satırına yazın ve ENTER'ı tıklatın. Bu, Giriş dizesinin Bu dize bir karmasını hesaplar hizmetine gönderir.  
  
5.  Hizmet istemci konsol penceresinde sonucu görüntülemek için çift yönlü bir geri çağırma anlaşması işlemi geri çağırdığında sonucu windows istemcisi üzerinde görüntüleyin. Uzun süre çalışan bir veri işleme işleminin benzetimini yapmak için hizmette kasıtlı bir gecikme olur.  
  
6.  (Herhangi biri tarafından çevrimiçi ağ izleme araçları Ağ İzleyicisi, Fiddler vb. gibi) HTTP trafiğini izleme gösteren bir dizisi iletişimi için istemci ile hizmet arasında güvenilir güvenli profili tarafından düzenlenir ve nasıl oluşturduğunuzu istemci 'Bağlantı Yap' isteklere hizmet yoklar. Hizmet işlenen yanıtını geri göndermek hazır aldığında son 'Bağlantı Yap' isteğin arka kanal sonuçları geri göndermek için kullanır.  
  
7.  Hizmeti kapatmak için hizmet konsol penceresinde ENTER tuşuna basın. İstemciyi kapatma işlemlerinin istemci konsol penceresinde ENTER tuşuna basın.
