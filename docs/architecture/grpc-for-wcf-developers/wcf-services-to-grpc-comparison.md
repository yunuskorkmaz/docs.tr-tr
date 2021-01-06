---
title: WCF geliştiricileri için WCF 'yi gRPC-gRPC ile karşılaştırma
description: Dağıtılmış uygulamalar oluşturmak için WCF ve gRPC çerçeveleri karşılaştırması.
ms.date: 12/15/2020
ms.openlocfilehash: 7dd41c3d6f248bb1ef5eacb323b1443c7bc575a7
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938500"
---
# <a name="comparing-wcf-to-grpc"></a>WCF 'yi gRPC ile karşılaştırma

Önceki bölümde, prototipte ve gRPC 'nin iletileri nasıl işleyeceği hakkında iyi bir görünüm vermuştur. Windows Communication Foundation (WCF) ' den gRPC 'ye ayrıntılı bir dönüştürme aracılığıyla çalışmadan önce, WCF 'de kullanılabilen özelliklerin gRPC 'de nasıl işlendiğini ve gRPC eşdeğeri olmadığında hangi geçici çözümlerin kullanılabileceğini bilmeniz önemlidir. Özellikle, bu bölümde aşağıdaki konular ele alınacaktır:

- İşlemler ve Yöntemler
- Bağlamalar ve aktarımlar
- RPC türleri
- Meta Veriler
- Hata işleme
- WS- \* protokoller

## <a name="grpc-example"></a>gRPC örneği

Visual Studio 2019 ' den veya komut satırından yeni bir ASP.NET Core 5,0 gRPC projesi oluşturduğunuzda, "Merhaba Dünya" gRPC eşdeğeri sizin için oluşturulur. `greeter.proto`Hizmeti ve iletilerini tanımlayan bir dosya ve `GreeterService.cs` hizmet uygulamasını içeren bir dosya içerir.

```protobuf
syntax = "proto3";

option csharp_namespace = "HelloGrpc";

package Greet;

// The greeting service definition.
service Greeter {
  // Sends a greeting
  rpc SayHello (HelloRequest) returns (HelloReply);
}

// The request message that contains the user's name.
message HelloRequest {
  string name = 1;
}

// The response message that contains the greetings.
message HelloReply {
  string message = 1;
}
```

```csharp
using System.Threading.Tasks;
using Grpc.Core;
using Microsoft.Extensions.Logging;

namespace HelloGrpc
{
    public class GreeterService : Greeter.GreeterBase
    {
        private readonly ILogger<GreeterService> _logger;
        public GreeterService(ILogger<GreeterService> logger)
        {
            _logger = logger;
        }

        public override Task<HelloReply> SayHello(HelloRequest request, ServerCallContext context)
        {
            return Task.FromResult(new HelloReply
            {
                Message = "Hello " + request.Name
            });
        }
    }
}
```

Bu bölüm, gRPC 'nin farklı kavramlarını ve özelliklerini açıklayarak bu örnek koda başvurur.

>[!div class="step-by-step"]
>[Önceki](protobuf-maps.md) 
> [Sonraki](wcf-endpoints-grpc-methods.md)
