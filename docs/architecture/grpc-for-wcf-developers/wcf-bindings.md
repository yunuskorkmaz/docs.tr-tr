---
title: WCF bağlamaları ve aktarımları-WCF geliştiricileri için gRPC
description: Farklı WCF bağlamalarının ve aktarımların gRPC ile nasıl karşılaştırılacağını öğrenin.
ms.date: 09/02/2019
ms.openlocfilehash: ebe324eace8f5f418b920c59f6d72eaaa686ef02
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503345"
---
# <a name="wcf-bindings-and-transports"></a>WCF bağlamaları ve aktarımları

Windows Communication Foundation (WCF), farklı ağ protokolleri, hat biçimleri ve diğer uygulama ayrıntılarını belirten yerleşik *bağlamalara* sahiptir. gRPC 'nin etkin bir şekilde yalnızca bir ağ protokolü ve tek bir hat biçimi vardır. (Teknik olarak, kablo biçimini özelleştirebilirsiniz, ancak bu kitabın kapsamına *göre daha fazla* .) GRPC 'nin çoğu durumda en iyi çözümü sunduğunu keşfedersiniz. 

Aşağıda, en ilgili WCF bağlamaları ve gRPC 'deki eşdeğerleri ile nasıl Karşılaştırıldığı hakkında kısa bir tartışma verilmiştir.

## <a name="nettcp"></a>NetTCP

WCF 'nin NetTCP bağlaması, kalıcı bağlantılar, küçük mesajlar ve iki yönlü mesajlaşma sağlar. Ancak yalnızca .NET istemcileri ve sunucuları arasında çalışmaktadır. gRPC aynı işlevselliğe izin verir ancak birden çok programlama dilinde ve platformunda desteklenir. 

gRPC, WCF 'nin NetTCP bağlamasının birçok özelliğine sahiptir, ancak her zaman aynı şekilde uygulanmaz. Örneğin, WCF 'de şifreleme yapılandırma ile denetlenir ve çerçevede işlenir. GRPC 'de şifreleme, TLS üzerinden HTTP/2 aracılığıyla bağlantı düzeyinde elde edilir.

## <a name="http"></a>HTTP

BasicHttpBinding adlı WCF bağlaması genellikle metin tabanlıdır ve Tel biçimi olarak SOAP kullanır. NetTCP bağlamasıyla karşılaştırıldığında yavaştır. Genellikle platformlar arası birlikte çalışabilirlik veya internet altyapısı üzerinden bağlantı sağlamak için kullanılır. 

GRPC 'deki eşdeğer, iletiler için ikili prototip tel biçimde temel alınan aktarım katmanı olarak HTTP/2 kullanır. Bu nedenle, tüm modern programlama dilleri ve çerçeveleri ile NetTCP hizmet düzeyinde ve tam platformlar arası birlikte çalışabilirlik performansı sunabilir.

## <a name="named-pipes"></a>Adlandırılmış Kanallar

WCF, aynı fiziksel makinedeki süreçler arasındaki iletişim için *adlandırılmış bir kanallar* bağlaması sağladı. ASP.NET Core gRPC 'nin ilk sürümü adlandırılmış kanalları desteklemez. Adlandırılmış Kanallar (ve UNIX etki alanı yuvaları) için istemci ve sunucu desteği eklemek gelecekteki bir sürüm için hedeftir.

## <a name="msmq"></a>MSMQ

MSMQ, özel bir Windows ileti kuyruğu. WCF 'nin MSMQ 'ya bağlanması, gelecekte herhangi bir zamanda işlenebilen istemcilerden gelen istekleri "yangın ve unutmasını" sağlar. gRPC hiçbir ileti kuyruğu işlevini yerel olarak sağlamaz. 

En iyi seçenek, Azure Service Bus, Oybbitmq veya Kafka gibi bir mesajlaşma sistemini doğrudan kullanmaktır. Bunu, istemci ile iletileri doğrudan sıraya yerleştirerek veya iletileri sıraya alan bir gRPC istemci akış hizmeti ile gerçekleştirebilirsiniz.

## <a name="webhttpbinding"></a>WebHttpBinding

`WebGet` ve `WebInvoke` öznitelikleriyle birlikte, WebHttpBinding (WCF REST olarak da bilinir), bu, daha az ortak olduğu zaman JSON ile konuşabilme API 'Leri geliştirmenize olanak sağlar. WCF REST ile derlenmiş bir yenilenmiş API varsa, bunu normal bir ASP.NET Core MVC web API uygulamasına geçirmeyi düşünün. Bu geçiş, gRPC 'ye dönüştürmeye aynı işlevselliği sağlar.

>[!div class="step-by-step"]
>[Önceki](wcf-endpoints-grpc-methods.md)
>[İleri](rpc-types.md)
