---
title: "NAT ve Güvenlik Duvarlarıyla Çalışma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- firewalls [WCF]
- NATs [WCF]
ms.assetid: 74db0632-1bf0-428b-89c8-bd53b64332e7
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a8fd5058179d9e7974e725d69bb2bf0740ab7f00
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="working-with-nats-and-firewalls"></a>NAT ve Güvenlik Duvarlarıyla Çalışma
İstemci ve sunucunun ağ bağlantısı sık değil doğrudan bir sahip ve iletişim için yol açın. Paket filtre, yönlendirilmiş, analiz ve uç nokta makinelerde hem ağ ara makineler tarafından dönüştürülmüş. Ağ adresi çevirisi (NAT) ve güvenlik duvarları ağ iletişiminde katılabilir Ara uygulamaları için ortak örnekleridir.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]farklı bir çok aktarımları ve iletinizi (MEPs) exchange düzenleri NAT ve güvenlik duvarlarıyla varlığını tepki. Bu konuda nasıl NAT ve güvenlik duvarlarıyla ortak ağ topolojileri işlev açıklanmaktadır. Belirli bir kombinasyonu için öneriler [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aktarımları ve MEPs verilir, uygulamalarınızı NAT ve güvenlik duvarlarıyla ağdaki için daha sağlam hale Yardım.  
  
## <a name="how-nats-affect-communication"></a>NAT iletişimi nasıl etkiler  
 NAT, tek bir dış IP adresi paylaşmak çeşitli makineler etkinleştirmek için oluşturuldu. Bir bağlantı noktası yeniden eşleme NAT bir iç IP adresi ve bağlantı için bağlantı noktası dış IP adresi yeni bir bağlantı noktası numarası ile eşleştirir. Yeni bağlantı noktası numarasını dönüş trafiği özgün iletişimi ilişkilendirmek NAT sağlar. Birçok ev kullanıcıları artık yalnızca özel olarak yönlendirilebilir bir IP adresine sahip ve genel paketlerin yönlendirilmesini sağlamak için bir NAT kullanır.  
  
 NAT, güvenlik sınırı sağlamaz. Ancak, NAT yapılandırmaların iç makineler doğrudan ele önleyebilir. Bu hem iç makineleri bazı istenmeyen bağlantılarından korur ve zaman uyumsuz olarak veriler istemciye göndermek zorunda sunucu uygulamaları yazmak zorlaştırır. NAT bağlantıları NAT makinenin kaynaklanan görünmesini sağlamak için paketler adresler yeniden yazar. Bu sunucunun bir bağlantı istemciye açmaya çalıştığında başarısız olmasına neden olur. Sunucu istemcinin algılanan adresini kullanıyorsa, istemci adresi genel olarak yönlendirilemiyor için başarısız olur. Sunucu NAT adresi kullanıyorsa, uygulama bu makinede dinlediğinden bağlanmak başarısız olur.  
  
 Bazı NAT dış makinelerin belirli bir iç makine bağlanmasına izin vermek için kurallar iletme yapılandırmasını destekler. İletme kurallarını yapılandırmak için yönergeleri farklı NAT arasında değişir ve son kullanıcıların kendi NAT yapılandırmasını değiştirmek için isteyen çoğu uygulama için önerilmez. Birçok son kullanıcıların olamaz ya da belirli bir uygulama için NAT yapılandırmalarını değiştirmek istiyor musunuz.  
  
## <a name="how-firewalls-affect-communication"></a>Güvenlik duvarları iletişimi nasıl etkiler  
 A *Güvenlik Duvarı* izin ver veya Reddet oluşturularak karar vermek için komut zincirinden geçen trafik kurallarını uygular yazılım veya donanım bir aygıttır. Gelen ve/veya giden trafik akışları incelemek için güvenlik duvarları yapılandırabilirsiniz. Güvenlik duvarının kenarına ya da ağ veya uç nokta konaktaki ağ için güvenlik sınırı sağlar. İş kullanıcıları, geleneksel kötü amaçlı saldırıları önlemek için bir güvenlik duvarının arkasında sunucularını tutulan. Kişisel Güvenlik Duvarı'nda giriş itibaren [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)], bir güvenlik duvarının arkasında Ev kullanıcıları sayısını önemli ölçüde de artırmıştır. Bu büyük olasılıkla bir hale getirir veya her iki ucuna ait bir bağlantı paketleri inceleyerek bir güvenlik duvarına sahip.  
  
 Güvenlik duvarları, paketleri incelenmesinin yetenek ve karmaşıklık açısından büyük ölçüde farklılık gösterir. Basit güvenlik duvarları kaynak ve hedef adresleri ve bağlantı noktalarını paketlerde dayalı kurallar geçerlidir. Akıllı güvenlik duvarları ayrıca kararları vermek için paket içeriğini inceleyebilirsiniz. Bu güvenlik duvarları birçok farklı yapılandırmalarda gelir ve genellikle özel uygulamalar için kullanılır.  
  
 Bir ortak bir ev kullanıcısı Güvenlik Duvarı için giden bir bağlantı bu makineye daha önce yapıldı sürece gelen bağlantıları engellemek için bir yapılandırmadır. Bir ortak iş kullanıcı güvenlik duvarı için özel olarak tanımlanan bir grubu dışındaki tüm bağlantı noktalarından gelen bağlantıları engellemek için bir yapılandırmadır. Tüm bağlantı noktaları 80 ve 443 HTTP ve HTTPS hizmet sağlamak için bağlantı noktalarını dışında bağlantılarında yasaklar bir güvenlik duvarı örneğidir. Güvenilen kullanıcı veya işlem güvenlik duvarı yapılandırmasını değiştirmek için makinede izin ev ve iş kullanıcıları için yönetilen güvenlik duvarları yok. Yönetilen güvenlik duvarları Ev kullanıcıları için daha sık olması durumunda ağ kullanımını denetleme şirket ilkesi yok.  
  
## <a name="using-teredo"></a>Teredo kullanma  
 Bir NAT arkasında makinelerin doğrudan çözümlenebilme sağlayan bir IPv6 geçiş teknolojisi teredo'dur Teredo olası bağlantıları bildirmek için genel ve genel olarak yönlendirilebilir bir sunucu kullanılmasına dayanır. Teredo sunucusu uygulama istemci ve sunucu, bunlar bağlantı bilgilerini exchange ortak bir toplantı noktası sağlar. Makineler sonra geçici bir Teredo adresi isteyin ve paketleri mevcut bir ağ tünel. Teredo desteği [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] işletim sisteminde IPv6 ve Teredo desteğini etkinleştirme gerektirir. [!INCLUDE[wxp](../../../../includes/wxp-md.md)]ve sonraki işletim sistemlerinde Teredo destekler. [!INCLUDE[wv](../../../../includes/wv-md.md)]ve sonraki işletim sistemlerinde varsayılan olarak IPv6'yı destekleyen ve yalnızca Teredo'yu etkinleştirmek kullanıcının gerektiren. [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]ve [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] hem IPv6 hem de Teredo'yu etkinleştirmek kullanıcının gerektirir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Teredo genel bakış](http://go.microsoft.com/fwlink/?LinkId=87571).  
  
## <a name="choosing-a-transport-and-message-exchange-pattern"></a>Taşıma ve ileti değişim deseni seçme  
 Taşıma ve MEP seçerek üç adımlık bir işlemdir:  
  
1.  Uç nokta makineler çözümlenebilme analiz edin. Bulunurken, son kullanıcıların yaygın olarak iç NAT tarafından engellenen kendi çözümlenebilme kurumsal sunucular genellikle doğrudan çözümlenebilme vardır. Bir NAT arkasında her iki uç noktaları varsa gibi son kullanıcılar arasında eşler arası senaryolarda sonra bir teknoloji çözümlenebilme sağlamak için Teredo gibi gerekebilir.  
  
2.  Uç nokta makineler protokolü ve bağlantı noktası kısıtlamalarını analiz edin. Kurumsal genellikle o blok güçlü güvenlik duvarının arkasındaki birçok bağlantı noktalarını sunucularıdır. Ancak, bağlantı noktası 80 HTTP trafiğine izin vermek için sık açık olan ve 443 numaralı bağlantı noktasını HTTPS trafiğine izin vermek için açık olan. Son kullanıcılar bağlantı noktası sınırlamalı olasılığı daha düşüktür, ancak yalnızca giden bağlantılara izin veren bir güvenlik duvarının arkasında olabilir. Bazı güvenlik duvarları, seçmeli olarak Bağlantıları'nı açmak için uç uygulamaların yönetim izin verir.  
  
3.  Taşımalar ve ağ çözümlenebilme ve bağlantı noktası kısıtlamalarını izin MEPs işlem.  
  
 İstemci-sunucu uygulamaları için ortak bir topolojiyi Teredo olmadan bir NAT'ın arkasında yalnızca giden bir güvenlik duvarı ve güçlü bir güvenlik duvarı ile doğrudan adreslenebilir bir sunucu ile istemciler olmalıdır. Bu senaryo, çift yönlü MEP ile TCP taşıma ve istek-yanıt ile bir HTTP aktarma MEP çalışma iyi. Eşler arası uygulamaları için ortak bir topolojiyi her iki uç noktaları NAT ve güvenlik duvarı arkasındaki olmalıdır. Bu senaryoda ve ağ topolojisini bilinmeyen olduğu senaryolarda aşağıdaki önerileri göz önünde bulundurun:  
  
-   Çift taşımaları kullanmayın. Bir çift taşıma, başarılı bir şekilde bağlanma ihtimalini azaltır daha fazla bağlantı açar.  
  
-   Kaynak bağlantısı üzerinden kurmanın arka kanal destekler. Çift yönlü TCP içinde gibi geri kanalları kullanarak, daha az bağlantılar, hangi başarıyla bağlanma olasılığı artar açar.  
  
-   Uç noktaları kaydetme veya trafiği geçişi için erişilebilir bir hizmet kullanın. Bir Teredo sunucusu gibi bir genel olarak erişilebilir bağlantı hizmetini kullanarak ağ topolojisini kısıtlayıcı veya bilinmeyen olduğunda başarıyla bağlanma ihtimalini büyük ölçüde artırır.  
  
 Aşağıdaki tablolarda tek yönlü, istek-yanıt ve çift yönlü MEPs ve standart TCP, TCP ile Teredo ve standart ve çift HTTP taşımaları inceleyin [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
|Çözümlenebilme|Sunucu doğrudan|Sunucu doğrudan NAT geçişi ile|Sunucu NAT|NAT geçişi NAT sunucusuyla|  
|--------------------|-------------------|--------------------------------------|----------------|-----------------------------------|  
|İstemci doğrudan|Herhangi bir aktarım ve MEP|Herhangi bir aktarım ve MEP|Desteklenmez.|Desteklenmez.|  
|İstemci ile NAT geçişi doğrudan|Tüm taşıma ve MEP.|Tüm taşıma ve MEP.|Desteklenmez.|TCP Teredo ve tüm MEP ile. [!INCLUDE[wv](../../../../includes/wv-md.md)]Teredo ile HTTP desteği için bir makine genelinde yapılandırma seçeneği vardır.|  
|İstemci NAT|Tüm ikili olmayan aktarım ve MEP. Çift yönlü MEP TCP Aktarım gerektirir.|Tüm ikili olmayan aktarım ve MEP. Çift yönlü MEP TCP Aktarım gerektirir.|Desteklenmez.|Desteklenmez.|  
|NAT geçişi NAT istemcisiyle|Tüm ikili olmayan aktarım ve MEP. Çift yönlü MEP TCP Aktarım gerektirir.|Tüm ikili HTTP ve tüm MEP. Çift yönlü MEP TCP Aktarım gerektirir. Çift TCP taşıma Teredo gerektirir. [!INCLUDE[wv](../../../../includes/wv-md.md)]Teredo ile HTTP desteği için bir makine genelinde yapılandırma seçeneği vardır.|Desteklenmez.|TCP Teredo ve tüm MEP ile. [!INCLUDE[wv](../../../../includes/wv-md.md)]Teredo ile HTTP desteği için bir makine genelinde yapılandırma seçeneği vardır.|  
  
|Güvenlik Duvarı kısıtlamaları|Sunucu Aç|Yönetilen güvenlik duvarı sunucusuyla|Sunucusu yalnızca HTTP güvenlik duvarı ile|Yalnızca giden güvenlik duvarı sunucusuyla|  
|---------------------------|-----------------|----------------------------------|-------------------------------------|-----------------------------------------|  
|İstemci Aç|Tüm taşıma ve MEP.|Tüm taşıma ve MEP.|Tüm HTTP taşıma ve MEP.|Desteklenmez.|  
|İstemcisiyle yönetilen güvenlik duvarı|Tüm ikili olmayan aktarım ve MEP. Çift yönlü MEP TCP Aktarım gerektirir.|Tüm ikili olmayan aktarım ve MEP. Çift yönlü MEP TCP Aktarım gerektirir.|Tüm HTTP taşıma ve MEP.|Desteklenmez.|  
|İstemci yalnızca HTTP güvenlik duvarı|Tüm HTTP taşıma ve MEP.|Tüm HTTP taşıma ve MEP.|Tüm HTTP taşıma ve MEP.|Desteklenmez.|  
|Yalnızca giden güvenlik duvarı istemcisi|Tüm ikili olmayan aktarım ve MEP. Çift yönlü MEP TCP Aktarım gerektirir.|Tüm ikili olmayan aktarım ve MEP. Çift yönlü MEP TCP Aktarım gerektirir.|Herhangi bir HTTP aktarım ve çift yönlü olmayan MEP.|Desteklenmez.|
