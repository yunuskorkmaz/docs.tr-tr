---
title: WCF geliştiricileri için meta veriler-gRPC
description: İstemci ve sunucular arasında ek bağlam iletmek için gRPC 'de meta veriler nasıl kullanılır.
ms.date: 09/02/2019
ms.openlocfilehash: 64fa94d1e63af480cbc7363631de161c5b8b8fb8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628585"
---
# <a name="metadata"></a><span data-ttu-id="07ad9-103">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="07ad9-103">Metadata</span></span>

<span data-ttu-id="07ad9-104">*Meta veriler* , istek ve yanıtların işlenmesi sırasında yararlı olabilecek ancak gerçek uygulama verilerinin bir parçası olmayan ek verilere başvurur.</span><span class="sxs-lookup"><span data-stu-id="07ad9-104">*Metadata* refers to additional data that might be useful during the processing of requests and responses but that’s not part of the actual application data.</span></span> <span data-ttu-id="07ad9-105">Meta veriler, kimlik doğrulama belirteçleri, izleme amaçları için istek tanımlayıcıları ve Etiketler, veri kümesindeki kayıt sayısı gibi veriler hakkında bilgi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="07ad9-105">Metadata might include authentication tokens, request identifiers and tags for monitoring purposes, and information about the data, like the number of records in a dataset.</span></span>

<span data-ttu-id="07ad9-106"><xref:System.ServiceModel.OperationContextScope> ve <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> özelliğini kullanarak Windows Communication Foundation (WCF) iletilerine genel anahtar/değer üstbilgileri eklemek ve bunları <xref:System.ServiceModel.Channels.MessageProperties>kullanarak işlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="07ad9-106">It's possible to add generic key/value headers to Windows Communication Foundation (WCF) messages by using an <xref:System.ServiceModel.OperationContextScope> and the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> property and handle them by using <xref:System.ServiceModel.Channels.MessageProperties>.</span></span>

<span data-ttu-id="07ad9-107">gRPC çağrıları ve yanıtları, HTTP üst bilgilerine benzer meta verileri de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="07ad9-107">gRPC calls and responses can also include metadata that's similar to HTTP headers.</span></span> <span data-ttu-id="07ad9-108">Bu meta veriler genellikle gRPC 'nin kendisine görünmez ve uygulama kodunuz veya ara yazılım tarafından işlenmek üzere geçirilir.</span><span class="sxs-lookup"><span data-stu-id="07ad9-108">This metadata is mostly invisible to gRPC itself and is passed through to be processed by your application code or middleware.</span></span> <span data-ttu-id="07ad9-109">Meta veriler anahtar/değer çiftleri olarak temsil edilir; burada anahtar bir dizedir ve değer bir dize ya da ikili veri olur.</span><span class="sxs-lookup"><span data-stu-id="07ad9-109">Metadata is represented as key/value pairs, where the key is a string and the value is either a string or binary data.</span></span> <span data-ttu-id="07ad9-110">`.proto` dosyasında meta veri belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="07ad9-110">You don’t need to specify metadata in the `.proto` file.</span></span>

<span data-ttu-id="07ad9-111">Meta veriler, [GRPC. Core. API](https://www.nuget.org/packages/Grpc.Core.Api/) NuGet paketinin `Metadata` sınıfı tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="07ad9-111">Metadata is handled by the `Metadata` class of the [Grpc.Core.Api](https://www.nuget.org/packages/Grpc.Core.Api/) NuGet package.</span></span> <span data-ttu-id="07ad9-112">Bu sınıf, koleksiyon başlatıcısı sözdizimi ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="07ad9-112">This class can be used with collection initializer syntax.</span></span>

<span data-ttu-id="07ad9-113">Bu örnek, bir C# istemciden bir çağrıya meta verilerin nasıl ekleneceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="07ad9-113">This example shows how to add metadata to a call from a C# client:</span></span>

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

<span data-ttu-id="07ad9-114">gRPC Hizmetleri, `ServerCallContext` bağımsız değişkeninin `RequestHeaders` özelliğinden meta verilere erişebilir:</span><span class="sxs-lookup"><span data-stu-id="07ad9-114">gRPC services can access metadata from the `ServerCallContext` argument's `RequestHeaders` property:</span></span>

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

<span data-ttu-id="07ad9-115">Hizmetler, `ServerCallContext``ResponseTrailers` özelliğini kullanarak istemcilere meta veri gönderebilir:</span><span class="sxs-lookup"><span data-stu-id="07ad9-115">Services can send metadata to clients by using the `ResponseTrailers` property of `ServerCallContext`:</span></span>

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    // ...
    context.ResponseTrailers.Add("Responder", _serverName);
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="07ad9-116">[Önceki](rpc-types.md)
>[İleri](error-handling.md)</span><span class="sxs-lookup"><span data-stu-id="07ad9-116">[Previous](rpc-types.md)
[Next](error-handling.md)</span></span>
