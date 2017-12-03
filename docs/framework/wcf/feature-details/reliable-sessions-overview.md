---
title: "Güvenilir Oturumlar Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b6ca4b3e254055c7142259ea6022a53f003ea25f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="reliable-sessions-overview"></a>Güvenilir Oturumlar Genel Bakış

[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]SOAP Güvenilir Mesajlaşma SOAP uç noktalar arasında uçtan uca ileti aktarımı güvenilirlik sağlar. Bunu üstesinden aktarım hataları ve SOAP iletisi düzeyi hataları tarafından güvenilmeyen ağlarda yapar. Özellikle, SOAP veya taşıma aracılar arasında gönderilen iletiler için oturum tabanlı, tek ve (isteğe bağlı) sıralı teslim sağlar. İsteğe bağlı iletilerinin sıralama ile bir oturumda iletileri gruplandırma için oturum tabanlı teslim sağlar.

Bu konu, güvenilir oturumlar nasıl açıklar ve bunların ne zaman kullanılacağı ve bunların güvenliğini sağlama.

## <a name="wcf-reliable-sessions"></a>WCF güvenilir oturumlar

[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]güvenilir oturumlar bir SOAP WS-ReliableMessaging protokolü tarafından tanımlanan ileti güvenilir uygulamasıdır.

[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]SOAP Güvenilir Mesajlaşma bir uçtan uca güvenilir oturum sayısını veya Mesajlaşma uç noktaları ayrı aracılar türünü bağımsız olarak iki uç noktalar arasında sağlar. Bu SOAP (örneğin, HTTP proxy) kullanmayan tüm aktarım aracılar içerir veya SOAP (örneğin, SOAP tabanlı yönlendiriciler veya köprüleri) kullanan uç noktaları arasında akan iletileri için gerekli olan aracılar. Güvenilir oturum kanalı destekleyen *etkileşimli* iletişimi; böylece bu tür bir kanal tarafından bağlı hizmetleri aynı anda çalıştırmak ve düşük gecikme süresi, diğer bir deyişle, koşullar altında exchange ve işlem iletileri içinde görece kısa zaman aralıkları. Bu yüzden aralarında sağlanan yalıtım yok Bu bağlantı bu bileşenlerin ilerleme birlikte olun veya birlikte başarısız anlamına gelir.

Güvenilir oturum hataları iki tür maskeleri:

- Kayıp veya yinelenen iletiler ve gelen iletileri bir farklı sırasından gönderilmiş içerir SOAP iletisi düzeyi hataları.

- Hataları taşıma.

Güvenilir oturum WS-ReliableMessaging protokolü ve bir bellek içi aktarımı penceresi maskesi SOAP iletisi düzeyi hatalarına uygular ve aktarım hatası durumunda bağlantı yeniden oluşturur.

Güvenilir oturum IP paketleri için TCP sağladıkları için SOAP iletilerine sağlar. Bir tekil TCP yuva bağlantı sağlar sıralı düğümler arasında IP paketlerini aktarımını. Güvenilir aktarımı aynı türde güvenilir bir kanal sağlar, ancak aşağıdaki yollarla TCP yuva güvenilirlik farklıdır:

- Güvenilirlik SOAP ileti düzeyi, bayt değil rasgele boyutlu bir paket için.

- Güvenilirlik yalnızca TCP üzerinden aktarımı için Aktarım Tarafsız ' dir.

- Güvenilirlik belirli aktarım oturumuna (örneğin, oturumu bir TCP bağlantısı sağlar) bağlı değil ve birden fazla aktarım oturumu güvenilir oturum ömrü boyunca aynı anda veya sıralı olarak kullanabilirsiniz.

- Güvenilir oturum gönderici ve alıcı arasında aktarım bağlantıları aralarında bağlantı için gerekli sayısından bağımsız olarak SOAP uç noktası değil. Kısacası, TCP güvenilirlik güvenilir oturum uçtan uca güvenilirlik sağlarken taşıma bağlantısı, sona ereceği sona erer.

