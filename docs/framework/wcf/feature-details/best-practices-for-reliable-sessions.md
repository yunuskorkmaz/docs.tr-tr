---
title: Güvenli Oturumlar için En İyi Uygulamalar
ms.date: 03/30/2017
ms.assetid: b94f6e01-8070-40b6-aac7-a2cb7b4cb4f2
ms.openlocfilehash: 1d9671e7e3124d535b66de8cd8468f76dcb32b10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857993"
---
# <a name="best-practices-for-reliable-sessions"></a>Güvenli Oturumlar için En İyi Uygulamalar

Bu konu, güvenilir oturumlar için en iyi uygulamaları açıklar.

## <a name="setting-maxtransferwindowsize"></a>MaxTransferWindowSize ayarlama

Güvenilir oturumlar Windows Communication Foundation (WCF) hizmet ve istemci iletileri tutmak için bir aktarım penceresi kullanın. Yapılandırılabilir özellik <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> aktarımı pencerenin tutabilir ileti sayısını gösterir.

Gönderenin, bu onayları için beklenirken aktarımı pencerenin içerebilir ileti sayısını gösterir. bir alıcı ile hizmet için arabelleğe alınacak ileti sayısını gösterir.

Doğru boyutta seçme, ağ verimliliğini ve en iyi kapasitesi etkiler. Aşağıdaki bölümlerde bu özellik ve değerin etkisi için bir değer seçerken dikkat etmeniz ayrıntılı olarak açıklanmaktadır.

Varsayılan aktarım pencere boyutu sekiz ileti ' dir.

### <a name="efficient-use-of-the-network"></a>Ağ verimli kullanımı

Bu bağlamda terimi *ağ* bir istemci (gönderen) ve (alıcı) hizmeti arasındaki iletişimi temeli olarak kullanılan her şeye karşılık gelir. Bu aktarım bağlantılarının ve herhangi bir aracı veya köprüler arasındaki, SOAP yönlendiriciler veya HTTP proxy/güvenlik duvarlarının da içerir.

Ağ verimli kullanımı, ağ kapasitesi tam olarak kullanılmasını sağlar. Her iki saniye başına ağ üzerinden aktarılması veri miktarı (*veri hızı*) ve veri gönderenden alıcıya aktarım süresini (*gecikme*) nasıl etkili bir şekilde etkilemeden ağ kullanılmaktadır.

Gönderen, özelliğin üzerinde <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> aktarma penceresi, katkıda bulunanlar için beklenirken tutabilir ileti sayısını gösterir. Varsa ağ gecikme süresi yüksek ve hızlı yanıt veren gönderen ve etkili ağ kullanımı sağlamak için Aktarım pencere boyutunu artırmanız gerekir.

Örneğin veri oranı ile gönderen sürdürdüğünden bile, gecikme süresi gönderen ve alıcı arasında birkaç aracılar mevcut veya veri kayıplı aracı veya ağ geçmelidir yüksek olabilir. Bu nedenle, kablo göndermek için yeni iletileri kabul etmeden önce aktarım penceresi iletileri için onayları için beklenecek göndericisi vardır. Daha az etkili yüksek gecikme süresiyle daha küçük arabellek ağ kullanımı. Diğer taraftan, çok yüksek bir aktarım pencere boyutu hizmet yüksek oranda istemci tarafından gönderilen verileri yakalamak gerekebileceğinden hizmet etkileyebilir.

### <a name="running-the-service-to-capacity"></a>Kapasiteye hizmet çalışıyor

İdeal olarak ağ verimli bir şekilde kullanılan kadar de en uygun kapasitede çalıştırmak için hizmet istersiniz. Alıcı aktarımı penceresi boyut özelliği, alıcı ara belleğe alabilir ileti sayısını gösterir. Bu iletiyi arabelleğe yalnızca ağ akış denetimi yardımcı olur, ancak ayrıca tam kapasitede çalışmaya hizmet sağlar. Örneğin, bir ileti arabellek ise ve hizmetin bunları işleyebileceğinden daha hızlı iletiler geldiğinde ardından ağ iletileri bırakmak ve kapasitesini boşa veya potansiyelinden az kullanılmasına neden.

