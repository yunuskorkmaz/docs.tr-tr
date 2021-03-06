---
title: 'Son değişiklik: parametreler Stream ile türetilmiş türlerde yeniden adlandırıldı'
description: Stream 'den türetilmiş türler yöntemlerinde bazı parametre adlarının değiştirildiği çekirdek .NET kitaplıklarında .NET 6,0 'in son değişikliği hakkında bilgi edinin.
ms.date: 03/04/2021
ms.openlocfilehash: c685fae6a7ed20ea47815d5f89a4e066c75e1178
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102260064"
---
# <a name="some-parameters-in-stream-derived-types-are-renamed"></a><span data-ttu-id="1e44a-103">Stream ile türetilmiş türlerde bazı parametreler yeniden adlandırıldı</span><span class="sxs-lookup"><span data-stu-id="1e44a-103">Some parameters in Stream-derived types are renamed</span></span>

<span data-ttu-id="1e44a-104">.NET 6 ' da, ' den türetilen türlerin bazı yöntemlerinin parametreleri <xref:System.IO.Stream?displayProperty=fullName> temel sınıfla eşleşecek şekilde yeniden adlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="1e44a-104">In .NET 6, some parameters of methods on types derived from <xref:System.IO.Stream?displayProperty=fullName> have been renamed to match the base class.</span></span>

## <a name="change-description"></a><span data-ttu-id="1e44a-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="1e44a-105">Change description</span></span>

<span data-ttu-id="1e44a-106">Önceki .NET sürümlerinde, geçersiz kılma yöntemlerinden türetilmiş çeşitli türler, <xref:System.IO.Stream> ancak temel tür tarafından kullanılanlardan farklı parametre adları kullanır.</span><span class="sxs-lookup"><span data-stu-id="1e44a-106">In previous .NET versions, several types derived from <xref:System.IO.Stream> override methods but use different parameter names than those used by the base type.</span></span> <span data-ttu-id="1e44a-107">Örneğin, ' ın byte array parametresi, <xref:System.IO.Compression.DeflateStream.Read(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType> `array` temel sınıf yöntemindeki karşılık gelen bağımsız değişken olarak adlandırılır `buffer` .</span><span class="sxs-lookup"><span data-stu-id="1e44a-107">For example, the byte array parameter of <xref:System.IO.Compression.DeflateStream.Read(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType> is named `array` while the corresponding argument in the base class method is named `buffer`.</span></span>

<span data-ttu-id="1e44a-108">.NET 6 ' da, eşleşmeyen parametre adlarından türetilen tüm türler, <xref:System.IO.Stream?displayProperty=fullName> temel türle aynı parametre adları kullanılarak temel türle uyumlu olarak getirildi.</span><span class="sxs-lookup"><span data-stu-id="1e44a-108">In .NET 6, all types that derive from <xref:System.IO.Stream?displayProperty=fullName> that had mismatched parameter names have been brought into conformance with the base type by using the same parameter names as the base type.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="1e44a-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="1e44a-109">Version introduced</span></span>

<span data-ttu-id="1e44a-110">6,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="1e44a-110">6.0 Preview 1</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="1e44a-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="1e44a-111">Reason for change</span></span>

<span data-ttu-id="1e44a-112">Değişikliğin çeşitli nedenleri vardır:</span><span class="sxs-lookup"><span data-stu-id="1e44a-112">There are several reasons for the change:</span></span>

- <span data-ttu-id="1e44a-113">Geçersiz bir bağımsız değişken geçirildiyse ve bir özel durum oluşursa, bu özel durum, uygulamaya bağlı olarak temel parametrenin adını ya da türetilmiş parametrenin adını içeriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="1e44a-113">If an invalid argument was passed and an exception was thrown, that exception might have contained the base parameter's name or the derived parameter's name, depending on the implementation.</span></span> <span data-ttu-id="1e44a-114">Çağıran, temel olarak veya türetilmiş tür olarak yazılmış bir başvuru kullanıyor olabileceğinden, özel durum içindeki bağımsız değişken adının her zaman doğru olması olanaksızdır.</span><span class="sxs-lookup"><span data-stu-id="1e44a-114">Since the caller may have been using a reference typed as the base or as the derived type, it's impossible for the argument name in the exception to always be correct.</span></span>
- <span data-ttu-id="1e44a-115">Farklı parametre adlarına sahip olmak, davranışı sürekli olarak tüm uygulamalarda doğrulamaya daha zor hale getirir <xref:System.IO.Stream> .</span><span class="sxs-lookup"><span data-stu-id="1e44a-115">Having different parameter names makes it harder to consistently validate behavior across all <xref:System.IO.Stream> implementations.</span></span>
- <span data-ttu-id="1e44a-116">.NET 6 <xref:System.IO.Stream> , bağımsız değişkenlerin doğrulanması için genel bir yöntem ekler ve bu yöntemlerin kullanmak için tutarlı bir parametre adı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1e44a-116">.NET 6 adds a public method on <xref:System.IO.Stream> for validating arguments, and that methods needs to have a consistent parameter name to use.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="1e44a-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="1e44a-117">Recommended action</span></span>

