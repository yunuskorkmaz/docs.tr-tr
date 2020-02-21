---
title: WCF geliştiricileri için gRPC hata işleme
description: GRPC 'de hata işlemeyle ilgili konular. En yaygın olarak kullanılan durum kodlarının tablosunu içerir.
ms.date: 09/02/2019
ms.openlocfilehash: c380c651f854adc97e8b2ead36d30c3b83662aac
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542799"
---
# <a name="error-handling"></a>Hata işleme

Windows Communication Foundation (WCF), SOAP hata standardını destekleme dahil, ayrıntılı hata bilgileri sağlamak için <xref:System.ServiceModel.FaultException%601> ve [FaultContract](xref:System.ServiceModel.FaultContractAttribute) kullanır.

Ne yazık ki, gRPC 'nin geçerli sürümü WCF ile gelişmiş algoritmaların mümkündür bulunamadı ve yalnızca basit durum kodlarına ve meta verilere göre sınırlı yerleşik hata işleme sahip. Aşağıdaki tabloda, en sık kullanılan durum kodlarına yönelik hızlı bir kılavuz verilmiştir:

| Durum kodu | Sorun |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | Yöntem yazılmadı. |
| `GRPC_STATUS_UNAVAILABLE` | Tüm hizmette sorun. |
| `GRPC_STATUS_UNKNOWN` | Geçersiz yanıt. |
| `GRPC_STATUS_INTERNAL` | Kodlama/kod çözme sorunu. |
| `GRPC_STATUS_UNAUTHENTICATED` | Kimlik doğrulama başarısız oldu. |
| `GRPC_STATUS_PERMISSION_DENIED` | Yetkilendirme başarısız oldu. |
| `GRPC_STATUS_CANCELLED` | Çağrı, genellikle çağıran tarafından iptal edildi. |

## <a name="raise-errors-in-aspnet-core-grpc"></a>ASP.NET Core gRPC 'de hata oluştur

ASP.NET Core gRPC hizmeti, aynı işlem içinde olduğu gibi istemci tarafından yakalanarak bir `RpcException`oluşturarak hata yanıtı gönderebilir. `RpcException` bir durum kodu ve açıklaması içermeli ve isteğe bağlı olarak meta verileri ve daha uzun bir özel durum iletisi içerebilir. Meta veriler, `FaultContract` nesnelerinin WCF hataları için ek verileri nasıl taşıyabilirim benzer şekilde destekleyici verileri göndermek için kullanılabilir.

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

## <a name="catch-errors-in-grpc-clients"></a>GRPC istemcilerinde hataları yakala

WCF istemcilerinin <xref:System.ServiceModel.FaultException%601> hataları yakalayabileceğini tıpkı, bir gRPC istemcisi hataları işlemek için bir `RpcException` yakalayabilir. `RpcException` genel bir tür olmadığından farklı bloklara farklı hata türlerini yakalayamazsınız. Ancak, aşağıdaki örnekte C#gösterildiği gibi farklı durum kodları için ayrı `catch` blokları bildirmek üzere *özel durum filtreleri* özelliğini kullanabilirsiniz:

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
> Hatalar için ek meta veriler sağladığınızda, API belgelerinize veya `.proto` dosyanızdaki açıklamalarda ilgili anahtar ve değerleri belgelediğinizden emin olun.

## <a name="grpc-richer-error-model"></a>gRPC daha zengin hata modeli

Google, WCF 'nin [FaultContract](xref:System.ServiceModel.FaultContractAttribute)gibi daha [zengin bir hata modeli](https://cloud.google.com/apis/design/errors#error_model) geliştirmiştir, ancak bu model henüz içinde C# desteklenmiyor. Şu anda yalnızca Go, Java, Python ve ile C++kullanılabilir.

>[!div class="step-by-step"]
>[Önceki](metadata.md)
>[İleri](ws-protocols.md)
