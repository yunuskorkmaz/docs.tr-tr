---
title: NAT ve Güvenlik Duvarlarıyla Çalışma
ms.date: 03/30/2017
helpviewer_keywords:
- firewalls [WCF]
- NATs [WCF]
ms.assetid: 74db0632-1bf0-428b-89c8-bd53b64332e7
ms.openlocfilehash: 9cecca0905baa4c0769359caf1fe1b477bf4d6bd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518931"
---
# <a name="working-with-nats-and-firewalls"></a>NAT ve Güvenlik Duvarlarıyla Çalışma
İstemci ve sunucu bir ağ bağlantısının sık değil doğrudan ve iletişim için yol. Paket filtre, yönlendirilmiş, analiz ve uç nokta makinelerde ve ağ ara makineler tarafından dönüştürülür. Ağ adresi çevirisi (NAT) ve güvenlik duvarları ağ iletişimi katılabilir Ara uygulamaları için ortak örnekleridir.  
  
 Windows Communication Foundation (WCF) aktarım ve exchange (MEPs) desenleri ileti farklı olarak, NAT ve güvenlik duvarlarıyla varlığını tepki verin. Bu konu nasıl NAT ve güvenlik duvarlarıyla ortak ağ topolojileri işlev açıklar. WCF aktarım ve MEPs belirli birleşimleri için öneriler, verilir uygulamalarınız için NAT ve güvenlik duvarlarıyla ağ üzerinde daha sağlam hale yardımcı olur.  
  
## <a name="how-nats-affect-communication"></a>NAT iletişimi nasıl etkiler?  
 NAT, tek bir dış IP adresi paylaşmak birkaç makine etkinleştirmek için oluşturuldu. Bir bağlantı noktası yeniden eşleme NAT bir iç IP adresi ve bağlantı noktası bağlantısı için dış IP adresi yeni bir bağlantı noktası numarası ile eşlenir. Yeni bağlantı noktası numarası, dönüş trafiği özgün iletişimi ile ilişkilendirmek NAT sağlar. Birçok ev kullanıcıları, artık, yalnızca özel olarak yönlendirilebilir IP adresi ve genel paketlerin yönlendirilmesini sağlamak için bir NAT'ı kullanır.  
  
 NAT, güvenlik sınırı sağlamaz. Ancak, NAT yapılandırmaların iç makineler doğrudan ele engeller. Bu hem iç makineler istenmeyen bazı bağlantılarından korur ve veriler zaman uyumsuz olarak istemciye geri göndermek zorunda sunucu uygulamaları yazmak zorlaştırır. NAT bağlantıları NAT makinenin kaynaklanan görünmesini sağlamak için paketlerin adresleri yeniden yazar. Bu, sunucu istemciye bir bağlantı açmaya çalıştığında başarısız olmasına neden olur. Sunucu istemcinin algılanan adresini kullanıyorsa, istemci adresi herkese açık şekilde yönlendirilemiyor çünkü başarısız olur. Sunucu NAT adresi kullanıyorsa, bu makinede hiçbir uygulama dinlediğinden bağlanmak başarısız olur.  
  
 Bazı NAT dış makinelerin belirli bir iç makinesine bağlanmaya izin vermek için kuralları iletme yapılandırmasını destekler. İletme kurallarını yapılandırmak için yönergeleri farklı NAT arasında farklılık gösterir ve son kullanıcıların NAT yapılandırmalarını değiştirmek isteyen çoğu uygulama için önerilmez. Pek çok son kullanıcının olamaz ya da belirli bir uygulama için NAT yapılandırmalarını değiştirmek istiyor musunuz.  
  