Eş zamanlı olarak alır ve daha önce alınan iletileri işlenirken bir ileti arabelleği gibi bir arabellek kullanarak hizmetinin kullanılabilirliğini artırır.

Aynı kullanmanız önerilir `MaxTransferWindowSize` gönderen ve alıcı.

### <a name="enabling-flow-control"></a>Akış denetimi etkinleştirme

*Akış denetimi* sağlar gönderen ve alıcı birbiriyle uydurmanıza, diğer bir deyişle, iletiler tüketilen ve izlemede bir mekanizma, üretilen kadar hızlı. Hizmet ve istemci aktarımı pencere boyutunu gönderen ve alıcı eşitleme makul bir pencere içinde olmasını sağlar.

Özelliğin ayarlanıp önerilen <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled%2A> için `true` bir WCF istemcisi ve bir WCF hizmeti arasında bir güvenilir oturum kullanırken.

## <a name="setting-maxpendingchannels"></a>MaxPendingChannels ayarlama

Farklı istemcilerden güvenilir oturum bağlantısı sağlayan bir hizmet yazarken, birden çok istemci aynı anda güvenilir oturum hizmeti oluşturmak mümkündür. Bu gibi durumlarda hizmetinin yanıt bağımlı `MaxPendingChannels` özelliği.

Gönderenin alıcı bir güvenilir oturum kanalı oluşturduğunda, bunlar arasında bir el sıkışması güvenilir bir oturum oluşturur. Güvenilir oturum kurulduktan sonra kanal kabul bekleyen kanal sırada hizmet tarafından koyulur. `MaxPendingChannels` Özelliği gösterir kaç kanalları, bu durumda olabilir.

Burada başka kanal kabul edemez bir durumda olması için hizmet mümkündür. Kuyruk dolu ise, bir güvenilir oturum kurma denemesi reddedilir ve istemciyi yeniden denemeniz gerekir.

Kuyrukta bekleyen kanalları için uzun bir süre sırada kalır mümkündür. Bu arada, kanala hatalı bir duruma neden olan bir güvenilir oturum etkin olmama zaman aşımı oluşabilir.

Birden çok istemci aynı anda Hizmetleri hizmet yazarken, gereksinimlerinize uygun bir değere ayarlamanız gerekir. Çok yüksek bir değer için ayarlama `MaxPendingChannels` özelliği çalışma kümenizi etkiler.

İçin varsayılan değer <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxPendingChannels%2A> dört kanallar.

## <a name="reliable-sessions-and-hosting"></a>Güvenilir oturumlar ve barındırma

Güvenilir oturumlar kullanan bir hizmet barındırma, web, aşağıdaki önemli noktalara dikkat dikkat etmeniz:

- Durum bilgisi olan güvenilir oturumlar ve AppDomain içinde durumu korunur. Başka bir deyişle, bir güvenilir oturum parçası olan tüm iletiler aynı AppDomain içinde işlenmesi gerekir. Bu kısıtlama, Grup veya bahçesi boyutu tek bir düğüm büyük olduğu Web grupları ve web bahçelerinde garanti edemez.

- İkili HTTP kanalları kullanarak güvenilir oturumlar (örneğin, kullanarak `WsDualHttpBinding`) en fazla iki HTTP bağlantıları her istemci varsayılan gerektirebilir. Başka bir deyişle, çift yönlü bir güvenilir oturum eş zamanlı uygulama ve protokol iletilerini her iki yöntemle herhangi bir zamanda aktarma çünkü her iki bağlantı gerektirebilir. Hizmetinin ileti değişim deseni bağlı olarak bazı koşullar altında bu ikili HTTP ve güvenilir oturumlar kullanarak web barındırılan hizmeti kilitlenme mümkün olduğunu gösterir. İstemci başına izin verilen HTTP bağlantı sayısını artırmak için ilgili yapılandırma dosyasına aşağıdakileri ekleyin (örneğin, *web.config* söz konusu hizmetin):

  ```xml
  <configuration>
    <system.net>
      <connectionManagement>
        <add name="*" maxconnection="4" />
      </connectionManagement>
    </system.net>
  </configuration>
  ```

  Değerini `maxconnection` özniteliktir gereken bağlantı sayısı. En az dört bağlantıları bu durumda olması gerekir.
