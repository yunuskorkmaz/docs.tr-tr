---
title: Taşıma Seçme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- choosing transports [WCF]
ms.assetid: b169462b-f7b6-4cf4-9fca-d306909ee8bf
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7b051cdeebf83b34b6e503d8d9cb54a38a46a2a6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="choosing-a-transport"></a>Taşıma Seçme
Bu konuda yer alan üç ana taşımalar arasından seçim ölçütleri ele alınmıştır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]: HTTP, TCP ve adlandırılmış kanallar. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Ayrıca içeren bir message queuing (MSMQ olarak da bilinir) taşıma, ancak bu belgede, message queuing kapsamaz.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Programlama modeli ayıran uç nokta işlemleri (bir hizmet sözleşmesini ifade edilen) aktarım düzeneğinden iki uç nokta bağlanır. Bu, hizmetlerinizi ağa kullanıma sunmak nasıl karar vermek için esnekliği sağlar.  
  
 İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], kullanarak uç noktaları arasında bir ağ üzerinden veri aktarımı nasıl belirttiğiniz bir *bağlama*, hangi oluşur bir dizi *bağlama öğeleri*. Bir taşıma bağlama parçası olan bir aktarım bağlama öğesi temsil edilir. Bir bağlama güvenlik gibi isteğe bağlı Protokolü bağlama öğeleri, gerekli ileti Kodlayıcı bağlama öğesi ve gerekli aktarım bağlama öğesi içerir. Bir taşıma gönderir veya bir ileti için veya başka bir uygulamadan serileştirilmiş biçiminde alır.  
  
 Bir mevcut istemci veya sunucu bağlanması gerekiyorsa, özel bir taşıma kullanma hakkında bir seçim olmayabilir. Ancak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri yapılabilir birden çok uç nokta, her biri farklı bir aktarım üzerinden erişilebilir. Tek bir aktarım hizmetiniz için hedef kitle kapsamaz, hizmet birden çok uç nokta gösterme göz önünde bulundurun. İstemci uygulamaları, daha sonra bunlar için en iyisidir uç noktası kullanabilirsiniz.  
  
 Bir taşıma seçtikten sonra bunu kullanan bir bağlama seçmeniz gerekir. Sistem tarafından sağlanan bir bağlamayı seçebilirsiniz (bkz [System-Provided bağlamaları](../../../../docs/framework/wcf/system-provided-bindings.md)), ya da kendi özel bağlama yapı (bkz [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)). Kendi bağlama de oluşturabilirsiniz. Daha fazla bilgi için bkz: [Creating User-Defined bağlamaları](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
## <a name="advantages-of-each-transport"></a>Her aktarım avantajları  
 Bu bölümde, aralarında seçmeye yönelik ayrıntılı karar grafiği dahil olmak üzere üç ana taşımalar herhangi birini seçerek ana nedenleri açıklanmaktadır.  
  
### <a name="when-to-use-http-transport"></a>HTTP taşıma kullanma zamanı  
 HTTP, istemciler ve sunucular arasındaki bir istek/yanıt kuralıdır. Bir Web sunucusu ile iletişim kuran Web tarayıcısı istemcilerinin en yaygın uygulama oluşur. İstemci, istemci istek iletileri için dinleyen bir sunucuya bir istek gönderir. Sunucu bir istek aldığında, istek durumunu içeren bir yanıt döndürür. Başarılı olursa, bir Web sayfası, bir hata iletisi veya diğer bilgileri gibi isteğe bağlı veriler döndürülür. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] HTTP Protokolü Bkz [HTTP - Köprü Metni Aktarım Protokolü](http://go.microsoft.com/fwlink/?LinkId=94858).  
  
 HTTP protokolü bağlantı tabanlı değildir — yanıt gönderildikten sonra hiçbir durumu korunur. Birden çok sayfa işlemleri işlemek için uygulama gerekli herhangi bir durum kalıcı olması gerekir.  
  
 İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], HTTP aktarım bağlama eski olmayan ile birlikte çalışabilirlik getirilmiştir[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sistemler. Tüm iletişim kuran tarafların kullanıyorsanız [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], TCP tabanlı veya adlandırılmış kanallar tabanlı bağlamalar daha hızlıdır. Daha fazla bilgi için bkz. <xref:System.ServiceModel.NetTcpBinding> ve <xref:System.ServiceModel.NetNamedPipeBinding>.  
  
### <a name="when-to-use-the-tcp-transport"></a>TCP taşıma kullanma zamanı  
 TCP, uçtan uca hata algılama ve düzeltme ile bir bağlantı tabanlı, akış odaklı teslimatı hizmetidir. *Bağlantı tabanlı* veri değişimi önce konakları arasındaki iletişimi oturum kurulduktan anlamına gelir. Mantıksal bir IP adresi ile tanımlanan bir TCP/IP ağı herhangi bir cihazda bir ana bilgisayardır.  
  
 TCP güvenilir veri teslimi ve kullanım kolaylığı sağlar. Özellikle, TCP paket teslimat göndereni bilgilendirmek paketleri gönderilmiş sırayla teslim edilmesini garanti eder, kayıp paketlerin edinceye ve veri paketlerinin değil yinelenir sağlar. Bu güvenilir teslim iki TCP/IP'yi düğümler arasında uygular ve aynı değil Not *WS-ReliableMessaging*uç noktaları arasında geçerlidir, bunlar olsun kaç ara düğümler içerebilir.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] TCP taşıma her iki ucuna iletişimin kullanmakta olduğu senaryo için iyileştirilmiş [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Bu bağlamanın daha hızlı olduğu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] farklı makineler arasında iletişim kurmasını gerektiren senaryolar için bağlama. İleti alış verişleri kullanım <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> en iyi duruma getirilmiş ileti aktarma için. TCP, istemci ağ adresi çevirisi (NAT) olsa bile, çift yönlü iletişimi ve bu nedenle çift yönlü sözleşmeler uygulamak için kullanılabilir sağlar.  
  
### <a name="when-to-use-the-named-pipe-transport"></a>Adlandırılmış kanal taşıma kullanma zamanı  
 Bir adlandırılmış kanal, Windows işletim sisteminin çekirdek işlemleri iletişimi için kullanabileceğiniz paylaşılan bellek bölümü gibi bir nesnedir. Bir adlandırılmış kanal bir ada sahip ve tek bir makinede işlemleri arasındaki tek yönlü veya çift yönlü iletişimi için kullanılabilir.  
  
 İletişim olduğunda arasında farklı gerekli [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamaları tek bir bilgisayar ve istediğiniz başka bir makineden tüm iletişimi önlemeye yeniden adlandırılmış kanallar taşıma kullanın. Başka bir kısıtlama ayrıcalıkları yükseltilmiş sürece Windows Uzak Masaüstü üzerinden çalışan işlemleri için aynı Windows Uzak Masaüstü oturumu kısıtlı olmasıdır.  
  
> [!WARNING]
>  Adlandırılmış kanal taşıma zayıf joker URL ayırmasını IIS'de barındırılan birden çok sitelerde ile kullanırken, aşağıdaki hata oluşabilir: '2' sitesi için dinleme çalışılırken 'Net.pipe' Protokolü ' NetPipeActivator' etkinleştirme hizmetinde bir hata oluştu Bu nedenle Protokolü site için geçici olarak devre dışıdır. Özel durum iletisi daha fazla ayrıntı için bkz. URL: WeakWildcard:net.pipe:/\<makine adı > / durumu: ConflictingRegistration özel durum: işlem adı: SMSvcHost işlem kimliği: 1076\  
  
## <a name="decision-points-for-choosing-a-transport"></a>Taşıma seçme için karar noktaları  
 Aşağıdaki tabloda bir aktarım seçmek için kullanılan ortak karar noktaları açıklar. Herhangi bir ek öznitelikler ve uygulamanız için taşımaları düşünmelisiniz. Uygulamanız için önemli olan öznitelikleri tanımlamak, perakendecilerden, özniteliklerinin her biriyle ilişkilendirmek taşımalar tanımlamaya ve en iyi öznitelik kümesiyle çalışan taşımalar seçin.  
  
|Öznitelik|Açıklama|Ayrıcalıklı taşımalar|  
|---------------|-----------------|------------------------|  
|Tanılamalar|Tanılama taşıma bağlantısı sorunları otomatik olarak algılamasını sağlar. Tüm aktarımları bağlantı açıklayan geri hata bilgileri gönderme olanağı destekler. Ancak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ağ sorunları incelemeye için tanılama araçları içermez.|Yok.|  
|Barındırma|Tüm [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç noktaları bir uygulama içinde barındırılmalıdır. [!INCLUDE[iis601](../../../../includes/iis601-md.md)] ve yalnızca HTTP taşıması kullanan uygulamaları barındırma önceki destekler. Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)], destek, tüm barındırmak için eklenir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] taşımaları, TCP dahil olmak üzere ve adlandırılmış kanallar. Daha fazla bilgi için bkz: [Internet Information Services'te barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md) ve [Windows İşlem Etkinleştirme hizmetinde barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).|HTTP|  
|Denetleme|Denetleme, ayıklayın ve iletim sırasında iletilerden bilgi işlem yeteneğidir. HTTP protokolünü Yönlendirme ve denetim bilgilerini inceleyin ve iletileri analiz araçları yapı kolaylaştırma verilerinden ayırır. İncelenecek kolay aktarımları da ağ uygulamaları, daha az işlem gücü gerektirebilir. İletileri Denetlenmekte olup olmadığını güvenlik düzeyini etkileri kullanılır.|HTTP|  
|Gecikme süresi|Gecikme süresi en az bir exchange iletilerinin tamamlamak için gereken süreyi ' dir. Tüm ağ işlemlerini fazla veya az gecikme aktarım seçimine bağlı olarak olmaz. İstek-yanıt, HTTP gibi ek gecikme iletilerinin zorlanmış bağıntı nedeniyle neden olabilir, yerel ileti değişim deseni olan bir taşıma ile çift yönlü veya tek yönlü iletişim kullanma. Bu durumda, yerel ileti değişim deseni gibi TCP çift yönlü bir aktarım kullanmayı düşünün.|Adlı TCP<br /><br /> Kanal|  
|Ulaşma|Bir taşıma ulaşabileceği nasıl özellikli taşıma olan diğer sistemleri ile bağlama sırasında yansıtır. Adlandırılmış kanal taşıma çok az ulaştığından; yalnızca aynı makinede çalışan hizmetlere bağlanabilir. TCP ve HTTP taşımaları mükemmel reach sahip hem bazı NAT ve güvenlik duvarı yapılandırmaları sızmasını. Daha fazla bilgi için bkz: [NAT ve güvenlik duvarlarıyla çalışma](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md).|HTTP, TCP|  
|Güvenlik|Güvenlik, gizlilik, bütünlük ve kimlik doğrulaması sağlayarak aktarımı sırasında iletileri korumanın yeteneğidir. İncelenmesi gelen ileti gizliliği korur, değiştirilmesini bir ileti bütünlük korur ve kimlik doğrulama veya iletinin vericinin hakkında güvence sağlar.<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] destekler aktarımı güvenlik hem ileti ve aktarım düzeyindeki. Taşıma arabelleğe alınan aktarım modunu destekliyorsa, ileti güvenliği ile aktarma oluşturur. Taşıma güvenliği için destek seçilen aktarım bağlı olarak değişir. HTTP, TCP ve adlandırılmış kanal taşımaları taşıma güvenliği için destek makul eşlik sahip.|Tümü|  
|Üretilen iş|Üretilen iş aktarılan ve belirtilen bir süre içinde işlenen veri miktarını ölçer. Gecikme süresi gibi seçtiğiniz aktarım hizmet işlemleri için işleme etkileyebilir. Bir taşıma için en yüksek düzeyde üretilen iş içerik aktarımı yanı sıra ileti alışverişlerinde tamamlanmasını bekleme süresini en aza hem yükünü en aza indirmenizi gerektirir. TCP ve adlandırılmış kanal taşımaları az ek yük ileti gövdesi ekleyin ve ileti yanıtları bekle azaltır yerel bir çift yönlü şekli destekler.|TCP, adlandırılmış kanal|  
|Araçları|Araç, üçüncü taraf uygulama geliştirme, tanılama, barındırma ve diğer etkinlikler için bir protokol desteği temsil eder. Araçlar ve HTTP protokolü ile çalışmak için yazılım geliştirme özellikle büyük yatırım belirtir.|HTTP|  
  
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
