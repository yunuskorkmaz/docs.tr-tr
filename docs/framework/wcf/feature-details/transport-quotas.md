---
title: "Taşıma Kotaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: transport quotas [WCF]
ms.assetid: 3e71dd3d-f981-4d9c-9c06-ff8abb61b717
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4de910e2e66bc480abefe228bd183fe95270fb69
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="transport-quotas"></a>Taşıma Kotaları
Taşıma kotaları bağlantı aşırı kaynakları zaman tüketen karar verme bir ilke sistemdir. Bir kota kota değeri aşıldı sonra ek kaynakların kullanımını engelleyen bir sınıra sahiptir. Taşıma kotaları kötü amaçlı veya istenmeyen hizmet reddi saldırılarını önler.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]taşımalar koruyucu tahsis edilen kaynakların dayalı varsayılan kota değerlerini vardır. Bu varsayılan değerler, geliştirme ortamları ve küçük yükleme senaryoları için uygundur. Hizmet yöneticileri, taşıma kotaları gözden geçirin ve yüklemenin kaynakları tükendi çalıştırıyorsa veya ek kaynaklar kullanılabilirlik rağmen bağlantıları sınırlı tek tek kota değerlerini ayarlayın.  
  
## <a name="types-of-transport-quotas"></a>Taşıma kotaları türleri  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]taşıma kotaları üç tür vardır:  
  
-   *Zaman aşımları* kaynakları uzun bir süre için bağlamadan kullanan hizmet reddi saldırılarını etkisini azaltır.  
  
-   *Bellek ayırma sınırları* sistem belleği tüketilmesine neden olabilir ve diğer bağlantılar hizmeti reddetme tek bir bağlantı engelleme.  
  
-   *Koleksiyon boyutu sınırları* sınırlı tedarike dolaylı olarak bellek ayırma ya da kaynaklarının kullanımını bağlı.  
  
## <a name="transport-quota-descriptions"></a>Aktarım kotası açıklamaları  
 Bu bölüm için standart kullanılabilir taşıma kotaları açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] taşımaları: HTTP (S), TCP/IP ve adlandırılmış kanallar. Özel taşımaları bu listede yer almayan kendi yapılandırılabilir kotalar getirebilir. Kotalarını hakkında bilgi almak özel bir taşıma için belgelere bakın.  
  
 Her kota ayarı türü, minimum değer ve varsayılan değer var. Bir kota en büyük değerini kendi türüne göre sınırlıdır. Makine sınırlamaları nedeniyle, her zaman bir kota için maksimum değeri ayarlamak mümkün değildir.  
  
