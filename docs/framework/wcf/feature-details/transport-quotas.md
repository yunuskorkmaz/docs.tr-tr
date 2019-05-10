---
title: Taşıma Kotaları
ms.date: 03/30/2017
helpviewer_keywords:
- transport quotas [WCF]
ms.assetid: 3e71dd3d-f981-4d9c-9c06-ff8abb61b717
ms.openlocfilehash: a40fa9beec1eabeb02c6ccc4e2ab8179aa49288c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64585781"
---
# <a name="transport-quotas"></a>Taşıma Kotaları
Taşıma kotaları bağlantı aşırı kaynakları tüketen ne zaman karar için bir ilke mekanizmasıdır. Kota kota değeri aşıldı sonra ek kaynaklar kullanımını engelleyen bir sınıra sahiptir. Taşıma kotaları kötü amaçlı veya istenmeyen hizmet reddi saldırılarını engeller.  
  
 Windows Communication Foundation (WCF) taşımalar koruyucu tahsis edilen kaynakların dayalı varsayılan kota değerlerini sahip. Bu varsayılan değerler, geliştirme ortamları ve küçük yükleme senaryoları için uygundur. Hizmet yöneticileri taşıma kotaları gözden geçirmeniz ve kaynaklar yetersiz bir yüklemesi çalışıyor veya ek kaynakların kullanılabilirliğini rağmen bağlantı sınırlı kotaya değerleri ayarlayın.  
  
## <a name="types-of-transport-quotas"></a>Taşıma kotaları türleri  
 WCF taşımalar kotalar üç tür vardır:  
  
- *Zaman aşımları* uzun bir süre için kaynakları bağlamadan üzerinde kullanan hizmet reddi saldırılarını azaltın.  
  
- *Bellek ayırma sınırı* engelle tüketme sistem belleği ve diğer bağlantıları için hizmet engelleme tek bir bağlantı.  
  
- *Koleksiyon boyutu sınırları* içinde sınırlı kaynağı dolaylı olarak bellek ya da kaynakların tüketimini bağlı.  
  
## <a name="transport-quota-descriptions"></a>Aktarım kotası açıklamaları  
 Bu bölümde, standart WCF taşımalar için kullanılabilir taşıma kotaları açıklanmaktadır: HTTP (S), TCP/IP ve adlandırılmış kanallar. Özel aktarımları bu listede yer almayan kendi yapılandırılabilir kotalar getirebilir. Kotalarını hakkında bilgi almak özel bir taşıma belgelerine bakın.  
  
 Her kota ayarı türü, minimum değer ve varsayılan değeri var. Kota en yüksek değeri kendi türüne göre sınırlıdır. Makine sınırlamaları nedeniyle, bu her zaman bir kota için maksimum değeri ayarlamak mümkün değildir.  
  
|Ad|Tür|Min.<br /><br /> value|Varsayılan<br /><br /> value|Açıklama|  
|----------|----------|--------------------|-----------------------|-----------------|  
|`ChannelInitializationTimeout`|TimeSpan|1 değer çizgisi|5 sn|İlk okuma sırasında giriş gönderilecek bir bağlantı için beklenecek en uzun süre. Kimlik doğrulaması gerçekleşmeden önce bu verileri alınır. Bu ayar genellikle daha küçüktür `ReceiveTimeout` kota değeri.|  
|`CloseTimeout`|TimeSpan|0|1 dakika|Bir bağlantı için bir özel durum taşıma yükseltmeden önce kapatmak beklenecek en uzun süre.|  
|`ConnectionBufferSize`|Tamsayı|1.|8 KB|, İletme bayt cinsinden boyut ve temel alınan aktarımda arabelleklerini alabilirsiniz. Arabellek boyutunu artırmayı büyük iletileri gönderirken, aktarım hızı artırabilir.|  
|`IdleTimeout`|TimeSpan|0|2 dk|Havuza alınan bağlantı kapatıldı önce boşta kalacağını en uzun süre.<br /><br /> Bu ayar yalnızca, havuza alınmış bağlantıları için de geçerlidir.|  
|`LeaseTimeout`|TimeSpan|0|5 dakika|Etkin bir havuza alınmış bağlantı en fazla ömrü. Belirtilen süre geçtikten sonra geçerli istek hizmet sonra bağlantıyı kapatır.<br /><br /> Bu ayar yalnızca, havuza alınmış bağlantıları için de geçerlidir.|  
|`ListenBacklog`|Tamsayı|1.|10|Dinleyici için bu endpoint ek bağlantılar önce unserviced bağlantı sayısı üst sınırı reddedilir.|  
|`MaxBufferPoolSize`|Uzun|0|512 KB|Taşıma, yeniden kullanılabilir ileti arabellek havuzu için düzeyde bayt cinsinden en yüksek bellek. İleti arabellek havuzu sağlayamazsınız, yeni bir arabellek geçici kullanım için ayrılır.<br /><br /> Pek çok kanal fabrikaları veya dinleyicileri oluşturma yüklemeler arabellek havuzu için büyük miktarlarda bellek ayırabilirsiniz. Bu arabellek boyutunu azaltma, bu senaryoda bellek kullanımı önemli ölçüde azaltabilir.|  
|`MaxBufferSize`|Tamsayı|1.|64 KB|Akış verileri için kullanılan arabelleğin bayt cinsinden en büyük boyutu. Bu aktarım kotası ayarlı değil, ya da akış taşıma kullanmıyor durumunda kota değeri küçük aynıdır, `MaxReceivedMessageSize` kota değeri ve <xref:System.Int32.MaxValue>.|  
|`MaxOutboundConnectionsPerEndpoint`|Tamsayı|1.|10|Belirli bir uç nokta ile ilişkilendirilebilir giden bağlantıları sayısı.<br /><br /> Bu ayar yalnızca, havuza alınmış bağlantıları için de geçerlidir.|  
|`MaxOutputDelay`|TimeSpan|0|200 ms|Ek iletiler tek bir işlemde toplu işleme için bir gönderme işlemi sonra beklenecek en uzun süre. Temel alınan aktarımda arabelleğinin dolarsa iletileri daha önce gönderilir. Ek ileti gönderme, gecikme süresi sıfırlanmaz.|  
|`MaxPendingAccepts`|Tamsayı|1.|1.|Sayısı kanallar için Dinleyicide bekleyen olduğunu kabul eder.<br /><br /> Bir accept tamamladıktan ve yeni başlangıç kabul arasındaki zaman aralığı yok. Bu koleksiyon boyutunu artırmayı bırakılmakta öğesinden bu aralık sırasında bağlanan istemciler engelleyebilirsiniz.|  
|`MaxPendingConnections`|Tamsayı|1.|10|Dinleyici uygulama tarafından kabul edilmeyi bekliyor olabilir bağlantılarının maksimum sayısı. Bu kota değeri aşıldığında, yeni gelen bağlantılar kesilir yerine kabul edilmeyi bekliyor.<br /><br /> Bağlantı özellikleri ileti güvenliği gibi birden fazla bağlantı açmak bir istemci neden olabilir. Hizmet yöneticileri, bu ek bağlantılar için bu kota değeri ayarlarken hesap.|  
|`MaxReceivedMessageSize`|Uzun|1.|64 KB|Bayt cinsinden aktarım özel durum harekete önce başlıkları dahil alınan iletinin en büyük boyutu.|  
|`OpenTimeout`|TimeSpan|0|1 dakika|Aktarım, özel durum harekete önce kurulan bir bağlantı için beklenecek en uzun süre.|  
|`ReceiveTimeout`|TimeSpan|0|10 dakikalık|Taşıma bir özel durum oluşturmadan önce tamamlamak okuma işlemi için beklenecek en uzun süre.|  
|`SendTimeout`|Zaman aralığı|0|1 dakika|Aktarım, özel durum harekete önce tamamlanması gereken bir yazma işlemi için beklenecek en uzun süre.|  
  
 Taşıma kotaları `MaxPendingConnections` ve `MaxOutboundConnectionsPerEndpoint` adlı bir tek aktarım kotası birleştirilir `MaxConnections` bağlama veya yapılandırma ayarlandığında. Yalnızca bağlama öğesi, özel olarak bu kota değerlerini ayrı ayrı ayarlamaya izin verir. `MaxConnections` Aktarım kotası, minimum ve varsayılan değerlerine sahip.  
  
