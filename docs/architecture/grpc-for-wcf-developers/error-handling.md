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
# <a name="error-handling"></a><span data-ttu-id="16a64-104">Hata işleme</span><span class="sxs-lookup"><span data-stu-id="16a64-104">Error handling</span></span>

<span data-ttu-id="16a64-105">Windows Communication Foundation (WCF), SOAP hata standardını destekleme dahil, ayrıntılı hata bilgileri sağlamak için <xref:System.ServiceModel.FaultException%601> ve [FaultContract](xref:System.ServiceModel.FaultContractAttribute) kullanır.</span><span class="sxs-lookup"><span data-stu-id="16a64-105">Windows Communication Foundation (WCF) uses <xref:System.ServiceModel.FaultException%601> and [FaultContract](xref:System.ServiceModel.FaultContractAttribute) to provide detailed error information, including supporting the SOAP Fault standard.</span></span>

<span data-ttu-id="16a64-106">Ne yazık ki, gRPC 'nin geçerli sürümü WCF ile gelişmiş algoritmaların mümkündür bulunamadı ve yalnızca basit durum kodlarına ve meta verilere göre sınırlı yerleşik hata işleme sahip.</span><span class="sxs-lookup"><span data-stu-id="16a64-106">Unfortunately, the current version of gRPC lacks the sophistication found with WCF, and only has limited built-in error handling based on simple status codes and metadata.</span></span> <span data-ttu-id="16a64-107">Aşağıdaki tabloda, en sık kullanılan durum kodlarına yönelik hızlı bir kılavuz verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="16a64-107">The following table is a quick guide to the most commonly used status codes:</span></span>

| <span data-ttu-id="16a64-108">Durum kodu</span><span class="sxs-lookup"><span data-stu-id="16a64-108">Status code</span></span> | <span data-ttu-id="16a64-109">Sorun</span><span class="sxs-lookup"><span data-stu-id="16a64-109">Problem</span></span> |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | <span data-ttu-id="16a64-110">Yöntem yazılmadı.</span><span class="sxs-lookup"><span data-stu-id="16a64-110">Method hasn’t been written.</span></span> |
| `GRPC_STATUS_UNAVAILABLE` | <span data-ttu-id="16a64-111">Tüm hizmette sorun.</span><span class="sxs-lookup"><span data-stu-id="16a64-111">Problem with the whole service.</span></span> |
| `GRPC_STATUS_UNKNOWN` | <span data-ttu-id="16a64-112">Geçersiz yanıt.</span><span class="sxs-lookup"><span data-stu-id="16a64-112">Invalid response.</span></span> |
| `GRPC_STATUS_INTERNAL` | <span data-ttu-id="16a64-113">Kodlama/kod çözme sorunu.</span><span class="sxs-lookup"><span data-stu-id="16a64-113">Problem with encoding/decoding.</span></span> |
| `GRPC_STATUS_UNAUTHENTICATED` | <span data-ttu-id="16a64-114">Kimlik doğrulama başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="16a64-114">Authentication failed.</span></span> |
| `GRPC_STATUS_PERMISSION_DENIED` | <span data-ttu-id="16a64-115">Yetkilendirme başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="16a64-115">Authorization failed.</span></span> |
| `GRPC_STATUS_CANCELLED` | <span data-ttu-id="16a64-116">Çağrı, genellikle çağıran tarafından iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="16a64-116">Call was canceled, usually by the caller.</span></span> |

## <a name="raise-errors-in-aspnet-core-grpc"></a><span data-ttu-id="16a64-117">ASP.NET Core gRPC 'de hata oluştur</span><span class="sxs-lookup"><span data-stu-id="16a64-117">Raise errors in ASP.NET Core gRPC</span></span>

<span data-ttu-id="16a64-118">ASP.NET Core gRPC hizmeti, aynı işlem içinde olduğu gibi istemci tarafından yakalanarak bir `RpcException`oluşturarak hata yanıtı gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="16a64-118">An ASP.NET Core gRPC service can send an error response by throwing an `RpcException`, which can be caught by the client as if it were in the same process.</span></span> <span data-ttu-id="16a64-119">`RpcException` bir durum kodu ve açıklaması içermeli ve isteğe bağlı olarak meta verileri ve daha uzun bir özel durum iletisi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="16a64-119">The `RpcException` must include a status code and description, and can optionally include metadata and a longer exception message.</span></span> <span data-ttu-id="16a64-120">Meta veriler, `FaultContract` nesnelerinin WCF hataları için ek verileri nasıl taşıyabilirim benzer şekilde destekleyici verileri göndermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16a64-120">The metadata can be used to send supporting data, similar to how `FaultContract` objects can carry additional data for WCF errors.</span></span>

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

## <a name="catch-errors-in-grpc-clients"></a><span data-ttu-id="16a64-121">GRPC istemcilerinde hataları yakala</span><span class="sxs-lookup"><span data-stu-id="16a64-121">Catch errors in gRPC clients</span></span>

<span data-ttu-id="16a64-122">WCF istemcilerinin <xref:System.ServiceModel.FaultException%601> hataları yakalayabileceğini tıpkı, bir gRPC istemcisi hataları işlemek için bir `RpcException` yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="16a64-122">Just like WCF clients can catch <xref:System.ServiceModel.FaultException%601> errors, a gRPC client can catch an `RpcException` to handle errors.</span></span> <span data-ttu-id="16a64-123">`RpcException` genel bir tür olmadığından farklı bloklara farklı hata türlerini yakalayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="16a64-123">Because `RpcException` isn't a generic type, you can't catch different error types in different blocks.</span></span> <span data-ttu-id="16a64-124">Ancak, aşağıdaki örnekte C#gösterildiği gibi farklı durum kodları için ayrı `catch` blokları bildirmek üzere *özel durum filtreleri* özelliğini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="16a64-124">But you can use C#'s *exception filters* feature to declare separate `catch` blocks for different status codes, as shown in the following example:</span></span>

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
> <span data-ttu-id="16a64-125">Hatalar için ek meta veriler sağladığınızda, API belgelerinize veya `.proto` dosyanızdaki açıklamalarda ilgili anahtar ve değerleri belgelediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="16a64-125">When you provide additional metadata for errors, be sure to document the relevant keys and values in your API documentation, or in comments in your `.proto` file.</span></span>

## <a name="grpc-richer-error-model"></a><span data-ttu-id="16a64-126">gRPC daha zengin hata modeli</span><span class="sxs-lookup"><span data-stu-id="16a64-126">gRPC richer error model</span></span>

<span data-ttu-id="16a64-127">Google, WCF 'nin [FaultContract](xref:System.ServiceModel.FaultContractAttribute)gibi daha [zengin bir hata modeli](https://cloud.google.com/apis/design/errors#error_model) geliştirmiştir, ancak bu model henüz içinde C# desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="16a64-127">Google has developed a [richer error model](https://cloud.google.com/apis/design/errors#error_model) that's more like WCF's [FaultContract](xref:System.ServiceModel.FaultContractAttribute), but this model isn't supported in C# yet.</span></span> <span data-ttu-id="16a64-128">Şu anda yalnızca Go, Java, Python ve ile C++kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16a64-128">Currently, it's only available for Go, Java, Python, and C++.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="16a64-129">[Önceki](metadata.md)
>[İleri](ws-protocols.md)</span><span class="sxs-lookup"><span data-stu-id="16a64-129">[Previous](metadata.md)
[Next](ws-protocols.md)</span></span>
