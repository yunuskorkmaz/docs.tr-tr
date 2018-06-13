---
title: Güvenli Oturumlar için En İyi Uygulamalar
ms.date: 03/30/2017
ms.assetid: b94f6e01-8070-40b6-aac7-a2cb7b4cb4f2
ms.openlocfilehash: 1d9671e7e3124d535b66de8cd8468f76dcb32b10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491633"
---
# <a name="best-practices-for-reliable-sessions"></a>Güvenli Oturumlar için En İyi Uygulamalar

Bu konu, güvenilir oturumlar için en iyi uygulamaları açıklar.

## <a name="setting-maxtransferwindowsize"></a>MaxTransferWindowSize ayarlama

Güvenilir oturumlar Windows Communication Foundation (WCF) aktarımı pencere iletileri istemci ve hizmet tutmak için kullanın. Yapılandırılabilir özellik <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> aktarımı penceresi tutun kaç iletileri gösterir.

Gönderenin, bu aktarım penceresi için onay beklenirken tutabilir kaç iletileri gösterir; Alıcı, hizmet için arabelleğe alınacak kaç iletileri gösterir.

Doğru boyutta seçme, ağ verimliliğini ve en iyi kapasitesi etkiler. Aşağıdaki bölümlerde bu özellik ve değer etkisini için bir değer seçerken dikkat edilmesi gerekenler ayrıntılı olarak açıklanmaktadır.

Varsayılan aktarımı pencere boyutu sekiz iletileri ' dir.

### <a name="efficient-use-of-the-network"></a>Verimli kullanımı, ağ

Bu bağlamda terimi *ağ* her şeyi (gönderen) istemci ve hizmet (alıcı) arasındaki iletişimin temel olarak kullanılan karşılık gelir. Bu aktarım bağlantıları ve herhangi bir aracı veya köprüleri arasındaki, SOAP yönlendiriciler veya HTTP Proxy/Güvenlik duvarları gibi içerir.

Verimli kullanımı, ağ, ağ kapasitesi tam olarak kullanılmasını sağlar. Her iki saniye başına ağ üzerinden aktarılabilir veri miktarını (*veri oranı*) ve veri gönderenden alıcıya aktarım süresini (*gecikme*) nasıl etkili bir şekilde etkileyen ağ kullanılır.

Gönderen, özellik üzerinde <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> aktarımı penceresi tutmak için onay beklenirken kaç iletileri gösterir. Varsa ağ gecikmesi yüksektir ve esnek gönderen ve etkili ağ kullanımını sağlamak için Aktarım pencere boyutunu artırmanız gerekir.

Örneğin gönderici ile veri oranı tutar durumunda bile, gecikme süresi birkaç aracılar gönderici ve alıcı arasında mevcut ya da veri kayıplı aracı veya ağ geçmesi gereken yüksek olabilir. Bu nedenle, kendi aktarımı penceresindeki iletileri için onayları kablo göndermek için yeni iletileri kabul etmeden önce beklenecek göndericisi vardır. Yüksek gecikme, daha az etkili küçük arabellekle ağ kullanımı. Diğer taraftan, istemci tarafından gönderilen verileri Yüksek orandaki yakalamak hizmet gerekebileceğinden çok yüksek bir aktarım pencere boyutu hizmet etkileyebilir.

### <a name="running-the-service-to-capacity"></a>Kapasitede hizmet çalışıyor

İdeal olarak ağ verimli bir şekilde kullanılan kadar da en iyi kapasitede çalıştırılacak hizmetinin isteyebilirsiniz. Alıcı aktarımı pencere boyutu özellikte alıcı arabellek kaç iletileri gösterir. Bu ileti arabelleğe alma, yalnızca ağ akış denetimi yardımcı olur, ancak ayrıca tam kapasite çalıştırmak hizmeti sağlar. Örneğin, bir ileti arabellek ise ve hizmet bunları işleyebileceğinden daha hızlı iletiler geldiğinde sonra ağ iletileri bırakmak ve kapasite küçülttüğü iyi bir şekilde veya az.

Aynı anda alır ve daha önce alınan iletileri işlenirken bir ileti arabelleği gibi bir arabellek kullanarak hizmet kullanılabilirliğini artırır.

