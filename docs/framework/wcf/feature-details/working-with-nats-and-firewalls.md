---
title: NAT ve Güvenlik Duvarlarıyla Çalışma
ms.date: 03/30/2017
helpviewer_keywords:
- firewalls [WCF]
- NATs [WCF]
ms.assetid: 74db0632-1bf0-428b-89c8-bd53b64332e7
ms.openlocfilehash: b8be10740c8e92d3dac7094f07b3372e8d78a3d9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743863"
---
# <a name="working-with-nats-and-firewalls"></a>NAT ve Güvenlik Duvarlarıyla Çalışma
Bir ağ bağlantısının istemci ve sunucusunun genellikle iletişim için doğrudan ve açık bir yolu yoktur. Paketler, hem uç nokta makinelerinde hem de ağdaki ara makinelerde filtrelenir, yönlendirilir, çözümlenir ve dönüştürülür. Ağ adresi çevirileri (NAT) ve güvenlik duvarları, ağ iletişimine katılabileceğiniz ara uygulamaların yaygın örnekleridir.  
  
 Windows Communication Foundation (WCF) aktarımları ve ileti değişimi desenleri (MEPs), NAT ve güvenlik duvarlarının varlığına göre farklı şekilde tepki verir. Bu konuda, NAT ve güvenlik duvarlarının ortak ağ topolojilerinde nasıl çalıştığı açıklanmaktadır. WCF aktarımları ve MEPs 'lerin belirli birleşimlerine yönelik öneriler, uygulamalarınızın ağ üzerinde NAT ve güvenlik duvarları konusunda daha sağlam olmasına yardımcı olur.  
  
## <a name="how-nats-affect-communication"></a>NAT 'Lar Iletişimi nasıl etkiler  
 NAT, birkaç makinenin tek bir dış IP adresi paylaşmasını sağlamak üzere oluşturulmuştur. Bir bağlantı noktası yeniden eşleme NAT, bir dış IP adresini ve bağlantı noktasını yeni bir bağlantı noktası numarasıyla bir dış IP adresi bağlantısı için eşler. Yeni bağlantı noktası numarası NAT 'nin orijinal iletişimle dönüş trafiği ile ilişkilendirilmesi için izin verir. Birçok ev kullanıcısı artık özel olarak yönlendirilebilir bir IP adresine sahiptir ve paketlerin küresel olarak yönlendirilmesini sağlamak için bir NAT kullanır.  
  
 NAT bir güvenlik sınırı sağlamaz. Ancak, yaygın NAT yapılandırmalarında iç makinelerin doğrudan giderilmesi önlenir. Bu, her ikisi de iç makineleri bazı istenmeyen bağlantılardan korur ve verileri istemciye geri zaman uyumsuz olarak göndermek zorunda olan sunucu uygulamaları yazmayı zorlaştırır. NAT, paketlerin NAT makinesinde yer aldığı gibi görünüyor olması için paketlerdeki adresleri yeniden yazar. Bu, istemcinin istemciye geri bağlantı açmayı denediğinde başarısız olmasına neden olur. Sunucu istemcinin algılanan adresini kullanıyorsa, istemci adresi genel olarak yönlendirilemediğinden başarısız olur. Sunucu NAT adresini kullanıyorsa, hiçbir uygulama bu makinede dinleme yaptığından bağlantı başarısız olur.  
  
 Bazı NAT 'ler, dış makinelerin belirli bir iç makineye bağlanmasına izin vermek için iletme kurallarının yapılandırılmasını destekler. İletme kurallarını yapılandırmaya yönelik yönergeler farklı NAT 'Lar arasında farklılık gösterir ve son kullanıcılardan, çoğu uygulama için NAT yapılandırmalarını değiştirmesini ister. Birçok Son Kullanıcı, belirli bir uygulama için NAT yapılandırmalarını değiştirmek ya da istemiyor.  
  
