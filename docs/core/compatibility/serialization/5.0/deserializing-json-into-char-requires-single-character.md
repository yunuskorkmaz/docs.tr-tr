---
title: 'Son değişiklik: karakter serisini kaldırma, tek karakterlik dize gerektirir'
description: System.Text.Json 'un, bir Char hedefine seri durumdan çıkarılırken JSON 'da tek char dizesi gerektirdiğini .NET 5 ' teki son değişiklik hakkında bilgi edinin.
ms.date: 12/15/2020
ms.openlocfilehash: e901f8ee7e7521af948a3bcde5cf969640436f7f
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256341"
---
# <a name="systemtextjson-requires-single-char-string-to-deserialize-a-char"></a><span data-ttu-id="5acaf-103">System.Text.Json, bir karakter serisini kaldırmak için tek char dizesi gerektirir</span><span class="sxs-lookup"><span data-stu-id="5acaf-103">System.Text.Json requires single-char string to deserialize a char</span></span>

<span data-ttu-id="5acaf-104">Bir using öğesini başarıyla serisini kaldırmak için <xref:System.Char> <xref:System.Text.Json> JSON dizesinin tek bir karakter içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5acaf-104">To successfully deserialize a <xref:System.Char> using <xref:System.Text.Json>, the JSON string must contain a single character.</span></span>

## <a name="change-description"></a><span data-ttu-id="5acaf-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="5acaf-105">Change description</span></span>

<span data-ttu-id="5acaf-106">Önceki .NET sürümlerinde, JSON 'daki çok dizeli bir `char` `char` özellik veya alana başarıyla seri hale getirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5acaf-106">In previous .NET versions, a multi-`char` string in the JSON is successfully deserialized to a `char` property or field.</span></span> <span data-ttu-id="5acaf-107">`char`Aşağıdaki örnekte olduğu gibi, yalnızca ilk dize kullanılır:</span><span class="sxs-lookup"><span data-stu-id="5acaf-107">Only the first `char` of the string is used, as in the following example:</span></span>

```csharp
// .NET Core 3.0 and 3.1: Returns the first char 'a'.
// .NET 5 and later: Throws JsonException because payload has more than one char.
char deserializedChar = JsonSerializer.Deserialize<char>("\"abc\"");
```

<span data-ttu-id="5acaf-108">.NET 5 ve üzeri sürümlerde, tek dize dışında bir şey, `char` <xref:System.Text.Json.JsonException> seri durumdan çıkarma hedefi bir olduğunda oluşturulmasına neden olur `char` .</span><span class="sxs-lookup"><span data-stu-id="5acaf-108">In .NET 5 and later, anything other than a single-`char` string causes a <xref:System.Text.Json.JsonException> to be thrown when the deserialization target is a `char`.</span></span> <span data-ttu-id="5acaf-109">Aşağıdaki örnek dize tüm .NET sürümlerinde başarıyla seri durumdan çıkarılacak:</span><span class="sxs-lookup"><span data-stu-id="5acaf-109">The following example string is successfully deserialized in all .NET versions:</span></span>

```csharp
// Correct usage.
char deserializedChar = JsonSerializer.Deserialize<char>("\"a\"");
```

## <a name="version-introduced"></a><span data-ttu-id="5acaf-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5acaf-110">Version introduced</span></span>

<span data-ttu-id="5acaf-111">5.0</span><span class="sxs-lookup"><span data-stu-id="5acaf-111">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="5acaf-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="5acaf-112">Reason for change</span></span>

<span data-ttu-id="5acaf-113">Seri durumdan çıkarma için ayrıştırma yalnızca, hedef türü için belirtilen yük geçerliyse başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="5acaf-113">Parsing for deserialization should only succeed when the provided payload is valid for the target type.</span></span> <span data-ttu-id="5acaf-114">Bir `char` tür için, yalnızca geçerli yük tek bir `char` dizedir.</span><span class="sxs-lookup"><span data-stu-id="5acaf-114">For a `char` type, the only valid payload is a single-`char` string.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="5acaf-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="5acaf-115">Recommended action</span></span>

<span data-ttu-id="5acaf-116">JSON serisini bir `char` hedefte kaldırdığınızda, dizenin tek dışında bulunduğundan emin olun `char` .</span><span class="sxs-lookup"><span data-stu-id="5acaf-116">When you deserialize JSON into a `char` target, make sure the string consists of a single `char`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="5acaf-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="5acaf-117">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`

### Category

Serialization

-->
