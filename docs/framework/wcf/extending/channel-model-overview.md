---
title: "Kanal Modeli Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- channel model [WCF]
ms.assetid: 07a81e11-3911-4632-90d2-cca99825b5bd
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7f6f45b788d825fed3c8f5d627190dd8911ec4c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="channel-model-overview"></a>Kanal Modeli Genel Bakış
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Kanal yığını olduğundan işlem iletileri bir veya daha fazla kanallar katmanlı iletişim yığını. Yığının sonuna (örneğin, TCP, HTTP, SMTP ve diğer türleri aktarım.) temel aktarımı kanal yığına uyarlamak için sorumlu bir aktarım kanalıdır. Kanallar ileti gönderme ve alma için alt düzey bir programlama modeli sağlar. Birkaç arabirimleri ve diğer türleri topluca olarak bilinen bu programlama modeli dayanan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanal modeli. Bu konuda, kanal şekil, temel kanal dinleyicisi (hizmette) ve (istemcide) kanal fabrikası yapımı anlatılmaktadır.  
  
## <a name="channel-stack"></a>Kanal yığını  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]uç noktaları kanal yığını adlı bir iletişim yığını kullanarak dünya ile iletişim kurar. Aşağıdaki diyagramda kanal yığınını diğer iletişim yığınları, örneğin TCP/IP ile karşılaştırır.  
  
 ![Kanal modeli](../../../../docs/framework/wcf/extending/media/wcfc-channelstackhighlevelc.gif "wcfc_ChannelStackHighLevelc")  
  
 İlk olarak, benzerlikleri: her iki durumda da, bazı soyutlama World aşağıdaki katman ve bu soyutlama doğrudan üstünde yalnızca katmana kullanıma yığınının her katman sağlar. Her katman yalnızca katmanının hemen altındaki soyutlama kullanır. Karşılık gelen katman diğer yığındaki her katman kurduğu iki yığınları iletişim kurduğunda de her iki durumda da, örneğin, IP katmanı IP katmanı ve TCP katman vb. TCP katmanla iletişim kurar.  
  
 Şimdi, farklar: sırada TCP yığınına fiziksel ağ için bir Özet sağlamak için tasarlanmış, kanal yığın yalnızca nasıl ileti, başka bir deyişle teslim edilir, taşıma, nedir gibi başka özellikler de bir Özet sağlamak için tasarlanmıştır ileti veya hangi protokolü, aktarım ancak daha çok daha fazlası dahil olmak üzere, iletişimi için kullanılır. Örneğin, güvenilir oturum bağlama öğesi kanal yığını parçası olan ancak aktarma veya taşıma altında değil. Bu soyutlama kanal yığın mimarisi için temel Aktarım Protokolü uyarlamak için yığındaki alt kanal gerektirerek elde edilir ve ardından güvenmek daha fazla güvenilirlik gibi iletişim özellikleri sağlamak için yığınında yukarı kanallar garanti ve güvenlik.  
  
 İletileri iletişim yığını aktığı <xref:System.ServiceModel.Channels.Message> nesneleri. Yukarıdaki şekilde gösterildiği gibi alt kanal taşıma kanal adı verilir. Gönderme ve alma iletilerini ve diğer taraf sorumludur kanalıdır. Bu dönüştürme sorumluluğunu içerir <xref:System.ServiceModel.Channels.Message> nesne için ve diğer kişilerle iletişim kurmak için kullanılan biçim. Taşıma kanalı olabilir protokol kanalını herhangi bir sayıda güvenilir teslim Güvenceleri gibi iletişim işlevi sağlamak için her sorumlu. Protokol kanalını çalışması aralarında biçiminde akan iletilerde <xref:System.ServiceModel.Channels.Message> nesnesi. Bunlar genellikle da üstbilgileri ekleme ya da gövdesi şifreleme ileti, örneğin, dönüştürme ya da gönderip kendi Protokolü Denetim iletileri, örneğin, giriş ilgili kaynaklar.  
  
## <a name="channel-shapes"></a>Kanal şekiller  
 Her bir kanala kanal şekli arabirimleri veya kanal şekiller olarak bilinen bir veya daha fazla arabirimlerini uygular. Bu kanal şekiller iletişimi odaklı yöntemleri gibi göndermek ve almak veya istek ve kanal uygular ve kanal kullanıcı çağırır yanıt sağlar. Kanal şekiller temeli <xref:System.ServiceModel.Channels.IChannel> sağlayan bir arabirimi olan arabirimi bir `GetProperty` \<T > yığınında kanalları tarafından sunulan rasgele özelliklerine erişmek için katmanlı mekanizması olarak hedeflenen yöntemi. Beş genişletmek şekiller kanal <xref:System.ServiceModel.Channels.IChannel> şunlardır:  
  
-   <xref:System.ServiceModel.Channels.IInputChannel>  
  
-   <xref:System.ServiceModel.Channels.IOutputChannel>  
  
-   <xref:System.ServiceModel.Channels.IRequestChannel>  
  
-   <xref:System.ServiceModel.Channels.IReplyChannel>  
  
-   <xref:System.ServiceModel.Channels.IDuplexChannel>  
  
 Ayrıca, her bu şekillerin genişleten bir eşdeğer bir gruba sahip <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> oturumları desteklemek için. Bunlar:  
  
-   <xref:System.ServiceModel.Channels.IInputSessionChannel>  
  
-   <xref:System.ServiceModel.Channels.IOutputSessionChannel>  
  
-   <xref:System.ServiceModel.Channels.IRequestSessionChannel>  
  
