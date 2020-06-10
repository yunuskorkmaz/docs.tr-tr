---
title: Taşıma Kotaları
ms.date: 03/30/2017
helpviewer_keywords:
- transport quotas [WCF]
ms.assetid: 3e71dd3d-f981-4d9c-9c06-ff8abb61b717
ms.openlocfilehash: fca5fbeffb560f848edda6421301785f02547d2c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585707"
---
# <a name="transport-quotas"></a>Taşıma Kotaları
Taşıma kotaları, bir bağlantının aşırı kaynak tükettiği durumlarda karar vermeye yönelik bir ilke mekanizmasıdır. Kota değeri aşıldıktan sonra, kota, ek kaynakların kullanılmasını önleyen bir sabit sınırdır. Taşıma kotaları, kötü amaçlı veya istenmeden hizmet reddi saldırılarına engel olabilir.  
  
 Windows Communication Foundation (WCF) aktarımları, kaynakların koruyucu bir ayırmasını temel alan varsayılan kota değerlerine sahiptir. Bu varsayılan değerler, geliştirme ortamları ve küçük yükleme senaryoları için uygundur. Hizmet yöneticileri, bir yükleme kaynakları tükeniyorsa veya ek kaynakların kullanılabilirliğine karşın bağlantıların sınırlandırılmasıyla ilgili olarak, aktarım kotalarını gözden geçirmeli ve tek tek kota değerlerini ayarlamanıza gerekir.  
  
## <a name="types-of-transport-quotas"></a>Aktarım kotası türleri  
 WCF aktarımlarında üç tür kota vardır:  
  
- *Zaman aşımları* , kaynakları uzun bir süre için bağlama kullanan hizmet reddi saldırılarını azaltır.  
  
- *Bellek ayırma sınırları* , tek bir bağlantının sistem belleğini tüketmasını ve hizmetin diğer bağlantılara erişimini engeller.  
  
- *Koleksiyon boyutu sınırları* , dolaylı olarak bellek ayıran veya sınırlı TEDARİKTEKİ kaynakların tüketimine bağımlıdır.  
  
## <a name="transport-quota-descriptions"></a>Taşıma kotası açıklamaları  
 Bu bölümde standart WCF aktarımları için kullanılabilen aktarım kotaları açıklanmaktadır: HTTP (S), TCP/IP ve adlandırılmış kanallar. Özel aktarımlar, bu listede bulunmayan kendi yapılandırılabilir kotalarını açığa çıkarır. Kotaları hakkında bilgi edinmek için özel bir taşımanın belgelerine danışın.  
  
 Her kota ayarında bir tür, en düşük değer ve varsayılan değer vardır. Kotanın en büyük değeri, türü ile sınırlıdır. Makine sınırlamaları nedeniyle, en yüksek değere sahip bir kota ayarlamak her zaman mümkün değildir.  
  
