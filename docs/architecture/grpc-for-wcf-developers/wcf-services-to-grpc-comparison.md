---
title: WCF geliştiricileri için WCF 'yi gRPC-gRPC ile karşılaştırma
description: Dağıtılmış uygulamalar oluşturmak için WCF ve gRPC çerçeveleri karşılaştırması.
ms.date: 09/02/2019
ms.openlocfilehash: 4f54db76c9512b770b4dd993496d95437dd89753
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503331"
---
# <a name="comparing-wcf-to-grpc"></a><span data-ttu-id="84771-103">WCF 'yi gRPC ile karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="84771-103">Comparing WCF to gRPC</span></span>

<span data-ttu-id="84771-104">Önceki bölümde, prototipte ve gRPC 'nin iletileri nasıl işleyeceği hakkında iyi bir görünüm vermuştur.</span><span class="sxs-lookup"><span data-stu-id="84771-104">The previous chapter gave you a good look at Protobuf and how gRPC handles messages.</span></span> <span data-ttu-id="84771-105">Windows Communication Foundation (WCF) ' den gRPC 'ye ayrıntılı bir dönüştürme aracılığıyla çalışmadan önce, WCF 'de kullanılabilen özelliklerin gRPC 'de nasıl işlendiğini ve gRPC eşdeğeri olmadığında hangi geçici çözümlerin kullanılabileceğini bilmeniz önemlidir.</span><span class="sxs-lookup"><span data-stu-id="84771-105">Before you work through a detailed conversion from Windows Communication Foundation (WCF) to gRPC, it's important know how the features available in WCF are handled in gRPC and what workarounds you can use when there's no gRPC equivalent.</span></span> <span data-ttu-id="84771-106">Özellikle, bu bölümde aşağıdaki konular ele alınacaktır:</span><span class="sxs-lookup"><span data-stu-id="84771-106">In particular, this chapter will cover the following subjects:</span></span>

- <span data-ttu-id="84771-107">İşlemler ve Yöntemler</span><span class="sxs-lookup"><span data-stu-id="84771-107">Operations and methods</span></span>
- <span data-ttu-id="84771-108">Bağlamalar ve aktarımlar</span><span class="sxs-lookup"><span data-stu-id="84771-108">Bindings and transports</span></span>
- <span data-ttu-id="84771-109">RPC türleri</span><span class="sxs-lookup"><span data-stu-id="84771-109">RPC types</span></span>
- <span data-ttu-id="84771-110">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="84771-110">Metadata</span></span>
- <span data-ttu-id="84771-111">Hata işleme</span><span class="sxs-lookup"><span data-stu-id="84771-111">Error handling</span></span>
- <span data-ttu-id="84771-112">WS-\* protokolleri</span><span class="sxs-lookup"><span data-stu-id="84771-112">WS-\* protocols</span></span>

## <a name="grpc-example"></a><span data-ttu-id="84771-113">gRPC örneği</span><span class="sxs-lookup"><span data-stu-id="84771-113">gRPC example</span></span>

<span data-ttu-id="84771-114">Visual Studio 2019 ' den veya komut satırından yeni bir ASP.NET Core 3,0 gRPC projesi oluşturduğunuzda, "Merhaba Dünya" gRPC eşdeğeri sizin için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="84771-114">When you create a new ASP.NET Core 3.0 gRPC project from Visual Studio 2019 or the command line, the gRPC equivalent of "Hello World" is generated for you.</span></span> <span data-ttu-id="84771-115">Hizmeti ve iletilerini tanımlayan bir `greeter.proto` dosyasından ve hizmetin uygulanmasıyla bir `GreeterService.cs` dosyası oluşur.</span><span class="sxs-lookup"><span data-stu-id="84771-115">It consists of a `greeter.proto` file that defines the service and its messages, and a `GreeterService.cs` file with an implementation of the service.</span></span>

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

<span data-ttu-id="84771-116">Bu bölüm, gRPC 'nin farklı kavramlarını ve özelliklerini açıklayarak bu örnek koda başvurur.</span><span class="sxs-lookup"><span data-stu-id="84771-116">This chapter will refer to this example code when explaining different concepts and features of gRPC.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="84771-117">[Önceki](protobuf-maps.md)
>[İleri](wcf-endpoints-grpc-methods.md)</span><span class="sxs-lookup"><span data-stu-id="84771-117">[Previous](protobuf-maps.md)
[Next](wcf-endpoints-grpc-methods.md)</span></span>
