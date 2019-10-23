---
title: WCF geliştiricileri için meta veriler-gRPC
description: İstemci ve sunucular arasında ek bağlam iletmek için gRPC 'de meta veriler nasıl kullanılır
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 71ac60cd4c389277675dd452430735fb698fd342
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72770487"
---
# <a name="metadata"></a><span data-ttu-id="76ca5-103">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="76ca5-103">Metadata</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="76ca5-104">"Meta veriler", istek ve yanıtları işlerken yararlı olabilecek ancak gerçek uygulama verilerinin bir parçası olmayan ek verilere başvurur.</span><span class="sxs-lookup"><span data-stu-id="76ca5-104">"Metadata" refers to additional data that may be useful while processing requests and responses but is not part of the actual application data.</span></span> <span data-ttu-id="76ca5-105">Meta veriler, kimlik doğrulama belirteçleri, izleme amacıyla istek tanımlayıcıları ve Etiketler ya da bir veri kümesindeki kayıt sayısı gibi veriler hakkında bilgi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="76ca5-105">Metadata might include authentication tokens, request identifiers and tags for monitoring purposes, or information about the data like the number of records in a dataset.</span></span>

<span data-ttu-id="76ca5-106">@No__t_0 ve <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> özelliğini kullanarak WCF iletilerine genel anahtar/değer üstbilgileri eklemek ve bunları <xref:System.ServiceModel.Channels.MessageProperties> kullanarak işlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="76ca5-106">It's possible to add generic key/value headers to WCF messages using an <xref:System.ServiceModel.OperationContextScope> and the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> property, and handle them using <xref:System.ServiceModel.Channels.MessageProperties>.</span></span>

<span data-ttu-id="76ca5-107">gRPC çağrıları ve yanıtları, HTTP üst bilgilerine benzer meta verileri de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="76ca5-107">gRPC calls and responses can also include metadata similar to HTTP headers.</span></span> <span data-ttu-id="76ca5-108">Bunlar genellikle gRPC 'nin kendisine görünmez ve uygulama kodunuz veya ara yazılım tarafından işlenmek üzere geçirilir.</span><span class="sxs-lookup"><span data-stu-id="76ca5-108">These are mostly invisible to gRPC itself and are passed through to be processed by your application code or middleware.</span></span> <span data-ttu-id="76ca5-109">Meta veriler, anahtarın bir dize olduğu ve değerin bir dize ya da ikili veri olduğu anahtar/değer çiftleri olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="76ca5-109">Metadata is represented as key/value pairs where the key is a string and the value is either a string or binary data.</span></span> <span data-ttu-id="76ca5-110">@No__t_0 dosyasında meta veri belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="76ca5-110">You don’t need to specify metadata in the `.proto` file.</span></span>

<span data-ttu-id="76ca5-111">Meta veriler, [GRPC. Core. API](https://www.nuget.org/packages/Grpc.Core.Api/) NuGet paketindeki `Metadata` sınıfı kullanılarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="76ca5-111">Metadata is handled using the `Metadata` class from the [Grpc.Core.Api](https://www.nuget.org/packages/Grpc.Core.Api/) NuGet package.</span></span> <span data-ttu-id="76ca5-112">Bu sınıf, koleksiyon başlatıcısı sözdizimi ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="76ca5-112">This class can be used with collection initializer syntax.</span></span>

<span data-ttu-id="76ca5-113">Aşağıdaki örnek, bir istemciden bir C# çağrıya meta verilerin nasıl ekleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="76ca5-113">The following example shows how to add metadata to a call from a C# client:</span></span>

```csharp
var metadata = new Metadata
{
    { "Requester", _clientName }
};

var request = new GetPortfolioRequest
{
    Id = portfolioId
};

var response = await client.GetPortfolioAsync(request, metadata);
```

<span data-ttu-id="76ca5-114">gRPC Hizmetleri, `ServerCallContext` bağımsız değişkeninin `RequestHeaders` özelliğinden meta verilere erişebilir:</span><span class="sxs-lookup"><span data-stu-id="76ca5-114">gRPC services can access metadata from the `ServerCallContext` argument's `RequestHeaders` property:</span></span>

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    var requesterHeader = context.RequestHeaders.FirstOrDefault(e => e.Key == "Requester");
    if (requesterHeader != null)
    {
        _logger.LogInformation($"Request from {requesterHeader.Value}");
    }
    // ...
}
```

<span data-ttu-id="76ca5-115">Hizmetler, `ServerCallContext` `ResponseTrailers` özelliğini kullanarak istemcilere meta veri gönderebilir:</span><span class="sxs-lookup"><span data-stu-id="76ca5-115">Services can send metadata to clients using the `ResponseTrailers` property of `ServerCallContext`:</span></span>

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    // ...
    context.ResponseTrailers.Add("Responder", _serverName);
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="76ca5-116">[Önceki](rpc-types.md)
>[İleri](error-handling.md)</span><span class="sxs-lookup"><span data-stu-id="76ca5-116">[Previous](rpc-types.md)
[Next](error-handling.md)</span></span>
