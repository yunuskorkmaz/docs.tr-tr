---
ms.openlocfilehash: e6e10b2ec451c07bf397cbdcac51ef57c29dab47
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568184"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a><span data-ttu-id="f1a91-101">JSON serileştirici özel durum türü `JsonException` `NotSupportedException` olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="f1a91-101">Json serializer exception type changed from `JsonException` to `NotSupportedException`</span></span>

<span data-ttu-id="f1a91-102">.NET Core 3,0 Preview 6 ile 8 ' de, seri hale getirici desteklenmeyen bir türetilmiş koleksiyon türüyle karşılaştığı zaman bir <xref:System.Text.Json.JsonException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1a91-102">In .NET Core 3.0 Preview 6 through 8, the serializer would throw a <xref:System.Text.Json.JsonException> when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="f1a91-103">.NET Core 3,0 Preview 9 ' dan başlayarak, serileştirici bunun yerine bir <xref:System.NotSupportedException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1a91-103">Starting in .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> instead.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f1a91-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="f1a91-104">Change description</span></span>

<span data-ttu-id="f1a91-105">.NET Core 3,0 Preview 6 ' da Preview 8 ' de, seri hale getirici desteklenmeyen bir türetilen koleksiyon türüyle karşılaşıldığında bir <xref:System.Text.Json.JsonException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1a91-105">In .NET Core 3.0 Preview 6 through Preview 8, the serializer would throw a <xref:System.Text.Json.JsonException>  when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="f1a91-106">*Desteklenmeyen bir türetilmiş koleksiyon türü* , aşağıdaki türlerden birine atanabilir olmayan herhangi bir koleksiyon türüdür:</span><span class="sxs-lookup"><span data-stu-id="f1a91-106">An *unsupported derived collection type* is any collection type that isn't assignable to one of the following types:</span></span>

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [<span data-ttu-id="f1a91-107">IDictionary\<dize, T ></span><span class="sxs-lookup"><span data-stu-id="f1a91-107">IDictionary\<String,T></span></span>](xref:System.Collections.Generic.IDictionary%602)

<span data-ttu-id="f1a91-108">.NET Core 3,0 Preview 9 ' dan itibaren, seri hale getirici desteklenmeyen bir koleksiyon türüyle karşılaşıldığında bir <xref:System.NotSupportedException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1a91-108">Starting with .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> When encountering an unsupported collection type.</span></span> <span data-ttu-id="f1a91-109">Yeni özel durum türü, serisini kaldırma işleminin başarısız olduğunu daha iyi yansıtır.</span><span class="sxs-lookup"><span data-stu-id="f1a91-109">The new exception type better reflects why the deserialization operation is failing.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f1a91-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f1a91-110">Version introduced</span></span>

<span data-ttu-id="f1a91-111">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="f1a91-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f1a91-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f1a91-112">Recommended action</span></span>

<span data-ttu-id="f1a91-113">Seri durumdan çıkarma sırasında <xref:System.Text.Json.JsonException> bulundursanız, <xref:System.NotSupportedException>de yakalamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1a91-113">If you're catching <xref:System.Text.Json.JsonException> when deserializing, you might want to consider also catching <xref:System.NotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="f1a91-114">Kategori</span><span class="sxs-lookup"><span data-stu-id="f1a91-114">Category</span></span>

<span data-ttu-id="f1a91-115">CoreFx</span><span class="sxs-lookup"><span data-stu-id="f1a91-115">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f1a91-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f1a91-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
