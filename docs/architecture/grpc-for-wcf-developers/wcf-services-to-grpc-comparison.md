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
# <a name="comparing-wcf-to-grpc"></a><span data-ttu-id="088d4-103">WCF 'yi gRPC ile karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="088d4-103">Comparing WCF to gRPC</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="088d4-104">Önceki bölümde, prototipte iyi bir bakış ve gRPC 'nin iletileri işleme biçimi verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="088d4-104">The previous chapter should have given you a good look at Protobuf and how gRPC handles messages.</span></span> <span data-ttu-id="088d4-105">WCF 'den gRPC 'ye yönelik ayrıntılı bir dönüştürme aracılığıyla çalışmadan önce, WCF 'de Şu anda kullanılabilir olan özellik aralığının gRPC 'de nasıl işlendiğini ve gRPC eşdeğeri olmadığı durumlarda kullanabileceğiniz geçici çözümleri öğrenmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="088d4-105">Before working through a detailed conversion from WCF to gRPC, it's important to look at how the range of features currently available in WCF are handled in gRPC and what workarounds you can use when there doesn't appear to be a gRPC equivalent.</span></span> <span data-ttu-id="088d4-106">Özellikle, bu bölümde aşağıdaki konular ele alınacaktır:</span><span class="sxs-lookup"><span data-stu-id="088d4-106">In particular, this chapter will cover the following subjects:</span></span>

- <span data-ttu-id="088d4-107">İşlemler ve Yöntemler</span><span class="sxs-lookup"><span data-stu-id="088d4-107">Operations and methods</span></span>
- <span data-ttu-id="088d4-108">Bağlamalar ve aktarımlar</span><span class="sxs-lookup"><span data-stu-id="088d4-108">Bindings and transports</span></span>
- <span data-ttu-id="088d4-109">RPC türleri</span><span class="sxs-lookup"><span data-stu-id="088d4-109">RPC types</span></span>
- <span data-ttu-id="088d4-110">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="088d4-110">Metadata</span></span>
- <span data-ttu-id="088d4-111">Hata işleme</span><span class="sxs-lookup"><span data-stu-id="088d4-111">Error handling</span></span>
- <span data-ttu-id="088d4-112">WS-\* protokoller</span><span class="sxs-lookup"><span data-stu-id="088d4-112">WS-\* protocols</span></span>

## <a name="grpc-example"></a><span data-ttu-id="088d4-113">gRPC örneği</span><span class="sxs-lookup"><span data-stu-id="088d4-113">gRPC example</span></span>

<span data-ttu-id="088d4-114">Visual Studio 2019 ' den veya komut satırından yeni bir ASP.NET Core 3,0 gRPC projesi oluşturduğunuzda, "Merhaba Dünya" gRPC eşdeğeri sizin için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="088d4-114">When you create a new ASP.NET Core 3.0 gRPC project from Visual Studio 2019 or the command line, the gRPC equivalent of "Hello World" is generated for you.</span></span> <span data-ttu-id="088d4-115">Hizmeti ve iletilerini tanımlayan `greeter.proto` bir dosya ve hizmet uygulamasını içeren bir `GreeterService.cs` dosya içerir.</span><span class="sxs-lookup"><span data-stu-id="088d4-115">It consists of a `greeter.proto` file that defines the service and its messages, and a `GreeterService.cs` file with an implementation of the service.</span></span>

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

<span data-ttu-id="088d4-116">Bu bölüm, gRPC 'nin çeşitli kavramlarını ve özelliklerini açıklayarak bu örnek koda başvurur.</span><span class="sxs-lookup"><span data-stu-id="088d4-116">This chapter will refer to this example code when explaining various concepts and features of gRPC.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="088d4-117">[Önceki](protobuf-maps.md)
>[İleri](wcf-endpoints-grpc-methods.md)</span><span class="sxs-lookup"><span data-stu-id="088d4-117">[Previous](protobuf-maps.md)
[Next](wcf-endpoints-grpc-methods.md)</span></span>
