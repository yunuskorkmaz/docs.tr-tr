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
# <a name="comparing-wcf-to-grpc"></a><span data-ttu-id="71d87-103">WCF 'yi gRPC ile karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="71d87-103">Comparing WCF to gRPC</span></span>

<span data-ttu-id="71d87-104">Önceki bölümde, prototipte ve gRPC 'nin iletileri nasıl işleyeceği hakkında iyi bir görünüm vermuştur.</span><span class="sxs-lookup"><span data-stu-id="71d87-104">The previous chapter gave you a good look at Protobuf and how gRPC handles messages.</span></span> <span data-ttu-id="71d87-105">Windows Communication Foundation (WCF) ' den gRPC 'ye ayrıntılı bir dönüştürme aracılığıyla çalışmadan önce, WCF 'de kullanılabilen özelliklerin gRPC 'de nasıl işlendiğini ve gRPC eşdeğeri olmadığında hangi geçici çözümlerin kullanılabileceğini bilmeniz önemlidir.</span><span class="sxs-lookup"><span data-stu-id="71d87-105">Before you work through a detailed conversion from Windows Communication Foundation (WCF) to gRPC, it's important know how the features available in WCF are handled in gRPC and what workarounds you can use when there's no gRPC equivalent.</span></span> <span data-ttu-id="71d87-106">Özellikle, bu bölümde aşağıdaki konular ele alınacaktır:</span><span class="sxs-lookup"><span data-stu-id="71d87-106">In particular, this chapter will cover the following subjects:</span></span>

- <span data-ttu-id="71d87-107">İşlemler ve Yöntemler</span><span class="sxs-lookup"><span data-stu-id="71d87-107">Operations and methods</span></span>
- <span data-ttu-id="71d87-108">Bağlamalar ve aktarımlar</span><span class="sxs-lookup"><span data-stu-id="71d87-108">Bindings and transports</span></span>
- <span data-ttu-id="71d87-109">RPC türleri</span><span class="sxs-lookup"><span data-stu-id="71d87-109">RPC types</span></span>
- <span data-ttu-id="71d87-110">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="71d87-110">Metadata</span></span>
- <span data-ttu-id="71d87-111">Hata işleme</span><span class="sxs-lookup"><span data-stu-id="71d87-111">Error handling</span></span>
- <span data-ttu-id="71d87-112">WS- \* protokoller</span><span class="sxs-lookup"><span data-stu-id="71d87-112">WS-\* protocols</span></span>

## <a name="grpc-example"></a><span data-ttu-id="71d87-113">gRPC örneği</span><span class="sxs-lookup"><span data-stu-id="71d87-113">gRPC example</span></span>

<span data-ttu-id="71d87-114">Visual Studio 2019 ' den veya komut satırından yeni bir ASP.NET Core 5,0 gRPC projesi oluşturduğunuzda, "Merhaba Dünya" gRPC eşdeğeri sizin için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="71d87-114">When you create a new ASP.NET Core 5.0 gRPC project from Visual Studio 2019 or the command line, the gRPC equivalent of "Hello World" is generated for you.</span></span> <span data-ttu-id="71d87-115">`greeter.proto`Hizmeti ve iletilerini tanımlayan bir dosya ve `GreeterService.cs` hizmet uygulamasını içeren bir dosya içerir.</span><span class="sxs-lookup"><span data-stu-id="71d87-115">It consists of a `greeter.proto` file that defines the service and its messages, and a `GreeterService.cs` file with an implementation of the service.</span></span>

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

<span data-ttu-id="71d87-116">Bu bölüm, gRPC 'nin farklı kavramlarını ve özelliklerini açıklayarak bu örnek koda başvurur.</span><span class="sxs-lookup"><span data-stu-id="71d87-116">This chapter will refer to this example code when explaining different concepts and features of gRPC.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="71d87-117">[Önceki](protobuf-maps.md) 
> [Sonraki](wcf-endpoints-grpc-methods.md)</span><span class="sxs-lookup"><span data-stu-id="71d87-117">[Previous](protobuf-maps.md)
[Next](wcf-endpoints-grpc-methods.md)</span></span>
