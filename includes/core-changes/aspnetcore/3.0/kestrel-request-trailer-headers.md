---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394373"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a><span data-ttu-id="99e98-101">Kestrel: yeni koleksiyona taşınan artbilgisi üstbilgileri ıste</span><span class="sxs-lookup"><span data-stu-id="99e98-101">Kestrel: Request trailer headers moved to new collection</span></span>

<span data-ttu-id="99e98-102">Önceki sürümlerde, istek gövdesi sonuna kadar okurken istek üstbilgileri koleksiyonuna HTTP/1.1 öbekli treyler üst bilgileri eklenmiş Kestrel.</span><span class="sxs-lookup"><span data-stu-id="99e98-102">In prior versions, Kestrel added HTTP/1.1 chunked trailer headers into the request headers collection when the request body was read to the end.</span></span> <span data-ttu-id="99e98-103">Bu davranış, üstbilgiler ve tanıtımları arasındaki belirsizlik hakkında kaygılara neden oldu.</span><span class="sxs-lookup"><span data-stu-id="99e98-103">This behavior caused concerns about ambiguity between headers and trailers.</span></span> <span data-ttu-id="99e98-104">Tanıtım listesini yeni bir koleksiyona taşımak için karar yapıldı.</span><span class="sxs-lookup"><span data-stu-id="99e98-104">The decision was made to move the trailers to a new collection.</span></span>

<span data-ttu-id="99e98-105">HTTP/2 istek fragmanları ASP.NET Core 2,2 ' de yoktu, ancak artık ASP.NET Core 3,0 ' de bu yeni koleksiyonda de kullanılabiliyor.</span><span class="sxs-lookup"><span data-stu-id="99e98-105">HTTP/2 request trailers were unavailable in ASP.NET Core 2.2 but are now also available in this new collection in ASP.NET Core 3.0.</span></span>

<span data-ttu-id="99e98-106">Bu treylara erişmek için yeni istek uzantısı yöntemleri eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="99e98-106">New request extension methods have been added to access these trailers.</span></span>

<span data-ttu-id="99e98-107">İstek gövdesinin tamamı okunduktan sonra HTTP/1.1 Treyi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="99e98-107">HTTP/1.1 trailers are available once the entire request body has been read.</span></span>

<span data-ttu-id="99e98-108">HTTP/2 treyler istemciden alındıkları bir kez kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="99e98-108">HTTP/2 trailers are available once they're received from the client.</span></span> <span data-ttu-id="99e98-109">İstemci, tüm istek gövdesinin sunucu tarafından en az arabelleğe alınana kadar Treyi göndermez.</span><span class="sxs-lookup"><span data-stu-id="99e98-109">The client won't send the trailers until the entire request body has been at least buffered by the server.</span></span> <span data-ttu-id="99e98-110">Arabellek alanını boşaltmak için istek gövdesini okumanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="99e98-110">You may need to read the request body to free up buffer space.</span></span> <span data-ttu-id="99e98-111">İstek gövdesini sonuna okuduğunuzda, Treyi her zaman kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="99e98-111">Trailers are always available if you read the request body to the end.</span></span> <span data-ttu-id="99e98-112">Treyi, gövdenin sonunu işaret eden bir değer.</span><span class="sxs-lookup"><span data-stu-id="99e98-112">The trailers mark the end of the body.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="99e98-113">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="99e98-113">Version introduced</span></span>

<span data-ttu-id="99e98-114">3.0</span><span class="sxs-lookup"><span data-stu-id="99e98-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="99e98-115">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="99e98-115">Old behavior</span></span>

<span data-ttu-id="99e98-116">@No__t-0 koleksiyonuna istek fragme üstbilgileri eklenecektir.</span><span class="sxs-lookup"><span data-stu-id="99e98-116">Request trailer headers would be added to the `HttpRequest.Headers` collection.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="99e98-117">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="99e98-117">New behavior</span></span>

<span data-ttu-id="99e98-118">@No__t-1 koleksiyonunda istek Fragmanı üstbilgileri **yok** .</span><span class="sxs-lookup"><span data-stu-id="99e98-118">Request trailer headers **aren't present** in the `HttpRequest.Headers` collection.</span></span> <span data-ttu-id="99e98-119">Bunlara erişmek için `HttpRequest` ' da aşağıdaki genişletme yöntemlerini kullanın:</span><span class="sxs-lookup"><span data-stu-id="99e98-119">Use the following extension methods on `HttpRequest` to access them:</span></span>

- <span data-ttu-id="99e98-120">`GetDeclaredTrailers()`-gövdeden sonra beklenme hakkında bilgi içeren "artbilgisi" üst bilgisini alır.</span><span class="sxs-lookup"><span data-stu-id="99e98-120">`GetDeclaredTrailers()` - Gets the request "Trailer" header that lists which trailers to expect after the body.</span></span>
- <span data-ttu-id="99e98-121">`SupportsTrailers()`-isteğin treyler üst bilgilerini almayı destekleyip desteklemediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="99e98-121">`SupportsTrailers()` - Indicates if the request supports receiving trailer headers.</span></span>
- <span data-ttu-id="99e98-122">`CheckTrailersAvailable()`-isteğin treyleri destekleyip desteklemediğini ve okuma için kullanılabilir olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="99e98-122">`CheckTrailersAvailable()` - Determines if the request supports trailers and if they're available for reading.</span></span>
- <span data-ttu-id="99e98-123">`GetTrailer(string trailerName)`-yanıtın sonunda istenen üst bilgiyi alır.</span><span class="sxs-lookup"><span data-stu-id="99e98-123">`GetTrailer(string trailerName)` - Gets the requested trailing header from the response.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="99e98-124">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="99e98-124">Reason for change</span></span>

<span data-ttu-id="99e98-125">Treyde gRPC gibi senaryolarda önemli bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="99e98-125">Trailers are a key feature in scenarios like gRPC.</span></span> <span data-ttu-id="99e98-126">İstek üst bilgilerinde tanıtımları birleştirme, kullanıcılar için kafa karıştırıcı.</span><span class="sxs-lookup"><span data-stu-id="99e98-126">Merging the trailers in to request headers was confusing to users.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="99e98-127">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="99e98-127">Recommended action</span></span>

<span data-ttu-id="99e98-128">Treyleri erişmek için `HttpRequest` ' da artılgili uzantı yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="99e98-128">Use the trailer-related extension methods on `HttpRequest` to access trailers.</span></span>

#### <a name="category"></a><span data-ttu-id="99e98-129">Kategori</span><span class="sxs-lookup"><span data-stu-id="99e98-129">Category</span></span>

<span data-ttu-id="99e98-130">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="99e98-130">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="99e98-131">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="99e98-131">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
