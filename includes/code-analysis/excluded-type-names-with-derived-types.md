---
ms.openlocfilehash: 150882f3e4c9ff7abe811e09da94b8141de75778
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97366833"
---
### <a name="exclude-specific-types-and-their-derived-types"></a><span data-ttu-id="359f0-101">Belirli türleri ve bunların türetilmiş türlerini Dışla</span><span class="sxs-lookup"><span data-stu-id="359f0-101">Exclude specific types and their derived types</span></span>

<span data-ttu-id="359f0-102">Belirli türleri ve bunların türetilmiş türlerini analizden dışlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="359f0-102">You can exclude specific types and their derived types from analysis.</span></span> <span data-ttu-id="359f0-103">Örneğin, kuralın adlandırılmış türler ve türetilmiş türleri içindeki herhangi bir yöntemde çalıştırılmamalıdır `MyType` ve aşağıdaki anahtar-değer çiftini projenizdeki bir *. editorconfig* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="359f0-103">For example, to specify that the rule should not run on any methods within types named `MyType` and their derived types, add the following key-value pair to an *.editorconfig* file in your project:</span></span>

```ini
dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType
```

<span data-ttu-id="359f0-104">Seçenek değerindeki izin verilen sembol adı biçimleri (ile ayrılmış `|` ):</span><span class="sxs-lookup"><span data-stu-id="359f0-104">Allowed symbol name formats in the option value (separated by `|`):</span></span>

- <span data-ttu-id="359f0-105">Yalnızca tür adı (kapsayan tür veya ad alanından bağımsız olarak adı olan tüm türleri içerir)..</span><span class="sxs-lookup"><span data-stu-id="359f0-105">Type name only (includes all types with the name, regardless of the containing type or namespace)..</span></span>
- <span data-ttu-id="359f0-106">Simgenin [belge kimliği biçimindeki](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings), isteğe bağlı ön ek olarak tam adlar `T:` .</span><span class="sxs-lookup"><span data-stu-id="359f0-106">Fully qualified names in the symbol's [documentation ID format](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings), with an optional `T:` prefix.</span></span>

<span data-ttu-id="359f0-107">Örnekler:</span><span class="sxs-lookup"><span data-stu-id="359f0-107">Examples:</span></span>

| <span data-ttu-id="359f0-108">Seçenek değeri</span><span class="sxs-lookup"><span data-stu-id="359f0-108">Option Value</span></span> | <span data-ttu-id="359f0-109">Özet</span><span class="sxs-lookup"><span data-stu-id="359f0-109">Summary</span></span> |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType` | <span data-ttu-id="359f0-110">Tüm `MyType` türetilmiş türlerini ve tüm türetilmiş türlerini eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="359f0-110">Matches all types named `MyType` and all of their derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType1|MyType2` | <span data-ttu-id="359f0-111">`MyType1`Ya da `MyType2` ve tüm türetilmiş türleri adlı tüm türleri eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="359f0-111">Matches all types named either `MyType1` or `MyType2` and all of their derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS.MyType` | <span data-ttu-id="359f0-112">`MyType`Verilen tam adı ve tüm türetilmiş türlerini içeren belirli bir türle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="359f0-112">Matches specific type `MyType` with given fully qualified name and all of its derived types.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS1.MyType1|M:NS2.MyType2` | <span data-ttu-id="359f0-113">Belirli türleri `MyType1` ve `MyType2` ilgili tam nitelikli adları ve tüm türetilmiş türlerini eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="359f0-113">Matches specific types `MyType1` and `MyType2` with the respective fully qualified names, and all of their derived types.</span></span> |
