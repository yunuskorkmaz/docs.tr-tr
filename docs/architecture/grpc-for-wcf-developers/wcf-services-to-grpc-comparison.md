---
title: WCF geliştiricileri için WCF 'yi gRPC-gRPC ile karşılaştırma
description: Dağıtılmış uygulamalar oluşturmak için WCF ve gRPC çerçeveleri karşılaştırması.
ms.date: 09/02/2019
ms.openlocfilehash: 312492dcce4bdef61feff0bf924c6df287b9c676
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966959"
---
# <a name="comparing-wcf-to-grpc"></a>WCF 'yi gRPC ile karşılaştırma

Önceki bölümde, prototipte iyi bir bakış ve gRPC 'nin iletileri işleme biçimi verilmelidir. WCF 'den gRPC 'ye yönelik ayrıntılı bir dönüştürme aracılığıyla çalışmadan önce, WCF 'de Şu anda kullanılabilir olan özellik aralığının gRPC 'de nasıl işlendiğini ve gRPC eşdeğeri olmadığı durumlarda kullanabileceğiniz geçici çözümleri öğrenmek önemlidir. Özellikle, bu bölümde aşağıdaki konular ele alınacaktır:

- İşlemler ve Yöntemler
- Bağlamalar ve aktarımlar
- RPC türleri
- Meta Veriler
- Hata işleme
- WS-\* protokolleri

## <a name="grpc-example"></a>gRPC örneği

Visual Studio 2019 ' den veya komut satırından yeni bir ASP.NET Core 3,0 gRPC projesi oluşturduğunuzda, "Merhaba Dünya" gRPC eşdeğeri sizin için oluşturulur. Hizmeti ve iletilerini tanımlayan bir `greeter.proto` dosyasından ve hizmetin uygulanmasıyla bir `GreeterService.cs` dosyası oluşur.

```protobuf
syntax = "proto3";

option csharp_namespace = "HelloGrpc";

package Greet;

// The greeting service definition.
service Greeter {
  // Sends a greeting
  rpc SayHello (HelloRequest) returns (HelloReply);
}

// The request message containing the user's name.
message HelloRequest {
  string name = 1;
}

// The response message containing the greetings.
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

Bu bölüm, gRPC 'nin çeşitli kavramlarını ve özelliklerini açıklayarak bu örnek koda başvurur.

>[!div class="step-by-step"]
>[Önceki](protobuf-maps.md)
>[İleri](wcf-endpoints-grpc-methods.md)
