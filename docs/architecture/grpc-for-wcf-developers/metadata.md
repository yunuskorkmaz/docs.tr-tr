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
# <a name="metadata"></a>Meta Veriler

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

"Meta veriler", istek ve yanıtları işlerken yararlı olabilecek ancak gerçek uygulama verilerinin bir parçası olmayan ek verilere başvurur. Meta veriler, kimlik doğrulama belirteçleri, izleme amacıyla istek tanımlayıcıları ve Etiketler ya da bir veri kümesindeki kayıt sayısı gibi veriler hakkında bilgi içerebilir.

Bir <xref:System.ServiceModel.OperationContextScope> <xref:System.ServiceModel.Channels.MessageProperties>ve özelliğini kullanarak WCF iletilerine genel anahtar/değer üst bilgileri eklemek ve bunları kullanarak işlemek mümkündür. <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType>

gRPC çağrıları ve yanıtları, HTTP üst bilgilerine benzer meta verileri de içerebilir. Bunlar genellikle gRPC 'nin kendisine görünmez ve uygulama kodunuz veya ara yazılım tarafından işlenmek üzere geçirilir. Meta veriler, anahtarın bir dize olduğu ve değerin bir dize ya da ikili veri olduğu anahtar/değer çiftleri olarak temsil edilir. `.proto` Dosyasında meta veri belirtmeniz gerekmez.

Meta veriler, `Metadata` [GRPC. Core](https://www.nuget.org/packages/Grpc.Core/) NuGet paketindeki sınıfı kullanılarak işlenir. Bu sınıf, koleksiyon başlatıcısı sözdizimi ile kullanılabilir.

Aşağıdaki örnek, bir istemciden bir C# çağrıya meta verilerin nasıl ekleneceğini göstermektedir:

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

GRPC Hizmetleri `ServerCallContext` `RequestHeaders` bağımsız değişkenin özelliğinden meta verilere erişebilir:

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

Hizmetler, `ResponseTrailers` şu `ServerCallContext`özelliği kullanılarak istemcilere meta veri gönderebilir:

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    // ...
    context.ResponseTrailers.Add("Responder", _serverName);
    // ...
}
```

>[!div class="step-by-step"]
>[Önceki](rpc-types.md)
>[İleri](error-handling.md)
