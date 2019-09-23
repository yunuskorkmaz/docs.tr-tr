---
title: WCF geliştiricileri için WCF 'yi gRPC-gRPC ile karşılaştırma
description: Dağıtılmış uygulamalar oluşturmak için WCF ve gRPC çerçeveleri karşılaştırması.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: c763048d09e7ed5ca0a3d5240f6b3cf5262f897c
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184045"
---
# <a name="comparing-wcf-to-grpc"></a>WCF 'yi gRPC ile karşılaştırma

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Önceki bölümde, prototipte iyi bir bakış ve gRPC 'nin iletileri işleme biçimi verilmelidir. WCF 'den gRPC 'ye yönelik ayrıntılı bir dönüştürme aracılığıyla çalışmadan önce, WCF 'de Şu anda kullanılabilir olan özellik aralığının gRPC 'de nasıl işlendiğini ve gRPC eşdeğeri olmadığı durumlarda kullanabileceğiniz geçici çözümleri öğrenmek önemlidir. Özellikle, bu bölümde aşağıdaki konular ele alınacaktır:

- İşlemler ve Yöntemler
- Bağlamalar ve aktarımlar
- RPC türleri
- Meta Veriler
- Hata işleme
- WS-\* protokoller

## <a name="grpc-example"></a>gRPC örneği

Visual Studio 2019 ' den veya komut satırından yeni bir ASP.NET Core 3,0 gRPC projesi oluşturduğunuzda, "Merhaba Dünya" gRPC eşdeğeri sizin için oluşturulur. Hizmeti ve iletilerini tanımlayan `greeter.proto` bir dosya ve hizmet uygulamasını içeren bir `GreeterService.cs` dosya içerir.

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
