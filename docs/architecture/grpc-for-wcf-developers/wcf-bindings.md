---
title: WCF bağlamaları ve aktarımları-WCF geliştiricileri için gRPC
description: Farklı WCF bağlamalarının ve aktarımların gRPC ile nasıl karşılaştırılacağını öğrenin.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 50bac73ee68d7156fc5fed55dfffb3ba7f2de924
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184059"
---
# <a name="wcf-bindings-and-transports"></a>WCF bağlamaları ve aktarımları

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

WCF, farklı ağ protokolleri, hat biçimleri ve diğer uygulama ayrıntılarını belirten birçok farklı yerleşik *bağlamaları* vardır. gRPC, tek bir ağ protokolüne ve tek bir hat biçimine sahiptir (Teknik olarak Tel biçimlendirme özelleştirilebilir ancak bu kitabın kapsamına göre daha fazla *olabilir* ). GRPC 'nin çoğu durumda en iyi çözümü sunduğunu keşfedersiniz. Aşağıda, en ilgili WCF bağlamaları ve gRPC 'deki eşdeğer değerleriyle nasıl Karşılaştırıldığı hakkında kısa bir tartışma verilmiştir.

## <a name="nettcp"></a>NetTCP

WCF 'nin NetTCP bağlaması kalıcı bağlantılar, küçük mesajlar ve iki yönlü mesajlaşma sağlar ancak yalnızca .NET istemcileri ve sunucuları arasında çalışmaktadır. gRPC aynı işlevselliğe izin verir ancak birden çok programlama dilinde ve platformunda desteklenir. gRPC, her zaman aynı şekilde uygulanmasa da, WCF NetTCP bağlamasının birçok özelliğine sahiptir. Örneğin, WCF 'de şifreleme yapılandırma ile denetlenir ve çerçevede işlenir. GRPC 'de şifreleme, TLS üzerinden HTTP/2 kullanılarak bağlantı düzeyinde elde edilir.

## <a name="http"></a>HTTP

WCF BasicHttpBinding genellikle metin tabanlıdır, hatta SOAP biçimi olarak SOAP kullanarak ve modern ağa bağlı uygulamaların standartları tarafından çok yavaştır. Yalnızca, platformlar arası birlikte çalışabilirlik veya internet altyapısı üzerinden bağlantı sağlamak için kullanılır. GRPC 'nin eşdeğeri; HTTP/2 ' de iletiler için ikili Protohat Tel biçimi ile temel alınan aktarım katmanı olarak HTTP/2 kullandığından, tüm modern programlama dilleri ile tam platformlar arası birlikte çalışabilirlik olanağı sunabilir ve çerçeveleri.

## <a name="named-pipes"></a>Adlandırılmış Kanallar

WCF, aynı fiziksel makinedeki süreçler arasındaki iletişim için adlandırılmış bir kanallar bağlaması sağladı. Adlandırılmış kanallar ASP.NET Core gRPC 'nin ilk sürümü tarafından desteklenmez.

Windows dışında, adlandırılmış kanallar tarafından sunulan işlevsellik bunun yerine genellikle UNIX etki alanı yuvaları tarafından sağlanır. Bu yuvalar `/var/run/docker.sock`, sistem ve sunucu olarak hangi GRPC ile çalışabileceği gibi, dosya sistemi adresleriyle temsil edilen normal TCP benzeri yuvalardır. Windows üzerinde adlandırılmış kanallar stili işlevini kullanmanız gerekiyorsa, Windows 10 ve Windows Server 'da bir sonraki güncelleştirme olan 2019 S4 içinde, etki alanı yuvalarını Windows içinde tam olarak desteklenen bir yerel özellik olarak ekler. Bu nedenle, Windows 'un bu ve sonraki sürümlerinde (veya Linux 'ta) çalışan gRPC Hizmetleri, adlandırılmış kanallar yerine etki alanı yuvaları kullanabilir. Ancak ekibiniz en son Windows sürümüne güncelleştiregerekmiyorsa, localhost TCP yuvalarını kullanmanız gerekir. Yerel TCP yuvalarını kullanmayla ilgili güvenlik sorunları, istemci ve sunucu arasında sertifika kimlik doğrulamasının kullanılmasıyla ele alınabilir.

## <a name="msmq"></a>MSMQ

MSMQ, özel bir Windows ileti kuyruğu. WCF 'nin MSMQ 'ya bağlanması, gelecekte herhangi bir zamanda işlenebilecek istemcilerden gelen istekleri "yangın ve unutmaları" sağlar. gRPC hiçbir ileti kuyruğu işlevini yerel olarak sağlamaz. En iyi alternatif, Azure Service Bus, ırbbitmq veya Kafka gibi bir mesajlaşma sistemini doğrudan kullanmaktır. Bu, istemci tarafından doğrudan sıraya ileti yerleştirilerek veya iletileri sıraya alan bir gRPC istemci akış hizmeti ile uygulanabilir.

## <a name="webhttpbinding"></a>WebHttpBinding

`WebGet` Ve`WebInvoke` öznitelikleri ile WebHttpBinding (WCF REST olarak da bilinir), bu, bundan daha az ortak olduğu zaman JSON 'ı tek seferde konuşabilme API 'leri geliştirmenize olanak sağlar. Bu nedenle, WCF REST ile oluşturulmuş bir yenilenmiş API 'niz varsa, gRPC 'ye dönüştürmek yerine eşdeğer işlevselliği sağlayacak şekilde onu düzenli bir ASP.NET Core MVC web API uygulamasına geçirmeyi düşünün.

>[!div class="step-by-step"]
>[Önceki](wcf-endpoints-grpc-methods.md)
>[İleri](rpc-types.md)
