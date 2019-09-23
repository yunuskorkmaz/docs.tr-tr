---
title: WCF geliştiricileri için meta veriler-gRPC
description: İstemci ve sunucular arasında ek bağlam iletmek için gRPC 'de meta veriler nasıl kullanılır
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 1a2131fa3ee3112eaa3c3e7f7c97017fea6b1004
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184332"
---
# <a name="metadata"></a><span data-ttu-id="fcc21-103">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="fcc21-103">Metadata</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="fcc21-104">"Meta veriler", istek ve yanıtları işlerken yararlı olabilecek ancak gerçek uygulama verilerinin bir parçası olmayan ek verilere başvurur.</span><span class="sxs-lookup"><span data-stu-id="fcc21-104">"Metadata" refers to additional data that may be useful while processing requests and responses but is not part of the actual application data.</span></span> <span data-ttu-id="fcc21-105">Meta veriler, kimlik doğrulama belirteçleri, izleme amacıyla istek tanımlayıcıları ve Etiketler ya da bir veri kümesindeki kayıt sayısı gibi veriler hakkında bilgi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fcc21-105">Metadata might include authentication tokens, request identifiers and tags for monitoring purposes, or information about the data like the number of records in a dataset.</span></span>

<span data-ttu-id="fcc21-106">Bir <xref:System.ServiceModel.OperationContextScope> <xref:System.ServiceModel.Channels.MessageProperties>ve özelliğini kullanarak WCF iletilerine genel anahtar/değer üst bilgileri eklemek ve bunları kullanarak işlemek mümkündür. <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="fcc21-106">It's possible to add generic key/value headers to WCF messages using an <xref:System.ServiceModel.OperationContextScope> and the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> property, and handle them using <xref:System.ServiceModel.Channels.MessageProperties>.</span></span>

<span data-ttu-id="fcc21-107">gRPC çağrıları ve yanıtları, HTTP üst bilgilerine benzer meta verileri de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fcc21-107">gRPC calls and responses can also include metadata similar to HTTP headers.</span></span> <span data-ttu-id="fcc21-108">Bunlar genellikle gRPC 'nin kendisine görünmez ve uygulama kodunuz veya ara yazılım tarafından işlenmek üzere geçirilir.</span><span class="sxs-lookup"><span data-stu-id="fcc21-108">These are mostly invisible to gRPC itself and are passed through to be processed by your application code or middleware.</span></span> <span data-ttu-id="fcc21-109">Meta veriler, anahtarın bir dize olduğu ve değerin bir dize ya da ikili veri olduğu anahtar/değer çiftleri olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="fcc21-109">Metadata is represented as key/value pairs where the key is a string and the value is either a string or binary data.</span></span> <span data-ttu-id="fcc21-110">`.proto` Dosyasında meta veri belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="fcc21-110">You don’t need to specify metadata in the `.proto` file.</span></span>

<span data-ttu-id="fcc21-111">Meta veriler, `Metadata` [GRPC. Core](https://www.nuget.org/packages/Grpc.Core/) NuGet paketindeki sınıfı kullanılarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="fcc21-111">Metadata is handled using the `Metadata` class from the [Grpc.Core](https://www.nuget.org/packages/Grpc.Core/) NuGet package.</span></span> <span data-ttu-id="fcc21-112">Bu sınıf, koleksiyon başlatıcısı sözdizimi ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fcc21-112">This class can be used with collection initializer syntax.</span></span>

<span data-ttu-id="fcc21-113">Aşağıdaki örnek, bir istemciden bir C# çağrıya meta verilerin nasıl ekleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="fcc21-113">The following example shows how to add metadata to a call from a C# client:</span></span>

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

<span data-ttu-id="fcc21-114">GRPC Hizmetleri `ServerCallContext` `RequestHeaders` bağımsız değişkenin özelliğinden meta verilere erişebilir:</span><span class="sxs-lookup"><span data-stu-id="fcc21-114">gRPC services can access metadata from the `ServerCallContext` argument's `RequestHeaders` property:</span></span>

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

<span data-ttu-id="fcc21-115">Hizmetler, `ResponseTrailers` şu `ServerCallContext`özelliği kullanılarak istemcilere meta veri gönderebilir:</span><span class="sxs-lookup"><span data-stu-id="fcc21-115">Services can send metadata to clients using the `ResponseTrailers` property of `ServerCallContext`:</span></span>

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    // ...
    context.ResponseTrailers.Add("Responder", _serverName);
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="fcc21-116">[Önceki](rpc-types.md)
>[İleri](error-handling.md)</span><span class="sxs-lookup"><span data-stu-id="fcc21-116">[Previous](rpc-types.md)
[Next](error-handling.md)</span></span>