Aynı kullanmanız önerilir `MaxTransferWindowSize` gönderici ve alıcı.

### <a name="enabling-flow-control"></a>Akış denetimi etkinleştirme

*Akış denetimi* sağlar göndereni ve alıcısı ayak birbirleri ile tutmak, diğer bir deyişle, iletiler tüketilen ve üzerinde işlem mekanizmasıdır üretilen kadar hızlı. İstemci ve hizmet aktarımı pencere boyutu göndereni ve alıcısı makul bir eşitleme pencere içinde olmasını sağlar.

Özellik set önerilen <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled%2A> için `true` bir WCF istemcisi ve bir WCF hizmeti arasında güvenli bir oturum kullanırken.

## <a name="setting-maxpendingchannels"></a>MaxPendingChannels ayarlama

Güvenilir oturum farklı istemcilerden gelen iletişimi sağlayan bir hizmet yazarken, birçok istemciniz hizmetine güvenilir oturum aynı anda oluşturmak mümkündür. Bu gibi durumlarda hizmetinin yanıt bağlıdır `MaxPendingChannels` özelliği.

Gönderenin alıcı bir güvenilir oturum kanalı oluşturduğunda, bunlar arasında bir el sıkışması güvenilir oturum kurar. Güvenilir oturum kurulduktan sonra kanal kabul bekleyen kanal sırada hizmet tarafından yerleştirilir. `MaxPendingChannels` Özelliği gösterir kaç kanalları bu durumda olabilir.

Daha fazla kanalları burada kabul edemez bir durumda olması için hizmet mümkündür. Sıra dolu olduğunda, güvenilir bir oturumu girişimi reddedilir ve istemci yeniden gerekir.

Sıranın bekleyen kanallarında uzun bir süre sırada kalmasını mümkündür. Bu arada, hatalı bir duruma geçiş kanalı neden bir güvenilir oturum etkin olmama zaman aşımı oluşabilir.

Aynı anda birden fazla istemciye hizmet bir hizmet yazarken, gereksinimlerinize uygun olan bir değer ayarlamanız gerekir. İçin çok yüksek bir değere ayarlamak `MaxPendingChannels` özelliği, çalışma kümesi etkiler.

İçin varsayılan değer <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxPendingChannels%2A> dört kanalları.

## <a name="reliable-sessions-and-hosting"></a>Güvenilir oturumlar ve barındırma

Güvenilir oturumlar kullanan bir hizmet barındırma zaman web, aşağıdaki önemli noktalar göz önünde bulundurmalıdır:

- Güvenilir oturumlar durum bilgisi olan ve durumu AppDomain'e korunur. Bu, güvenilir bir oturum parçası olan tüm iletileri aynı AppDomain'e işlenmelidir anlamına gelir. Web grupları ve web bahçelerinde grubu ya da bahçesi boyutunu tek bir düğüm büyük olduğu bu kısıtlamayı garanti edemez.

- Güvenilir oturumlar çift HTTP kanalı kullanılarak (örneğin, kullanarak `WsDualHttpBinding`) en fazla iki HTTP bağlantıları stemci varsayılan gerektirebilir. Başka bir deyişle, belirli bir zamanda her eş zamanlı uygulama ve protokol iletilerini aktarma çünkü en fazla iki bağlantıları her şekilde çift yönlü bir güvenilir oturum gerektirebilir. Hizmetinin ileti değişim deseni bağlı olarak belirli koşullar altında bu çift HTTP ve güvenilir oturumlar kullanarak bir web barındırılan hizmet kilitlenme mümkün olduğu anlamına gelir. Aşağıdaki istemci başına izin verilen HTTP bağlantılarını sayısını artırmak için ilgili yapılandırma dosyasına ekleyin (örneğin, *web.config* söz konusu hizmetinin):

  ```xml
  <configuration>
    <system.net>
      <connectionManagement>
        <add name="*" maxconnection="4" />
      </connectionManagement>
    </system.net>
  </configuration>
  ```

  Değeri `maxconnection` özniteliği gereken bağlantı sayısıdır. En az dört bağlantıları bu durumda olması gerekir.
