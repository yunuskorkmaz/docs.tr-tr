---
title: WCF ciltlemeler ve taşımalar - WCF geliştiricileri için gRPC
description: Farklı WCF bağlamalarının ve aktarımlarının gRPC ile karşılaştırıldığında nasıl olduğunu öğrenin.
ms.date: 09/02/2019
ms.openlocfilehash: 3a295268b486578c70c2c98f1d05f89070daaeb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147730"
---
# <a name="wcf-bindings-and-transports"></a>WCF bağlamaları ve aktarımları

Windows Communication Foundation (WCF), farklı ağ protokollerini, kablo biçimlerini ve diğer uygulama ayrıntılarını belirten yerleşik *bağlamalara* sahiptir. gRPC etkili sadece bir ağ protokolü ve bir tel biçimi vardır. (Teknik olarak tel biçimini *özelleştirebilirsiniz,* ancak bu kitabın kapsamı dışındadır.) GRPC'nin çoğu durumda en iyi çözümü sunduğunu keşfedeceksiniz.

Aşağıda en alakalı WCF ciltleri ve gRPC'deki eşdeğerleriyle nasıl karşılaştırıldıkları hakkında kısa bir tartışma yapılır.

## <a name="nettcp"></a>NetTCP

WCF'nin NetTCP bağlaması kalıcı bağlantılara, küçük iletilere ve çift yönlü iletilere olanak tanır. Ancak yalnızca .NET istemcileri ve sunucuları arasında çalışır. gRPC aynı işlevselliği sağlar, ancak birden çok programlama dili ve platformu arasında desteklenir.

gRPC WCF NetTCP bağlama birçok özelliğe sahiptir, ancak her zaman aynı şekilde uygulanmaz. Örneğin, WCF'de şifreleme yapılandırma yoluyla denetlenir ve çerçevede işlenir. gRPC'de, TLS üzerinden HTTP/2 üzerinden bağlantı düzeyinde şifreleme elde edilir.

## <a name="http"></a>HTTP

BasicHttpBinding adı verilen WCF bağlaması genellikle metin tabanlıdır ve tel biçimi olarak SOAP kullanır. NetTCP bağlama ile karşılaştırıldığında yavaş. Genellikle çapraz platform birlikte çalışabilirlik veya internet altyapısı üzerinden bağlantı sağlamak için kullanılır.

gRPC'deki eşdeğer, iletiler için ikili Protobuf tel biçimine sahip temel aktarım katmanı olarak HTTP/2'yi kullanır. Böylece NetTCP hizmet düzeyinde performans ve tüm modern programlama dilleri ve çerçeveleri ile tam çapraz platform birlikte çalışabilirlik sunabilir.

## <a name="named-pipes"></a>Adlandırılmış borular

WCF, aynı fiziksel makinedeki işlemler arasındaki iletişim için *bağlayıcı adlandırılmış bir boru* sağladı. ASP.NET Core gRPC'nin ilk sürümü adlandırılmış boruları desteklemez. Adlandırılmış borular (ve Unix etki alanı soketleri) için istemci ve sunucu desteği eklemek, gelecekteki bir sürüm için bir hedeftir.

## <a name="msmq"></a>MSMQ

MSMQ özel bir Windows ileti sırasıdır. WCF'nin MSMQ'ya bağlanması, gelecekte herhangi bir zamanda işlenebilecek istemcilerden gelen "yangın ve unut" isteklerini mümkün kılar. gRPC yerel olarak ileti sırası işlevselliği sağlamaz.

En iyi alternatif doğrudan Azure Servis Veri Servisi, RabbitMQ veya Kafka gibi bir mesajlaşma sistemi kullanmaktır. Bunu, istemcinin iletileri doğrudan kuyruğa yerleştirmesiyle veya iletileri sıraya koyan bir gRPC istemci akış hizmetiyle uygulayabilirsiniz.

## <a name="webhttpbinding"></a>Web'e Bağlanma

WebHttpBinding (ayrıca WCF REST olarak `WebGet` `WebInvoke` da bilinir), ve öznitelikleri ile, bu daha az yaygın olduğu bir zamanda JSON konuşabilen RESTful API'ler geliştirmek için etkin. WCF REST ile oluşturulmuş bir YENIDEN DOLU API'niz varsa, bunu düzenli bir ASP.NET Core MVC Web API uygulamasına geçirtmeyi düşünün. Bu geçiş, gRPC'ye dönüşümle aynı işlevselliği sağlar.

>[!div class="step-by-step"]
>[Önceki](wcf-endpoints-grpc-methods.md)
>[Sonraki](rpc-types.md)
