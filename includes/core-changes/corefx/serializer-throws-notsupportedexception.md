---
ms.openlocfilehash: a35439efce25db94e70420fc6aeaf04816525758
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71263315"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a><span data-ttu-id="5bdfd-101">JSON serileştirici özel durum türü `JsonException` iken`NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="5bdfd-101">Json serializer exception type changed from `JsonException` to `NotSupportedException`</span></span>

<span data-ttu-id="5bdfd-102">.NET Core 3,0 Preview 6 ' dan 8 ' de, seri hale getirici <xref:System.Text.Json.JsonException> desteklenmeyen bir türetilmiş koleksiyon türüyle karşılaşıldığında bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5bdfd-102">In .NET Core 3.0 Preview 6 through 8, the serializer would throw a <xref:System.Text.Json.JsonException> when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="5bdfd-103">.NET Core 3,0 Preview 9 ' dan başlayarak, serileştirici bir <xref:System.NotSupportedException> yerine bir atar.</span><span class="sxs-lookup"><span data-stu-id="5bdfd-103">Starting in .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> instead.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5bdfd-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="5bdfd-104">Change description</span></span>

<span data-ttu-id="5bdfd-105">.NET Core 3,0 Preview 6 ' da Preview 8 ' de, seri hale getirici <xref:System.Text.Json.JsonException> desteklenmeyen bir türetilmiş koleksiyon türüyle karşılaşıldığında bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5bdfd-105">In .NET Core 3.0 Preview 6 through Preview 8, the serializer would throw a <xref:System.Text.Json.JsonException>  when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="5bdfd-106">*Desteklenmeyen bir türetilmiş koleksiyon türü* , aşağıdaki türlerden birine atanabilir olmayan herhangi bir koleksiyon türüdür:</span><span class="sxs-lookup"><span data-stu-id="5bdfd-106">An *unsupported derived collection type* is any collection type that isn't assignable to one of the following types:</span></span>

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>`
- <xref:System.Collections.IDictionary>
- [<span data-ttu-id="5bdfd-107">IDictionary\<dizesi, T ></span><span class="sxs-lookup"><span data-stu-id="5bdfd-107">IDictionary\<String,T></span></span>](xref:System.Collections.Generic.IDictionary%602)

<span data-ttu-id="5bdfd-108">.NET Core 3,0 Preview 9 ' dan itibaren, seri hale getirici <xref:System.NotSupportedException> desteklenmeyen bir koleksiyon türüyle karşılaşıldığında bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5bdfd-108">Starting with .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> When encountering an unsupported collection type.</span></span> <span data-ttu-id="5bdfd-109">Yeni özel durum türü, serisini kaldırma işleminin başarısız olduğunu daha iyi yansıtır.</span><span class="sxs-lookup"><span data-stu-id="5bdfd-109">The new exception type better reflects why the deserialization operation is failing.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5bdfd-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5bdfd-110">Version introduced</span></span>

<span data-ttu-id="5bdfd-111">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="5bdfd-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5bdfd-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="5bdfd-112">Recommended action</span></span>

<span data-ttu-id="5bdfd-113">Seri durumdan çıkarma sırasında <xref:System.Text.Json.JsonException> yakalama yapıyorsanız, bunu <xref:System.NotSupportedException>da ele almanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="5bdfd-113">If you're catching <xref:System.Text.Json.JsonException> when deserializing, you might want to consider also catching <xref:System.NotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="5bdfd-114">Kategori</span><span class="sxs-lookup"><span data-stu-id="5bdfd-114">Category</span></span>

<span data-ttu-id="5bdfd-115">CoreFx</span><span class="sxs-lookup"><span data-stu-id="5bdfd-115">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5bdfd-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="5bdfd-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
