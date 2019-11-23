---
title: WCF bağlamaları ve aktarımları-WCF geliştiricileri için gRPC
description: Farklı WCF bağlamalarının ve aktarımların gRPC ile nasıl karşılaştırılacağını öğrenin.
ms.date: 09/02/2019
ms.openlocfilehash: 233e3d030bc1f4450bd5cd6a7d7770486ca9e95a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966899"
---
# <a name="wcf-bindings-and-transports"></a>WCF bağlamaları ve aktarımları

WCF, farklı ağ protokolleri, hat biçimleri ve diğer uygulama ayrıntılarını belirten birçok farklı yerleşik *bağlamaları* vardır. gRPC, tek bir ağ protokolüne ve tek bir hat biçimine sahiptir (Teknik olarak Tel biçimlendirme özelleştirilebilir ancak bu kitabın kapsamına göre daha fazla *olabilir* ). GRPC 'nin çoğu durumda en iyi çözümü sunduğunu keşfedersiniz. Aşağıda, en ilgili WCF bağlamaları ve gRPC 'deki eşdeğer değerleriyle nasıl Karşılaştırıldığı hakkında kısa bir tartışma verilmiştir.

## <a name="nettcp"></a>NetTCP

WCF 'nin NetTCP bağlaması kalıcı bağlantılar, küçük mesajlar ve iki yönlü mesajlaşma sağlar ancak yalnızca .NET istemcileri ve sunucuları arasında çalışmaktadır. gRPC aynı işlevselliğe izin verir ancak birden çok programlama dilinde ve platformunda desteklenir. gRPC, her zaman aynı şekilde uygulanmasa da, WCF NetTCP bağlamasının birçok özelliğine sahiptir. Örneğin, WCF 'de şifreleme yapılandırma ile denetlenir ve çerçevede işlenir. GRPC 'de şifreleme, TLS üzerinden HTTP/2 kullanılarak bağlantı düzeyinde elde edilir.

## <a name="http"></a>HTTP

WCF BasicHttpBinding genellikle metin tabanlıdır, hatta SOAP biçimi olarak SOAP kullanarak ve NetTCP bağlamasıyla karşılaştırıldığında yavaştır. Genellikle platformlar arası birlikte çalışabilirlik veya internet altyapısı üzerinden bağlantı sağlamak için kullanılır. GRPC 'nin eşdeğeri; HTTP/2 ' de iletiler için ikili Protohat Tel biçimi ile temel alınan aktarım katmanı olarak HTTP/2 kullandığından, tüm modern programlama dilleri ile tam platformlar arası birlikte çalışabilirlik olanağı sunabilir ve çerçeveleri.

## <a name="named-pipes"></a>Adlandırılmış Kanallar

WCF, aynı fiziksel makinedeki süreçler arasındaki iletişim için adlandırılmış bir kanallar bağlaması sağladı. Adlandırılmış kanallar ASP.NET Core gRPC 'nin ilk sürümü tarafından desteklenmez. Adlandırılmış Kanallar (ve UNIX etki alanı yuvaları) için istemci ve sunucu desteği eklemek gelecekteki bir sürüm için hedeftir.

## <a name="msmq"></a>MSMQ

MSMQ, özel bir Windows ileti kuyruğu. WCF 'nin MSMQ 'ya bağlanması, gelecekte herhangi bir zamanda işlenebilecek istemcilerden gelen istekleri "yangın ve unutmaları" sağlar. gRPC hiçbir ileti kuyruğu işlevini yerel olarak sağlamaz. En iyi alternatif, Azure Service Bus, ırbbitmq veya Kafka gibi bir mesajlaşma sistemini doğrudan kullanmaktır. Bu, istemci tarafından doğrudan sıraya ileti yerleştirilerek veya iletileri sıraya alan bir gRPC istemci akış hizmeti ile uygulanabilir.

## <a name="webhttpbinding"></a>WebHttpBinding

`WebGet` ve `WebInvoke` öznitelikleriyle birlikte, WebHttpBinding (WCF ReST olarak da bilinir), bu, bundan daha az ortak olduğu zaman, JSON 'ı tek seferde konuşabilme API 'Leri geliştirmenize olanak sağlar. Bu nedenle, WCF REST ile oluşturulmuş bir yenilenmiş API 'niz varsa, gRPC 'ye dönüştürmek yerine eşdeğer işlevselliği sağlayacak şekilde onu düzenli bir ASP.NET Core MVC web API uygulamasına geçirmeyi düşünün.

>[!div class="step-by-step"]
>[Önceki](wcf-endpoints-grpc-methods.md)
>[İleri](rpc-types.md)
