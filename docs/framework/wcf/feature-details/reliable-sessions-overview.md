---
title: Güvenilir Oturumlar Genel Bakış
ms.date: 03/30/2017
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
ms.openlocfilehash: a85a34c5e2ec7928c01586e4b01cdf5e90e896a7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601094"
---
# <a name="reliable-sessions-overview"></a>Güvenilir Oturumlar Genel Bakış

Windows Communication Foundation (WCF) SOAP ile güvenilir mesajlaşma, SOAP uç noktaları arasında uçtan uca ileti aktarım güvenilirliği sağlar. Bu, çok fazla aktarım hatalarıyla ve SOAP ileti düzeyi hatalarıyla güvenilir olmayan ağlarda bunu yapar. Özellikle, SOAP veya aktarım aracıları arasında gönderilen iletiler için oturum tabanlı, tek ve (isteğe bağlı) sıralı teslim sağlar. Oturum tabanlı teslim, iletilerin isteğe bağlı sıralamasına sahip bir oturumdaki iletileri gruplandırmak için sağlar.

Bu konuda güvenilir oturumlar, nasıl ve ne zaman kullanılacağı ve bunların nasıl güvenliği sağlanacağı açıklanmaktadır.

## <a name="wcf-reliable-sessions"></a>WCF güvenilir oturumlar

WCF güvenilir oturumlar, WS-ReliableMessaging protokolü tarafından tanımlanan SOAP Güvenilir Mesajlaşma 'nın bir uygulamasıdır.

WCF SOAP Güvenilir Mesajlaşma, mesajlaşma uç noktalarını ayıran aracıların sayısından veya türünden bağımsız olarak iki uç nokta arasında uçtan uca güvenilir bir oturum sağlar. Bu, uç noktalar arasında akışı yapılan iletiler için gereken SOAP (örneğin, SOAP tabanlı yönlendiriciler veya köprüler) kullanan tüm aktarım aracıları içerir. Güvenilir bir oturum kanalı, bu tür bir kanalla bağlanan hizmetlerin aynı anda ve Exchange ve iletileri düşük gecikme süresi (görece kısa bir süre içinde) altında işlemesini sağlayacak şekilde *etkileşimli* iletişimi destekler. Bu, bu bileşenlerin birlikte ilerlemesini veya birlikte başarısız olduğunu, bu nedenle aralarında yalıtımsız olduğunu gösterir.

Güvenilir oturum maskeleri iki tür başarısızlık:

- Kayıp veya yinelenen iletileri ve gönderildikleri sırada farklı bir sıraya ulaşan iletileri içeren SOAP ileti düzeyindeki hatalar.

- Aktarım sorunları.

Güvenilir bir oturum, SOAP ileti düzeyindeki hataların maskesini yapmak ve aktarım hatalarının oluşması durumunda bağlantıları yeniden eklemek için WS-ReliableMessaging protokolünü ve bellek içi Aktarım penceresini uygular.

Güvenilir bir oturum, TCP 'nin IP paketleri için sağladığı SOAP iletilerine yöneliktir. TCP yuvası bağlantısı, düğümler arasında IP paketlerinin tekil, sıralı bir aktarımını sağlar. Güvenilir kanal aynı türde güvenilir aktarım sağlar, ancak aşağıdaki yollarla TCP yuvası güveninden farklıdır:

- Güvenilirlik, rastgele boyutlu bir bayt paketi için değil, SOAP ileti düzeyidir.

- Güvenilirlik, yalnızca TCP üzerinden aktarım için değil, aktarım açısından tarafdır.

- Güvenilirlik, belirli bir aktarım oturumuna bağlı değildir (örneğin, bir TCP bağlantısının sağladığı oturum) ve eşzamanlı olarak veya güvenilir oturumun kullanım ömrü boyunca ardışık olarak birden çok aktarım oturumu kullanabilir.

