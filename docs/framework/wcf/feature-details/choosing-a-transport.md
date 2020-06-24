---
title: Taşıma Seçme
description: 'WCF tarafından sunulan ana aktarımlar arasında seçim yapma ölçütü hakkında bilgi edinin: HTTP, TCP ve adlandırılmış kanallar.'
ms.date: 03/30/2017
helpviewer_keywords:
- choosing transports [WCF]
ms.assetid: b169462b-f7b6-4cf4-9fca-d306909ee8bf
ms.openlocfilehash: e1a92203de25aa399316eea91a758802768442a0
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247500"
---
# <a name="choosing-a-transport"></a>Taşıma Seçme
Bu konu, Windows Communication Foundation (WCF) ' de yer alan üç ana taşıma arasında seçim yapma ölçütlerini anlatmaktadır: HTTP, TCP ve adlandırılmış kanallar. WCF Ayrıca bir Message Queuing (MSMQ olarak da bilinir) taşıması içerir, ancak bu belge Message Queuing 'i kapsamaz.  
  
 WCF programlama modeli, uç nokta işlemlerini (bir hizmet sözleşmesinde gösterildiği gibi) iki uç noktayı bağlayan taşıma mekanizmasından ayırır. Bu, hizmetlerinizi ağa sunmaya nasıl karar vereceğinize ilişkin esneklik sağlar.  
  
 WCF 'de, *bağlama öğelerinden*oluşan bir diziyle oluşturulan *bağlama*kullanarak, bir ağ üzerinde nasıl veri aktaracağınızla belirlenir. Bir aktarım, bağlamanın bir parçası olan bir aktarım bağlama öğesi tarafından temsil edilir. Bağlama, güvenlik, gerekli bir ileti Kodlayıcısı bağlama öğesi ve gerekli bir aktarım bağlama öğesi gibi isteğe bağlı protokol bağlama öğelerini içerir. Bir aktarım, başka bir uygulamadan veya bir iletinin seri hale getirilmiş formunu gönderir veya alır.  
  
 Var olan bir istemciye veya sunucuya bağlanmanız gerekiyorsa, belirli bir aktarımı kullanma seçeneğiniz olmayabilir. Ancak, WCF Hizmetleri, her biri farklı bir taşıma ile birden fazla uç nokta aracılığıyla erişilebilir hale getirilebilir. Tek bir taşıma hizmetinize yönelik hedef kitleyi kapsamıyorsa, hizmeti birden fazla uç nokta üzerinden kullanıma sunma seçeneğini göz önünde bulundurun. İstemci uygulamaları daha sonra kendileri için en iyi uç noktayı kullanabilir.  
  
 Bir taşıma seçtikten sonra, onu kullanan bir bağlama seçmelisiniz. Sistem tarafından sağlanmış bir bağlama (bkz. [sistem tarafından sağlanmış bağlamalar](../system-provided-bindings.md)) seçebilir veya kendi özel bağlamlarınızı oluşturabilirsiniz (bkz. [Özel Bağlamalar](../extending/custom-bindings.md)). Kendi bağlamalarınızı da oluşturabilirsiniz. Daha fazla bilgi için bkz. [Kullanıcı Tanımlı Bağlamalar Oluşturma](../extending/creating-user-defined-bindings.md).  
  
## <a name="advantages-of-each-transport"></a>Her bir taşımanın avantajları  
 Bu bölümde, aralarında seçim yapmak üzere ayrıntılı bir karar grafiği de dahil olmak üzere üç ana aktarımdan birini seçmek için başlıca nedenler açıklanmaktadır.  
  