|Name|Tür|Min.<br /><br /> değer|Varsayılan<br /><br /> değer|Açıklama|  
|----------|----------|--------------------|-----------------------|-----------------|  
|`ChannelInitializationTimeout`|TimeSpan|1 değer çizgisi|5 sn|İlk okuma sırasında girişin gönderilmesi için beklenecek en uzun süre. Bu veriler, kimlik doğrulaması gerçekleşmeden önce alınır. Bu ayar, kota değerinden genellikle daha küçüktür `ReceiveTimeout` .|  
|`CloseTimeout`|TimeSpan|0|1 dk|Aktarım bir özel durum harekete geçmeden önce bağlantının kapanması için beklenecek en uzun süre.|  
|`ConnectionBufferSize`|Tamsayı|1|8 KB|Temel alınan taşımanın iletim ve alma arabelleklerinin bayt cinsinden boyutu. Arabellek boyutunu artırmak, büyük iletileri gönderirken üretilen işi iyileştirebilir.|  
|`IdleTimeout`|TimeSpan|0|2 dk|Havuza alınmış bir bağlantının kapatılmadan önce boşta kalabileceği en uzun süre.<br /><br /> Bu ayar yalnızca havuza alınmış bağlantılar için geçerlidir.|  
|`LeaseTimeout`|TimeSpan|0|5 dakika|Etkin havuza alınmış bir bağlantının maksimum ömrü. Belirtilen süre dolduktan sonra, bağlantı geçerli istek verildikten sonra kapanır.<br /><br /> Bu ayar yalnızca havuza alınmış bağlantılar için geçerlidir.|  
|`ListenBacklog`|Tamsayı|1|10|Bu uç noktaya yönelik ek bağlantılar reddedilmez ve dinleyicinin izin verilebilmesi için en fazla bağlantı sayısı.|  
|`MaxBufferPoolSize`|Kalacağını|0|512 KB|Taşımanın yeniden kullanılabilir ileti arabelleklerini havuza aldığı bayt cinsinden maksimum bellek. Havuz bir ileti arabelleği sağlayamayabilir, geçici kullanım için yeni bir arabellek ayrılır.<br /><br /> Birçok kanal fabrikası veya dinleyicisi oluşturan Yüklemeler, arabellek havuzları için büyük miktarda bellek ayırabilir. Bu arabellek boyutunu azaltmak, Bu senaryodaki bellek kullanımını büyük ölçüde azaltabilir.|  
|`MaxBufferSize`|Tamsayı|1|64 KB|Akış verileri için kullanılan bir arabelleğin bayt cinsinden en büyük boyutu. Bu taşıma kotası ayarlanmamışsa veya aktarım akış kullanıyorsa, kota değeri `MaxReceivedMessageSize` Kota değeri ve ile aynı olur <xref:System.Int32.MaxValue> .|  
|`MaxOutboundConnectionsPerEndpoint`|Tamsayı|1|10|Belirli bir uç nokta ile ilişkilendirilebilen en fazla giden bağlantı sayısı.<br /><br /> Bu ayar yalnızca havuza alınmış bağlantılar için geçerlidir.|  
|`MaxOutputDelay`|TimeSpan|0|200 MS|Tek bir işlemde ek iletileri toplu işleme için bir gönderme işleminden sonra beklenecek en uzun süre. Temel alınan taşımanın arabelleği doluysa iletiler daha önce gönderilir. Ek iletiler gönderilmesi gecikme süresini sıfırlamaz.|  
|`MaxPendingAccepts`|Tamsayı|1|1|Dinleyicinin bekleyebilen kanallar için en fazla kabul etme sayısı.<br /><br /> Kabul etme tamamlanırken ve yeni bir kabul etme başlatılırken zaman aralığı vardır. Bu koleksiyon boyutunun artırılması, bu Aralık sırasında bağlanan istemcilerin bırakılmasına engel olabilir.|  
|`MaxPendingConnections`|Tamsayı|1|10|Dinleyicinin uygulama tarafından kabul edilmesini bekleye, en fazla bağlantı sayısı. Bu kota değeri aşıldığında, kabul edilmesini beklemek yerine yeni gelen bağlantılar bırakılır.<br /><br /> İleti güvenliği gibi bağlantı özellikleri istemcinin birden fazla bağlantı açmasına neden olabilir. Bu kota değerini ayarlarken hizmet yöneticileri bu ek bağlantıları dikkate almalıdır.|  
|`MaxReceivedMessageSize`|Kalacağını|1|64 KB|Aktarım bir özel durum harekete geçirdikten sonra, üstbilgiler dahil olmak üzere, alınan bir iletinin bayt cinsinden en büyük boyutu.|  
|`OpenTimeout`|TimeSpan|0|1 dk|Aktarım, bir özel durum harekete geçmeden önce bağlantı kurulması için beklenecek en uzun süre.|  
|`ReceiveTimeout`|TimeSpan|0|10 dakika|Aktarım bir özel durum harekete geçirdikten sonra okuma işleminin tamamlanmasını beklemek için beklenecek en uzun süre.|  
|`SendTimeout`|Timespan|0|1 dk|Aktarım bir özel durum harekete geçirmadan önce bir yazma işleminin tamamlanmasını beklemek için beklenecek en uzun süre.|  
  
 Taşıma kotaları `MaxPendingConnections` ve `MaxOutboundConnectionsPerEndpoint` `MaxConnections` bağlama veya yapılandırma aracılığıyla ayarlandığında adlı tek bir aktarım kotasına birleştirilir. Yalnızca Binding öğesi bu kota değerlerini ayrı ayrı ayarlamaya izin verir. `MaxConnections`Aktarım kotası aynı minimum ve varsayılan değerlere sahiptir.  
  