|Ad|Tür|Min.<br /><br /> value|Varsayılan<br /><br /> value|Açıklama|  
|----------|----------|--------------------|-----------------------|-----------------|  
|`ChannelInitializationTimeout`|TimeSpan|1 onay|5 saniye|İlk okuma sırasında girişin gönderilecek bir bağlantı için beklenecek en uzun süre. Kimlik doğrulaması gerçekleşmeden önce bu veri aldı. Bu ayar genellikle çok daha küçük `ReceiveTimeout` kota değeri.|  
|`CloseTimeout`|TimeSpan|0|1 dak|Bir bağlantı için bir özel durum taşıma oluşturmadan önce kapatmak beklenecek en uzun süre.|  
|`ConnectionBufferSize`|Tamsayı|1.|8 KB|, İletme bayt cinsinden boyutu ve arka plandaki aktarım arabelleklerini alabilirsiniz. Arabellek boyutunu artırmayı büyük iletileri gönderirken üretilen işi artırabilir.|  
|`IdleTimeout`|TimeSpan|0|2 min|Bir havuza alınan bağlantı kapalı önce boşta kalabileceği en uzun süre.<br /><br /> Bu ayar yalnızca havuza alınmış bağlantılara uygulanır.|  
|`LeaseTimeout`|TimeSpan|0|5 dk.|Etkin bir havuza alınan bağlantı en uzun kullanım ömrünü. Belirtilen süre geçtikten sonra geçerli istek hizmet sonra bağlantıyı kapatır.<br /><br /> Bu ayar yalnızca havuza alınmış bağlantılara uygulanır.|  
|`ListenBacklog`|Tamsayı|1.|10|Dinleyici ek bağlantılar, uç nokta için önce unserviced bağlantısı sayısı reddedilir.|  
|`MaxBufferPoolSize`|uzun|0|512 KB|Yeniden kullanılabilir ileti arabellek havuzu için taşıma düzeyde bayt cinsinden en yüksek bellek. İleti arabellek havuzu sağlayamıyor yeni bir arabellek geçici kullanım için ayrılır.<br /><br /> Birçok kanal fabrikaları veya dinleyicileri oluşturma yüklemeleri büyük miktarlarda bellek arabellek havuzu için tahsis edebilirsiniz. Bu arabellek boyutunu azaltma bellek kullanımı bu senaryoda önemli ölçüde azaltabilir.|  
|`MaxBufferSize`|Tamsayı|1.|64 KB|Veri akış için kullanılan arabelleğin bayt cinsinden en büyük boyutu. Bu aktarım kotası ayarlanmadı veya taşıma akış kullanmayan durumunda kota değeri küçük aynıdır, `MaxReceivedMessageSize` kota değeri ve <xref:System.Int32.MaxValue>.|  
|`MaxOutboundConnectionsPerEndpoint`|Tamsayı|1.|10|En fazla özel bir uç nokta ile ilişkilendirilebilir giden bağlantı sayısı.<br /><br /> Bu ayar yalnızca havuza alınmış bağlantılara uygulanır.|  
|`MaxOutputDelay`|TimeSpan|0|200 ms|Ek iletiler tek bir işlemde toplu işleme için gönderme işleminden sonra beklenecek en uzun süre. Arka plandaki aktarım arabellek dolarsa iletileri daha önce gönderilir. Ek ileti gönderme gecikme süresi sıfırlamaz.|  
|`MaxPendingAccepts`|Tamsayı|1.|1.|Maksimum sayısı için kanal dinleyicisi bekliyor olabilir kabul eder.<br /><br /> Bir accept tamamlama ve yeni başlangıç kabul arasında zaman aralığı yok. Bu koleksiyon boyutunu artırmayı bırakılan gelen bu aralığında bağlanan istemciler engelleyebilir.|  
|`MaxPendingConnections`|Tamsayı|1.|10|Uygulama tarafından kabul edilmesi için bekleyen dinleyicisi olabilir bağlantılarının maksimum sayısı. Bu kota değeri aşıldığında, yeni gelen bağlantıları bırakılan yerine kabul edilmesi için bekleniyor.<br /><br /> İleti güvenliği gibi bağlantı özellikleri birden fazla bağlantı açmak bir istemci neden olabilir. Hizmet yöneticileri bu ek bağlantılar için bu kota değeri ayarlanırken dikkate.|  
|`MaxReceivedMessageSize`|uzun|1.|64 KB|Bayt cinsinden üst bilgiler, özel bir durum taşıma oluşturmadan önce dahil olmak üzere bir alınan iletinin en büyük boyutu.|  
|`OpenTimeout`|TimeSpan|0|1 dak|Bir bağlantının önce taşıma kurulmasını beklemek için en uzun süre bir özel durum oluşturur.|  
|`ReceiveTimeout`|TimeSpan|0|10 min|Taşıma bir özel durum oluşturmadan önce bir okuma işlemin tamamlanması için beklenecek en uzun süre.|  
|`SendTimeout`|TimeSpan|0|1 dak|Önce aktarımı tamamlamak bir yazma işlemi için beklenecek en uzun süre bir özel durum oluşturur.|  
  
 Taşıma kotaları `MaxPendingConnections` ve `MaxOutboundConnectionsPerEndpoint` olarak adlandırılan tek aktarım kota birleştirilir `MaxConnections` bağlama veya yapılandırma ayarlandığında. Bu kota değerlerini ayrı ayrı ayarı yalnızca bağlama öğesi sağlar. `MaxConnections` Aktarım kotası minimum ve varsayılan değerlere sahip.  
  