### <a name="when-to-use-http-transport"></a>HTTP taşıması ne zaman kullanılır?  
 HTTP, istemciler ve sunucular arasında bir istek/yanıt protokolüdür. En yaygın uygulama, bir Web sunucusuyla iletişim kuran Web tarayıcısı istemcilerinden oluşur. İstemci, istemci isteği iletilerini dinleyen bir sunucuya istek gönderir. Sunucu bir istek aldığında, isteğin durumunu içeren bir yanıt döndürür. Başarılı olursa, bir Web sayfası, bir hata iletisi veya diğer bilgiler gibi isteğe bağlı veriler döndürülür. HTTP protokolü hakkında daha fazla bilgi için bkz. [http-HyperText aktarım protokolü](https://www.w3.org/Protocols/).  
  
 HTTP protokolü bağlantı tabanlı değil — yanıt gönderildikten sonra durum korunmaz. Birden çok sayfalı işlemleri işlemek için, uygulamanın gerekli tüm durumları kalıcı hale getirilmesi gerekir.  
  
 WCF 'de HTTP taşıma bağlaması, eski WCF olmayan sistemlerle birlikte çalışabilirlik için iyileştirilmiştir. İletişim kuran tüm taraflar WCF kullanıyorsa, TCP tabanlı veya adlandırılmış kanallar tabanlı bağlamalar daha hızlıdır. Daha fazla bilgi için <xref:System.ServiceModel.NetTcpBinding> ve <xref:System.ServiceModel.NetNamedPipeBinding> bölümlerine bakın.  
  
### <a name="when-to-use-the-tcp-transport"></a>TCP aktarımı ne zaman kullanılır?  
 TCP, uçtan uca hata algılama ve düzeltme ile bağlantı tabanlı, akış odaklı bir dağıtım hizmetidir. *Bağlantı tabanlı* , konaklar arasındaki bir iletişim oturumunun veri değiş tokuşu yapılmadan önce kurulması anlamına gelir. Ana bilgisayar, bir mantıksal IP adresi tarafından tanımlanan TCP/IP ağındaki herhangi bir cihazdır.  
  
 TCP, güvenilir veri teslimi ve kullanım kolaylığı sağlar. Özellikle TCP, Paket teslimi gönderisini bilgilendirir, paketlerin gönderildikleri sırada teslim edilmesini garanti eder, kayıp paketleri yeniden iletir ve veri paketlerinin çoğaltılmamasını sağlar. Bu güvenilir teslimin iki TCP/IP düğümü arasında uygulandığını ve hangi ara düğümlerin dahil ettiğine bakılmaksızın uç noktalar arasında geçerli olan *WS-ReliableMessaging*ile aynı şey olmadığını unutmayın.  
  
 WCF TCP taşıması, iletişimin her iki ucunun de WCF kullandığı senaryo için en iyi duruma getirilmiştir. Bu bağlama, farklı makineler arasında iletişim kuran senaryolar için en hızlı WCF bağlamasıdır. İleti alışverişi, <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> iyileştirilmiş ileti aktarımı için kullanır. TCP çift yönlü iletişim sağlar ve bu nedenle, istemci ağ adresi çevirisi (NAT) arkasında olsa bile çift yönlü sözleşmeleri uygulamak için kullanılabilir.  
  
### <a name="when-to-use-the-named-pipe-transport"></a>Adlandırılmış kanal taşıması ne zaman kullanılır?  
 Adlandırılmış kanal, Windows işletim sistemi çekirdekte, işlemlerin iletişim için kullanabileceği paylaşılan belleğin bir bölümü gibi bir nesnedir. Adlandırılmış kanal bir ada sahiptir ve tek bir makinedeki süreçler arasındaki tek yönlü veya çift yönlü iletişim için kullanılabilir.  
  
 Tek bilgisayardaki farklı WCF uygulamaları arasında iletişim gerektiğinde ve başka bir makineden gelen iletişimi engellemek istediğinizde, adlandırılmış kanallar aktarımını kullanın. Ek bir kısıtlama, yükseltilmiş ayrıcalıklara sahip olmadıkları müddetçe Windows Uzak Masaüstü ile çalışan işlemlerin aynı Windows Uzak Masaüstü oturumuyla sınırlı olabileceğini de sağlar.  
  
> [!WARNING]
> IIS 'de barındırılan birden çok sitede zayıf bir joker karakterli URL ayırması ile adlandırılmış kanal aktarımını kullanırken şu hata oluşabilir: ' 2 ' sitesini dinlemeye çalışırken ' net. pipe ' protokolünün ' Netpipeactivation ' etkinleştirme hizmetinde bir hata oluştu, bu nedenle protokol site için geçici olarak devre dışı bırakıldı. Daha fazla ayrıntı için özel durum iletisine bakın. URL: WeakWildcard: net. pipe:/ \<machine name> /durum: ConflictingRegistration özel durumu: Işlem adı: SMSvcHost Işlem kimliği: 1076 \  
  
## <a name="decision-points-for-choosing-a-transport"></a>Taşıma seçme için karar noktaları  
 Aşağıdaki tabloda, bir taşıma seçmek için kullanılan yaygın karar noktaları açıklanmaktadır. Uygulamanıza uygulanan ek öznitelikleri ve taşımaları göz önünde bulundurmanız gerekir. Uygulamanız için önemli olan öznitelikleri belirleyin, favorably ilişkilendirmekte olan taşımaları belirleyin ve ardından öznitelik kümesi ile en iyi şekilde çalışan taşımaları seçin.  
  
|Öznitelik|Açıklama|Sık sık kırmızı aktarımlar|  
|---------------|-----------------|------------------------|  
|Tanılama|Tanılama, aktarım bağlantı sorunlarını otomatik olarak algılamanıza olanak tanır. Tüm aktarımlar, bağlantıyı açıklayan hata bilgilerini geri gönderme olanağını destekler. Ancak, WCF ağ sorunlarını araştırmak için tanılama araçları içermez.|Yok|  
|Hosting|Tüm WCF uç noktaları, bir uygulama içinde barındırılmalıdır. IIS 6,0 ve önceki sürümler yalnızca HTTP taşımasını kullanan uygulamaları destekler. Windows Vista 'da, TCP ve adlandırılmış kanallar dahil olmak üzere tüm WCF taşımalarını barındırmak için destek eklenmiştir. Daha fazla bilgi için bkz. [Windows Işlem etkinleştirme hizmetinde](hosting-in-windows-process-activation-service.md) [barındırma Internet Information Services](hosting-in-internet-information-services.md) ve barındırma.|HTTP|  
|İncelemesi|İnceleme, iletim sırasında iletilerden bilgi ayıklama ve işleme olanağıdır. HTTP protokolü, Yönlendirme ve denetim bilgilerini verilerden ayırır, böylece iletileri denetleyen ve çözümleyen araçların oluşturulması kolaylaşır. İncelemesi kolay olan aktarımlar, ağ gereçlerinde daha az işlem gücü gerektirebilir. Kullanılan güvenlik düzeyi, iletilerin incelenemeyeceğini etkiler.|HTTP|  
|Gecikme süresi|Gecikme süresi, bir ileti alışverişinin tamamlanışında gereken en kısa süredir. Tüm ağ işlemleri, taşıma seçimine bağlı olarak daha fazla veya daha az gecikme süresine sahiptir. Yerel ileti değişimi deseninin istek-Yanıtla (HTTP gibi) istek yanıtı olduğu bir aktarımla çift yönlü veya tek yönlü iletişim kullanmak, iletilerin zorla bağıntısı nedeniyle ek gecikmeye neden olabilir. Bu durumda, yerel ileti değişimi deseninin TCP gibi çift yönlü olduğu bir taşıma kullanmayı düşünün.|TCP, adlandırılmış<br /><br /> Kapatıldığı|  
|Reach|Bir taşımanın bağlantısı, taşımanın diğer sistemlerle ne kadar uyumlu olduğunu yansıtır. Adlandırılmış kanal aktarımında çok az erişim vardır; yalnızca aynı makinede çalışan hizmetlere bağlanabilir. TCP ve HTTP aktarımları için her ikisi de mükemmel bir erişime sahiptir ve bazı NAT ve güvenlik duvarı yapılandırmalarına sızma edebilir. Daha fazla bilgi için bkz. [NAT ve güvenlik duvarları Ile çalışma](working-with-nats-and-firewalls.md).|HTTP, TCP|  
|Güvenlik|Güvenlik, gizlilik, bütünlük veya kimlik doğrulaması sağlayarak aktarım sırasında iletileri koruma yeteneğidir. Gizlilik bir iletinin incelenmeden korunmasını, bütünlüğünden bir iletinin değiştirilmesini koruduğunu ve kimlik doğrulamasının, iletinin göndereni veya alıcısı hakkında bilgi verir.<br /><br /> WCF, hem ileti düzeyinde hem de Aktarım düzeyinde aktarım güvenliğini destekler. İleti güvenliği, aktarım, arabelleğe alınmış bir aktarım modunu destekliyorsa bir aktarımla birlikte oluşturur. Taşıma güvenliği için destek, seçilen aktarıma göre farklılık gösterir. HTTP, TCP ve adlandırılmış kanal aktarımları, aktarım güvenliği için desteğiyle makul bir eşliği vardır.|Tümü|  
|Aktarım hızı|Verimlilik, belirli bir süre içinde iletilebilecek ve işlenebileceğiniz veri miktarını ölçer. Gecikme süresi gibi, seçilen aktarım hizmeti işlemleri için aktarım hızını etkileyebilir. Bir taşımanın aktarım hızını en üst düzeye çıkarmak, içerik iletme yükünün yanı sıra ileti alışverişinin tamamlanması için beklerken geçen süreyi en aza indirmenizi gerektirir. Hem TCP hem de adlandırılmış kanal aktarımları, ileti gövdesine çok fazla yük ekler ve ileti yanıtlarının beklenme şeklini azaltan yerel bir çift yönlü şekli destekler.|TCP, adlandırılmış kanal|  
|Araçlar|Tooling, geliştirme, tanılama, barındırma ve diğer etkinlikler için bir protokol için üçüncü taraf uygulama desteğini temsil eder. HTTP protokolüyle birlikte çalışmak için araç ve yazılım geliştirme, özellikle büyük bir yatırım anlamına gelir.|HTTP|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSDualHttpBinding>
- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- [Bağlamalar](bindings.md)
- [Sistem tarafından sağlanmış bağlamalar](../system-provided-bindings.md)
- [Kullanıcı Tanımlı Bağlamalar Oluşturma](../extending/creating-user-defined-bindings.md)
