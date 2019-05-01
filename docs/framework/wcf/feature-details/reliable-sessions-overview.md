---
title: Güvenilir Oturumlar Genel Bakış
ms.date: 03/30/2017
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
ms.openlocfilehash: 6dd90ef800daf236d77c419d48c0857ac2d78aa2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962663"
---
# <a name="reliable-sessions-overview"></a>Güvenilir Oturumlar Genel Bakış

Windows Communication Foundation (WCF) SOAP Güvenilir Mesajlaşma SOAP uç noktalar arasında uçtan uca ileti aktarım güvenilirlik sağlar. Bunu aktarım hataları üstesinden ve SOAP ileti düzeyi hataları tarafından güvenilmeyen ağlarda yapar. Özellikle, SOAP veya aktarım aracılar arasında gönderilen iletiler için oturum tabanlı, tek ve (isteğe bağlı olarak) sıralı teslim sağlar. İsteğe bağlı iletilerin sıralama ile bir oturumda iletileri gruplandırma için oturum tabanlı teslim sağlar.

Bu konu, güvenilir oturumlar nasıl açıklar ve bunların ne zaman kullanılacağı ve bunların güvenliğini sağlama.

## <a name="wcf-reliable-sessions"></a>WCF güvenilir oturumlar

SOAP WS-ReliableMessaging protokolü tarafından tanımlandığı gibi Mesajlaşma güvenilir uygulaması WCF güvenilir oturumlar var.

WCF SOAP Güvenilir Mesajlaşma için Mesajlaşma son noktalarını ayrı aracılar türü ve numarası bağımsız olarak iki uç noktalar arasında uçtan uca bir güvenilir oturum sağlar. Bu, SOAP (örneğin, HTTP proxy) kullanmayan herhangi bir aktarım aracılar içerir veya akış uç noktaları arasında iletileri için gerekli olan SOAP (örneğin, SOAP tabanlı yönlendiriciler veya köprüler) kullanan aracılar. Güvenilir oturum kanalı destekleyen *etkileşimli* iletişim böyle bir kanal tarafından bağlı hizmetleri aynı anda çalışmasını ve oldukça düşük gecikme süresi, diğer bir deyişle, koşulları altında exchange ve işlem iletileri içindeki kısa zaman aralıkları. Bunlar arasında sağlanan yalıtımsız olduğundan bu bağlantı bu bileşenler birlikte ilerlemekte veya birlikte, yük anlamına gelir.

Güvenilir oturum iki tür hatalardan maskeleri:

- Kayıp veya yinelenen iletileri ve gelen iletileri içinde gönderildikleri sırayla ile farklı sırada içeren SOAP ileti düzeyi hataları.

- Hataları taşıma.

Güvenilir oturum WS-ReliableMessaging protokolü ve bir bellek içi aktarımı penceresine maskesi SOAP ileti düzeyi hataları uygular ve aktarım hatası durumunda bağlantıları yeniden oluşturur.

Güvenilir oturum için SOAP iletilerini, TCP IP paketleri için sağlanan korumanın sağlar. TCP yuvası bağlantısı sağlayan bir tekil sırayla düğümleri arasında IP paketlerini aktarımı. Güvenilir Aktarım aynı türde güvenilir bir kanal sağlar, ancak aşağıdaki yollarla TCP yuva güvenilirlik farklıdır:

- Güvenilirlik en SOAP ileti düzeyi, bayt değil rasgele boyutlu bir paket için.

- Güvenilirlik, yalnızca TCP üzerinden aktarım için Aktarım konumlandırılıp.

- Güvenilirlik, belirli bir aktarım oturumu (örneğin, oturum TCP bağlantısı sağlar) bağlı değildir ve eşzamanlı olarak ya da sıralı olarak bir güvenilir oturum yaşam süresi boyunca birden çok aktarım oturumu kullanabilirsiniz.

