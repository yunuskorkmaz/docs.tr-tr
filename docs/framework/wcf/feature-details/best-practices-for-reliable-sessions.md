---
description: 'Hakkında daha fazla bilgi edinin: güvenilir oturumlar için En Iyi uygulamalar'
title: Güvenli Oturumlar için En İyi Uygulamalar
ms.date: 03/30/2017
ms.assetid: b94f6e01-8070-40b6-aac7-a2cb7b4cb4f2
ms.openlocfilehash: 4b05dd914d2c5b8ec7941417b727bec1e5b43ba4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643676"
---
# <a name="best-practices-for-reliable-sessions"></a>Güvenli Oturumlar için En İyi Uygulamalar

Bu konu, güvenilir oturumlar için en iyi uygulamaları açıklamaktadır.

## <a name="setting-maxtransferwindowsize"></a>MaxTransferWindowSize ayarlama

Windows Communication Foundation (WCF) güvenilir oturumlar istemci ve hizmette iletileri tutmak için bir aktarım penceresi kullanır. Yapılandırılabilir özelliği, <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> Aktarım penceresinin kaç ileti tutabileceğini gösterir.

Gönderen üzerinde, bu, aktarım penceresinin, bildirimlerin beklediği sırada kaç ileti tutabileceğini belirtir; alıcıda, hizmet için arabelleğe eklenecek ileti sayısını gösterir.

Doğru boyutun seçilmesi, ağın verimliliğini ve hizmetin en iyi kapasitesini etkiler. Aşağıdaki bölümler, bu özellik için bir değer seçerken göz önünde bulundurulması gereken ayrıntıları ve değerin etkisini ayrıntılandırır.

Varsayılan aktarım penceresi boyutu sekiz mesaj olur.

### <a name="efficient-use-of-the-network"></a>Ağın verimli kullanımı

Bu bağlamda, *ağ* terimi, bir istemci (Gönderen) ve hizmet (alıcı) arasındaki iletişimin temeli olarak kullanılan her şeye karşılık gelir. Bu, SOAP yönlendiricileri veya HTTP proxy 'leri/güvenlik duvarları dahil olmak üzere aktarım bağlantılarını ve arasındaki tüm ara veya köprüleri içerir.

Ağın verimli kullanımı, ağ kapasitesinin tam olarak kullanılmasını sağlar. Ağ üzerinden saniye başına aktarılabilen veri miktarı (*veri hızı*) ve gönderenin verileri göndericiden alıcıya aktarılması için geçen süre (*gecikme süresi*), ağın ne kadar verimli bir şekilde kullanıldığını etkiler.

Gönderici üzerinde, özelliği, <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> Aktarım penceresinin, bildirimlerin beklediği sırada kaç ileti tutabileceğini gösterir. Ağ gecikmesi yüksekse ve yanıt veren gönderici ve etkin ağ kullanımı sağlamak için aktarım penceresi boyutunu artırmanız gerekir.

Örneğin, gönderici veri hızına sahip olsa bile, gönderici ve alıcı arasında birden fazla aracı varsa veya veriler kayıplı bir ara veya ağ üzerinden geçmesi gerekiyorsa gecikme süresi yüksek olabilir. Bu nedenle, gönderenin, Tel bağlantı göndermek üzere yeni iletileri kabul etmeden önce aktarım penceresindeki iletiler için bekleyen bildirimleri beklemesi gerekir. Yüksek gecikme süresine sahip arabellek ne kadar küçükse, ağ kullanımı daha az etkin olur. Öte yandan, hizmetin istemci tarafından gönderilen yüksek hızda veri yakalayabilmesi gerekebileceğinden, aktarım penceresi boyutunun çok yüksek olması hizmeti etkileyebilir.

### <a name="running-the-service-to-capacity"></a>Hizmeti kapasiteye çalıştırma

Ağın etkili bir şekilde kullanıldığı kadar ideal olarak hizmetin en iyi kapasiteye göre çalıştırılmasını de istersiniz. Alıcının aktarım penceresi boyutu özelliği, alıcının arabelleğe aldığı ileti sayısını gösterir. Bu ileti arabelleğe alma, yalnızca ağ akışı denetiminin değil hizmetin tam kapasiteye çalışmasına de olanak sağlar. Örneğin, arabellek bir ileti ise ve iletiler hizmetin işleyebileceğinden daha hızlı ulaştığında, ağ iletileri bırakabilir ve kapasite harcanarak veya aşırı kullanılabilir.

