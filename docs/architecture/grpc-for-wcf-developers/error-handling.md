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
# <a name="error-handling"></a><span data-ttu-id="a8665-104">Hata işleme</span><span class="sxs-lookup"><span data-stu-id="a8665-104">Error handling</span></span>

<span data-ttu-id="a8665-105">Windows Communication Foundation (WCF), <xref:System.ServiceModel.FaultException%601> SOAP Hatası standardını desteklemek de dahil olmak üzere ayrıntılı hata bilgileri sağlamak için Hata [Sözleşmesi](xref:System.ServiceModel.FaultContractAttribute) kullanır.</span><span class="sxs-lookup"><span data-stu-id="a8665-105">Windows Communication Foundation (WCF) uses <xref:System.ServiceModel.FaultException%601> and [FaultContract](xref:System.ServiceModel.FaultContractAttribute) to provide detailed error information, including supporting the SOAP Fault standard.</span></span>

<span data-ttu-id="a8665-106">Ne yazık ki, gRPC'nin mevcut sürümü WCF ile bulunan gelişmişlik ten yoksunve yalnızca basit durum kodları ve meta verilere dayalı sınırlı yerleşik hata işleme vardır.</span><span class="sxs-lookup"><span data-stu-id="a8665-106">Unfortunately, the current version of gRPC lacks the sophistication found with WCF, and only has limited built-in error handling based on simple status codes and metadata.</span></span> <span data-ttu-id="a8665-107">Aşağıdaki tablo, en sık kullanılan durum kodları için hızlı bir kılavuzdur:</span><span class="sxs-lookup"><span data-stu-id="a8665-107">The following table is a quick guide to the most commonly used status codes:</span></span>

| <span data-ttu-id="a8665-108">Durum kodu</span><span class="sxs-lookup"><span data-stu-id="a8665-108">Status code</span></span> | <span data-ttu-id="a8665-109">Sorun</span><span class="sxs-lookup"><span data-stu-id="a8665-109">Problem</span></span> |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | <span data-ttu-id="a8665-110">Yöntem yazılmadı.</span><span class="sxs-lookup"><span data-stu-id="a8665-110">Method hasn't been written.</span></span> |
| `GRPC_STATUS_UNAVAILABLE` | <span data-ttu-id="a8665-111">Tüm servisle ilgili bir sorun var.</span><span class="sxs-lookup"><span data-stu-id="a8665-111">Problem with the whole service.</span></span> |
| `GRPC_STATUS_UNKNOWN` | <span data-ttu-id="a8665-112">Geçersiz yanıt.</span><span class="sxs-lookup"><span data-stu-id="a8665-112">Invalid response.</span></span> |
| `GRPC_STATUS_INTERNAL` | <span data-ttu-id="a8665-113">Kodlama/kod çözme sorunu.</span><span class="sxs-lookup"><span data-stu-id="a8665-113">Problem with encoding/decoding.</span></span> |
| `GRPC_STATUS_UNAUTHENTICATED` | <span data-ttu-id="a8665-114">Kimlik doğrulaması gerçekleştirilemedi.</span><span class="sxs-lookup"><span data-stu-id="a8665-114">Authentication failed.</span></span> |
| `GRPC_STATUS_PERMISSION_DENIED` | <span data-ttu-id="a8665-115">Yetkilendirme başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="a8665-115">Authorization failed.</span></span> |
| `GRPC_STATUS_CANCELLED` | <span data-ttu-id="a8665-116">Arama genellikle arayan kişi tarafından iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a8665-116">Call was canceled, usually by the caller.</span></span> |

## <a name="raise-errors-in-aspnet-core-grpc"></a><span data-ttu-id="a8665-117">Core gRPCASP.NETdeki hataları yükseltme</span><span class="sxs-lookup"><span data-stu-id="a8665-117">Raise errors in ASP.NET Core gRPC</span></span>

<span data-ttu-id="a8665-118">Bir ASP.NET Core gRPC hizmeti, istemci `RpcException`tarafından aynı işlemde yatmış gibi yakalanabilen bir hata yanıtı gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="a8665-118">An ASP.NET Core gRPC service can send an error response by throwing an `RpcException`, which can be caught by the client as if it were in the same process.</span></span> <span data-ttu-id="a8665-119">Durum `RpcException` kodu ve açıklama içermelidir ve isteğe bağlı olarak meta veriler ve daha uzun bir özel durum iletisi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a8665-119">The `RpcException` must include a status code and description, and can optionally include metadata and a longer exception message.</span></span> <span data-ttu-id="a8665-120">Meta veriler, nesnelerin WCF hataları için ek `FaultContract` verileri nasıl taşıyabildiği gibi destekleyici veriler göndermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a8665-120">The metadata can be used to send supporting data, similar to how `FaultContract` objects can carry additional data for WCF errors.</span></span>

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

## <a name="catch-errors-in-grpc-clients"></a><span data-ttu-id="a8665-121">gRPC istemcilerinde hataları yakalama</span><span class="sxs-lookup"><span data-stu-id="a8665-121">Catch errors in gRPC clients</span></span>

<span data-ttu-id="a8665-122">WCF istemcilerinin hataları <xref:System.ServiceModel.FaultException%601> yakalayabileceği gibi, gRPC istemcisi de hataları işlemek için bir `RpcException` hata yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="a8665-122">Just like WCF clients can catch <xref:System.ServiceModel.FaultException%601> errors, a gRPC client can catch an `RpcException` to handle errors.</span></span> <span data-ttu-id="a8665-123">`RpcException` Genel bir tür olmadığından, farklı bloklarda farklı hata türlerini yakalayamadığınız.</span><span class="sxs-lookup"><span data-stu-id="a8665-123">Because `RpcException` isn't a generic type, you can't catch different error types in different blocks.</span></span> <span data-ttu-id="a8665-124">Ancak, aşağıdaki örnekte gösterildiği gibi, farklı `catch` durum kodları için ayrı bloklar bildirmek için C#'ın *özel durum filtreleri* özelliğini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a8665-124">But you can use C#'s *exception filters* feature to declare separate `catch` blocks for different status codes, as shown in the following example:</span></span>

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
> <span data-ttu-id="a8665-125">Hatalar için ek meta veriler sağladığınızda, API belgelerinizde veya dosyanızdaki açıklamalarda ilgili `.proto` anahtarları ve değerleri belgelediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a8665-125">When you provide additional metadata for errors, be sure to document the relevant keys and values in your API documentation, or in comments in your `.proto` file.</span></span>

## <a name="grpc-richer-error-model"></a><span data-ttu-id="a8665-126">gRPC daha zengin hata modeli</span><span class="sxs-lookup"><span data-stu-id="a8665-126">gRPC richer error model</span></span>

<span data-ttu-id="a8665-127">Google [WCF's FaultContract](xref:System.ServiceModel.FaultContractAttribute)gibi daha zengin bir [hata modeli](https://cloud.google.com/apis/design/errors#error_model) geliştirdi , ama bu model henüz C # desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a8665-127">Google has developed a [richer error model](https://cloud.google.com/apis/design/errors#error_model) that's more like WCF's [FaultContract](xref:System.ServiceModel.FaultContractAttribute), but this model isn't supported in C# yet.</span></span> <span data-ttu-id="a8665-128">Şu anda yalnızca Go, Java, Python ve C++ için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a8665-128">Currently, it's only available for Go, Java, Python, and C++.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a8665-129">[Önceki](metadata.md)
>[Sonraki](ws-protocols.md)</span><span class="sxs-lookup"><span data-stu-id="a8665-129">[Previous](metadata.md)
[Next](ws-protocols.md)</span></span>
