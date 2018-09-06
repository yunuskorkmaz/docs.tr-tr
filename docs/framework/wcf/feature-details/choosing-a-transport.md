---
title: Taşıma Seçme
ms.date: 03/30/2017
helpviewer_keywords:
- choosing transports [WCF]
ms.assetid: b169462b-f7b6-4cf4-9fca-d306909ee8bf
ms.openlocfilehash: c98fd4bb76074c2d96b702a37bf1964600d365e3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864634"
---
# <a name="choosing-a-transport"></a>Taşıma Seçme
Windows Communication Foundation (WCF) içerdiği üç ana taşımalar arasından seçim ölçütleri bu konuda ele alınmıştır: HTTP, TCP ve adlandırılmış kanallar. WCF de içeren bir message queuing (MSMQ olarak da bilinir) taşıma, ancak message queuing bu belgede ele alınmamaktadır.  
  
 WCF programlama modeli, iki uç nokta bağlanan taşıma düzeneğinden uç nokta işlemleri (bir hizmet sözleşmesi içerisinde ifade edilen) ayırır. Bu, hizmetlerinizi ağa nasıl sunacağınızı öğrenin karar verme esnekliğine sağlar.  
  
 WCF'de, belirttiğiniz kullanarak uç noktalar arasında bir ağ üzerinden veri aktarmak nasıl bir *bağlama*, bir dizi yapılan *bağlama öğelerinin*. Aktarım bağlama parçası olan bir aktarım bağlama öğesi tarafından temsil edilir. Bir bağlama güvenlik gibi isteğe bağlı Protokolü bağlama öğeleri, gerekli ileti Kodlayıcı bağlama öğesi ve gerekli aktarım bağlama öğesi içerir. Bir taşıma gönderir veya için veya başka bir uygulamadan bir ileti seri hala getirilmiş biçimini alır.  
  
 Bir mevcut istemci veya sunucu bağlanmanız durumunda, belirli taşıma kullanma hakkında bir seçim olmayabilir. Ancak, WCF hizmetleri birden fazla uç noktası, her biri farklı bir aktarım üzerinden erişilebilir hale getirilebilir. Tek bir aktarım hizmetiniz için hedef kitle ele alınmamaktadır, hizmet birden fazla uç nokta kullanıma sunma göz önünde bulundurun. İstemci uygulamaları, daha sonra bunlar için en iyi uç noktası kullanabilirsiniz.  
  
 Bir taşıma seçtikten sonra bunu kullanan bir bağlama seçmeniz gerekir. Sistem tarafından sağlanan bir bağlamayı tercih edebilirsiniz (bkz [System-Provided bağlamaları](../../../../docs/framework/wcf/system-provided-bindings.md)), veya kendi özel bağlama oluşturabilirsiniz (bkz [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)). Ayrıca, kendi bağlama oluşturabilirsiniz. Daha fazla bilgi için [Creating User-Defined bağlamaları](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
## <a name="advantages-of-each-transport"></a>Her aktarım avantajları  
 Bu bölümde, bunlar arasında seçmeye yönelik bir ayrıntılı karar grafiği dahil olmak üzere üç ana taşımalar herhangi birini seçerek ana nedeni açıklanmaktadır.  
  
### <a name="when-to-use-http-transport"></a>Ne zaman HTTP aktarımı kullanın  
 İstemciler ve sunucular arasındaki bir istek/yanıt protokol HTTP'dir. En yaygın uygulama bir Web sunucusu ile iletişim kuran Web tarayıcısı istemcileri oluşur. İstemci, istemci istek iletileri dinler bir sunucuya bir isteği gönderir. Sunucu bir istek aldığında, istek durumunu içeren bir yanıt döndürür. Başarılı olursa, bir Web sayfası, bir hata iletisi veya diğer bilgileri gibi isteğe bağlı verileri döndürülür. HTTP protokolü hakkında daha fazla bilgi için bkz: [HTTP - Köprü Metni Aktarım Protokolü](https://go.microsoft.com/fwlink/?LinkId=94858).  
  
 HTTP protokolü bağlantı tabanlı değildir — yanıt gönderildikten sonra yok durumu korunur. Uygulama, çok sayfalı işlemleri işlemek için gerekli olan herhangi bir durumu kalıcı gerekir.  
  
 Wcf'de HTTP aktarım bağlama WCF olmayan eski sistemleri ile birlikte çalışabilirlik için getirilmiştir. WCF iletişim kuran tüm tarafları kullanıyorsanız, TCP tabanlı veya adlandırılmış kanallar tabanlı bağlamalar daha hızlıdır. Daha fazla bilgi için bkz. <xref:System.ServiceModel.NetTcpBinding> ve <xref:System.ServiceModel.NetNamedPipeBinding>.  
  
### <a name="when-to-use-the-tcp-transport"></a>Ne zaman TCP aktarımı kullanın  
 TCP, uçtan uca hata algılama ve düzeltme ile bir bağlantı tabanlı, akış odaklı teslimatı hizmetidir. *Bağlantı tabanlı* veri değişimi önce konakları arasındaki iletişimi oturum kurulduktan anlamına gelir. Mantıksal bir IP adresine göre tanımlanan bir TCP/IP ağı herhangi bir cihazda bir ana bilgisayardır.  
  
 TCP, güvenilir veri sunma ve kullanım kolaylığı sağlar. Özellikle, TCP paket teslimini göndereni bilgilendirir paketleri, gönderildiği aynı sırada teslim edilmesini garanti eder, kayıp paketlerin edinceye ve veri paketlerinin yinelenmemesini sağlar. Bu güvenilir teslim iki TCP/IP'yi düğümler arasında uygular ve aynı değil unutmayın *WS-ReliableMessaging*uç noktaları arasında geçerli olduğu, kaç Ara düğümleri ne olursa olsun, bunlar içerebilir.  
  
 WCF TCP taşıma, her iki ucunda da iletişim WCF burada kullandığınız senaryo için optimize edilmiştir. Bu bağlama, farklı makineler arasında iletişim kurmasını gerektiren senaryolar için en hızlı WCF bağlamadır. İleti kullanım birbiriyle değiştirir <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> en iyi duruma getirilmiş ileti aktarım için. TCP, istemci ağ adresi çevirisi (NAT) olsa bile, çift yönlü iletişim ve bu nedenle çift yönlü sözleşmeler uygulamak için kullanılabilir sağlar.  
  
### <a name="when-to-use-the-named-pipe-transport"></a>Adlandırılmış kanal taşıma kullanıldığı durumlar  
 Adlandırılmış kanal işlemleri iletişimi için kullanabileceğiniz paylaşılan bellek bölümü gibi Windows işletim sistemi Çekirdeği'nde bir nesnedir. Adlandırılmış kanal bir ada sahip ve tek bir makinede işlemler arasında tek yönlü veya çift yönlü iletişim için kullanılabilir.  
  
 Tek bir bilgisayara farklı WCF uygulamaları arasındaki iletişimi gereklidir ve başka bir makineden hiçbir iletişim önlemek istiyorsanız, adlandırılmış taşıma'ni kullanın. Başka bir kısıtlama yükseltilmiş ayrıcalıklara sahip oldukları sürece Windows Uzak Masaüstü'nden çalışan işlemler aynı Windows Uzak Masaüstü oturumundan sınırlı olmasıdır.  
  
> [!WARNING]
>  Adlandırılmış kanal taşıma zayıf joker URL ayırmasını IIS'de barındırılan birden çok sitelerde kullanırken, şu hata ortaya çıkabilir: '2' sitesi için dinleme çalışılırken 'Net.pipe' protokol ' NetPipeActivator' etkinleştirme hizmetinde bir hata oluştu Bu nedenle protokolü için site geçici olarak devre dışıdır. Özel durum iletisi daha fazla ayrıntı için bkz. URL: WeakWildcard:net.pipe:/\<makine adı > / durumu: ConflictingRegistration özel durum: işlem adı: SMSvcHost işlem kimliği: 1076\  
  
## <a name="decision-points-for-choosing-a-transport"></a>Taşıma seçme için karar noktaları  
 Aşağıdaki tabloda, ortak bir aktarım seçmek için kullanılan karar noktalarının açıklanmaktadır. Herhangi bir ek öznitelikler ve uygulamanız için taşımalar düşünmelisiniz. Uygulamanız için önemli olan öznitelikleri tanımlamak, perakendecilerden özniteliklerinizin her biriyle ilişkilendirmek taşımalar tanımlamak ve, öznitelik kümesi ile en iyi şekilde çalıştığı aktarımlar'ı seçin.  
  
|Öznitelik|Açıklama|Ayrıcalıklı taşımalar|  
|---------------|-----------------|------------------------|  
|Tanılamalar|Tanılama Aktarım bağlantısı sorunları otomatik olarak algılamasını sağlar. Tüm aktarımları bağlantı açıklayan geri hata bilgileri göndermeyi destekler. Ancak, WCF, ağ sorunlarını araştırma için tanılama araçları içermez.|Yok.|  
|Barındırma|Tüm WCF uç noktaları, bir uygulama içinde barındırılması gerekir. [!INCLUDE[iis601](../../../../includes/iis601-md.md)] ve yalnızca HTTP aktarımı kullanan uygulamaları barındırma önceki destekler. Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)], destek TCP dahil olmak üzere tüm WCF taşımalar barındırmak için eklenir ve adlandırılmış kanallar. Daha fazla bilgi için [Internet Information Services'te barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md) ve [Windows İşlem Etkinleştirme hizmetinde barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).|HTTP|  
|İnceleme|İnceleme, ayıklayın ve iletim sırasında iletileri bilgi işlem yeteneğidir. HTTP protokolü, Yönlendirme ve denetim bilgileri inceleyin ve iletileri analiz araçları yapı kolaylaştıran verilerden ayırır. İncelemek kolay taşımalar daha az işlem gücü, ağ Gereçleri de gerektirebilir. İletileri inceledi olmadığını güvenlik düzeyini etkileri kullanılır.|HTTP|  
|Gecikme süresi|Gecikme süresi en az bir exchange ileti tamamlamak için gereken süre miktarıdır. Tüm ağ işlemlerini daha fazla veya daha az gecikme süresine aktarım seçimi bağlı olarak sahiptir. İstek-yanıt HTTP gibi ek gecikme nedeniyle ileti zorlamalı bağıntı neden olabilir, yerel ileti değişim deseni olan bir taşıma ile çift yönlü veya tek yönlü iletişimi kullanarak. Bu durumda, yerel ileti değişim deseni TCP gibi çift yönlü bir taşıma kullanarak göz önünde bulundurun.|TCP ve adlandırılmış<br /><br /> Kanal|  
|Ulaşın|Bir taşıma erişim ağını nasıl özellikli taşımanın olup diğer sistemleri ile bağlama sırasında yansıtır. Adlandırılmış kanal taşıma çok az ulaştığından; yalnızca aynı makinede çalışan hizmetlere bağlanabilir. TCP ve HTTP taşımaları hem mükemmel ulaşma sahiptir ve bazı NAT ve güvenlik duvarı yapılandırmaları duvarlarından geçebildiği. Daha fazla bilgi için [NAT ve güvenlik duvarlarıyla çalışma](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md).|HTTP, TCP|  
|Güvenlik|Güvenlik iletilerin gizliliğini, bütünlüğünü veya kimlik doğrulaması sağlanarak aktarım sırasında koruma olanağı sağlıyor. İncelenmekte olan bir ileti gizliliğini korur, caspol.exe'in bir ileti bütünlüğü korur ve kimlik doğrulaması gönderen veya alıcı iletinin hakkında güvence sağlar.<br /><br /> WCF aktarım güvenliği hem ileti düzeyi ve aktarım düzeyinde destekler. Taşıma bir arabelleğe alınan aktarım modunu destekliyorsa, taşıma ile ileti güvenliği oluşturur. Aktarım güvenliği için destek, seçilen taşıma bağlı olarak değişir. HTTP, TCP ve adlandırılmış kanal taşıma makul eşlik aktarım güvenliği için destek sağlamak.|Tümü|  
|Aktarım hızı|Aktarım aktarılan ve belirtilen bir süre içinde işlenen veri miktarını ölçer. Gecikme süresi gibi seçtiğiniz taşıma hizmeti işlemleri için aktarım hızını etkileyebilir. İçerik aktarımı yanı sıra ileti alışverişlerinde tamamlanmasını beklerken geçen süre en aza indirir, her iki yükünü en aza aktarım için en yüksek düzeyde üretilen iş gerektirir. TCP ve adlandırılmış kanal taşıma az ek yük ileti gövdesi ekleyin ve ileti yanıtı bekle azaltır yerel bir çift yönlü şekli destekler.|TCP ve adlandırılmış kanal|  
|Araç kullanımı|Araçları, geliştirme, tanılama, barındırma ve diğer etkinlikler için bir protokol için üçüncü taraf uygulama desteği temsil eder. Araçlar ve HTTP protokolü ile çalışmak için yazılım geliştirme, özellikle büyük bir yatırım gösterir.|HTTP|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>  
  <<!--zz <xref:System.ServiceModel.WsDualHttpBinding> --> `System.ServiceModel.WsDualHttpBinding`
 <<!--zz <xref:System.ServiceModel.WsFederationHttpBinding>  --> `System.ServiceModel.WsFederationHttpBinding` <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.NetTcpBinding>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
 <xref:System.ServiceModel.NetNamedPipeBinding>  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
 [Bağlamalar](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Kullanıcı Tanımlı Bağlamalar Oluşturma](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)