## <a name="setting-transport-quotas"></a>Aktarım kotalarını ayarlama  
 Taşıma kotaları, taşıma bağlama öğesi, aktarım bağlama, uygulama yapılandırması veya konak ilkesi aracılığıyla ayarlanır. Bu belge konak ilkesi üzerinden taşıma ayarlarını kapsamaz. Konak ilkesi kotaları ayarlarını saptamak için temel alınan taşımanın belgelerine başvurun. [Http ve https yapılandırma](configuring-http-and-https.md) konusunun http. sys sürücüsü için kota ayarları açıklanmaktadır. HTTP, TCP/IP ve adlandırılmış kanal bağlantılarında Windows sınırlarını yapılandırma hakkında daha fazla bilgi için Microsoft Bilgi Bankası 'Nda arama yapın.  
  
 Diğer kota türleri, aktarımlara dolaylı olarak uygulanır. Taşımanın bir iletiyi bayta dönüştürmek için kullandığı ileti Kodlayıcısı kendi kota ayarlarına sahip olabilir. Ancak, bu kotalar kullanılmakta olan taşımanın türünden bağımsızdır.  
  
### <a name="controlling-transport-quotas-from-the-binding-element"></a>Bağlama öğesinden aktarım kotalarını denetleme  
 Bağlama öğesi aracılığıyla aktarım kotalarını ayarlamak, taşımanın davranışını denetleme konusunda en büyük esnekliği sunar. Kapatma, açma, alma ve gönderme işlemleri için varsayılan zaman aşımları, bir kanal oluşturulduğunda bağlamadan alınır.  
  
|Name|HTTP|TCP/IP|Adlandırılmış kanal|  
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
  
### <a name="controlling-transport-quotas-from-the-binding"></a>Bağlamadan aktarım kotalarını denetleme  
 Bağlama aracılığıyla aktarım kotalarını ayarlamak, en yaygın kota değerlerine erişim sağlarken, ' ın arasından seçim yapmak için basitleştirilmiş bir kota kümesi sunar.  
  
|Name|HTTP|TCP/IP|Adlandırılmış kanal|  
|----------|----------|-------------|----------------|  
|`ChannelInitializationTimeout`||||  
|`CloseTimeout`|X|X|X|  
|`ConnectionBufferSize`||||  
|`IdleTimeout`||||  
|`LeaseTimeout`||||  
|`ListenBacklog`||X||  
|`MaxBufferPoolSize`|X|X|X|  
|`MaxBufferSize`|1|X|X|  
|`MaxOutboundConnectionsPerEndpoint`||2|2|  
|`MaxOutputDelay`||||  
|`MaxPendingAccepts`||||  
|`MaxPendingConnections`||2|2|  
|`MaxReceivedMessageSize`|X|X|X|  
|`OpenTimeout`|X|X|X|  
|`ReceiveTimeout`|X|X|X|  
|`SendTimeout`|X|X|X|  
  
1. `MaxBufferSize`Aktarım kotası yalnızca `BasicHttp` bağlamada kullanılabilir. `WSHttp`Bağlamalar akış aktarım modlarını desteklemeyen senaryolar içindir.  
  
2. Taşıma kotaları `MaxPendingConnections` ve `MaxOutboundConnectionsPerEndpoint` adlı tek bir aktarım kotasına birleştirilir `MaxConnections` .  
  
### <a name="controlling-transport-quotas-from-configuration"></a>Aktarım kotalarını yapılandırmadan denetleme  
 Uygulama yapılandırması, bir bağlamasındaki özelliklere doğrudan erişerek aynı aktarım kotalarını ayarlayabilir. Yapılandırma dosyalarında, bir aktarım kotasının adı her zaman küçük harfle başlar. Örneğin, `CloseTimeout` bir bağlamadaki özelliği `closeTimeout` yapılandırma ayarına karşılık gelir ve `MaxConnections` bir bağlamadaki özelliği `maxConnections` yapılandırma ayarına karşılık gelir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
