---
title: Kanal Modeli Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- channel model [WCF]
ms.assetid: 07a81e11-3911-4632-90d2-cca99825b5bd
ms.openlocfilehash: c29b3e3d5eff426ac573ddf5224259f0a6c28e53
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664922"
---
# <a name="channel-model-overview"></a>Kanal Modeli Genel Bakış
Windows Communication Foundation (WCF) kanal bir katmanlı iletişim yığını iletileri işleyen bir veya daha fazla kanallar yığınıdır. Yığının en altında (örneğin, TCP, HTTP, SMTP ve diğer aktarım türlerini.) temel alınan aktarımda kanal yığına uyarlamak için sorumlu bir aktarım kanalıdır. Kanalları ileti gönderme ve alma için alt düzey bir programlama modeli sunar. Çeşitli arabirimler ve topluca WCF kanalı modeli olarak bilinen diğer türleri bu programlama modeli kullanır. Bu konu, kanal şekiller, oluşumunu temel kanal dinleyicisi (hizmette) ve kanal fabrikası (istemcide) açıklar.  
  
## <a name="channel-stack"></a>Kanal yığını  
 WCF bitiş noktalarını kanal yığın adlı bir iletişim yığını kullanarak tüm dünya ile iletişim kurar. Aşağıdaki diyagramda, kanal yığın diğer iletişim yığınları, örneğin TCP/IP ile karşılaştırır.  
  
 ![Kanal modeli](../../../../docs/framework/wcf/extending/media/wcfc-channelstackhighlevelc.gif "wcfc_ChannelStackHighLevelc")  
  
 İlk olarak, benzerlikler: Her iki durumda da, bazı Özet dünyanın aşağıdaki katman ve bu soyutlama hemen üstündeki yalnızca katmana kullanıma yığınının her katmanı sağlar. Her katman Soyutlama Katmanı yalnızca hemen altına kullanır. Her katman diğer yığınında karşılık gelen katmanı ile iletişim kurar iki yığınları iletişim kurduğunda de her iki durumda da, örneğin, IP katmanı IP katmanı ve TCP katman vb. TCP katmanla iletişim kurar.  
  
 Şimdi, fark: TCP yığınına fiziksel ağ soyutlaması sağlamak için tasarlanmış olsa da, kanal yığın bir soyutlamasıdır yalnızca nasıl ileti, yani teslim edilir, taşıma, aynı zamanda ileti veya ne nedir gibi diğer özellikleri sağlamak üzere tasarlanmıştır Protokolü, aktarım ancak daha fazlasını içeren, iletişimi için kullanılır. Örneğin, güvenilir oturum bağlama öğesi kanal yığının bir parçasıdır ancak aktarma veya taşıma altında değil. Bu soyutlama, kanal yığını mimarisinin temel alınan Aktarım Protokolü uyum yığındaki alt kanal gerektirerek elde edilir ve daha sonra bağlı daha fazla güvenilirlik gibi iletişim özellikler sağlamak için yığınında yukarı kanallar garantileri ve güvenlik.  
  
 Akış iletişim yığını aracılığıyla iletileri <xref:System.ServiceModel.Channels.Message> nesneleri. Yukarıdaki şekilde gösterildiği gibi alt kanal taşıma kanalı olarak adlandırılır. Ve ileti gönderip diğer taraflara sorumludur kanalıdır. Bu dönüştürme sorumluluğunu içerir <xref:System.ServiceModel.Channels.Message> nesne için ve diğer kişilerle iletişim kurmak için kullanılan biçim. Taşıma kanalının olabilir herhangi bir sayıda protokol kanalını güvenilir teslimat garantileriyle gibi bir iletişim işlevi sağlamaktan sorumlu. Protokol kanalını çalışması aracılığıyla biçiminde akan iletilerinde <xref:System.ServiceModel.Channels.Message> nesne. Bunlar genellikle ya da ileti üstbilgileri ekleme ya da gövdesi şifreleme gibi dönüştürme veya kendi Protokolü Denetim iletileri gönderip, örneğin, giriş bildirimler.  
  
## <a name="channel-shapes"></a>Kanal şekiller  
 Her kanal kanal şekli arabirimleri veya kanal şekiller olarak bilinen bir veya daha fazla arabirim uygular. Bu kanal şekiller iletişim odaklı yöntemleri gibi göndermek ve almak veya istek ve kanal uygular ve kanalının kullanıcı çağırır yanıt sağlar. Kanal şekillerinin temeli <xref:System.ServiceModel.Channels.IChannel> sağlayan bir arabirimi olan arabirimi bir `GetProperty` \<T > yığın kanallarında tarafından kullanıma sunulan rastgele özelliklerine erişmek için katmanlı bir mekanizma hedeflenen yöntemi. Beş genişleten şekiller kanal <xref:System.ServiceModel.Channels.IChannel> şunlardır:  
  
- <xref:System.ServiceModel.Channels.IInputChannel>  
  
- <xref:System.ServiceModel.Channels.IOutputChannel>  
  
- <xref:System.ServiceModel.Channels.IRequestChannel>  
  
- <xref:System.ServiceModel.Channels.IReplyChannel>  
  
- <xref:System.ServiceModel.Channels.IDuplexChannel>  
  
 Ayrıca, her biri bu şekilleri genişleten eşdeğer sahip <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> oturumları desteklemek için. Bunlar:  
  
