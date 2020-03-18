---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394373"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a><span data-ttu-id="569df-101">Kerkenez: İstek römork başlıkları yeni koleksiyona taşındı</span><span class="sxs-lookup"><span data-stu-id="569df-101">Kestrel: Request trailer headers moved to new collection</span></span>

<span data-ttu-id="569df-102">Önceki sürümlerde Kestrel, istek gövdesi sonuna kadar okunduğunda istek üstbilgikoleksiyonuna HTTP/1.1 ötücü römork başlıklarını eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="569df-102">In prior versions, Kestrel added HTTP/1.1 chunked trailer headers into the request headers collection when the request body was read to the end.</span></span> <span data-ttu-id="569df-103">Bu davranış, üstbilgi ve römorklar arasındaki belirsizlik le ilgili endişelere neden oldu.</span><span class="sxs-lookup"><span data-stu-id="569df-103">This behavior caused concerns about ambiguity between headers and trailers.</span></span> <span data-ttu-id="569df-104">Römorkların yeni bir koleksiyona taşınmasına karar verildi.</span><span class="sxs-lookup"><span data-stu-id="569df-104">The decision was made to move the trailers to a new collection.</span></span>

<span data-ttu-id="569df-105">HTTP /2 istek römorkASP.NET Core 2.2 kullanılamaz ama şimdi de ASP.NET Core 3.0 bu yeni koleksiyonda mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="569df-105">HTTP/2 request trailers were unavailable in ASP.NET Core 2.2 but are now also available in this new collection in ASP.NET Core 3.0.</span></span>

<span data-ttu-id="569df-106">Bu fragmanlara erişmek için yeni istek uzatma yöntemleri eklendi.</span><span class="sxs-lookup"><span data-stu-id="569df-106">New request extension methods have been added to access these trailers.</span></span>

<span data-ttu-id="569df-107">TÜM istek gövdesi okunduktan sonra HTTP/1.1 fragmanları mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="569df-107">HTTP/1.1 trailers are available once the entire request body has been read.</span></span>

<span data-ttu-id="569df-108">HTTP/2 römorkları istemciden alındıktan sonra kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="569df-108">HTTP/2 trailers are available once they're received from the client.</span></span> <span data-ttu-id="569df-109">İstemci, tüm istek gövdesi en azından sunucu tarafından arabelleğe alana gelene kadar römorkları göndermez.</span><span class="sxs-lookup"><span data-stu-id="569df-109">The client won't send the trailers until the entire request body has been at least buffered by the server.</span></span> <span data-ttu-id="569df-110">Arabellek alanını boşaltmak için istek gövdesini okumanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="569df-110">You may need to read the request body to free up buffer space.</span></span> <span data-ttu-id="569df-111">İstek gövdesini sonuna kadar okursanız, römorklar her zaman kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="569df-111">Trailers are always available if you read the request body to the end.</span></span> <span data-ttu-id="569df-112">Römorklar vücudun sonunu işaret ediyor.</span><span class="sxs-lookup"><span data-stu-id="569df-112">The trailers mark the end of the body.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="569df-113">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="569df-113">Version introduced</span></span>

<span data-ttu-id="569df-114">3,0</span><span class="sxs-lookup"><span data-stu-id="569df-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="569df-115">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="569df-115">Old behavior</span></span>

<span data-ttu-id="569df-116">İstek römork başlıkları koleksiyona `HttpRequest.Headers` eklenecek.</span><span class="sxs-lookup"><span data-stu-id="569df-116">Request trailer headers would be added to the `HttpRequest.Headers` collection.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="569df-117">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="569df-117">New behavior</span></span>

<span data-ttu-id="569df-118">İstek römork üstbilgisi `HttpRequest.Headers` koleksiyonda **bulunmaz.**</span><span class="sxs-lookup"><span data-stu-id="569df-118">Request trailer headers **aren't present** in the `HttpRequest.Headers` collection.</span></span> <span data-ttu-id="569df-119">Bunlara erişmek `HttpRequest` için aşağıdaki uzantı yöntemlerini kullanın:</span><span class="sxs-lookup"><span data-stu-id="569df-119">Use the following extension methods on `HttpRequest` to access them:</span></span>

- <span data-ttu-id="569df-120">`GetDeclaredTrailers()`- Hangi römorklar vücut sonra beklemek listeler istek "Römork" başlık alır.</span><span class="sxs-lookup"><span data-stu-id="569df-120">`GetDeclaredTrailers()` - Gets the request "Trailer" header that lists which trailers to expect after the body.</span></span>
- <span data-ttu-id="569df-121">`SupportsTrailers()`- İsteğin römork üstbilgisini almayı destekleyip desteklemeyin gösterir.</span><span class="sxs-lookup"><span data-stu-id="569df-121">`SupportsTrailers()` - Indicates if the request supports receiving trailer headers.</span></span>
- <span data-ttu-id="569df-122">`CheckTrailersAvailable()`- İsteğin römorkları destekleyip desteklemediklerini ve okumaya uygun olup olmadıklarını belirler.</span><span class="sxs-lookup"><span data-stu-id="569df-122">`CheckTrailersAvailable()` - Determines if the request supports trailers and if they're available for reading.</span></span>
- <span data-ttu-id="569df-123">`GetTrailer(string trailerName)`- İstenilen sondaki üstbilgiyanıttan alır.</span><span class="sxs-lookup"><span data-stu-id="569df-123">`GetTrailer(string trailerName)` - Gets the requested trailing header from the response.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="569df-124">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="569df-124">Reason for change</span></span>

<span data-ttu-id="569df-125">Römorklar gRPC gibi senaryolarda önemli bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="569df-125">Trailers are a key feature in scenarios like gRPC.</span></span> <span data-ttu-id="569df-126">Römorkları üstbilgi istemek için birleştirmek kullanıcılar için kafa karıştırıcıydı.</span><span class="sxs-lookup"><span data-stu-id="569df-126">Merging the trailers in to request headers was confusing to users.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="569df-127">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="569df-127">Recommended action</span></span>

<span data-ttu-id="569df-128">Römorklara erişmek `HttpRequest` için römorkla ilgili uzatma yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="569df-128">Use the trailer-related extension methods on `HttpRequest` to access trailers.</span></span>

#### <a name="category"></a><span data-ttu-id="569df-129">Kategori</span><span class="sxs-lookup"><span data-stu-id="569df-129">Category</span></span>

<span data-ttu-id="569df-130">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="569df-130">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="569df-131">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="569df-131">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
