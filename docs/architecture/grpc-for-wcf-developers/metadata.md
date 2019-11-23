---
title: WCF geliştiricileri için meta veriler-gRPC
description: İstemci ve sunucular arasında ek bağlam iletmek için gRPC 'de meta veriler nasıl kullanılır
ms.date: 09/02/2019
ms.openlocfilehash: 723d877bfbf0c2b0785949ff15939aedbac4d4e9
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971984"
---
# <a name="metadata"></a>Meta Veriler

"Meta veriler", istek ve yanıtları işlerken yararlı olabilecek ancak gerçek uygulama verilerinin bir parçası olmayan ek verilere başvurur. Meta veriler, kimlik doğrulama belirteçleri, izleme amacıyla istek tanımlayıcıları ve Etiketler ya da bir veri kümesindeki kayıt sayısı gibi veriler hakkında bilgi içerebilir.

<xref:System.ServiceModel.OperationContextScope> ve <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> özelliğini kullanarak WCF iletilerine genel anahtar/değer üstbilgileri eklemek ve bunları <xref:System.ServiceModel.Channels.MessageProperties>kullanarak işlemek mümkündür.

gRPC çağrıları ve yanıtları, HTTP üst bilgilerine benzer meta verileri de içerebilir. Bunlar genellikle gRPC 'nin kendisine görünmez ve uygulama kodunuz veya ara yazılım tarafından işlenmek üzere geçirilir. Meta veriler, anahtarın bir dize olduğu ve değerin bir dize ya da ikili veri olduğu anahtar/değer çiftleri olarak temsil edilir. `.proto` dosyasında meta veri belirtmeniz gerekmez.

Meta veriler, [GRPC. Core. API](https://www.nuget.org/packages/Grpc.Core.Api/) NuGet paketindeki `Metadata` sınıfı kullanılarak işlenir. Bu sınıf, koleksiyon başlatıcısı sözdizimi ile kullanılabilir.

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

gRPC Hizmetleri, `ServerCallContext` bağımsız değişkeninin `RequestHeaders` özelliğinden meta verilere erişebilir:

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

Hizmetler, `ServerCallContext``ResponseTrailers` özelliğini kullanarak istemcilere meta veri gönderebilir:

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