- Güvenilir oturum, gönderen ve alıcı SOAP uç noktaları arasındadır, aralarında bağlantı için gereken aktarım bağlantısı sayısı ne olursa olsun. Kısacası, güvenli bir oturum uçtan uca güvenilirlik sağladığından, aktarım bağlantısının bittiği yerde TCP güvenilirliği sona erer.

## <a name="reliable-sessions-and-bindings"></a>Güvenilir Oturumlar ve bağlamalar

Daha önce belirtildiği gibi, güvenilir bir oturum taşıma taraflıdır. Ayrıca, istek-yanıt veya çift yönlü gibi birçok ileti değişim deseninden güvenilir bir oturum kurabilirsiniz. WCF güvenilir oturumu bir bağlama kümesinin özelliği olarak sunulur.

Kullanan uç noktalarda güvenilir bir oturum kullanın:

- HTTP tabanlı Aktarım standart bağlamaları:

  - `WsHttpBinding`ve istek-yanıt veya tek yönlü sözleşmeleri kullanıma sunar.

  - İstek-yanıt veya basit tek yönlü hizmet sözleşmesi üzerinde güvenilir oturum kullanırken.

  - `WsDualHttpBinding`ve çift yönlü, istek-yanıt veya tek yönlü sözleşmeleri kullanıma sunar.

  - `WsFederationHttpBinding`ve istek-yanıt veya tek yönlü sözleşmeleri kullanıma sunar.

- TCP tabanlı Aktarım standart bağlamaları:

  - `NetTcpBinding`ve çift yönlü, istek yanıtı veya tek yönlü sözleşmeleri kullanıma sunar.

HTTPS gibi özel bir bağlama oluşturarak (sorunlar hakkında daha fazla bilgi için bkz. <a href="#reliable-sessions-and-security">Güvenilir Oturumlar ve güvenlik</a>) veya adlandırılmış bir kanal bağlamasında güvenilir bir oturum kullanın.

Farklı temel alınan kanal türlerinde güvenilir bir oturum yığabilirsiniz ve sonuçta elde edilen güvenilir oturum kanalı şekli farklılık gösterir. Hem istemcide hem de sunucuda, desteklenen güvenilir oturum kanalının türü, kullanılan temeldeki kanalın türüne bağlıdır. Aşağıdaki tabloda, istemci üzerinde temel alınan kanal türünün bir işlevi olarak desteklenen oturum kanalının türleri listelenmektedir.

| Desteklenen güvenilir oturum kanalı türleri&#8224; | `IRequestChannel` | `IRequestSessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :---------------: | :----------------------: | :--------------: | :---------------------: |
| `IOutputSessionChannel`                         | Yes               | Yes                      | Yes              | Yes                     |
| `IRequestSessionChannel`                        | Yes               | Yes                      | Hayır               | Hayır                      |
| `IDuplexSessionChannel`                         | Hayır                | Hayır                       | Yes              | Yes                     |

Desteklenen kanal türleri &#8224;, `TChannel` metoduna geçirilen genel parametre değeri için kullanılabilir değerlerdir <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> .

Aşağıdaki tabloda, sunucuda, temel alınan kanal türünün bir işlevi olarak desteklenen oturum kanalı türleri listelenmektedir.

| Desteklenen güvenilir oturum kanalı türleri&#8225; | `IReplyChannel` | `IReplySessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :-------------: | :--------------------: | :--------------: | :---------------------: |
| `IInputSessionChannel`                          | Yes             | Yes                    | Yes              | Yes                     |
| `IReplySessionChannel`                          | Yes             | Yes                    | Hayır               | Hayır                      |
| `IDuplexSessionChannel`                         | Hayır              | Hayır                     | Yes              | Yes                     |

Desteklenen kanal türleri &#8225;, `TChannel` metoduna geçirilen genel parametre değeri için kullanılabilir değerlerdir <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> .

## <a name="reliable-sessions-and-security"></a>Güvenilir Oturumlar ve güvenlik

