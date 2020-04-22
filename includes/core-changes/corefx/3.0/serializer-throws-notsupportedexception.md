---
ms.openlocfilehash: cc3251e3b31143bd95793b407e50cf76e0e30142
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021661"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a><span data-ttu-id="f40f9-101">Json serializer özel `JsonException` durum türü nden`NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="f40f9-101">Json serializer exception type changed from `JsonException` to `NotSupportedException`</span></span>

<span data-ttu-id="f40f9-102">.NET Core 3.0 Preview 6 ile 8'de, <xref:System.Text.Json.JsonException> serileştirici desteklenmeyen türemiş bir koleksiyon türüyle karşılaştığında bir atar.</span><span class="sxs-lookup"><span data-stu-id="f40f9-102">In .NET Core 3.0 Preview 6 through 8, the serializer would throw a <xref:System.Text.Json.JsonException> when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="f40f9-103">.NET Core 3.0 Preview 9'dan başlayarak, <xref:System.NotSupportedException> serileştirici yerine bir atar.</span><span class="sxs-lookup"><span data-stu-id="f40f9-103">Starting in .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> instead.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f40f9-104">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="f40f9-104">Change description</span></span>

<span data-ttu-id="f40f9-105">.NET Core 3.0 Preview 6 ile Preview 8'de, serileştirici desteklenmeyen türemiş bir koleksiyon türüyle karşılaştığında bir <xref:System.Text.Json.JsonException> atar.</span><span class="sxs-lookup"><span data-stu-id="f40f9-105">In .NET Core 3.0 Preview 6 through Preview 8, the serializer would throw a <xref:System.Text.Json.JsonException>  when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="f40f9-106">*Desteklenmeyen türemiş koleksiyon türü,* aşağıdaki türlerden birine atayılamayan herhangi bir koleksiyon türüdür:</span><span class="sxs-lookup"><span data-stu-id="f40f9-106">An *unsupported derived collection type* is any collection type that isn't assignable to one of the following types:</span></span>

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [<span data-ttu-id="f40f9-107">IDictionary\<Dize,T></span><span class="sxs-lookup"><span data-stu-id="f40f9-107">IDictionary\<String,T></span></span>](xref:System.Collections.Generic.IDictionary%602)

<span data-ttu-id="f40f9-108">.NET Core 3.0 Preview 9 ile başlayarak, <xref:System.NotSupportedException> serializer desteklenmeyen bir koleksiyon türüyle karşılaştığında bir a atar.</span><span class="sxs-lookup"><span data-stu-id="f40f9-108">Starting with .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> When encountering an unsupported collection type.</span></span> <span data-ttu-id="f40f9-109">Yeni özel durum türü, deserialization işleminin neden başarısız olduğunu daha iyi yansıtır.</span><span class="sxs-lookup"><span data-stu-id="f40f9-109">The new exception type better reflects why the deserialization operation is failing.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f40f9-110">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="f40f9-110">Version introduced</span></span>

<span data-ttu-id="f40f9-111">3.0 Önizleme 9</span><span class="sxs-lookup"><span data-stu-id="f40f9-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f40f9-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f40f9-112">Recommended action</span></span>

<span data-ttu-id="f40f9-113">Deserializing yaparken <xref:System.Text.Json.JsonException> yakalamak iseniz, aynı zamanda yakalamak <xref:System.NotSupportedException>düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f40f9-113">If you're catching <xref:System.Text.Json.JsonException> when deserializing, you might want to consider also catching <xref:System.NotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="f40f9-114">Kategori</span><span class="sxs-lookup"><span data-stu-id="f40f9-114">Category</span></span>

<span data-ttu-id="f40f9-115">Çekirdek .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="f40f9-115">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f40f9-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f40f9-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