Arabellek kullanmak, daha önce alınan iletileri işlerken aynı anda aldığı ve bir iletiyi arabelleğe aldığından hizmetin kullanılabilirliğini artırır.

`MaxTransferWindowSize`Hem gönderenin hem de alıcının aynısını kullanmanızı öneririz.

### <a name="enabling-flow-control"></a>Akış denetimini etkinleştirme

*Akış denetimi* , gönderici ve alıcının birbirleriyle hızlımasını ve diğer bir deyişle, iletilerin üretildikleri kadar hızlı şekilde tüketilmesini ve bu şekilde işlem yapılmasını sağlayan bir mekanizmadır. İstemci ve hizmet üzerindeki aktarım penceresi boyutu, gönderenin ve alıcının makul bir eşitleme penceresi dahilinde olmasını sağlar.

<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled%2A> `true` WCF ISTEMCISI ile WCF hizmeti arasında güvenilir bir oturum kullandığınızda özelliği olarak ayarlamanız önemle tavsiye ederiz.

## <a name="setting-maxpendingchannels"></a>MaxPendingChannels ayarlanıyor

Farklı istemcilerden güvenilir oturum iletişimini sağlayan bir hizmet yazarken, birçok istemcinin aynı anda hizmette güvenilir bir oturum kurması mümkündür. Bu durumlarda hizmetin yanıtı özelliğe göre değişir `MaxPendingChannels` .

Gönderen bir alıcıya güvenilir bir oturum kanalı oluşturduğunda, aralarındaki bir el sıkışma güvenilir bir oturum oluşturur. Güvenilir oturum kurulduktan sonra kanal, hizmet tarafından kabul edilmesi için bekleyen bir kanal kuyruğuna konur. `MaxPendingChannels`Özelliği, bu durumda kaç kanal kullanılabileceğini gösterir.

Hizmetin daha fazla kanal kabul edebildiği bir durumda olması mümkündür. Sıra doluysa, güvenilir bir oturum oluşturma girişimi reddedilir ve istemci yeniden denenmelidir.

Kuyruktaki bekleyen kanalların daha uzun bir süre için kuyrukta kalması da mümkündür. Bu sırada, güvenilir oturumdaki etkin olmama zaman aşımı oluşabilir ve kanalın hatalı duruma geçmesine neden olabilir.

Aynı anda birden çok istemciye hizmet veren bir hizmet yazarken, gereksinimlerinize uygun bir değer ayarlamanız gerekir. Özellik için çok yüksek bir değer ayarlamak `MaxPendingChannels` çalışma ayarınızı etkiler.

İçin varsayılan değer <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxPendingChannels%2A> dört kanaldır.

## <a name="reliable-sessions-and-hosting"></a>Güvenilir Oturumlar ve barındırma

Web, güvenilir oturumlar kullanan bir hizmeti barındırdığında aşağıdaki önemli noktaları göz önünde bulundurmanız gerekir:

- Güvenilir oturumlar durum bilgisi durumundadır ve durum AppDomain içinde tutulur. Bu, güvenilir bir oturumun parçası olan tüm iletilerin aynı AppDomain 'de işlenmesi gerektiği anlamına gelir. Grup veya bahçe boyutunun bir düğümden daha büyük olduğu Web grupları ve Web bahçeleri bu kısıtlamayı garanti edemez.

- Çift HTTP kanalları (örneğin, kullanarak) kullanan güvenilir oturumlar `WsDualHttpBinding` , istemci başına ıkı http bağlantısının varsayılan değerinden fazlasını gerektirebilir. Bu, çift yönlü güvenilir bir oturumun her bir şekilde her zaman bir şekilde aktarılabileceğinden, her şekilde iki bağlantıya kadar bağlantı gerektirebileceği anlamına gelir. Hizmetin ileti değişimi düzenine bağlı olarak belirli koşullar altında, bu, çift HTTP ve güvenilir oturumları kullanarak Web 'de barındırılan bir hizmetin kilitlenmesi mümkün olduğu anlamına gelir. İstemci başına izin verilen HTTP bağlantısı sayısını artırmak için, ilgili yapılandırma dosyasına aşağıdakini ekleyin (örneğin, söz konusu hizmetin *web.config* ):

  ```xml
  <configuration>
    <system.net>
      <connectionManagement>
        <add name="*" maxconnection="4" />
      </connectionManagement>
    </system.net>
  </configuration>
  ```

  Özniteliğin değeri, `maxconnection` gereken bağlantı sayısıdır. Bu durumda en az dört bağlantı olmalıdır.
