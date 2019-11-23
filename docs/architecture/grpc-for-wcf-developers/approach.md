---
title: GRPC, WCF geliştiricileri için RPC-gRPC 'ye yaklaşır
description: WCF 'nin temel özellikleri gRPC ile karşılaştırılıyor.
ms.date: 09/02/2019
ms.openlocfilehash: 1ebfd102217c9685c5ff5200386c642b2017e98f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968124"
---
# <a name="how-grpc-approaches-rpc"></a>gRPC'nin RPC yaklaşımı

Windows Communication Foundation (WCF) ve gRPC, *uzak yordam çağrısı* (RPC) deseninin her iki uygulamasıdır, farklı bir makinede çalışan hizmetlere çağrı yapmayı ve farklı bir işlemde, istemci uygulamasında yalnızca Yöntem çağrılarıyla sorunsuz bir şekilde çalışır. WCF ve GRPC 'nin amaçlar aynı olsa da, uygulamanın ayrıntıları oldukça farklıdır.

Aşağıdaki tabloda, WCF 'nin temel özelliklerinin gRPC ile nasıl ilişkilendirilebileceği ve kitabın geri kalanında daha ayrıntılı açıklamalar bulabileceğiniz yer verilmiştir.

| Özellikler | WCF | gRPC |
| -------- | --- | ---- |
| Hedefi | İş kodunu ağ uygulamasından ayır | İş kodunu arabirim tanımı ve ağ uygulamasından ayır |
| Hizmetleri ve iletileri tanımlama (Bölüm 3-4)  | Hizmet sözleşmesi, Işlem sözleşmesi ve veri sözleşmesi | Hizmetleri ve iletileri bildirmek için proto dosyasını kullanır |
| Dil (Bölüm 3-5) | C# Veya Visual Basic yazılan sözleşmeler | Protokol arabelleği dili |
| Tel biçimi (Bölüm 3) | SOAP/XML, düz XML, JSON, .NET Ikili vb. dahil olmak üzere yapılandırılabilir. | Protokol arabelleği ikili biçimi (diğer biçimleri kullanmak mümkün olsa da).
| Birlikte çalışabilirlik (Bölüm 4) | HTTP üzerinden SOAP kullanırken | Resmi destek: .NET, Java, Python, JavaScript, C/C++, Go, Rust, Ruby, Swift, Dart, php. Topluluktaki diğer diller için resmi olmayan destek. |
| Ağ oluşturma (Bölüm 4) | Çalışma zamanında yapılandırıldı. NetTCP, HTTP, MSMQ vb. arasında geçiş yapın. | HTTP/2, şu anda yalnızca ASP.NET Core gRPC ile TCP üzerinde. |
| Yaklaşım (Bölüm 4) | Temel sınıflarda serileştirme/serisini kaldırma ve ağ kodu oluşturma çalışma zamanı oluşturma | Temel sınıflarda serileştirme/serisini kaldırma ve ağ kodu oluşturma zamanı oluşturma |
| Güvenlik (Bölüm 6) | Kimlik doğrulaması, WS-güvenlik, ileti şifreleme | Kimlik bilgileri, ASP.NET Core güvenliği, TLS ağı |

>[!div class="step-by-step"]
>[Önceki](grpc-overview.md)
>[İleri](interface-definition-language.md)