## <a name="how-firewalls-affect-communication"></a>Güvenlik Duvarı iletişimi nasıl etkiler?  
 A *Güvenlik Duvarı* izin verdiğini veya reddettiğini oluşturularak karar vermek için üzerinden geçen trafik kuralları uygulayan bir yazılım veya donanım cihazıdır. Gelen ve/veya giden trafik akışları incelemek için güvenlik duvarları yapılandırabilirsiniz. Güvenlik Duvarı, uçta ya da ağ veya uç nokta konak üzerinde ağ için bir güvenlik sınırı sağlar. İş kullanıcıları, geleneksel olarak sunucularından kötü amaçlı saldırıları önlemek için bir güvenlik duvarının arkasındaki tutmuş. Kişisel Güvenlik Duvarı'nda sunulmasından beri [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)], ev kullanıcıları bir güvenlik duvarının arkasındaki sayısını de önemli ölçüde arttı. Bu büyük olasılıkla bir hale getirir veya paket İnceleme bir güvenlik duvarı her iki ucunda da bir bağlantı sağlayın.  
  
 Güvenlik duvarları, karmaşıklığı ve paket İnceleme için özellik açısından önemli ölçüde farklılık gösterir. Basit güvenlik duvarları, kaynak ve hedef adresleri ve bağlantı noktaları paketlerde göre kuralları uygulayın. Akıllı güvenlik duvarları, ayrıca kararları vermek için paket içeriğini inceleyebilirsiniz. Bu güvenlik duvarları, birçok farklı yapılandırmalarda gelir ve genellikle özel uygulamalar için kullanılır.  
  
 Yaygın bir ev kullanıcısı Güvenlik Duvarı için giden bir bağlantı daha önce bu makineye yapıldığı sürece gelen bağlantıları engelleyecek şekilde bir yapılandırmadır. Yaygın iş kullanıcı güvenlik duvarı için özel olarak tanımlanan bir grubu dışındaki tüm bağlantı noktalarındaki gelen bağlantıları engelleyecek şekilde bir yapılandırmadır. Bir güvenlik duvarı bağlantı noktaları 80 ve 443, HTTP ve HTTPS hizmeti sağlamak amacıyla dışında tüm bağlantı noktalarındaki bağlantılarını engeller buna bir örnektir. Yönetilen güvenlik duvarları, güvenilen kullanıcı veya işlem makinede güvenlik duvarı yapılandırmasını değiştirmek için izin hem giriş hem de iş kullanıcıları için mevcut. Yönetilen güvenlik duvarları Ev kullanıcıları için daha yaygın bulunduğu ağ kullanımını denetleme şirket ilkesi yok.  
  
