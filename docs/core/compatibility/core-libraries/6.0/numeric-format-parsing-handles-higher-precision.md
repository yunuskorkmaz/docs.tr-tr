---
title: 'Son değişiklik: standart sayısal biçim ayrıştırma duyarlığı'
description: Standart sayısal biçim ayrıştırması artık daha yüksek olan ön ekleri işlediği çekirdek .NET kitaplıklarında .NET 6,0 son değişikliği hakkında bilgi edinin.
ms.date: 02/26/2021
ms.openlocfilehash: ba8829cd720d9c31e6e73b31f95279269162b9b1
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102108737"
---
# <a name="standard-numeric-format-parsing-precision"></a><span data-ttu-id="949e0-103">Standart sayısal biçim ayrıştırma duyarlığı</span><span class="sxs-lookup"><span data-stu-id="949e0-103">Standard numeric format parsing precision</span></span>

<span data-ttu-id="949e0-104">.NET artık, ve kullanarak sayıları dize olarak biçimlendirirken daha büyük duyarlık değerlerini desteklemektedir `ToString` `TryFormat` .</span><span class="sxs-lookup"><span data-stu-id="949e0-104">.NET now supports greater precision values when formatting numbers as strings using `ToString` and `TryFormat`.</span></span>

## <a name="change-description"></a><span data-ttu-id="949e0-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="949e0-105">Change description</span></span>

