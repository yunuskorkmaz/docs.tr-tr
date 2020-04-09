---
title: Hata işleme - WCF Geliştiricileri için gRPC
description: gRPC'de hata işleme ile ilgili konular. En sık kullanılan durum kodlarının bir tablosunu içerir.
ms.date: 09/02/2019
ms.openlocfilehash: 64a2355a8bd608c074f9bc420312b23aba0c1fb2
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988953"
---
# <a name="error-handling"></a>Hata işleme

Windows Communication Foundation (WCF), <xref:System.ServiceModel.FaultException%601> SOAP Hatası standardını desteklemek de dahil olmak üzere ayrıntılı hata bilgileri sağlamak için Hata [Sözleşmesi](xref:System.ServiceModel.FaultContractAttribute) kullanır.

Ne yazık ki, gRPC'nin mevcut sürümü WCF ile bulunan gelişmişlik ten yoksunve yalnızca basit durum kodları ve meta verilere dayalı sınırlı yerleşik hata işleme vardır. Aşağıdaki tablo, en sık kullanılan durum kodları için hızlı bir kılavuzdur:

| Durum kodu | Sorun |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | Yöntem yazılmadı. |
| `GRPC_STATUS_UNAVAILABLE` | Tüm servisle ilgili bir sorun var. |
| `GRPC_STATUS_UNKNOWN` | Geçersiz yanıt. |
| `GRPC_STATUS_INTERNAL` | Kodlama/kod çözme sorunu. |
| `GRPC_STATUS_UNAUTHENTICATED` | Kimlik doğrulaması gerçekleştirilemedi. |
| `GRPC_STATUS_PERMISSION_DENIED` | Yetkilendirme başarısız oldu. |
| `GRPC_STATUS_CANCELLED` | Arama genellikle arayan kişi tarafından iptal edildi. |

## <a name="raise-errors-in-aspnet-core-grpc"></a>Core gRPCASP.NETdeki hataları yükseltme

Bir ASP.NET Core gRPC hizmeti, istemci `RpcException`tarafından aynı işlemde yatmış gibi yakalanabilen bir hata yanıtı gönderebilir. Durum `RpcException` kodu ve açıklama içermelidir ve isteğe bağlı olarak meta veriler ve daha uzun bir özel durum iletisi içerebilir. Meta veriler, nesnelerin WCF hataları için ek `FaultContract` verileri nasıl taşıyabildiği gibi destekleyici veriler göndermek için kullanılabilir.

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    var user = context.GetHttpContext().User;
    if (!ValidateUser(user))
    {
        var metadata = new Metadata
        {
            { "User", user.Identity.Name }
        };
        throw new RpcException(new Status(StatusCode.PermissionDenied, "Permission denied"), metadata);
    }
}
```

## <a name="catch-errors-in-grpc-clients"></a>gRPC istemcilerinde hataları yakalama

WCF istemcilerinin hataları <xref:System.ServiceModel.FaultException%601> yakalayabileceği gibi, gRPC istemcisi de hataları işlemek için bir `RpcException` hata yakalayabilir. `RpcException` Genel bir tür olmadığından, farklı bloklarda farklı hata türlerini yakalayamadığınız. Ancak, aşağıdaki örnekte gösterildiği gibi, farklı `catch` durum kodları için ayrı bloklar bildirmek için C#'ın *özel durum filtreleri* özelliğini kullanabilirsiniz:

```csharp
try
{
    var portfolio = await client.GetPortfolioAsync(new GetPortfolioRequest { Id = id });
}
catch (RpcException ex) when (ex.StatusCode == StatusCode.PermissionDenied)
{
    var userEntry = ex.Trailers.FirstOrDefault(e => e.Key == "User");
    Console.WriteLine($"User '{userEntry.Value}' does not have permission to view this portfolio.");
}
catch (RpcException)
{
    // Handle any other error type ...
}
```

> [!IMPORTANT]
> Hatalar için ek meta veriler sağladığınızda, API belgelerinizde veya dosyanızdaki açıklamalarda ilgili `.proto` anahtarları ve değerleri belgelediğinizden emin olun.

## <a name="grpc-richer-error-model"></a>gRPC daha zengin hata modeli

Google [WCF's FaultContract](xref:System.ServiceModel.FaultContractAttribute)gibi daha zengin bir [hata modeli](https://cloud.google.com/apis/design/errors#error_model) geliştirdi , ama bu model henüz C # desteklenmez. Şu anda yalnızca Go, Java, Python ve C++ için kullanılabilir.

>[!div class="step-by-step"]
>[Önceki](metadata.md)
>[Sonraki](ws-protocols.md)