## <a name="how-firewalls-affect-communication"></a>Güvenlik duvarları Iletişimi nasıl etkiler  
 *Güvenlik duvarı* , geçişine izin verip vermeyeceğine karar vermek için geçiş yapan trafiğe yönelik kurallar uygulayan bir yazılım veya donanım aygıtıdır. Gelen ve/veya giden trafik akışlarını incelemek için güvenlik duvarlarını yapılandırabilirsiniz. Güvenlik Duvarı, ağın kenarından veya uç nokta ana bilgisayarında ağ için bir güvenlik sınırı sağlar. İş kullanıcıları, kötü amaçlı saldırıları engellemek için sunucularını bir güvenlik duvarının arkasında geleneksel olarak tutmıştır. [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]' de kişisel güvenlik duvarının kullanıma sunulmasından sonra, güvenlik duvarının arkasındaki ev kullanıcılarının sayısı da büyük ölçüde artmıştır. Bu, bir bağlantının bir veya her iki ucunun de paketleri İnceleme güvenlik duvarı olmasını sağlar.  
  
 Güvenlik duvarları, paketlerin incelenmesinde karmaşıklık ve becerileri bakımından büyük ölçüde farklılık gösterir. Basit güvenlik duvarları, paketlerindeki kaynak ve hedef adreslere ve bağlantı noktalarına göre kuralları uygular. Akıllı güvenlik duvarları Ayrıca kararlar almak için paketlerin içeriğini inceleyebilir. Bu güvenlik duvarları birçok farklı yapılandırmada gelir ve genellikle özelleştirilmiş uygulamalar için kullanılır.  
  
 Ana Kullanıcı güvenlik duvarı için ortak bir yapılandırma, daha önce o makineye giden bir bağlantı yapılmadığı takdirde gelen bağlantıları yasaklayabilmelidir. Bir iş kullanıcısı güvenlik duvarı için ortak bir yapılandırma, özel olarak tanımlanmış bir grup hariç tüm bağlantı noktalarında gelen bağlantıları yasaklayadır. HTTP ve HTTPS hizmeti sağlamak için 80 ve 443 bağlantı noktaları dışındaki tüm bağlantı noktalarında bağlantıları yasaklayasaklayan bir güvenlik duvarıdır. Yönetilen güvenlik duvarları, hem ev hem de iş kullanıcıları için, makinede güvenilir bir kullanıcıya veya işleme izin veren güvenlik duvarı yapılandırmasını değiştirebilir. Yönetilen güvenlik duvarları, ağ kullanımını denetleyen kurumsal bir ilke olmadığı ev kullanıcıları için daha yaygındır.  
  
## <a name="using-teredo"></a>Teredo 'Yu kullanma  

 Teredo, bir NAT arkasındaki makinelerin doğrudan adreslenebilirliğini sağlayan bir IPv6 geçiş teknolojisidir. Teredo, olası bağlantıları tanıtmak için herkese açık ve genel olarak yönlendirilemeyen bir sunucu kullanımına dayanır. Teredo sunucusu, uygulama istemcisine ve sunucusuna, bağlantı bilgilerini değiş tokuş ettikleri ortak bir toplantı noktası sağlar. Daha sonra makineler geçici bir Teredo adresi ister ve paketler mevcut ağ üzerinden tünellenmiş. WCF 'de Teredo desteği, işletim sisteminde IPv6 ve Teredo desteğinin etkinleştirilmesini gerektirir. [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ve üzeri işletim sistemleri Teredo 'Yu destekler. Windows Vista ve sonraki işletim sistemleri IPv6 'Yı varsayılan olarak destekler ve yalnızca kullanıcının Teredo 'Yu etkinleştirmesini gerektirir. [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] ve Windows Server 2003, kullanıcının hem IPv6 hem de Teredo 'Yu etkinleştirmesini gerektirir. Daha fazla bilgi için bkz. [Teredo 'Ya genel bakış](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-xp/bb457011(v%3dtechnet.10)).  
  
## <a name="choosing-a-transport-and-message-exchange-pattern"></a>Aktarım ve Ileti değişim modelini seçme  
 Bir taşımanın ve MEP 'nin seçilmesi üç adımlı bir işlemdir:  
  
1. Uç nokta makinelerinin adreslenebilirliğini çözümleyin. Kuruluş sunucularının genellikle doğrudan adreslenebilirliği vardır, son kullanıcılar genellikle NAT 'Lar tarafından engellenen adreslenebilirliği vardır. Her iki uç nokta, son kullanıcılar arasındaki eşler arası senaryolar gibi bir NAT 'nin arkasındaysa, adreslenebilirliği sağlamak için Teredo gibi bir teknolojinin olması gerekebilir.  
  
2. Uç nokta makinelerinin protokol ve bağlantı noktası kısıtlamalarını çözümleyin. Kurumsal sunucular genellikle birçok bağlantı noktasını engelleyen güçlü güvenlik duvarlarının arkasında bulunur. Ancak, bağlantı noktası 80 genellikle HTTP trafiğine izin vermek için açıktır ve HTTPS trafiğine izin vermek için bağlantı noktası 443 açıktır. Son kullanıcılar, bağlantı noktası kısıtlamalarına sahip olma olasılığını azaltır, ancak yalnızca giden bağlantılara izin veren bir güvenlik duvarının arkasında olabilir. Bazı güvenlik duvarları uç noktada uygulamaların yönetimine seçmeli olarak bağlantı açmasına olanak sağlar.  
  
