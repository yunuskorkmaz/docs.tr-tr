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
# <a name="error-handling"></a><span data-ttu-id="62276-103">Hata işleme</span><span class="sxs-lookup"><span data-stu-id="62276-103">Error handling</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="62276-104">WCF, `FaultException<T>` SOAP `FaultContract` hata standardını destekleme dahil, ayrıntılı hata bilgileri sağlamak için ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="62276-104">WCF uses `FaultException<T>` and `FaultContract` to provide detailed error information, including supporting the SOAP Fault standard.</span></span>

<span data-ttu-id="62276-105">Ne yazık ki, gRPC 'nin geçerli sürümünde WCF 'de bulunan gelişmiş algoritmaların mümkündür yok ve yalnızca basit durum kodlarına ve meta verilere göre sınırlı yerleşik hata işleme sahip.</span><span class="sxs-lookup"><span data-stu-id="62276-105">Unfortunately, the current version of gRPC lacks the sophistication found with WCF and only has limited built-in error handling based on simple status codes and metadata.</span></span> <span data-ttu-id="62276-106">Aşağıdaki tabloda, en sık kullanılan durum kodlarına yönelik hızlı bir kılavuz verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="62276-106">The following table is a quick guide to the most commonly used status codes:</span></span>

| <span data-ttu-id="62276-107">Durum kodu</span><span class="sxs-lookup"><span data-stu-id="62276-107">Status Code</span></span> | <span data-ttu-id="62276-108">Gidermek</span><span class="sxs-lookup"><span data-stu-id="62276-108">Problem</span></span> |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | <span data-ttu-id="62276-109">Yöntem yazılmadı.</span><span class="sxs-lookup"><span data-stu-id="62276-109">Method hasn’t been written.</span></span> |
| `GRPC_STATUS_UNAVAILABLE` | <span data-ttu-id="62276-110">Tüm hizmette sorun.</span><span class="sxs-lookup"><span data-stu-id="62276-110">Problem with the whole service.</span></span> |
| `GRPC_STATUS_UNKNOWN` | <span data-ttu-id="62276-111">Geçersiz yanıt.</span><span class="sxs-lookup"><span data-stu-id="62276-111">Invalid response.</span></span> |
| `GRPC_STATUS_INTERNAL` | <span data-ttu-id="62276-112">Kodlama/kod çözme sorunu.</span><span class="sxs-lookup"><span data-stu-id="62276-112">Problem with encoding/decoding.</span></span> |
| `GRPC_STATUS_UNAUTHENTICATED` | <span data-ttu-id="62276-113">Kimlik doğrulama başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="62276-113">Authentication failed.</span></span> |
| `GRPC_STATUS_PERMISSION_DENIED` | <span data-ttu-id="62276-114">Yetkilendirme başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="62276-114">Authorization failed.</span></span> |
| `GRPC_STATUS_CANCELLED` | <span data-ttu-id="62276-115">Çağrı, genellikle çağıran tarafından iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="62276-115">Call was canceled, usually by the caller.</span></span> |

## <a name="raising-errors-in-aspnet-core-grpc"></a><span data-ttu-id="62276-116">ASP.NET Core gRPC 'de hataları oluşturma</span><span class="sxs-lookup"><span data-stu-id="62276-116">Raising errors in ASP.NET Core gRPC</span></span>

<span data-ttu-id="62276-117">ASP.NET Core GRPC hizmeti, istemci tarafından aynı işlemle yapılmış gibi yakalanarak `RpcException`bir hata yanıtı gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="62276-117">An ASP.NET Core gRPC service can send an error response by throwing an `RpcException`, which can be caught by the client as if it were in the same process.</span></span> <span data-ttu-id="62276-118">Bir durum kodu ve açıklaması içermesi ve isteğe bağlı olarak meta verileri ve daha uzun bir özel durum iletisi içermesi gerekir.`RpcException`</span><span class="sxs-lookup"><span data-stu-id="62276-118">The `RpcException` must include a status code and description, and can optionally include metadata and a longer exception message.</span></span> <span data-ttu-id="62276-119">Meta veriler, nesnelerin WCF hataları için ek verileri nasıl `FaultContract` taşıyabiliriz benzer şekilde destekleyici verileri göndermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="62276-119">The metadata can be used to send supporting data, similar to how `FaultContract` objects could carry additional data for WCF errors.</span></span>

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

## <a name="catching-errors-in-grpc-clients"></a><span data-ttu-id="62276-120">GRPC istemcilerinde yakalama hataları</span><span class="sxs-lookup"><span data-stu-id="62276-120">Catching errors in gRPC clients</span></span>

<span data-ttu-id="62276-121">WCF istemcilerinin hataları yakalayabileceğini <xref:System.ServiceModel.FaultException%601> tıpkı bir GRPC istemcisi hataları işlemek için bir `RpcException` yakalayabilirler.</span><span class="sxs-lookup"><span data-stu-id="62276-121">Just like WCF clients can catch <xref:System.ServiceModel.FaultException%601> errors, a gRPC client can catch an `RpcException` to handle errors.</span></span> <span data-ttu-id="62276-122">Genel bir tür `catch` C# olmadığından farklı bloklar halinde farklı hata türlerini yakalayamaz, ancak farklı durum kodları için aşağıdakiler gösterildiği gibi ayrı blokları bildirmek üzere özel durum filtreleri özelliği kullanabilirsiniz `RpcException` örneğinde</span><span class="sxs-lookup"><span data-stu-id="62276-122">Since `RpcException` isn't a generic type, you can't catch different error types in different blocks, but you can use C#'s *exception filters* feature to declare separate `catch` blocks for different status codes, as shown in the following example:</span></span>

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
> <span data-ttu-id="62276-123">Hatalar için ek meta veriler sağladığınızda, API belgelerinize veya `.proto` dosyanızdaki açıklamalarda ilgili anahtar ve değerleri belgelediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="62276-123">When you provide additional metadata for errors, be sure to document the relevant keys and values in your API documentation, or in comments in your `.proto` file.</span></span>

## <a name="grpc-richer-error-model"></a><span data-ttu-id="62276-124">gRPC daha zengin hata modeli</span><span class="sxs-lookup"><span data-stu-id="62276-124">gRPC Richer Error Model</span></span>

<span data-ttu-id="62276-125">Bu konuda, Google, WCF 'nin [FaultContract](xref:System.ServiceModel.FaultContractAttribute)gibi daha [zengin bir hata modeli](https://cloud.google.com/apis/design/errors#error_model) geliştirmiştir, ancak C# henüz desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="62276-125">Looking ahead, Google has developed a [richer error model](https://cloud.google.com/apis/design/errors#error_model) that is more like WCF's [FaultContract](xref:System.ServiceModel.FaultContractAttribute), but isn't supported in C# yet.</span></span> <span data-ttu-id="62276-126">Şu anda yalnızca Go, Java, Python ve C++için kullanılabilir, ancak için C# destek için bir sonraki yıl gelmesi beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="62276-126">Currently, it's only available for Go, Java, Python and C++, but support for C# is expected to come next year.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="62276-127">[Önceki](metadata.md)
>[İleri](ws-protocols.md)</span><span class="sxs-lookup"><span data-stu-id="62276-127">[Previous](metadata.md)
[Next](ws-protocols.md)</span></span>
