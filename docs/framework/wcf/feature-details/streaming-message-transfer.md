---
title: "İleti Aktarma Akışı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72a47a51-e5e7-4b76-b24a-299d51e0ae5a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a751245f0a933fda649d5919bab86abf2969dbf6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="streaming-message-transfer"></a>İleti Aktarma Akışı
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]taşımalar iletileri aktarmak için iki modunu destekler:  
  
-   Aktarım işlemi tamamlanana kadar arabelleğe alınan aktarımları tüm ileti bir bellek arabelleği basılı tutun. Bir alıcı okumadan önce arabelleğe alınan ileti tamamen teslim gerekir.  
  
-   Akış aktarımları ileti akışı olarak kullanıma sunar. Alıcı tamamen teslim edilmeden önce iletiyi işlemeyi başlatır.  
  
-   Akış aktarımları bir hizmeti ölçeklenebilirliği büyük bellek arabelleği gereksinimini ortadan kaldırarak artırabilir. Aktarım modunu değiştirme ölçeklenebilirliği artırır olup olmadığını aktarılan iletileri boyutuna bağlıdır. Büyük ileti boyutları akış aktarımları kullanarak favor.  
  
 Varsayılan olarak HTTP, TCP/IP'yi ve adlandırılmış kanal taşımaları arabelleğe alınan aktarımları kullanır. Bu belge, bu taşımalar arabelleğe alınan bir geçiş yapmak açıklar akış aktarım modu ve böylece sonuçlarıyla.  
  
## <a name="enabling-streamed-transfers"></a>Akış aktarımları etkinleştirme  
 Arabelleğe alınan ve akış aktarımı modlar arasında seçerek aktarım bağlama öğesi üzerindeki gerçekleştirilir. Bağlama öğeye sahip bir <xref:System.ServiceModel.TransferMode> ayarlanabilir özelliği `Buffered`, `Streamed`, `StreamedRequest`, veya `StreamedResponse`. Aktarım Modu ayarını `Streamed` akış iki yönlü iletişimi etkinleştirir. Aktarım Modu ayarını `StreamedRequest` veya `StreamedResponse` akış belirtilen yönde yalnızca iletişimi etkinleştirir.  
  
 <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.NetTcpBinding>, Ve <xref:System.ServiceModel.NetNamedPipeBinding> bağlamaları açığa <xref:System.ServiceModel.TransferMode> özelliği. Diğer aktarımı için aktarım modu ayarlamak için özel bağlama oluşturmanız gerekir.  
  
 Arabelleğe alınan veya akış aktarımları kullanmaya karar, uç noktanın yerel bir karardır. HTTP taşımaları için aktarım modu bağlantısı üzerinden veya sunuculara ve diğer aracılar dağıtılmaz. Aktarım modunu ayarlama hizmet arabirimi açıklamasında yansıtılmaz. Bir hizmet için bir istemci sınıfı oluşturduktan sonra akış aktarımları modu ayarlamak için kullanılması hedeflenen Hizmetleri için yapılandırma dosyasını düzenlemeniz gerekir. TCP ve adlandırılmış kanal aktarımlar, aktarım modu İlkesi onaylama yayılır.  
  
 Kod örnekleri için bkz: [nasıl yapılır: etkinleştirmek akış](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md).  
  
## <a name="enabling-asynchronous-streaming"></a>Zaman uyumsuz akış etkinleştirme  
 Zaman uyumsuz akışını etkinleştirmek için ekleme <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> uç noktası davranışı hizmeti ana bilgisayarı ve kümesi için kendi <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> özelliğine `true`.  
  
 WCF bu sürümü ayrıca adde true zaman uyumsuz gönderme tarafında akış özelliği. Bu, burada iletileri bazıları okuma yavaş olan birden çok istemciye akış senaryoları hizmetinde ölçeklenebilirliğini artırır; büyük olasılıkla Ağ Tıkanıklığı veya olan nedeniyle hiç okuma değil. Bu senaryolarda WCF Hizmeti istemci başına üzerinde tek tek iş parçacığı artık engeller. Bu hizmet böylece hizmet ölçeklenebilirliğini geliştirmek çok daha fazla istemci işleyebilmesi olmasını sağlar.  
  
## <a name="restrictions-on-streamed-transfers"></a>Akış aktarımları kısıtlamalar  
 Akış aktarım modunu kullanarak ek kısıtlamalarını uygulamak çalışma süresi neden olur.  
  
 Akışlı bir aktarım gerçekleşen işlem giriş veya çıkış en fazla bir parametre ile bir sözleşme olabilir. Bu parametrenin tüm ileti gövdesi için karşılık gelen ve olmalıdır bir <xref:System.ServiceModel.Channels.Message>, bir tür türetilmiş <xref:System.IO.Stream>, veya bir <xref:System.Xml.Serialization.IXmlSerializable> uygulaması. Bir işlemin dönüş değeri bir output parametresi zorunda eşdeğerdir.  
  
 Bazı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenilir Mesajlaşma, işlemleri ve SOAP iletisi düzeyi güvenliği gibi özellikleri kullanan iletileri aktarımları için arabelleğe. Bu özellikleri kullanarak azaltın veya akış kullanılarak elde performans avantajı ortadan kaldırmak. Bir akış taşıma güvenliğini sağlamak için yalnızca aktarım düzeyinde güvenlik kullanın veya aktarım düzeyinde güvenlik artı yalnızca kimlik doğrulama ileti güvenliği kullanın.  
  
 Bile aktarım modu akış ayarlandığında SOAP üstbilgileri her zaman, arabelleğe alınmamış. Bir ileti için üstbilgiler boyutunu aşmamalıdır `MaxBufferSize` aktarım kotası. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Bu ayar, bkz. [taşıma kotaları](../../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
## <a name="differences-between-buffered-and-streamed-transfers"></a>Arabelleğe alınan ve akış aktarımı arasındaki farklar  
 Akışı arabelleğe aktarımı modundan değiştirme TCP ve adlandırılmış kanal taşımaları yerel kanal şeklini değiştirir. Arabelleğe alınan aktarımları için yerel kanal şeklin olduğu <xref:System.ServiceModel.Channels.IDuplexSessionChannel>. Yerel kanal akış aktarımları için olan <xref:System.ServiceModel.Channels.IRequestChannel> ve <xref:System.ServiceModel.Channels.IReplyChannel>. Bunlar kullanan mevcut bir uygulamayı aktarım modunda değiştirme taşımaları doğrudan (diğer bir deyişle, bir hizmet sözleşmesini üzerinden değil) beklenen kanal şekli kanal fabrikaları ve dinleyiciler için değiştirilmesi gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Akışı Etkinleştirme](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