3. Ağ ve bağlantı noktası kısıtlamalarına izin veren taşımaları ve MEPs 'Leri hesaplama.  
  
 İstemci-sunucu uygulamaları için ortak bir topoloji, bir NAT 'ın arkasında, yalnızca giden bir güvenlik duvarıyla ve güçlü bir güvenlik duvarıyla doğrudan adreslenebilir bir sunucuyla Teredo olmadan bir NAT 'ın arkasında yer alan istemcilere sahip olur. Bu senaryoda, çift yönlü bir MEP ile TCP taşıması ve istek-yanıt verme için bir HTTP taşıması iyi bir şekilde çalışır. Eşler arası uygulamalar için ortak topoloji, NAT ve güvenlik duvarlarının arkasında her iki uç noktaya sahip olur. Bu senaryoda ve ağ topolojisinin bilinmediği senaryolarda aşağıdaki önerileri göz önünde bulundurun:  
  
- Çift aktarımlar kullanmayın. Çift bir aktarım daha fazla bağlantı açar, bu da başarıyla bağlanma olasılığını azaltır.  
  
- Kaynak bağlantısı üzerinden kanalları geri oluşturmayı destekler. Çift yönlü TCP gibi geri kanalları kullanmak, daha az bağlantı açar, bu da başarıyla bağlanma olasılığını artırır.  
  
- Uç noktaların veya geçiş trafiğinin kaydedilmesi için erişilebilir bir hizmet kullanmayı seçebilirsiniz. Ağ topolojisi kısıtlayıcıysa veya bilinmiyorsa, genel olarak erişilebilen bir bağlantı hizmetinin (örneğin, Teredo sunucusu) kullanılması, büyük bir olasılıkla başarıyla bağlanma olasılığını artırır.  
  
 Aşağıdaki tablolarda tek yönlü, istek-yanıt ve çift yönlü MEPs ve WCF ile standart TCP, TCP, Teredo ile standart ve çift HTTP aktarımları incelenecektir.  
  
|Çözümlenebilme|Doğrudan sunucu|NAT geçişi ile doğrudan sunucu|Sunucu NAT|NAT geçişi ile sunucu NAT|  
|--------------------|-------------------|--------------------------------------|----------------|-----------------------------------|  
|Doğrudan istemci|Herhangi bir taşıma ve MEP|Herhangi bir taşıma ve MEP|Desteklenmez.|Desteklenmez.|  
|NAT çapraz geçişine sahip istemci doğrudan|Herhangi bir taşıma ve MEP.|Herhangi bir taşıma ve MEP.|Desteklenmez.|Teredo ve herhangi bir MEP ile TCP. Windows Vista, Teredo ile HTTP 'yi desteklemeye yönelik makine genelindeki bir yapılandırma seçeneğidir.|  
|İstemci NAT|Tüm ikili olmayan taşıma ve MEP. Çift yönlü MEP TCP taşıması gerektirir.|Tüm ikili olmayan taşıma ve MEP. Çift yönlü MEP TCP taşıması gerektirir.|Desteklenmez.|Desteklenmez.|  
|NAT geçişi ile istemci NAT|Tüm ikili olmayan taşıma ve MEP. Çift yönlü MEP TCP taşıması gerektirir.|Hepsi, ikili HTTP ve herhangi bir MEP. Çift yönlü MEP TCP taşıması gerektirir. Çift TCP taşıması Teredo gerektirir. Windows Vista, Teredo ile HTTP 'yi desteklemeye yönelik makine genelindeki bir yapılandırma seçeneğidir.|Desteklenmez.|Teredo ve herhangi bir MEP ile TCP. Windows Vista, Teredo ile HTTP 'yi desteklemeye yönelik makine genelindeki bir yapılandırma seçeneğidir.|  
  
|Güvenlik duvarı kısıtlamaları|Sunucu açık|Yönetilen güvenlik duvarı olan sunucu|Yalnızca HTTP güvenlik duvarı olan sunucu|Yalnızca giden güvenlik duvarı olan sunucu|  
|---------------------------|-----------------|----------------------------------|-------------------------------------|-----------------------------------------|  
|İstemci açık|Herhangi bir taşıma ve MEP.|Herhangi bir taşıma ve MEP.|Herhangi bir HTTP taşıması ve MEP.|Desteklenmez.|  
|Yönetilen güvenlik duvarı olan istemci|Tüm ikili olmayan taşıma ve MEP. Çift yönlü MEP TCP taşıması gerektirir.|Tüm ikili olmayan taşıma ve MEP. Çift yönlü MEP TCP taşıması gerektirir.|Herhangi bir HTTP taşıması ve MEP.|Desteklenmez.|  
|Yalnızca HTTP güvenlik duvarı olan istemci|Herhangi bir HTTP taşıması ve MEP.|Herhangi bir HTTP taşıması ve MEP.|Herhangi bir HTTP taşıması ve MEP.|Desteklenmez.|  
|Yalnızca giden güvenlik duvarı olan istemci|Tüm ikili olmayan taşıma ve MEP. Çift yönlü MEP TCP taşıması gerektirir.|Tüm ikili olmayan taşıma ve MEP. Çift yönlü MEP TCP taşıması gerektirir.|Herhangi bir HTTP taşıması ve tüm çift yönlü olmayan MEP.|Desteklenmez.|
