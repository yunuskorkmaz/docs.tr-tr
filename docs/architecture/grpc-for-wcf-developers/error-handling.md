---
title: WCF geliştiricileri için gRPC hata işleme
description: YAZILACAK
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 3535a00aad49f532eb5f5f778116454a12bfd639
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184458"
---
# <a name="error-handling"></a>Hata işleme

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

WCF, `FaultException<T>` SOAP `FaultContract` hata standardını destekleme dahil, ayrıntılı hata bilgileri sağlamak için ve kullanır.

Ne yazık ki, gRPC 'nin geçerli sürümünde WCF 'de bulunan gelişmiş algoritmaların mümkündür yok ve yalnızca basit durum kodlarına ve meta verilere göre sınırlı yerleşik hata işleme sahip. Aşağıdaki tabloda, en sık kullanılan durum kodlarına yönelik hızlı bir kılavuz verilmiştir:

| Durum kodu | Gidermek |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | Yöntem yazılmadı. |
| `GRPC_STATUS_UNAVAILABLE` | Tüm hizmette sorun. |
| `GRPC_STATUS_UNKNOWN` | Geçersiz yanıt. |
| `GRPC_STATUS_INTERNAL` | Kodlama/kod çözme sorunu. |
| `GRPC_STATUS_UNAUTHENTICATED` | Kimlik doğrulama başarısız oldu. |
| `GRPC_STATUS_PERMISSION_DENIED` | Yetkilendirme başarısız oldu. |
| `GRPC_STATUS_CANCELLED` | Çağrı, genellikle çağıran tarafından iptal edildi. |

## <a name="raising-errors-in-aspnet-core-grpc"></a>ASP.NET Core gRPC 'de hataları oluşturma

ASP.NET Core GRPC hizmeti, istemci tarafından aynı işlemle yapılmış gibi yakalanarak `RpcException`bir hata yanıtı gönderebilir. Bir durum kodu ve açıklaması içermesi ve isteğe bağlı olarak meta verileri ve daha uzun bir özel durum iletisi içermesi gerekir.`RpcException` Meta veriler, nesnelerin WCF hataları için ek verileri nasıl `FaultContract` taşıyabiliriz benzer şekilde destekleyici verileri göndermek için kullanılabilir.

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

WCF istemcilerinin hataları yakalayabileceğini <xref:System.ServiceModel.FaultException%601> tıpkı bir GRPC istemcisi hataları işlemek için bir `RpcException` yakalayabilirler. Genel bir tür `catch` C# olmadığından farklı bloklar halinde farklı hata türlerini yakalayamaz, ancak farklı durum kodları için aşağıdakiler gösterildiği gibi ayrı blokları bildirmek üzere özel durum filtreleri özelliği kullanabilirsiniz `RpcException` örneğinde

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