- <xref:System.ServiceModel.Channels.IInputSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IOutputSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IRequestSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IReplySessionChannel>  
  
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel>  
  
 Bazı temel ileti desenler mevcut aktarım protokolleri tarafından desteklenen exchange sonra kanal şekilleri desenli. Örneğin, tek yönlü mesajlaşmayı karşılık gelen bir <xref:System.ServiceModel.Channels.IInputChannel> / <xref:System.ServiceModel.Channels.IOutputChannel> karşılık gelen istek-yanıt çifti <xref:System.ServiceModel.Channels.IRequestChannel> / <xref:System.ServiceModel.Channels.IReplyChannel> çiftleri ve iki yönlü çift yönlü iletişimler karşılık gelen <xref:System.ServiceModel.Channels.IDuplexChannel> (her ikisi de genişleten <xref:System.ServiceModel.Channels.IInputChannel> ve <xref:System.ServiceModel.Channels.IOutputChannel>).  
  
## <a name="programming-with-the-channel-stack"></a>Kanal yığın ile programlama  
 Kanal yığınları genellikle burada kanal yığın bağlama oluşturur bir Fabrika deseni kullanılarak oluşturulur. Gönderme tarafında bir bağlama oluşturmak için kullanılan bir <xref:System.ServiceModel.ChannelFactory>, hangi sırayla bir kanal yapılar yığın ve kanal yığında bir üst başvuru döndürür. Uygulama, ileti göndermek için bu kanal sonra kullanabilirsiniz. Daha fazla bilgi için [istemci kanal düzeyi programlama](../../../../docs/framework/wcf/extending/client-channel-level-programming.md).  
  
 Alma tarafında bir bağlama oluşturmak için kullanılan bir <xref:System.ServiceModel.Channels.IChannelListener>, gelen iletileri dinler. <xref:System.ServiceModel.Channels.IChannelListener> Kanal yığınları oluşturarak ve üst kanal uygulama referansı gönderdikten dinleme uygulama iletilerin sağlar. Uygulama daha sonra bu kanal, gelen iletileri almak için kullanır. Daha fazla bilgi için [hizmet kanal düzeyi programlama](../../../../docs/framework/wcf/extending/service-channel-level-programming.md).  
  
## <a name="the-channel-object-model"></a>Kanal nesne modeli  
 Kanal nesne modeli arabirimleri Kanallar, kanal dinleyicileri ve kanal fabrikaları uygulamak için gereken çekirdek kümesidir. Özel uygulamalarında yardımcı olmak için sağlanan bazı temel sınıflar da vardır.  
  
 Kanal dinleyicileri gelen iletiler için dinleme ve bunları katmana kanal dinleyicisi tarafından oluşturulan bir kanal üzerinden teslim yükümlü olursunuz.  
  
 İleti göndermek için kullanılan kanalları oluşturmaktan sorumlu kanal fabrikaları ve kanal fabrikası kapatıldığında tüm kanalları kapatma için oluşturdukları.  
  
 <xref:System.ServiceModel.ICommunicationObject> Tüm iletişim nesneleri uygulayan temel durum makinesinin tanımlar çekirdek arabirimidir. <xref:System.ServiceModel.Channels.CommunicationObject> diğer kanal sınıfları arabirimi tekrar uygulamak yerine türeyebilir bu çekirdek arabiriminin bir uygulamasını sağlar. Ancak, bu gerekli değildir: özel bir kanalda uygulayabilirsiniz <xref:System.ServiceModel.ICommunicationObject> doğrudan ve öğesinden devralmayan <xref:System.ServiceModel.Channels.CommunicationObject>. Şekil 3'te sınıflardan hiçbiri kanal modelinin bir parçası olarak kabul edilir; kullanılabilir kanallar oluşturmak istediğiniz özel kanal uygulayıcılar Yardımcıları değildirler.  
  
 ![Kanal modeli](../../../../docs/framework/wcf/extending/media/wcfc-wcfcchannelsigure3omumtreec.gif "wcfc_WCFCChannelsigure3OMUMTreec")  
  
 Aşağıdaki konular, kanal nesne modeli ve bunun yanı sıra özel kanallar oluşturmanıza yardımcı çeşitli geliştirme alanları açıklar.  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[Hizmet: Kanal dinleyicileri ve kanallar](../../../../docs/framework/wcf/extending/service-channel-listeners-and-channels.md)|Bir hizmet uygulaması gelen kanallarında dinler kanal dinleyicileri, açıklar.|  
|[İstemci: Kanal fabrikaları ve kanallar](../../../../docs/framework/wcf/extending/client-channel-factories-and-channels.md)|Bir hizmet uygulamasına bağlanmak için kanal oluşturma kanal fabrikaları açıklar.|  
|[Durum Değişikliklerini Anlama](../../../../docs/framework/wcf/extending/understanding-state-changes.md)|Açıklayan nasıl <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType> arabirimi kanalları durum değişiklikleri modeller.|  
|[İleti Değişim Deseni Seçme](../../../../docs/framework/wcf/extending/choosing-a-message-exchange-pattern.md)|Kanalları destekleyebileceği altı temel ileti exchange desenleri açıklar.|  
|[Özel Durum ve Hataları İşleme](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)|Hatalar ve özel bir kanalda özel durumları nasıl ele alınacağını açıklar.|  
|[Yapılandırma ve Meta Veri Desteği](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)|Uygulama modelinden özel kanallar kullanımını desteklemek ve bağlamalar ve bağlama öğeleri kullanarak meta verileri içeri ve dışarı aktarmak açıklar.|
