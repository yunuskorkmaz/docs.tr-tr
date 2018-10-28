---
title: WCF ve ASP.NET Web API
ms.date: 03/30/2017
ms.assetid: 08ceded3-fd9a-4467-9715-c4cbd9c7228e
ms.openlocfilehash: 9ff974ca59b5a6448a140cbb1e7d6e8114840bdf
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50040654"
---
# <a name="wcf-and-aspnet-web-api"></a>WCF ve ASP.NET Web API
WCF hizmet odaklı uygulamalar oluşturmak için Microsoft'un programlama modelidir. Bu, geliştiricilerin platformlar arasında tümleştirin ve mevcut yatırımlarınızdan ile birlikte çalışmak güvenli, güvenilir, hizmetteki çözümleri oluşturmasına olanak sağlar. [ASP.NET Web API](https://www.asp.net/web-api) istemciler, tarayıcılar ve mobil cihazlar dahil olmak üzere geniş bir yelpazede ulaşan HTTP hizmetlerini oluşturmayı kolaylaştıran bir çerçevedir. ASP.NET Web API'si, .NET Framework üzerinde RESTful uygulamaları geliştirmek için ideal bir platformdur. Bu konuda, hangi teknoloji ihtiyaçlarınızı en iyi karşılayacak karar vermenize yardımcı olacak rehberlik sunulmaktadır.  
  
## <a name="choosing-which-technology-to-use"></a>Kullanılacak teknolojileri seçme  
 Aşağıdaki tabloda her bir teknolojiyi önemli özelliklerini açıklar.  
  
|WCF|ASP.NET Web API|  
|---------|---------------------|  
|Birden çok aktarım protokolünü (HTTP, TCP, UDP ve özel taşımalar) destekleyen yapı hizmetleri sağlar ve bunlar arasında geçişi sağlar.|Yalnızca HTTP. HTTP için birinci sınıf programlama modeli. Çeşitli tarayıcılarda, mobil cihazlara ulaşın geniş vb. etkinleştirme erişim için daha uygundur.|  
|Aynı mesajın birden fazla kodlamaları (metin, MTOM ve ikili) destekleyen hizmetler oluşturmaya etkinleştirir, yazın ve bunlar arasında geçişi sağlar.|Medya türleri XML, JSON vb. dahil olmak üzere çeşitli destek Web API'leri oluşturmaya olanak tanır.|  
|WS - hizmetleri oluşturmaya destekler * standartları güvenilir Mesajlaşma işlemleri, ileti güvenliği ister.|Temel protokolünü kullanır ve HTTP, WebSockets, SSL, JSON ve XML gibi biçimlendirir. Güvenilir Mesajlaşma veya işlemleri gibi daha yüksek düzey protokoller için desteği yoktur.|  
|İstek-yanıt, bir şekilde ve çift yönlü ileti exchange desenleri destekler.|HTTP istek/yanıt olduğunda ancak ek desenleri aracılığıyla desteklenmesi [SignalR](https://github.com/SignalR/SignalR) ve WebSockets tümleştirme.|  
|SOAP WCF Hizmetleri istemci proxy'leri karmaşık şemaları ile Hizmetleri için bile oluşturmak için WSDL otomatik araçlar sağlayan içindeki açıklanabilir.|Bir OData API'leri tümleşik yapısal meta verileri için kod parçacıkları açıklayan otomatik olarak oluşturulan HTML Yardım sayfasından arasında değişen bir Web API'sini açıklamak için çeşitli yollar vardır.|  
|.NET framework ile birlikte gönderilmektedir.|.NET framework ile birlikte gelir ancak açık kaynaklı ve ayrıca kullanılabilir-bant bağımsız indirirsiniz.|  
  
 WCF taşımalar çeşitli erişilebilir olan güvenilir, güvenli web hizmetleri oluşturmak için kullanın. Çok çeşitli istemcileri erişilebilir olan HTTP tabanlı hizmetler oluşturmak için ASP.NET Web API'sini kullanın. ASP.NET Web API oluşturma ve yeni REST stili hizmetler tasarlama kullanın. WCF REST stilinde Hizmetleri yazmak için bazı destek sağlar, ancak KALAN ASP.NET Web API desteği daha tamamlandı ve gelecekteki tüm REST özellik geliştirmeleri, ASP.NET Web API'de hale getirilir. Mevcut bir WCF Hizmeti varsa ve ek REST uç noktalarını kullanıma sunmak istediğiniz WCF kullanın ve <xref:System.ServiceModel.WebHttpBinding>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Communication Foundation nedir?](../../../docs/framework/wcf/whats-wcf.md)  
 [Temel Windows Communication Foundation Kavramları](../../../docs/framework/wcf/fundamental-concepts.md)  
