---
ms.openlocfilehash: 39d1b2dba8077bf9bf998775f8967d455f36b549
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119284"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a><span data-ttu-id="7ee25-101">JSON serileştirici özel durum türü `JsonException` iken`NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="7ee25-101">Json serializer exception type changed from `JsonException` to `NotSupportedException`</span></span>

<span data-ttu-id="7ee25-102">.NET Core 3,0 Preview 6 ' dan 8 ' de, seri hale getirici <xref:System.Text.Json.JsonException> desteklenmeyen bir türetilmiş koleksiyon türüyle karşılaşıldığında bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7ee25-102">In .NET Core 3.0 Preview 6 through 8, the serializer would throw a <xref:System.Text.Json.JsonException> when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="7ee25-103">.NET Core 3,0 Preview 9 ' dan başlayarak, serileştirici bir <xref:System.NotSupportedException> yerine bir atar.</span><span class="sxs-lookup"><span data-stu-id="7ee25-103">Starting in .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> instead.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7ee25-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="7ee25-104">Change description</span></span>

<span data-ttu-id="7ee25-105">.NET Core 3,0 Preview 6 ' da Preview 8 ' de, seri hale getirici <xref:System.Text.Json.JsonException> desteklenmeyen bir türetilmiş koleksiyon türüyle karşılaşıldığında bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7ee25-105">In .NET Core 3.0 Preview 6 through Preview 8, the serializer would throw a <xref:System.Text.Json.JsonException>  when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="7ee25-106">*Desteklenmeyen bir türetilmiş koleksiyon türü* , aşağıdaki türlerden birine atanabilir olmayan herhangi bir koleksiyon türüdür:</span><span class="sxs-lookup"><span data-stu-id="7ee25-106">An *unsupported derived collection type* is any collection type that isn't assignable to one of the following types:</span></span>

 - <xref:System.Collections.IList>
 - <xref:System.Collections.Generic.ICollection%601>
 - <xref:System.Collections.Generic.Stack%601>
 - <xref:System.Collections.Generic.Queue%601>`
 - <xref:System.Collections.IDictionary>
 - [<span data-ttu-id="7ee25-107">IDictionary\<dizesi, T ></span><span class="sxs-lookup"><span data-stu-id="7ee25-107">IDictionary\<String,T></span></span>](xref:System.Collections.Generic.IDictionary%602)

<span data-ttu-id="7ee25-108">.NET Core 3,0 Preview 9 ' dan itibaren, seri hale getirici <xref:System.NotSupportedException> desteklenmeyen bir koleksiyon türüyle karşılaşıldığında bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7ee25-108">Starting with .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> When encountering an unsupported collection type.</span></span> <span data-ttu-id="7ee25-109">Yeni özel durum türü, serisini kaldırma işleminin başarısız olduğunu daha iyi yansıtır.</span><span class="sxs-lookup"><span data-stu-id="7ee25-109">The new exception type better reflects why the deserialization operation is failing.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7ee25-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7ee25-110">Version introduced</span></span>

<span data-ttu-id="7ee25-111">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="7ee25-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7ee25-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="7ee25-112">Recommended action</span></span>

<span data-ttu-id="7ee25-113">Seri durumdan çıkarma sırasında <xref:System.Text.Json.JsonException> yakalama yapıyorsanız, bunu <xref:System.NotSupportedException>da ele almanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="7ee25-113">If you're catching <xref:System.Text.Json.JsonException> when deserializing, you might want to consider also catching <xref:System.NotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="7ee25-114">Kategori</span><span class="sxs-lookup"><span data-stu-id="7ee25-114">Category</span></span>

<span data-ttu-id="7ee25-115">CoreFx</span><span class="sxs-lookup"><span data-stu-id="7ee25-115">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7ee25-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7ee25-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
