---
title: WCF geliştiricileri için gRPC hata işleme
description: YAZıLACAK
ms.date: 09/02/2019
ms.openlocfilehash: 2c44bd9264c877a7c7a86c115b6da9f759006016
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967787"
---
# <a name="error-handling"></a>Hata işleme

WCF, SOAP hata standardını destekleme dahil, ayrıntılı hata bilgileri sağlamak için `FaultException<T>` ve `FaultContract` kullanır.

Ne yazık ki, gRPC 'nin geçerli sürümünde WCF 'de bulunan gelişmiş algoritmaların mümkündür yok ve yalnızca basit durum kodlarına ve meta verilere göre sınırlı yerleşik hata işleme sahip. Aşağıdaki tabloda, en sık kullanılan durum kodlarına yönelik hızlı bir kılavuz verilmiştir:

| Durum Kodu | Sorun |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | Yöntem yazılmadı. |
| `GRPC_STATUS_UNAVAILABLE` | Tüm hizmette sorun. |
| `GRPC_STATUS_UNKNOWN` | Geçersiz yanıt. |
| `GRPC_STATUS_INTERNAL` | Kodlama/kod çözme sorunu. |
| `GRPC_STATUS_UNAUTHENTICATED` | Kimlik doğrulama başarısız oldu. |
| `GRPC_STATUS_PERMISSION_DENIED` | Yetkilendirme başarısız oldu. |
| `GRPC_STATUS_CANCELLED` | Çağrı, genellikle çağıran tarafından iptal edildi. |

## <a name="raising-errors-in-aspnet-core-grpc"></a>ASP.NET Core gRPC 'de hataları oluşturma

ASP.NET Core gRPC hizmeti, aynı işlem içinde olduğu gibi istemci tarafından yakalanarak bir `RpcException`oluşturarak hata yanıtı gönderebilir. `RpcException` bir durum kodu ve açıklaması içermeli ve isteğe bağlı olarak meta verileri ve daha uzun bir özel durum iletisi içerebilir. Meta veriler, `FaultContract` nesnelerinin WCF hataları için ek verileri nasıl taşıyabiliriz benzer şekilde destekleyici verileri göndermek için kullanılabilir.

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

## <a name="catching-errors-in-grpc-clients"></a>GRPC istemcilerinde yakalama hataları

WCF istemcilerinin <xref:System.ServiceModel.FaultException%601> hataları yakalayabileceğini tıpkı, bir gRPC istemcisi hataları işlemek için bir `RpcException` yakalayabilir. `RpcException` genel bir tür olmadığından farklı bloklerdeki farklı hata türlerini yakalayamaz, ancak aşağıdaki örnekte gösterildiği gibi farklı durum C#kodları için ayrı `catch` blokları bildirmek üzere *özel durum filtreleri* özelliğini kullanabilirsiniz:

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

Bu konuda, Google, WCF 'nin [FaultContract](xref:System.ServiceModel.FaultContractAttribute)gibi daha [zengin bir hata modeli](https://cloud.google.com/apis/design/errors#error_model) geliştirmiştir, ancak C# henüz desteklenmiyor. Şu anda yalnızca Go, Java, Python ve C++için kullanılabilir, ancak için C# destek için bir sonraki yıl gelmesi beklenmektedir.

>[!div class="step-by-step"]
>[Önceki](metadata.md)
>[İleri](ws-protocols.md)