<span data-ttu-id="949e0-106">Sayıları dize olarak biçimlendirirken, [biçim dizesindeki](../../../../standard/base-types/standard-numeric-format-strings.md) *duyarlık belirleyicisi* , sonuçta elde edilen dizedeki basamak sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="949e0-106">When formatting numbers as strings, the *precision specifier* in the [format string](../../../../standard/base-types/standard-numeric-format-strings.md) represents the number of digits in the resulting string.</span></span> <span data-ttu-id="949e0-107">[Dizenin başındaki karakter](../../../../standard/base-types/standard-numeric-format-strings.md#standard-format-specifiers)olan *Biçim belirticisine* bağlı olarak duyarlık, toplam basamak sayısını, önemli basamak sayısını veya ondalık basamak sayısını temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="949e0-107">Depending on the *format specifier*, which is the [character at the beginning of the string](../../../../standard/base-types/standard-numeric-format-strings.md#standard-format-specifiers), the precision can represent the total number of digits, the number of significant digits, or the number of decimal digits.</span></span>

<span data-ttu-id="949e0-108">Önceki .NET sürümlerinde, standart sayısal biçim ayrıştırma mantığı 99 veya daha az bir duyarlıkla sınırlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="949e0-108">In previous .NET versions, the standard numeric format parsing logic is limited to a precision of 99 or less.</span></span> <span data-ttu-id="949e0-109">Bazı sayısal türler daha fazla duyarlığa sahiptir, ancak `ToString(string format)` doğru bir şekilde kullanıma sunmaz.</span><span class="sxs-lookup"><span data-stu-id="949e0-109">Some numeric types have more precision, but `ToString(string format)` does not expose it correctly.</span></span> <span data-ttu-id="949e0-110">Örneğin, 99 'den büyük bir duyarlık belirtirseniz, `32.ToString("C100")` Biçim dizesi "precision 100 ile para birimi" yerine [özel bir sayısal biçim dizesi](../../../../standard/base-types/custom-numeric-format-strings.md) olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="949e0-110">If you specify a precision greater than 99, for example, `32.ToString("C100")`, the format string is interpreted as a [custom numeric format string](../../../../standard/base-types/custom-numeric-format-strings.md) instead of "currency with precision 100".</span></span> <span data-ttu-id="949e0-111">Özel sayısal biçim dizelerinde, karakterler [karakter sabit değerleri](../../../../standard/base-types/custom-numeric-format-strings.md#character-literals)olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="949e0-111">In custom numeric format strings, characters are interpreted as [character literals](../../../../standard/base-types/custom-numeric-format-strings.md#character-literals).</span></span> <span data-ttu-id="949e0-112">Ayrıca, geçersiz Biçim belirleyicisi içeren bir biçim dizesi duyarlık değerine göre farklı şekilde yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="949e0-112">In addition, a format string that contains an invalid format specifier is interpreted differently depending on the precision value.</span></span> <span data-ttu-id="949e0-113">`H99`<xref:System.FormatException>geçersiz biçim belirticisi için, `H100` özel bir sayısal biçim dizesi olarak yorumlanırken bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="949e0-113">`H99` throws a <xref:System.FormatException> for the invalid format specifier, while `H100` is interpreted as a custom numeric format string.</span></span>

<span data-ttu-id="949e0-114">.Net 6 ' dan başlayarak, .NET, hassasiyetini destekler <xref:System.Int32.MaxValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="949e0-114">Starting in .NET 6, .NET supports precision up to <xref:System.Int32.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="949e0-115">Herhangi bir sayıda basamakla bir biçim belirticisinden oluşan bir biçim dizesi, standart bir sayısal biçim dizesi olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="949e0-115">A format string that consists of a format specifier with any number of digits is interpreted as a standard numeric format string with precision.</span></span> <span data-ttu-id="949e0-116"><xref:System.FormatException>Aşağıdaki koşullardan biri veya her ikisi için bir oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="949e0-116">A <xref:System.FormatException> is thrown for either or both of the following conditions:</span></span>

- <span data-ttu-id="949e0-117">Biçim belirleyicisi karakteri [Standart bir biçim belirticisi](../../../../standard/base-types/standard-numeric-format-strings.md#standard-format-specifiers)değil.</span><span class="sxs-lookup"><span data-stu-id="949e0-117">The format specifier character is not a [standard format specifier](../../../../standard/base-types/standard-numeric-format-strings.md#standard-format-specifiers).</span></span>
- <span data-ttu-id="949e0-118">Duyarlık daha büyüktür <xref:System.Int32.MaxValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="949e0-118">The precision is greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="949e0-119">Bu değişiklik, tüm sayısal türleri etkileyen ayrıştırma mantığı 'nda uygulandı.</span><span class="sxs-lookup"><span data-stu-id="949e0-119">This change was implemented in the parsing logic that affects all numeric types.</span></span>

<span data-ttu-id="949e0-120">Aşağıdaki tabloda, çeşitli biçim dizeleri için davranış değişiklikleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="949e0-120">The following table shows the behavior changes for various format strings.</span></span>

| <span data-ttu-id="949e0-121">Biçimlendirme dizesi</span><span class="sxs-lookup"><span data-stu-id="949e0-121">Format string</span></span> | <span data-ttu-id="949e0-122">Önceki davranış</span><span class="sxs-lookup"><span data-stu-id="949e0-122">Previous behavior</span></span> | <span data-ttu-id="949e0-123">.NET 6 + davranışı</span><span class="sxs-lookup"><span data-stu-id="949e0-123">.NET 6+ behavior</span></span> |
| - | - | - |
| `C2` | <span data-ttu-id="949e0-124">İki ondalık basamaklı para birimini belirtir</span><span class="sxs-lookup"><span data-stu-id="949e0-124">Denotes currency with two decimal digits</span></span> | <span data-ttu-id="949e0-125">İki ondalık basamaklı para birimini belirtir (*değişiklik yok*)</span><span class="sxs-lookup"><span data-stu-id="949e0-125">Denotes currency with two decimal digits (*no change*)</span></span> |
| `C100` | <span data-ttu-id="949e0-126">"C100" yazdıran özel sayısal biçim dizesini belirtir</span><span class="sxs-lookup"><span data-stu-id="949e0-126">Denotes custom numeric format string that prints "C100"</span></span> | <span data-ttu-id="949e0-127">100 ondalık basamak içeren para birimini belirtir</span><span class="sxs-lookup"><span data-stu-id="949e0-127">Denotes currency with 100 decimal digits</span></span> |
| `H99` | <span data-ttu-id="949e0-128"><xref:System.FormatException>Geçersiz Standart Biçim belirleyicisi "H" nedeniyle atar</span><span class="sxs-lookup"><span data-stu-id="949e0-128">Throws <xref:System.FormatException> due to invalid standard format specifier "H"</span></span> | <span data-ttu-id="949e0-129"><xref:System.FormatException>Geçersiz Standart Biçim belirleyicisi "H" (*değişiklik yok*) nedeniyle atar</span><span class="sxs-lookup"><span data-stu-id="949e0-129">Throws <xref:System.FormatException> due to invalid standard format specifier "H" (*no change*)</span></span> |
| `H100` | <span data-ttu-id="949e0-130">Özel sayısal biçim dizesini belirtir</span><span class="sxs-lookup"><span data-stu-id="949e0-130">Denotes custom numeric format string</span></span> | <span data-ttu-id="949e0-131"><xref:System.FormatException>Geçersiz Standart Biçim belirleyicisi "H" nedeniyle atar</span><span class="sxs-lookup"><span data-stu-id="949e0-131">Throws <xref:System.FormatException> due to invalid standard format specifier "H"</span></span> |

## <a name="version-introduced"></a><span data-ttu-id="949e0-132">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="949e0-132">Version introduced</span></span>

<span data-ttu-id="949e0-133">6,0 Preview 2</span><span class="sxs-lookup"><span data-stu-id="949e0-133">6.0 Preview 2</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="949e0-134">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="949e0-134">Reason for change</span></span>

<span data-ttu-id="949e0-135">Bu değişiklik, sayısal biçim ayrıştırma için daha yüksek duyarlık kullanılırken beklenmeyen davranışı düzeltir.</span><span class="sxs-lookup"><span data-stu-id="949e0-135">This change corrects unexpected behavior when using higher precision for numeric format parsing.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="949e0-136">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="949e0-136">Recommended action</span></span>

<span data-ttu-id="949e0-137">Çoğu durumda, hiçbir eylem gerekmez ve sonuçta elde edilen dizelerde doğru duyarlık gösterilir.</span><span class="sxs-lookup"><span data-stu-id="949e0-137">In most cases, no action is necessary and the correct precision will be shown in the resulting strings.</span></span>

<span data-ttu-id="949e0-138">Ancak, duyarlık 99 ' den büyükse, Biçim belirticisinin sabit karakter olarak yorumlanacağı önceki davranışa geri dönmek istiyorsanız, bu karakteri tek tırnak içinde sarın ve ters eğik çizgiyle kaçış yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="949e0-138">However, if you want to revert to the previous behavior where the format specifier is interpreted as a literal character when the precision is greater than 99, you can wrap that character in single quotes or escape it with a backslash.</span></span> <span data-ttu-id="949e0-139">Örneğin, önceki .NET sürümlerinde, `42.ToString("G999")` döndürür `G999` .</span><span class="sxs-lookup"><span data-stu-id="949e0-139">For example, in previous .NET versions, `42.ToString("G999")` returns `G999`.</span></span> <span data-ttu-id="949e0-140">Bu davranışı sürdürmek için, biçim dizesini veya olarak değiştirin `"'G'999"` `"\\G999"` .</span><span class="sxs-lookup"><span data-stu-id="949e0-140">To maintain that behavior, change the format string to `"'G'999"` or `"\\G999"`.</span></span> <span data-ttu-id="949e0-141">Bu işlem .NET Framework, .NET Core ve .NET 5 + ' da çalışır.</span><span class="sxs-lookup"><span data-stu-id="949e0-141">This will work on .NET Framework, .NET Core, and .NET 5+.</span></span>

<span data-ttu-id="949e0-142">Aşağıdaki biçim dizeleri özel sayısal biçim dizeleri olarak yorumlanmasına devam edecektir:</span><span class="sxs-lookup"><span data-stu-id="949e0-142">The following format strings will continue to be interpreted as custom numeric format strings:</span></span>

- <span data-ttu-id="949e0-143">ASCII alfabetik karakteri olmayan herhangi bir karakterle başlayın, örneğin `$` veya `è` .</span><span class="sxs-lookup"><span data-stu-id="949e0-143">Start with any character that is not an ASCII alphabetical character, for example, `$` or `è`.</span></span>
- <span data-ttu-id="949e0-144">Örneğin, bir ASCII basamağına ait olmayan bir ASCII alfabetik karakteriyle başlayın `A$` .</span><span class="sxs-lookup"><span data-stu-id="949e0-144">Start with an ASCII alphabetical character that's not followed by an ASCII digit, for example, `A$`.</span></span>
- <span data-ttu-id="949e0-145">ASCII sayı dizisi ve ardından ASCII basamak karakteri olmayan herhangi bir karakterle (örneğin,) ASCII alfabetik karakteriyle başlayın `A12A` .</span><span class="sxs-lookup"><span data-stu-id="949e0-145">Start with an ASCII alphabetical character, followed by an ASCII digit sequence, and then any character that is not an ASCII digit character, for example, `A12A`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="949e0-146">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="949e0-146">Affected APIs</span></span>

<span data-ttu-id="949e0-147">Bu değişiklik, tüm sayısal türleri etkileyen ayrıştırma mantığı 'nda uygulandı.</span><span class="sxs-lookup"><span data-stu-id="949e0-147">This change was implemented in the parsing logic that affects all numeric types.</span></span>

- <xref:System.Numerics.BigInteger.ToString(System.String)?displayProperty=fullName>
- <xref:System.Numerics.BigInteger.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Numerics.BigInteger.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int32.ToString(System.String)?displayProperty=fullName>
- <xref:System.Int32.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int32.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt32.ToString(System.String)?displayProperty=fullName>
- <xref:System.UInt32.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt32.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Byte.ToString(System.String)?displayProperty=fullName>
- <xref:System.Byte.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Byte.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.SByte.ToString(System.String)?displayProperty=fullName>
- <xref:System.SByte.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.SByte.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int16.ToString(System.String)?displayProperty=fullName>
- <xref:System.Int16.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int16.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt16.ToString(System.String)?displayProperty=fullName>
- <xref:System.UInt16.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt16.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int64.ToString(System.String)?displayProperty=fullName>
- <xref:System.Int64.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int64.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt64.ToString(System.String)?displayProperty=fullName>
- <xref:System.UInt64.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt64.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Half.ToString(System.String)?displayProperty=fullName>
- <xref:System.Half.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Half.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Single.ToString(System.String)?displayProperty=fullName>
- <xref:System.Single.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Single.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Double.ToString(System.String)?displayProperty=fullName>
- <xref:System.Double.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Double.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Decimal.ToString(System.String)?displayProperty=fullName>
- <xref:System.Decimal.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Decimal.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>

## <a name="see-also"></a><span data-ttu-id="949e0-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="949e0-148">See also</span></span>

- [<span data-ttu-id="949e0-149">Standart sayısal biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="949e0-149">Standard numeric format strings</span></span>](../../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="949e0-150">Özel Biçim dizelerinde karakter sabit değerleri</span><span class="sxs-lookup"><span data-stu-id="949e0-150">Character literals in custom format strings</span></span>](../../../../standard/base-types/custom-numeric-format-strings.md#character-literals)

<!--

### Category

Core .NET libraries

### Affected APIs

- `M:System.Numerics.BigInteger.ToString(System.String)`
- `M:System.Numerics.BigInteger.ToString(System.String,System.IFormatProvider)`
- `M:System.Numerics.BigInteger.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Int32.ToString(System.String)`
- `M:System.Int32.ToString(System.String,System.IFormatProvider)`
- `M:System.Int32.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.UInt32.ToString(System.String)`
- `M:System.UInt32.ToString(System.String,System.IFormatProvider)`
- `M:System.UInt32.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Byte.ToString(System.String)`
- `M:System.Byte.ToString(System.String,System.IFormatProvider)`
- `M:System.Byte.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.SByte.ToString(System.String)`
- `M:System.SByte.ToString(System.String,System.IFormatProvider)`
- `M:System.SByte.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Int16.ToString(System.String)`
- `M:System.Int16.ToString(System.String,System.IFormatProvider)`
- `M:System.Int16.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.UInt16.ToString(System.String)`
- `M:System.UInt16.ToString(System.String,System.IFormatProvider)`
- `M:System.UInt16.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Int64.ToString(System.String)`
- `M:System.Int64.ToString(System.String,System.IFormatProvider)`
- `M:System.Int64.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.UInt64.ToString(System.String)`
- `M:System.UInt64.ToString(System.String,System.IFormatProvider)`
- `M:System.UInt64.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Half.ToString(System.String)`
- `M:System.Half.ToString(System.String,System.IFormatProvider)`
- `M:System.Half.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Single.ToString(System.String)`
- `M:System.Single.ToString(System.String,System.IFormatProvider)`
- `M:System.Single.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Double.ToString(System.String)`
- `M:System.Double.ToString(System.String,System.IFormatProvider)`
- `M:System.Double.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Decimal.ToString(System.String)`
- `M:System.Decimal.ToString(System.String,System.IFormatProvider)`
- `M:System.Decimal.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`

-->