Güvenilir bir oturumun güvenli hale getirilmesi, iletişim tarafların (hizmet ve istemci) kimliğinin doğrulanmasını ve oturumda değiştirilen iletilerin üzerinde oynanmamasını sağlamak açısından önemlidir. Ayrıca, her bireysel güvenilir oturumun bütünlüğünden emin olmak önemlidir. Güvenilir bir oturum, güvenlik oturumu kanalı tarafından temsil edilen ve yönetilen bir güvenlik bağlamına bağlayarak güvenli hale getirilir. Güvenlik kanalı bir güvenlik oturumu sağlar. Oturum oluşturma sırasında değiş tokuş edilen güvenlik belirteçleri, güvenilir oturumdaki iletilerin güvenliğini sağlamak için kullanılır.

Güvenilir bir oturum TCP-S üzerinden olduğunda, TCP oturumu güvenilir oturuma bağlanır. Bu nedenle, taşıma güvenliği güvenliğin güvenilir oturuma da bağlı olmasını sağlar. Bu durumda, bağlantı yeniden kurma kapalıdır.

Tek özel durum HTTPS kullanılırken olur. Güvenli Yuva Katmanı (SSL) oturumu güvenilir oturumla bağlantılı değil. Bu, bir güvenlik bağlamını (SSL oturumu) paylaşan oturumlar birbirinden korunmadığı için bir tehdit getirir; Bu, uygulamaya bağlı olarak gerçek bir tehdit olabilir veya olmayabilir.

## <a name="using-reliable-sessions"></a>Güvenilir oturumları kullanma

WCF güvenilir oturumlarını kullanmak için, güvenilir bir oturumu destekleyen bağlama ile bir uç nokta oluşturun. Güvenilir oturum etkinken WCF 'nin sağladığı sistem tarafından sağlanan bağlamalardan birini kullanın veya bunu yapan kendi özel bağlamalarınızı oluşturun.

Varsayılan olarak güvenilir bir oturumu destekleyen ve etkinleştiren sistem tarafından tanımlanan bağlamalar şunları içerir:

- <xref:System.ServiceModel.WSDualHttpBinding>

Bir seçenek olarak güvenilir bir oturumu destekleyen ancak varsayılan olarak bir tane etkinleştirmeyin sistem tarafından sağlanmış bağlamalar şunları içerir:

- <xref:System.ServiceModel.WSHttpBinding>

- <xref:System.ServiceModel.WSFederationHttpBinding>

- <xref:System.ServiceModel.NetTcpBinding>

Özel bağlamanın nasıl oluşturulacağı hakkında bir örnek için bkz. [nasıl yapılır: https Ile özel güvenilir oturum bağlama oluşturma](how-to-create-a-custom-reliable-session-binding-with-https.md).

Güvenilir oturumları destekleyen WCF bağlamalarıyla ilgili bir tartışma için bkz. [sistem tarafından sunulan bağlamalar](../system-provided-bindings.md).

## <a name="when-to-use-reliable-sessions"></a>Güvenilir oturumlar ne zaman kullanılır?

Uygulamanızda güvenilir oturumların ne zaman kullanılacağını anlamak önemlidir. WCF, etkin ve canlı uç noktalar arasındaki güvenilir oturumları aynı anda destekler. Uygulamanız bir süre için uç noktalardan birini gerektiriyorsa, güvenilirlik elde etmek için kuyrukları kullanın.

Senaryo TCP üzerinden bağlı iki uç nokta gerektiriyorsa, TCP güvenilir ileti alışverişi sağlamak için yeterli olabilir. TCP, paketlerin sırayla ve yalnızca bir kez ulaşmasını gerektirdiğinden, güvenilir bir oturum kullanılması gerekli değildir.

Senaryonuz aşağıdaki özelliklerden herhangi birini içeriyorsa güvenilir bir oturum kullanmayı göz önünde bulundurmanız gerekir.

- SOAP yönlendiricileri gibi SOAP aracıları

- Proxy aracıları veya aktarım köprüleri

- Aralıklı bağlantı

- HTTP üzerinden oturumlar

## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../using-bindings-to-configure-services-and-clients.md)
- [WS Güvenilir Oturum](../samples/ws-reliable-session.md)