## <a name="using-teredo"></a>Teredo kullanma  
 Bir NAT arkasında makinelerin doğrudan çözümlenebilme sağlayan bir IPv6 geçiş teknolojisi teredo'dur Teredo üzerinde olası bağlantıları tanıtmak için genel ve genel olarak yönlendirilebilir bir sunucunun kullanımına dayanır. Teredo sunucu uygulaması istemci ve sunucu, bunlar bağlantı bilgilerini exchange ortak bir toplantı noktası sağlar. Makineleri ardından geçici bir Teredo adresi istemek ve paketleri mevcut ağ üzerinden iletilmesine. Wcf'de Teredo desteği, işletim sisteminde IPv6 ve Teredo desteğini etkinleştirme gerektirir. [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ve sonraki işletim sistemlerinde Teredo destekler. [!INCLUDE[wv](../../../../includes/wv-md.md)] ve sonraki işletim sistemlerinde varsayılan olarak IPv6 desteği ve yalnızca kullanıcının Teredo'yu etkinleştirmek gereklidir. [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] ve [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] IPv6 ve Teredo etkinleştirmek kullanıcının gerektirir. Daha fazla bilgi için [Teredo genel bakış](https://go.microsoft.com/fwlink/?LinkId=87571).  
  
## <a name="choosing-a-transport-and-message-exchange-pattern"></a>Bir taşıma ve ileti değişim deseni seçme  
 Bir taşıma seçip MEP üç adımlık bir işlemdir:  
  
1.  Uç nokta makinelerin çözümlenebilme analiz edin. Son kullanıcıların yaygın olarak NAT tarafından engellenen kendi çözümlenebilme kurumsal sunucular genellikle doğrudan çözümlenebilme bulunur. Her iki bitiş noktasında bir NAT'nin arkasında ise gibi son kullanıcılar arasındaki eşler arası senaryolarda ardından, Teredo çözümlenebilme sağlamak gibi bir teknoloji gerekebilir.  
  
2.  Uç nokta makinelerin protokolü ve bağlantı noktası kısıtlamaları analiz edin. Kurumsal sunucular, genellikle o blok güçlü güvenlik duvarının arkasındaki birçok bağlantı noktalarıdır. Ancak, 80 numaralı bağlantı noktası HTTP trafiğine izin vermek için sıklıkla açık olduğundan ve 443 numaralı bağlantı noktasını HTTPS trafiğine izin vermek için açık olduğundan. Son kullanıcılar, bağlantı noktası kısıtlamalara sahip olma olasılığını azaltacak ancak yalnızca giden bağlantılara izin veren bir güvenlik duvarının arkasında olabilir. Bazı güvenlik duvarları, seçmeli olarak Bağlantıları'nı açmak için uç noktasında uygulamaların yönetim izin verir.  
  
3.  Aktarım ve ağ adreslenebilirliği ve bağlantı noktası kısıtlamaları izin MEPs işlem.  
  
 İstemci-sunucu uygulamaları için ortak bir topoloji, yalnızca giden güvenlik duvarı ve güçlü bir güvenlik duvarı ile doğrudan adreslenebilir bir sunucuya Teredo olmadan bir NAT arkasındaki istemciler olmasını sağlamaktır. Bu senaryo, bir çift yönlü MEP ile TCP taşıma ve istek-yanıt ile bir HTTP aktarımı MEP çalışmak iyi. Eşler arası uygulamalar için ortak bir topoloji, NAT ve güvenlik duvarlarıyla arkasında iki uç noktaları sağlamaktır. Bu senaryoda ve ağ topolojisi bilinmeyen olduğu senaryolarda aşağıdaki önerileri göz önünde bulundurun:  
  
-   Çift taşımalar kullanmayın. İkili aktarım bağlantı başarıyla kurulduktan olasılığını azaltır daha fazla bağlantı açar.  
  
-   Kaynak bağlantısı üzerinden kurmanın arka kanal desteği. Arka kanal gibi çift yönlü TCP kullanarak, daha az bağlantı, bağlantı başarıyla kurulduktan olasılığını artırır açılır.  
  
-   Erişilebilir bir hizmet uç noktaları kaydetme veya trafik geçişini kullanır. Teredo sunucusu gibi bir genel olarak erişilebilen bağlantı hizmeti kullanarak, ağ topolojisini kısıtlayıcı veya bilinmeyen olduğunda bağlantı başarıyla kurulduktan olasılığını önemli ölçüde artırır.  
  
 Tek yönlü, istek-yanıt ve çift yönlü MEPs ve standart TCP, TCP ile Teredo, aşağıdaki tablolarda inceleyin ve standart ve ikili HTTP WCF'de taşır.  
  
|Çözümlenebilme|Sunucu doğrudan|Sunucu doğrudan NAT geçişi ile|NAT sunucusu|NAT sunucusu ile bir NAT geçişi|  
|--------------------|-------------------|--------------------------------------|----------------|-----------------------------------|  
|İstemci doğrudan|Herhangi bir aktarım ve MEP|Herhangi bir aktarım ve MEP|Desteklenmez.|Desteklenmez.|  
|NAT geçişi ile doğrudan istemci|Hiçbir taşıma ve MEP.|Hiçbir taşıma ve MEP.|Desteklenmez.|Teredo ve tüm MEP TCP. [!INCLUDE[wv](../../../../includes/wv-md.md)] Teredo ile HTTP desteği için bir makine genelindeki yapılandırma seçeneği vardır.|  
|İstemci NAT|Tüm ikili olmayan aktarım ve MEP. Çift yönlü MEP TCP taşıması gerekir.|Tüm ikili olmayan aktarım ve MEP. Çift yönlü MEP TCP taşıması gerekir.|Desteklenmez.|Desteklenmez.|  
|NAT istemcisiyle NAT geçişi|Tüm ikili olmayan aktarım ve MEP. Çift yönlü MEP TCP taşıması gerekir.|Tüm ikili HTTP ve tüm MEP. Çift yönlü MEP TCP taşıması gerekir. Çift TCP taşıma Teredo gerektirir. [!INCLUDE[wv](../../../../includes/wv-md.md)] Teredo ile HTTP desteği için bir makine genelindeki yapılandırma seçeneği vardır.|Desteklenmez.|Teredo ve tüm MEP TCP. [!INCLUDE[wv](../../../../includes/wv-md.md)] Teredo ile HTTP desteği için bir makine genelindeki yapılandırma seçeneği vardır.|  
  
|Güvenlik Duvarı kısıtlamaları|Sunucu Aç|Yönetilen bir güvenlik duvarı ile sunucu|Yalnızca HTTP güvenlik duvarı ile sunucu|Yalnızca giden güvenlik duvarı ile sunucu|  
|---------------------------|-----------------|----------------------------------|-------------------------------------|-----------------------------------------|  
|İstemci Aç|Hiçbir taşıma ve MEP.|Hiçbir taşıma ve MEP.|Tüm HTTP taşıma ve MEP.|Desteklenmez.|  
|İstemcisiyle yönetilen bir güvenlik duvarı|Tüm ikili olmayan aktarım ve MEP. Çift yönlü MEP TCP taşıması gerekir.|Tüm ikili olmayan aktarım ve MEP. Çift yönlü MEP TCP taşıması gerekir.|Tüm HTTP taşıma ve MEP.|Desteklenmez.|  
|İstemci yalnızca HTTP güvenlik duvarı|Tüm HTTP taşıma ve MEP.|Tüm HTTP taşıma ve MEP.|Tüm HTTP taşıma ve MEP.|Desteklenmez.|  
|Yalnızca giden güvenlik duvarı ile istemci|Tüm ikili olmayan aktarım ve MEP. Çift yönlü MEP TCP taşıması gerekir.|Tüm ikili olmayan aktarım ve MEP. Çift yönlü MEP TCP taşıması gerekir.|Herhangi bir HTTP aktarım ve herhangi bir çift yönlü olmayan MEP.|Desteklenmez.|