## <a name="setting-transport-quotas"></a>Taşıma kotaları ayarlama  
 Taşıma kotaları aktarım bağlama öğesi, aktarım bağlama, uygulama yapılandırması veya ana bilgisayar ilkesine ayarlanır. Bu belge, ana bilgisayar ilkesi aracılığıyla ayarı taşımalar kapsamaz. Ana bilgisayar ilkesi kotalar ayarlarını bulmak temel alınan aktarımda belgelerine bakın. [Yapılandırma HTTP ve HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md) konu, Http.sys sürücüsü için kota ayarları açıklar. Windows yapılandırma hakkında daha fazla bilgi için Microsoft Bilgi Bankası arama HTTP, TCP/IP'yi ve adlandırılmış kanal bağlantılarına sınırlar.  
  
 Diğer tip kotalar taşımalarına dolaylı olarak uygulanır. Bir iletiyi baytlara dönüştürmek için taşıma kullanan ileti Kodlayıcı kendi kota ayarları olabilir. Ancak, bu kotalar kullanılan taşıma türü bağımsızdır.  
  
### <a name="controlling-transport-quotas-from-the-binding-element"></a>Taşıma kotaları bağlama öğesinden denetleme  
 Taşıma kotaları bağlama öğesi aracılığıyla ayarı taşıma ait davranışı denetlemek, en büyük esnekliği sunar. Varsayılan zaman aşımlarını, alma, açık, kapatın ve kanal oluşturulduğunda operations bağlamayı alınır gönderin.  
  
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
 Taşıma kotaları ayarlama bağlama aracılığıyla yine de en sık karşılaşılan kota değerlerine erişim sağlarken aralarından seçim yapabileceğiniz kotalar basitleştirilmiş bir dizi sunar.  
  
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
  
1. `MaxBufferSize` Aktarım kotası kullanılabilir ise yalnızca `BasicHttp` bağlama. `WSHttp` Bağlamaları akış aktarım modu desteği olmayan senaryolar için vardır.  
  
2. Taşıma kotaları `MaxPendingConnections` ve `MaxOutboundConnectionsPerEndpoint` adlı bir tek aktarım kotası birleştirilir `MaxConnections`.  
  
### <a name="controlling-transport-quotas-from-configuration"></a>Taşıma kotaları yapılandırmasından denetleme  
 Uygulama yapılandırması, doğrudan bir bağlaması üzerindeki özelliklerine erişme olarak aynı taşıma kotaları ayarlayabilirsiniz. Yapılandırma dosyalarında aktarım kotası adını her zaman küçük harfle başlar. Örneğin, `CloseTimeout` karşılık gelen bir bağlama özelliği `closeTimeout` yapılandırmasında ayarlama ve `MaxConnections` karşılık gelen bir bağlama özelliği `maxConnections` yapılandırmasında ayarlama.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
