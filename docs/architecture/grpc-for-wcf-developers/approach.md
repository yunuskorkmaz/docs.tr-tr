---
title: GRPC, WCF geliştiricileri için RPC-gRPC 'ye yaklaşır
description: WCF 'nin temel özellikleri gRPC ile karşılaştırılıyor.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 65d61c8246569d81dfec3aeb8e3df4bea26258dc
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184605"
---
# <a name="how-grpc-approaches-rpc"></a>GRPC 'nin RPC 'ye yaklaşımı

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Windows Communication Foundation (WCF) ve gRPC, *uzak yordam çağrısı* (RPC) deseninin her iki uygulaması da, farklı bir makinede çalışan hizmetlere çağrı yapmayı ve farklı bir işlemde, sorunsuz bir şekilde çalışmasını sağlar istemci uygulamasında Yöntem çağrıları. WCF ve GRPC 'nin amaçlar aynı olsa da, uygulamanın ayrıntıları oldukça farklıdır.

Aşağıdaki tabloda, WCF 'nin temel özelliklerinin gRPC ile nasıl ilişkilendirilebileceği ve kitabın geri kalanında daha ayrıntılı açıklamalar bulabileceğiniz yer verilmiştir.

| Özellikler | WCF | gRPC |
| -------- | --- | ---- |
| Hedefi | İş kodunu ağ uygulamasından ayır | İş kodunu arabirim tanımı ve ağ uygulamasından ayır |
| Hizmetleri ve iletileri tanımlama (Bölüm 3-4)  | Hizmet sözleşmesi, Işlem sözleşmesi ve veri sözleşmesi | Hizmetleri ve iletileri bildirmek için proto dosyasını kullanır |
| Dil (Bölüm 3-5) | C# Veya Visual Basic yazılan sözleşmeler | Protokol arabelleği dili |
| Tel biçimi (Bölüm 3) | SOAP/XML, düz XML, JSON, .NET Ikili vb. dahil olmak üzere yapılandırılabilir. | Protokol arabelleği ikili biçimi (diğer biçimleri kullanmak mümkün olsa da).
| Birlikte çalışabilirlik (Bölüm 4) | HTTP üzerinden SOAP kullanırken | Resmi destek: .NET, Java, Python, JavaScript, C/C++, Go, Rust, Ruby, Swift, Dart, php. Topluluktaki diğer diller için resmi olmayan destek. |
| Ağ oluşturma (Bölüm 4) | Çalışma zamanında yapılandırıldı. TCP, HTTP, MSMQ vb. arasında geçiş yapın. | Always HTTP/2 |
| Yaklaşım (Bölüm 4) | Temel sınıflarda serileştirme/serisini kaldırma ve ağ kodu oluşturma çalışma zamanı oluşturma | Temel sınıflarda serileştirme/serisini kaldırma ve ağ kodu oluşturma zamanı oluşturma |
| Güvenlik (Bölüm 6) | Kimlik doğrulaması, WS-güvenlik, ileti şifreleme | Kimlik bilgileri, ASP.NET Core güvenliği, TLS ağı |

>[!div class="step-by-step"]
>[Önceki](grpc-overview.md)
>[İleri](interface-definition-language.md)