<span data-ttu-id="1e44a-118">Bu son değişikliğin etkisi en az:</span><span class="sxs-lookup"><span data-stu-id="1e44a-118">The effect of this breaking change is minimal:</span></span>

- <span data-ttu-id="1e44a-119">Mevcut ikililer için, etkilenen türetilmiş türlerdeki parametrelerin adlarını incelemek üzere yansıma kullanan kodla sınırlı olur.</span><span class="sxs-lookup"><span data-stu-id="1e44a-119">For existing binaries, its impact is limited to code that uses reflection to examine the names of parameters on the affected derived types.</span></span>
- <span data-ttu-id="1e44a-120">Kaynak kodu için, bu türetilmiş tür olarak yazılmış bir değişken kullanılarak türetilmiş akış türündeki yöntemleri çağırmak için adlandırılmış parametreleri kullanan kodla sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="1e44a-120">For source code, its impact is limited to code that uses named parameters to invoke methods on the derived stream type using a variable typed as that derived type.</span></span>

<span data-ttu-id="1e44a-121">Her iki durumda da önerilen eylem, temel parametre adını sürekli olarak kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="1e44a-121">In both cases, the recommended action is to consistently use the base parameter name.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="1e44a-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="1e44a-122">Affected APIs</span></span>

- <xref:System.IO.BufferedStream.Read(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.IO.BufferedStream.Write(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.IO.Compression.DeflateStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.IO.Compression.DeflateStream.Read(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.IO.Compression.DeflateStream.ReadAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.IO.Compression.DeflateStream.Write(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.IO.Compression.DeflateStream.WriteAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.IO.Compression.GZipStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.IO.Compression.GZipStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.IO.Compression.GZipStream.Read(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.IO.Compression.GZipStream.ReadAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.IO.Compression.GZipStream.Write(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.IO.Compression.GZipStream.WriteAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.IO.FileStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.IO.FileStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.IO.FileStream.Read(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.IO.FileStream.Write(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.Net.Sockets.NetworkStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.Net.Sockets.NetworkStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)?displayProperty=fullName>
- <xref:System.Net.Sockets.NetworkStream.Read(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.Net.Sockets.NetworkStream.ReadAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.Net.Sockets.NetworkStream.Write(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>
- <xref:System.Net.Sockets.NetworkStream.WriteAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `M:System.IO.Compression.DeflateStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.IO.Compression.DeflateStream.Read(System.Byte[],System.Int32,System.Int32)`
- `M:System.IO.Compression.DeflateStream.ReadAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)`
- `M:System.IO.Compression.DeflateStream.Write(System.Byte[],System.Int32,System.Int32)`
- `M:System.IO.Compression.DeflateStream.WriteAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)`
- `M:System.IO.Compression.GZipStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.IO.Compression.GZipStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.IO.Compression.GZipStream.Read(System.Byte[],System.Int32,System.Int32)`
- `M:System.IO.Compression.GZipStream.ReadAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)`
- `M:System.IO.Compression.GZipStream.Write(System.Byte[],System.Int32,System.Int32)`
- `M:System.IO.Compression.GZipStream.WriteAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)`
- `M:System.IO.BufferedStream.Read(System.Byte[],System.Int32,System.Int32)`
- `M:System.IO.BufferedStream.Write(System.Byte[],System.Int32,System.Int32)`
- `M:System.IO.FileStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.IO.FileStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.IO.FileStream.Read(System.Byte[],System.Int32,System.Int32)`
- `M:System.IO.FileStream.Write(System.Byte[],System.Int32,System.Int32)`
- `M:System.Net.Sockets.NetworkStream.BeginRead(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.Net.Sockets.NetworkStream.BeginWrite(System.Byte[],System.Int32,System.Int32,System.AsyncCallback,System.Object)`
- `M:System.Net.Sockets.NetworkStream.Read(System.Byte[],System.Int32,System.Int32)`
- `M:System.Net.Sockets.NetworkStream.ReadAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)`
- `M:System.Net.Sockets.NetworkStream.Write(System.Byte[],System.Int32,System.Int32)`
- `M:System.Net.Sockets.NetworkStream.WriteAsync(System.Byte[],System.Int32,System.Int32,System.Threading.CancellationToken)`

-->