## <a name="reliable-sessions-and-bindings"></a>Güvenilir oturumlar ve bağlamaları

Daha önce belirtildiği gibi bir güvenilir oturum taşıma nötr değil. Ayrıca, istek-yanıt ya da çift yönlü gibi birçok ileti exchange düzenleri üzerinden bir güvenilir oturum kurabilirsiniz. A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenilir oturum bağlamaları kümesinden bir özellik olarak gösterilir.

Güvenilir oturum kullanan uç noktalarda kullanın:

- HTTP tabanlı aktarım standart bağlamaları:

  - `WsHttpBinding`ve istek-yanıt ya da tek yönlü sözleşmeler kullanıma sunar.

  - Güvenilir oturum bir istek-yanıt veya basit tek yönlü hizmet sözleşmesi kullanırken.

  - `WsDualHttpBinding`ve çift yönlü, istek-yanıt ya da tek yönlü sözleşmeler kullanıma sunar.

  - `WsFederationHttpBinding`ve istek-yanıt ya da tek yönlü sözleşmeler kullanıma sunar.

- TCP tabanlı aktarım standart bağlamaları:

  - `NetTcpBinding`ve çift yönlü, istek yanıt ya da tek yönlü sözleşmeler kullanıma sunar.

HTTPS gibi özel bir bağlama oluşturarak üzerinde hiçbir bir bağlama güvenilir oturum kullanın (sorunlar hakkında daha fazla bilgi için bkz: <a href="#reliable-sessions-and-security">güvenilir oturumlar ve güvenlik</a>) veya bir adlandırılmış kanal bağlama.

Güvenilir oturum farklı temel kanal türlerinde yığın ve sonuçta elde edilen güvenilir oturum kanalı şekli değişir. Hem istemci hem de sunucunun desteklediği güvenilir oturum kanal türünü kullanılan temel kanal türüne bağlıdır. Aşağıdaki tabloda istemci üzerinde temel alınan kanal türü bir işlevi olarak desteklenen oturum kanalları türlerini listeler.

| Güvenilir oturum kanal türleri &#8224;desteklenen; | `IRequestChannel` | `IRequestSessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :---------------: | :----------------------: | :--------------: | :---------------------: |
| `IOutputSessionChannel`                         | Evet               | Evet                      | Evet              | Evet                     |
| `IRequestSessionChannel`                        | Evet               | Evet                      | Hayır               | Hayır                      |
| `IDuplexSessionChannel`                         | Hayır                | Hayır                       | Evet              | Evet                     |

&#8224; Desteklenen kanal türleri için genel kullanılabilir değerler `TChannel` içine geçirilen parametre değeri <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> yöntemi.

Aşağıdaki tabloda, sunucu üzerinde temel alınan kanal türü bir işlevi olarak desteklenen oturum kanalları türlerini listeler.

| Güvenilir oturum kanal türleri &#8225;desteklenen; | `IReplyChannel` | `IReplySessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :-------------: | :--------------------: | :--------------: | :---------------------: |
| `IInputSessionChannel`                          | Evet             | Evet                    | Evet              | Evet                     |
| `IReplySessionChannel`                          | Evet             | Evet                    | Hayır               | Hayır                      |
| `IDuplexSessionChannel`                         | Hayır              | Hayır                     | Evet              | Evet                     |

&#8225; Desteklenen kanal türleri için genel kullanılabilir değerler `TChannel` içine geçirilen parametre değeri <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> yöntemi.

## <a name="reliable-sessions-and-security"></a>Güvenilir oturumlar ve güvenlik