- Güvenilir oturum gönderen ve alıcı arasında taşıma bağlantılarıyla bunları arasında bağlantı kurmak için gerekli sayısından bağımsız olarak SOAP uç noktası olan. Kısacası, TCP güvenilirlik güvenilir oturum uçtan uca güvenilirlik sağlarken Aktarım bağlantısı, sona ereceği sona erer.

## <a name="reliable-sessions-and-bindings"></a>Güvenilir oturumlar ve bağlamaları

Daha önce bahsedildiği gibi bir güvenilir oturum aktarımı nötr ' dir. Ayrıca, istek-yanıt ya da çift yönlü gibi çok sayıda ileti exchange düzenleri üzerinden bir güvenilir oturum kurabilirsiniz. Bir WCF güvenilir oturum bağlama bir dizi özelliği olarak kullanıma sunulur.

Güvenilir oturum kullanan uç noktalarda kullanın:

- HTTP tabanlı taşıma standart bağlamaları:

  - `WsHttpBinding` ve istek-yanıt ya da tek yönlü sözleşmeler kullanıma sunar.

  - Güvenilir oturum, istek-yanıt ya da basit tek yönlü hizmet sözleşmesi üzerinden kullanırken.

  - `WsDualHttpBinding` ve çift yönlü, istek-yanıt ya da tek yönlü sözleşmeler kullanıma sunar.

  - `WsFederationHttpBinding` ve istek-yanıt ya da tek yönlü sözleşmeler kullanıma sunar.

- TCP tabanlı taşıma standart bağlamaları:

  - `NetTcpBinding` ve çift yönlü, istek yanıt veya tek yönlü sözleşmeler kullanıma sunar.

Güvenilir oturum HTTPS gibi özel bir bağlama oluşturarak diğer bağlamalarda kullanın (sorunları hakkında daha fazla bilgi için bkz. <a href="#reliable-sessions-and-security">güvenilir oturumlar ve güvenlik</a>) veya bir adlandırılmış kanal bağlama.

Arka plandaki kanal farklı güvenilir bir oturumda yığınlayabilir ve sonuçta elde edilen güvenilir oturum kanal şekli değişir. Hem istemci hem de sunucu desteklenen güvenilir oturum kanal türünü kullanılan temel alınan kanal türüne bağlıdır. Aşağıdaki tabloda, istemcide bir arka plandaki kanal türü işlevi olarak desteklenen oturum kanalları türlerini listeler.

| Güvenilir oturum kanalı türleri desteklenir&#8224; | `IRequestChannel` | `IRequestSessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :---------------: | :----------------------: | :--------------: | :---------------------: |
| `IOutputSessionChannel`                         | Evet               | Evet                      | Evet              | Evet                     |
| `IRequestSessionChannel`                        | Evet               | Evet                      | Hayır               | Hayır                      |
| `IDuplexSessionChannel`                         | Hayır                | Hayır                       | Evet              | Evet                     |

&#8224;Desteklenen kanal türleri için genel kullanılabilir değerler: `TChannel` yöntemlere geçirilen parametre değeri <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> yöntemi.

Aşağıdaki tabloda, sunucuda desteklenen bir arka plandaki kanal türü işlevi olarak oturum kanalları türlerini listeler.

| Güvenilir oturum kanalı türleri desteklenir&#8225; | `IReplyChannel` | `IReplySessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :-------------: | :--------------------: | :--------------: | :---------------------: |
| `IInputSessionChannel`                          | Evet             | Evet                    | Evet              | Evet                     |
| `IReplySessionChannel`                          | Evet             | Evet                    | Hayır               | Hayır                      |
| `IDuplexSessionChannel`                         | Hayır              | Hayır                     | Evet              | Evet                     |

&#8225;Desteklenen kanal türleri için genel kullanılabilir değerler: `TChannel` yöntemlere geçirilen parametre değeri <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> yöntemi.

## <a name="reliable-sessions-and-security"></a>Güvenilir oturumlar ve güvenlik

