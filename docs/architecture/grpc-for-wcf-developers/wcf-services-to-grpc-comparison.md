---
title: WCF geliştiricileri için WCF 'yi gRPC-gRPC ile karşılaştırma
description: Dağıtılmış uygulamalar oluşturmak için WCF ve gRPC çerçeveleri karşılaştırması.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 5ab1380d4ded52abff08c35c430adf2f3ed7c58b
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846065"
---
# <a name="comparing-wcf-to-grpc"></a><span data-ttu-id="e545c-103">WCF 'yi gRPC ile karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="e545c-103">Comparing WCF to gRPC</span></span>

<span data-ttu-id="e545c-104">Önceki bölümde, prototipte iyi bir bakış ve gRPC 'nin iletileri işleme biçimi verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e545c-104">The previous chapter should have given you a good look at Protobuf and how gRPC handles messages.</span></span> <span data-ttu-id="e545c-105">WCF 'den gRPC 'ye yönelik ayrıntılı bir dönüştürme aracılığıyla çalışmadan önce, WCF 'de Şu anda kullanılabilir olan özellik aralığının gRPC 'de nasıl işlendiğini ve gRPC eşdeğeri olmadığı durumlarda kullanabileceğiniz geçici çözümleri öğrenmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e545c-105">Before working through a detailed conversion from WCF to gRPC, it's important to look at how the range of features currently available in WCF are handled in gRPC and what workarounds you can use when there doesn't appear to be a gRPC equivalent.</span></span> <span data-ttu-id="e545c-106">Özellikle, bu bölümde aşağıdaki konular ele alınacaktır:</span><span class="sxs-lookup"><span data-stu-id="e545c-106">In particular, this chapter will cover the following subjects:</span></span>

- <span data-ttu-id="e545c-107">İşlemler ve Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e545c-107">Operations and methods</span></span>
- <span data-ttu-id="e545c-108">Bağlamalar ve aktarımlar</span><span class="sxs-lookup"><span data-stu-id="e545c-108">Bindings and transports</span></span>
- <span data-ttu-id="e545c-109">RPC türleri</span><span class="sxs-lookup"><span data-stu-id="e545c-109">RPC types</span></span>
- <span data-ttu-id="e545c-110">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="e545c-110">Metadata</span></span>
- <span data-ttu-id="e545c-111">Hata işleme</span><span class="sxs-lookup"><span data-stu-id="e545c-111">Error handling</span></span>
- <span data-ttu-id="e545c-112">WS-\* protokolleri</span><span class="sxs-lookup"><span data-stu-id="e545c-112">WS-\* protocols</span></span>

## <a name="grpc-example"></a><span data-ttu-id="e545c-113">gRPC örneği</span><span class="sxs-lookup"><span data-stu-id="e545c-113">gRPC example</span></span>

<span data-ttu-id="e545c-114">Visual Studio 2019 ' den veya komut satırından yeni bir ASP.NET Core 3,0 gRPC projesi oluşturduğunuzda, "Merhaba Dünya" gRPC eşdeğeri sizin için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e545c-114">When you create a new ASP.NET Core 3.0 gRPC project from Visual Studio 2019 or the command line, the gRPC equivalent of "Hello World" is generated for you.</span></span> <span data-ttu-id="e545c-115">Hizmeti ve iletilerini tanımlayan bir `greeter.proto` dosyasından ve hizmetin uygulanmasıyla bir `GreeterService.cs` dosyası oluşur.</span><span class="sxs-lookup"><span data-stu-id="e545c-115">It consists of a `greeter.proto` file that defines the service and its messages, and a `GreeterService.cs` file with an implementation of the service.</span></span>

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

<span data-ttu-id="e545c-116">Bu bölüm, gRPC 'nin çeşitli kavramlarını ve özelliklerini açıklayarak bu örnek koda başvurur.</span><span class="sxs-lookup"><span data-stu-id="e545c-116">This chapter will refer to this example code when explaining various concepts and features of gRPC.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e545c-117">[Önceki](protobuf-maps.md)
>[İleri](wcf-endpoints-grpc-methods.md)</span><span class="sxs-lookup"><span data-stu-id="e545c-117">[Previous](protobuf-maps.md)
[Next](wcf-endpoints-grpc-methods.md)</span></span>