## <a name="setting-transport-quotas"></a>Ayar taşıma kotaları  
 Taşıma kotaları aktarım bağlama öğesi, aktarım bağlama, uygulama yapılandırması veya ana bilgisayar ilkesine ayarlanır. Bu belge ana bilgisayar ilkesi aracılığıyla ayarı taşımaları kapsamaz. Ana bilgisayar ilkesi kotaları ayarlarını bulmak temel aktarımı belgelerine bakın. [Yapılandırma HTTP ve HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md) konu Http.sys sürücüsünü için kota ayarları açıklar. Windows'u yapılandırma hakkında daha fazla bilgi için Microsoft Bilgi Bankası arama HTTP, TCP/IP'yi ve adlandırılmış kanal bağlantılarına sınırlar.  
  
 Diğer türler kotaları dolaylı olarak aktarımları için geçerlidir. Bir ileti baytlara dönüştürmek için taşıma kullanır ileti Kodlayıcı kendi kota ayarları olabilir. Ancak, bu kotalar kullanılan aktarım türünü bağımsızdır.  
  
### <a name="controlling-transport-quotas-from-the-binding-element"></a>Taşıma kotaları bağlama öğeden denetleme  
 Bağlama öğesi aracılığıyla taşıma kotaları ayarlama taşıma'nin davranışını denetleme içindeki en büyük esnekliği sağlar. Varsayılan zaman aşımlarını, alma, Aç, Kapat ve bir kanal yapılandırıldığında işlemleri bağlamayı alınır gönderin.  
  
|Ad|HTTP|TCP/IP|Adlandırılmış kanal|  
|----------|----------|-------------|----------------|  
|`ChannelInitializationTimeout`||X|X|  
|`CloseTimeout`||||  
|`ConnectionBufferSize`||X|X|  
|`IdleTimeout`||X|X|  
|`LeaseTimeout`||X||  
|`ListenBacklog`||X||  
|`MaxBufferPoolSize`|X|X|X|  
|`MaxBufferSize`|X|X|X|  
|`MaxOutboundConnectionsPerEndpoint`||X|X|  
|`MaxOutputDelay`||X|X|  
|`MaxPendingAccepts`||X|X|  
|`MaxPendingConnections`||X|X|  
|`MaxReceivedMessageSize`|X|X|X|  
|`OpenTimeout`||||  
|`ReceiveTimeout`||||  
|`SendTimeout`||||  
  
### <a name="controlling-transport-quotas-from-the-binding"></a>Taşıma kotaları bağlama gelen denetleme  
 Bağlama aracılığıyla taşıma kotaları ayarlama hala yaygın kota değerlerini erişim verilirken aralarından seçim yapabileceğiniz kotalarını basitleştirilmiş bir dizi sunar.  
  
|Ad|HTTP|TCP/IP|Adlandırılmış kanal|  
|----------|----------|-------------|----------------|  
|`ChannelInitializationTimeout`||||  
|`CloseTimeout`|X|X|X|  
|`ConnectionBufferSize`||||  
|`IdleTimeout`||||  
|`LeaseTimeout`||||  
|`ListenBacklog`||X||  
|`MaxBufferPoolSize`|X|X|X|  
|`MaxBufferSize`|1.|X|X|  
|`MaxOutboundConnectionsPerEndpoint`||2|2|  
|`MaxOutputDelay`||||  
|`MaxPendingAccepts`||||  
|`MaxPendingConnections`||2|2|  
|`MaxReceivedMessageSize`|X|X|X|  
|`OpenTimeout`|X|X|X|  
|`ReceiveTimeout`|X|X|X|  
|`SendTimeout`|X|X|X|  
  
1.  `MaxBufferSize` Aktarım kotası kullanılabilir ise yalnızca `BasicHttp` bağlama. `WSHttp` Bağlamaları için akış aktarım modları desteklemeyen senaryolar vardır.  
  
2.  Taşıma kotaları `MaxPendingConnections` ve `MaxOutboundConnectionsPerEndpoint` olarak adlandırılan tek aktarım kota birleştirilir `MaxConnections`.  
  
### <a name="controlling-transport-quotas-from-configuration"></a>Taşıma kotaları yapılandırmasından denetleme  
 Uygulama yapılandırması, bir bağlama özellikleri doğrudan erişimini olarak aynı taşıma kotaları ayarlayabilirsiniz. Yapılandırma dosyalarında bir aktarım kotasına adını her zaman küçük harfle başlar. Örneğin, `CloseTimeout` bağlama özelliğine karşılık gelir `closeTimeout` yapılandırmasında ayarlama ve `MaxConnections` karşılık gelen bir bağlama özellikte `maxConnections` yapılandırmasında ayarlama.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