-   <xref:System.ServiceModel.Channels.IReplySessionChannel>  
  
-   <xref:System.ServiceModel.Channels.IDuplexSessionChannel>  
  
 Bazı temel ileti desenleri varolan aktarım protokolleri tarafından desteklenen exchange sonra kanal şekiller desenleri. Örneğin, tek yönlü mesajlaşmayı karşılık gelen bir <xref:System.ServiceModel.Channels.IInputChannel> / <xref:System.ServiceModel.Channels.IOutputChannel> çifti, istek-yanıt karşılık gelen <xref:System.ServiceModel.Channels.IRequestChannel> / <xref:System.ServiceModel.Channels.IReplyChannel> çiftleri ve iki yönlü çift yönlü iletişim karşılık gelen <xref:System.ServiceModel.Channels.IDuplexChannel> (her ikisi de genişleten <xref:System.ServiceModel.Channels.IInputChannel> ve <xref:System.ServiceModel.Channels.IOutputChannel>).  
  
## <a name="programming-with-the-channel-stack"></a>Kanal yığını ile programlama  
 Kanal yığınları genellikle bir bağlama kanal yığın oluşturur Fabrika düzeni kullanılarak oluşturulur. Gönderen tarafında bir bağlama oluşturmak için kullanılan bir <xref:System.ServiceModel.ChannelFactory>, hangi sırayla derlemeleri kanal bir yığın ve üst referansı döndürür kanal yığınında. Uygulama sonra iletileri göndermek için bu kanalı'nı kullanabilirsiniz. Daha fazla bilgi için bkz: [istemci kanal düzeyi programlama](../../../../docs/framework/wcf/extending/client-channel-level-programming.md).  
  
 Alma tarafında bir bağlama oluşturmak için kullanılan bir <xref:System.ServiceModel.Channels.IChannelListener>, gelen iletiler için dinler. <xref:System.ServiceModel.Channels.IChannelListener> Kanal yığınları oluşturarak ve üst kanal uygulama referansı gönderdikten dinleme uygulamaya iletileri sağlar. Uygulama bu kanal, gelen iletileri almak için kullanır. Daha fazla bilgi için bkz: [hizmet kanal düzeyi programlama](../../../../docs/framework/wcf/extending/service-channel-level-programming.md).  
  
## <a name="the-channel-object-model"></a>Kanal nesne modeli  
 Kanal nesne modeli Kanallar, kanal dinleyicileri ve kanal fabrikaları uygulamak için gereken arabirimler çekirdek kümesidir. Özel uygulamalarında yardımcı olmak için sağlanan bazı temel sınıflar vardır.  
  
 Kanal dinleyicileri gelen iletiler için dinleme, sonra bunları katmana kanal dinleyicisi tarafından oluşturulan kanallar aracılığıyla teslim sorumludur.  
  
 Kanal fabrikaları ileti göndermek için kullanılan kanalları oluşturmaktan sorumlu olan ve kanal fabrikası kapatıldığı zaman tüm kanalları kapatma için bunlar oluşturulur.  
  
 <xref:System.ServiceModel.ICommunicationObject>Tüm iletişimi nesneleri uygulamak temel durum makinesinin tanımlar çekirdek arabirimidir. <xref:System.ServiceModel.Channels.CommunicationObject>diğer kanal sınıfları arabirimi yeniden uygulamak yerine türetilen bu çekirdek arabirim uygulaması sağlar. Ancak, bu gerekli değildir: özel bir kanalda uygulayabilirsiniz <xref:System.ServiceModel.ICommunicationObject> doğrudan ve devralınmalıdır değil <xref:System.ServiceModel.Channels.CommunicationObject>. Şekil 3'te sınıfları hiçbiri kanal modelin parçası olarak kabul edilir; Bunlar kanallar oluşturmak istediğiniz özel kanal Implementers kullanılabilir yardımcılardır.  
  
 ![Kanal modeli](../../../../docs/framework/wcf/extending/media/wcfc-wcfcchannelsigure3omumtreec.gif "wcfc_WCFCChannelsigure3OMUMTreec")  
  
 Aşağıdaki konular, kanal nesne modeli ve bunun yanı sıra özel kanalları oluşturmanıza yardımcı çeşitli geliştirme alanları açıklar.  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[Hizmet: Kanal Dinleyicileri ve Kanallar](../../../../docs/framework/wcf/extending/service-channel-listeners-and-channels.md)|Bir hizmet uygulaması gelen kanallarında dinlemek kanal dinleyicileri açıklar.|  
|[İstemci: Kanal Fabrikaları ve Kanallar](../../../../docs/framework/wcf/extending/client-channel-factories-and-channels.md)|Bir hizmet uygulaması'na bağlanmak için kanal oluşturma kanal fabrikaları açıklar.|  
|[Durum Değişikliklerini Anlama](../../../../docs/framework/wcf/extending/understanding-state-changes.md)|Açıklar nasıl <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType> arabirimi durumu değişiklikleri kanaldaki modeller.|  
|[İleti Değişim Deseni Seçme](../../../../docs/framework/wcf/extending/choosing-a-message-exchange-pattern.md)|Kanallar destekleyebilir altı temel ileti exchange desenleri açıklar.|  
|[Özel Durum ve Hataları İşleme](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)|Hataları ve özel durumları özel kanal yapılacağını açıklar.|  
|[Yapılandırma ve Meta Veri Desteği](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)|Uygulama modeli özel kanaldan kullanımını desteklemek ve bağlamalar ve bağlama öğeleri kullanarak meta verilerini almak ve vermek açıklar.|
