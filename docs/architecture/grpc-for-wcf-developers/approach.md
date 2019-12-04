---
title: GRPC, WCF geliştiricileri için RPC-gRPC 'ye yaklaşır
description: WCF 'nin temel özellikleri gRPC ile karşılaştırılıyor.
ms.date: 09/02/2019
ms.openlocfilehash: b924d2f20b54de2d6476a0b27626d5dd7fd0986f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711486"
---
# <a name="how-grpc-approaches-rpc"></a>gRPC'nin RPC yaklaşımı

Windows Communication Foundation (WCF) ve gRPC, *uzak yordam çağrısı* (RPC) deseninin her iki uygulamalarıdır. Bu model, farklı bir makinede çalışan hizmetlere çağrı yapmak için veya farklı bir işlemde, istemci uygulamasındaki Yöntem çağrıları gibi sorunsuz bir şekilde çalışır. WCF ve GRPC 'nin amaçlar aynı olsa da, uygulamanın ayrıntıları oldukça farklıdır.

Aşağıdaki tabloda, WCF 'nin temel özelliklerinin gRPC ile ilişkilendirilmesi ve daha ayrıntılı açıklamaları bulabileceğiniz yer verilmiştir.

| Özellikler | WCF | gRPC |
| -------- | --- | ---- |
| Hedefi | İş kodunu ağ uygulamasından ayırın. | İş kodunu arabirim tanımı ve ağ uygulamasından ayırın. |
| Hizmetleri ve iletileri tanımlama (Bölüm 3-4)  | Hizmet sözleşmesi, Işlem sözleşmesi ve veri sözleşmesi. | Hizmetleri ve iletileri bildirmek için proto dosyasını kullanır. |
| Dil (Bölüm 3-5) | C# Veya Visual Basic yazılan sözleşmeler. | Protokol arabelleği dili. |
| Tel biçimi (Bölüm 3) | SOAP/XML, düz XML, JSON ve .NET Ikili gibi yapılandırılabilir. | Protokol arabelleği ikili biçimi (diğer biçimleri kullanmak mümkün olsa da).
| Birlikte çalışabilirlik (Bölüm 4) | HTTP üzerinden SOAP kullanırken. | Resmi destek: .NET, Java, Python, JavaScript, C/C++, Go, Rust, Ruby, Swift, Dart, php. Topluluktaki diğer diller için resmi olmayan destek. |
| Ağ oluşturma (Bölüm 4) | Çalışma zamanında yapılandırıldı. NetTCP, HTTP ve MSMQ arasında geçiş yapın. | HTTP/2, şu anda yalnızca ASP.NET Core gRPC ile TCP üzerinde. |
| Yaklaşım (Bölüm 4) | Temel sınıflarda serileştirme, seri durumdan çıkarma ve ağ kodunun çalışma zamanı oluşturma. | Temel sınıflarda serileştirme, seri durumdan çıkarma ve ağ kodu oluşturma zamanı oluşturma. |
| Güvenlik (Bölüm 6) | Kimlik doğrulaması, WS-güvenlik, ileti şifreleme. | Kimlik bilgileri, ASP.NET Core güvenliği, TLS ağı. |

>[!div class="step-by-step"]
>[Önceki](grpc-overview.md)
>[İleri](interface-definition-language.md)
