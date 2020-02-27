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
# <a name="metadata"></a>Meta Veriler

*Meta veriler* , istek ve yanıtların işlenmesi sırasında yararlı olabilecek ancak gerçek uygulama verilerinin bir parçası olmayan ek verilere başvurur. Meta veriler, kimlik doğrulama belirteçleri, izleme amaçları için istek tanımlayıcıları ve Etiketler, veri kümesindeki kayıt sayısı gibi veriler hakkında bilgi içerebilir.

<xref:System.ServiceModel.OperationContextScope> ve <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> özelliğini kullanarak Windows Communication Foundation (WCF) iletilerine genel anahtar/değer üstbilgileri eklemek ve bunları <xref:System.ServiceModel.Channels.MessageProperties>kullanarak işlemek mümkündür.

gRPC çağrıları ve yanıtları, HTTP üst bilgilerine benzer meta verileri de içerebilir. Bu meta veriler genellikle gRPC 'nin kendisine görünmez ve uygulama kodunuz veya ara yazılım tarafından işlenmek üzere geçirilir. Meta veriler anahtar/değer çiftleri olarak temsil edilir; burada anahtar bir dizedir ve değer bir dize ya da ikili veri olur. `.proto` dosyasında meta veri belirtmeniz gerekmez.

Meta veriler, [GRPC. Core. API](https://www.nuget.org/packages/Grpc.Core.Api/) NuGet paketinin `Metadata` sınıfı tarafından işlenir. Bu sınıf, koleksiyon başlatıcısı sözdizimi ile kullanılabilir.

Bu örnek, bir C# istemciden bir çağrıya meta verilerin nasıl ekleneceğini gösterir:

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