Güvenilir oturum güvenli hale getirme (hizmet ve istemci) iletişim kuran taraflar doğrulanır ve oturumda değiştirilen iletilerin ile değiştirilmiş olmayan emin olmak önemlidir. Ayrıca, her tek tek güvenilir oturum bütünlüğünü sağlamak önemlidir. Güvenilir oturum temsil ve bir güvenlik oturumu kanalı tarafından yönetilen bir güvenlik bağlamı bağlayarak güvenlik altına alınır. Güvenlik kanal güvenlik oturumu sağlar. Oturum kurulması sırasında alınıp güvenlik belirteçleri, daha sonra Güvenilir oturumda iletileri güvenli hale getirmek için kullanılır.

Güvenilir oturum TCP-S olduğunda, TCP oturumu güvenilir oturum bağlıdır. Bu nedenle, güvenlik de güvenilir oturum bağlanmış taşıma güvenliği sağlar. Bu durumda, bağlantının yeniden kurulması kapalıdır.

Yalnızca HTTPS kullanırken istisnadır. Güvenli Yuva Katmanı (SSL) oturum güvenilir oturum bağlı değil. Bir güvenlik bağlamı (SSL oturumu) paylaşımı oturumları birbirinden korunmayan çünkü bu bir tehdit uygular; Bu olabilir veya uygulamaya bağlı olarak gerçek bir tehdit olmayabilir.

## <a name="using-reliable-sessions"></a>Güvenilir oturumlar kullanma

Kullanılacak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenilir oturumlar destekleyen bir güvenilir oturum bağlama ile bir uç nokta oluşturun. Sistem tarafından sağlanan bağlamalar birini kullanın, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bunu yapar, kendi özel bağlama oluşturma veya etkin güvenilir oturum ile sağlar.

Destekleyen ve güvenilir bir oturum varsayılan olarak etkin sistem tanımlı bağlamalar şunları içerir:

- <xref:System.ServiceModel.WSDualHttpBinding>

Güvenilir oturum bir seçenek olarak destekleyen ama bir varsayılan etkinleştirmezseniz sistem tarafından sağlanan bağlamalar şunları içerir:

- <xref:System.ServiceModel.WSHttpBinding>

- <xref:System.ServiceModel.WSFederationHttpBinding>

- <xref:System.ServiceModel.NetTcpBinding>

Özel bağlama oluşturma konusunda bir örnek için bkz: [nasıl yapılır: HTTPS ile özel bir güvenilir oturum bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).

Bir irdelemesi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenilir oturumlar destek bağlamaları bkz [System-Provided bağlamaları](../../../../docs/framework/wcf/system-provided-bindings.md).

## <a name="when-to-use-reliable-sessions"></a>Güvenilir oturumlar kullanma zamanı

Güvenilir oturumlar, uygulamanızda kullanmak ne zaman anlamak önemlidir. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]aynı anda etkin ve etkin uç noktalar arasında güvenilir oturumlar destekler. Uygulamanızı uç noktalardan biri gerektiriyorsa bir süre için kullanılamaz ve ardından sıraları güvenilirlik elde etmek için kullanın.

Senaryo iki uç nokta TCP üzerinden bağlı gerektiriyorsa, TCP güvenilir ileti alışverişlerinde sağlamak için yeterli olabilir. TCP sağlar bu yana bir güvenilir oturum kullanmak için gerekli olmasa da, paketleri sırası ve yalnızca bir kez ulaşır.

Senaryonuz herhangi biri aşağıdaki özelliklere sahipse, daha sonra ciddi bir güvenilir oturum kullanarak dikkate almanız gerekir.

- SOAP yönlendiriciler gibi SOAP aracılar

- Proxy aracıları veya taşıma köprüleri

- Aralıklı bağlantısı

- HTTP üzerinden oturumları

## <a name="see-also"></a>Ayrıca bkz.

[Hizmetler ve istemcileri yapılandırmak için bağlamaları kullanma](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)   
[WS güvenilir oturum](../../../../docs/framework/wcf/samples/ws-reliable-session.md)