Güvenilir oturum güvenli hale getirme (hizmet ve istemci) iletişim kuran taraflar doğrulanır ve oturumda alınıp verilen iletileri ile değiştirilmiş olmayan sağlamak önemlidir. Ayrıca, tek tek her güvenilir oturum bütünlüğünü sağlamak önemlidir. Güvenilir oturum, temsil ve güvenlik oturum kanalı tarafından yönetilen bir güvenlik bağlamı bağlayarak güvenli hale getirilir. Güvenlik kanalı güvenlik oturumu sağlar. Oturum kurulması sırasında değiştirilen güvenlik belirteçleri, daha sonra güvenilir bir oturumda iletileri güvenli hale getirmek için kullanılır.

TCP-S üzerinden bir güvenilir oturum olduğunda, TCP oturumu için güvenilir oturum bağlıdır. Bu nedenle, güvenlik için güvenilir oturum bağlıdır aktarım güvenliği sağlar. Bu durumda, bağlantının yeniden kurulması kapalıdır.

HTTPS kullanarak tek özel durum andır. Güvenli Yuva Katmanı (SSL) oturum güvenilir oturuma bağlı değil. Bir güvenlik bağlamı (SSL oturumu) paylaşımı oturumları birbirinden korunmayan çünkü bu bir tehdit uygular; Bu işlem sonrasında veya uygulamaya bağlı olarak gerçek bir tehdit olabilir.

## <a name="using-reliable-sessions"></a>Güvenilir oturumlar kullanma

WCF güvenilir oturumlar kullanmak için bir uç nokta destekleyen bir güvenilir oturum bağlama ile oluşturun. WCF ile güvenilir oturum sağlar sistem tarafından sağlanan bağlamalar birini kullanın, etkin veya bunu kendi özel bir bağlama oluşturun.

Destekleyen ve bir güvenilir oturum varsayılan olarak etkin sistem tanımlı bağlamalar şunlardır:

- <xref:System.ServiceModel.WSDualHttpBinding>

İsteğe bağlı olarak bir güvenilir oturum destekleyen ancak bir varsayılan olarak etkinleştirme sistem tarafından sağlanan bağlamalar şunlardır:

- <xref:System.ServiceModel.WSHttpBinding>

- <xref:System.ServiceModel.WSFederationHttpBinding>

- <xref:System.ServiceModel.NetTcpBinding>

Özel bağlama oluşturma örneği için bkz: [nasıl yapılır: HTTPS ile özel bir güvenilir oturum bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).

Güvenilir oturumlar destekleyen WCF bağlamaları için bkz [System-Provided bağlamaları](../../../../docs/framework/wcf/system-provided-bindings.md).

## <a name="when-to-use-reliable-sessions"></a>Güvenilir oturumlar kullanıldığı durumlar

Güvenilir oturumlar kullanmak ne zaman anlamak önemlidir. WCF aynı anda etkin ve etkin uç noktalar arasında güvenilir oturumları destekler. Uygulamanız uç noktalardan biri gerektiriyorsa bir süre için kullanılamaz ve güvenilirlik elde etmek için sıraları kullanın.

Senaryo iki uç nokta TCP üzerinden bağlı gerektiriyorsa, TCP güvenilir ileti alışverişlerinde sağlamak için yeterli olabilir. TCP sağlar bu yana bir güvenilir oturum kullanmak için gerekli olmasa da, paketleri sırasını ve yalnızca bir kez ulaşır.

Senaryonuz herhangi biri aşağıdaki özelliklere sahip, ardından ciddi bir güvenilir oturum kullanmayı düşünmeniz gerekir.

- SOAP yönlendiriciler gibi SOAP aracıları

- Proxy aracıları veya aktarım köprüleri

- Aralıklı bağlantı

- HTTP üzerinden oturumlar

## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [WS Güvenilir Oturum](../../../../docs/framework/wcf/samples/ws-reliable-session.md)
