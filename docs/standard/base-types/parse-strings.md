---
title: .NET 'teki dize ayrıştırma teknikleri
description: String. Split, normal ifadeler ve String. SUBSTRING dahil olmak üzere bir dizenin parçalarını ayıklamaya yönelik farklı teknikler hakkında bilgi edinin.
ms.date: 10/30/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET], breaking up
ms.openlocfilehash: de979b711a850bbb9ce91e1f1704d40a2f78f363
ms.sourcegitcommit: ffd4d5e824db6c5f0c3521c0e802fd9e8f0edcbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93343365"
---
# <a name="extract-elements-from-a-string"></a><span data-ttu-id="814e8-103">Dizeden öğeleri Ayıkla</span><span class="sxs-lookup"><span data-stu-id="814e8-103">Extract elements from a string</span></span>

<span data-ttu-id="814e8-104">Bu makalede bir dizenin parçalarını ayıklamanıza yönelik bazı farklı teknikler ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="814e8-104">This article covers some different techniques for extracting parts of a string.</span></span>

- <span data-ttu-id="814e8-105">İstediğiniz alt dizeler bilinen bir sınırlandırma karakteriyle (veya karakterler) ayrıldığı sırada [split yöntemini](#stringsplit-method) kullanın.</span><span class="sxs-lookup"><span data-stu-id="814e8-105">Use the [Split method](#stringsplit-method) when the substrings you want are separated by a known delimiting character (or characters).</span></span>
- <span data-ttu-id="814e8-106">[Normal ifadeler](#regular-expressions) , dize sabit bir düzene uygun olduğunda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="814e8-106">[Regular expressions](#regular-expressions) are useful when the string conforms to a fixed pattern.</span></span>
- <span data-ttu-id="814e8-107">Bir dizedeki *Tüm* alt dizeleri ayıklamak Istemediğinizde, [IndexOf ve substring yöntemlerini](#stringindexof-and-stringsubstring-methods) birlikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="814e8-107">Use the [IndexOf and Substring methods](#stringindexof-and-stringsubstring-methods) in conjunction when you don't want to extract *all* of the substrings in a string.</span></span>

## <a name="stringsplit-method"></a><span data-ttu-id="814e8-108">String. Split yöntemi</span><span class="sxs-lookup"><span data-stu-id="814e8-108">String.Split method</span></span>

<span data-ttu-id="814e8-109"><xref:System.String.Split%2A?displayProperty=nameWithType> belirlediğiniz bir veya daha fazla sınırlandırma karakteri temelinde bir dizeyi bir alt dizeler grubuna bölmek için yardımcı olmak üzere çok sayıda aşırı yükleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="814e8-109"><xref:System.String.Split%2A?displayProperty=nameWithType> provides a handful of overloads to help you break up a string into a group of substrings based on one or more delimiting characters that you specify.</span></span> <span data-ttu-id="814e8-110">Son sonuçdaki toplam alt dize sayısını sınırlayabilirsiniz, alt dizelerin boşluk karakterlerini kırpabilir veya boş alt dizeleri dışlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="814e8-110">You can choose to limit the total number of substrings in the final result, trim white-space characters from substrings, or exclude empty substrings.</span></span>

<span data-ttu-id="814e8-111">Aşağıdaki örneklerde üç farklı aşırı yüklemesi gösterilmektedir `String.Split()` .</span><span class="sxs-lookup"><span data-stu-id="814e8-111">The following examples show three different overloads of `String.Split()`.</span></span> <span data-ttu-id="814e8-112">İlk örnek, <xref:System.String.Split(System.Char[])> hiçbir ayırıcı karakter geçirmeden aşırı yüklemeyi çağırır.</span><span class="sxs-lookup"><span data-stu-id="814e8-112">The first example calls the <xref:System.String.Split(System.Char[])> overload without passing any separator characters.</span></span> <span data-ttu-id="814e8-113">Herhangi bir sınırlandırma karakteri belirtmezseniz, `String.Split()` dizeyi ayırmak için boşluk karakterleri olan varsayılan sınırlayıcıları kullanır.</span><span class="sxs-lookup"><span data-stu-id="814e8-113">When you don't specify any delimiting characters, `String.Split()` uses default delimiters, which are white-space characters, to split up the string.</span></span>

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#1)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="1":::

<span data-ttu-id="814e8-114">Gördüğünüz gibi, nokta karakterleri ( `.` ) alt dizelerin iki içine dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="814e8-114">As you can see, the period characters (`.`) are included in two of the substrings.</span></span> <span data-ttu-id="814e8-115">Süre karakterlerini dışlamak istiyorsanız, Period karakterini ek sınırlandırma karakteri olarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="814e8-115">If you want to exclude the period characters, you can add the period character as an additional delimiting character.</span></span> <span data-ttu-id="814e8-116">Sonraki örnekte bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="814e8-116">The next example shows how to do this.</span></span>

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#2)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="2":::

<span data-ttu-id="814e8-117">Dönemler alt dizelerdeki çıktı, ancak artık iki ek boş alt dize eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="814e8-117">The periods are gone from the substrings, but now two extra empty substrings have been included.</span></span> <span data-ttu-id="814e8-118">Bu boş alt dize, sözcük ve onu izleyen nokta arasındaki alt dizeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="814e8-118">These empty substring represent the substring between the word and the period that follows it.</span></span> <span data-ttu-id="814e8-119">Sonuç dizisindeki boş alt dizeleri atlamak için, <xref:System.String.Split(System.Char[],System.StringSplitOptions)> aşırı yüklemeyi çağırabilir ve <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parametresi için belirtebilirsiniz `options` .</span><span class="sxs-lookup"><span data-stu-id="814e8-119">To omit empty substrings from the resulting array, you can call the <xref:System.String.Split(System.Char[],System.StringSplitOptions)> overload and specify <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> for the `options` parameter.</span></span>

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#3)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="3":::

## <a name="regular-expressions"></a><span data-ttu-id="814e8-120">Normal ifadeler</span><span class="sxs-lookup"><span data-stu-id="814e8-120">Regular expressions</span></span>

<span data-ttu-id="814e8-121">Dizeniz sabit bir düzene uyuyorsa, öğelerini ayıklamak ve işlemek için normal bir ifade kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="814e8-121">If your string conforms to a fixed pattern, you can use a regular expression to extract and handle its elements.</span></span> <span data-ttu-id="814e8-122">Örneğin, dizeler " *Number* *Operand* *Number* " biçimini alıyorsa, dizenin öğelerini ayıklamak ve işlemek için [normal bir ifade](regular-expressions.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="814e8-122">For example, if strings take the form " *number* *operand* *number* ", you can use a [regular expression](regular-expressions.md) to extract and handle the string's elements.</span></span> <span data-ttu-id="814e8-123">İşte bir örnek:</span><span class="sxs-lookup"><span data-stu-id="814e8-123">Here's an example:</span></span>

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="1" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="1":::

<span data-ttu-id="814e8-124">Normal ifade deseninin `(\d+)\s+([-+*/])\s+(\d+)` şöyle olduğu tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="814e8-124">The regular expression pattern `(\d+)\s+([-+*/])\s+(\d+)` is defined like this:</span></span>

|<span data-ttu-id="814e8-125">Desen</span><span class="sxs-lookup"><span data-stu-id="814e8-125">Pattern</span></span>|<span data-ttu-id="814e8-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="814e8-126">Description</span></span>|
|-------------|-----------------|
|`(\d+)`|<span data-ttu-id="814e8-127">Bir veya daha fazla ondalık basamağı eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="814e8-127">Match one or more decimal digits.</span></span> <span data-ttu-id="814e8-128">Bu ilk yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="814e8-128">This is the first capturing group.</span></span>|
|`\s+`|<span data-ttu-id="814e8-129">Bir veya daha fazla boşluk karakteri eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="814e8-129">Match one or more white-space characters.</span></span>|
|`([-+*/])`|<span data-ttu-id="814e8-130">Aritmetik işleç işaretiyle Eşleştir (+,-, \*, veya/).</span><span class="sxs-lookup"><span data-stu-id="814e8-130">Match an arithmetic operator sign (+, -, \*, or /).</span></span> <span data-ttu-id="814e8-131">Bu ikinci yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="814e8-131">This is the second capturing group.</span></span>|
|`\s+`|<span data-ttu-id="814e8-132">Bir veya daha fazla boşluk karakteri eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="814e8-132">Match one or more white-space characters.</span></span>|
|`(\d+)`|<span data-ttu-id="814e8-133">Bir veya daha fazla ondalık basamağı eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="814e8-133">Match one or more decimal digits.</span></span> <span data-ttu-id="814e8-134">Bu, üçüncü yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="814e8-134">This is the third capturing group.</span></span>|

<span data-ttu-id="814e8-135">Ayrıca, sabit bir karakter kümesi yerine bir düzene göre bir dizeden alt dizeleri ayıklamak için normal bir ifade kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="814e8-135">You can also use a regular expression to extract substrings from a string based on a pattern rather than a fixed set of characters.</span></span> <span data-ttu-id="814e8-136">Bu koşullardan biri gerçekleştiğinde yaygın bir senaryodur:</span><span class="sxs-lookup"><span data-stu-id="814e8-136">This is a common scenario when either of these conditions occurs:</span></span>

- <span data-ttu-id="814e8-137">Sınırlayıcı karakterlerden biri veya birkaçı *her zaman* örnekteki sınırlayıcı olarak görev yapmaz <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="814e8-137">One or more of the delimiter characters does not *always* serve as a delimiter in the <xref:System.String> instance.</span></span>

- <span data-ttu-id="814e8-138">Sınırlayıcı karakterlerin sırası ve sayısı değişken veya bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="814e8-138">The sequence and number of delimiter characters is variable or unknown.</span></span>

<span data-ttu-id="814e8-139">Örneğin, <xref:System.String.Split%2A> yöntemi aşağıdaki dizeyi ayırmak için kullanılamaz, çünkü `\n` (yeni satır) karakter değişken olduğundan ve her zaman sınırlayıcılar olarak kullanılmazlar.</span><span class="sxs-lookup"><span data-stu-id="814e8-139">For example, the <xref:System.String.Split%2A> method cannot be used to split the following string, because the number of `\n` (newline) characters is variable, and they don't always serve as delimiters.</span></span>

```text
[This is captured\ntext.]\n\n[\n[This is more captured text.]\n]
\n[Some more captured text:\n   Option1\n   Option2][Terse text.]
```

<span data-ttu-id="814e8-140">Aşağıdaki örnekte gösterildiği gibi, normal bir ifade bu dizeyi kolayca bölebilir.</span><span class="sxs-lookup"><span data-stu-id="814e8-140">A regular expression can split this string easily, as the following example shows.</span></span>

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="2" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="2":::

<span data-ttu-id="814e8-141">Normal ifade deseninin `\[([^\[\]]+)\]` şöyle olduğu tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="814e8-141">The regular expression pattern `\[([^\[\]]+)\]` is defined like this:</span></span>

|<span data-ttu-id="814e8-142">Desen</span><span class="sxs-lookup"><span data-stu-id="814e8-142">Pattern</span></span>|<span data-ttu-id="814e8-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="814e8-143">Description</span></span>|
|-------------|-----------------|
|`\[`|<span data-ttu-id="814e8-144">Açma köşeli ayracını eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="814e8-144">Match an opening bracket.</span></span>|
|`([^\[\]]+)`|<span data-ttu-id="814e8-145">Bir veya daha fazla kez açma veya kapatma ayracı olmayan herhangi bir karakterle eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="814e8-145">Match any character that is not an opening or a closing bracket one or more times.</span></span> <span data-ttu-id="814e8-146">Bu ilk yakalama grubudur.</span><span class="sxs-lookup"><span data-stu-id="814e8-146">This is the first capturing group.</span></span>|
|`\]`|<span data-ttu-id="814e8-147">Bir kapanış parantezini eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="814e8-147">Match a closing bracket.</span></span>|

<span data-ttu-id="814e8-148"><xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType>Yöntemi <xref:System.String.Split%2A?displayProperty=nameWithType> , bir dizeyi sabit karakter kümesi yerine normal ifade düzenine göre bölünmeyeceği dışında, ile neredeyse aynıdır.</span><span class="sxs-lookup"><span data-stu-id="814e8-148">The <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method is almost identical to <xref:System.String.Split%2A?displayProperty=nameWithType>, except that it splits a string based on a regular expression pattern instead of a fixed character set.</span></span> <span data-ttu-id="814e8-149">Örneğin, aşağıdaki örnek, <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> çeşitli tire ve diğer karakter birleşimleri ile ayrılmış alt dizeler içeren bir dizeyi ayırmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="814e8-149">For example, the following example uses the <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method to split a string that contains substrings delimited by various combinations of hyphens and other characters.</span></span>

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="3" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="3":::

<span data-ttu-id="814e8-150">Normal ifade deseninin `\s-\s?[+*]?\s?-\s` şöyle olduğu tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="814e8-150">The regular expression pattern `\s-\s?[+*]?\s?-\s` is defined like this:</span></span>

|<span data-ttu-id="814e8-151">Desen</span><span class="sxs-lookup"><span data-stu-id="814e8-151">Pattern</span></span>|<span data-ttu-id="814e8-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="814e8-152">Description</span></span>|
|-------------|-----------------|
|`\s-`|<span data-ttu-id="814e8-153">Bir boşluk karakteri ve ardından bir tire ile eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="814e8-153">Match a white-space character followed by a hyphen.</span></span>|
|`\s?`|<span data-ttu-id="814e8-154">Sıfır veya bir beyaz boşluk karakterini eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="814e8-154">Match zero or one white-space character.</span></span>|
|`[+*]?`|<span data-ttu-id="814e8-155">+ Ya da \* karakterinin sıfır veya bir oluşumunu eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="814e8-155">Match zero or one occurrence of either the + or \* character.</span></span>|
|`\s?`|<span data-ttu-id="814e8-156">Sıfır veya bir beyaz boşluk karakterini eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="814e8-156">Match zero or one white-space character.</span></span>|
|`-\s`|<span data-ttu-id="814e8-157">Bir kısa çizgi karakteri ve ardından boşluk karakteri ile eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="814e8-157">Match a hyphen followed by a white-space character.</span></span>|

## <a name="stringindexof-and-stringsubstring-methods"></a><span data-ttu-id="814e8-158">String. IndexOf ve String. SUBSTRING yöntemleri</span><span class="sxs-lookup"><span data-stu-id="814e8-158">String.IndexOf and String.Substring methods</span></span>

<span data-ttu-id="814e8-159">Bir dizedeki tüm alt dizeleri ilgilenmiyorsanız, eşleşmenin başladığı dizini döndüren dize karşılaştırma yöntemlerinden biriyle çalışmayı tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="814e8-159">If you aren't interested in all of the substrings in a string, you might prefer to work with one of the string comparison methods that returns the index at which the match begins.</span></span> <span data-ttu-id="814e8-160">Daha sonra istediğiniz alt <xref:System.String.Substring%2A> dizeyi ayıklamak için yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="814e8-160">You can then call the <xref:System.String.Substring%2A> method to extract the substring that you want.</span></span> <span data-ttu-id="814e8-161">Dize karşılaştırma yöntemleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="814e8-161">The string comparison methods include:</span></span>

- <span data-ttu-id="814e8-162"><xref:System.String.IndexOf%2A>, bir dize örneğindeki bir karakter veya dizenin ilk oluşumunun sıfır tabanlı dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="814e8-162"><xref:System.String.IndexOf%2A>, which returns the zero-based index of the first occurrence of a character or string in a string instance.</span></span>

- <span data-ttu-id="814e8-163"><xref:System.String.IndexOfAny%2A>, bir karakter dizisindeki herhangi bir karakterin geçerli dize örneğindeki sıfır tabanlı dizini döndürür.</span><span class="sxs-lookup"><span data-stu-id="814e8-163"><xref:System.String.IndexOfAny%2A>, which returns the zero-based index in the current string instance of the first occurrence of any character in a character array.</span></span>

- <span data-ttu-id="814e8-164"><xref:System.String.LastIndexOf%2A>, bir dize örneğindeki bir karakter veya dizenin son oluşumunun sıfır tabanlı dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="814e8-164"><xref:System.String.LastIndexOf%2A>, which returns the zero-based index of the last occurrence of a character or string in a string instance.</span></span>

- <span data-ttu-id="814e8-165"><xref:System.String.LastIndexOfAny%2A>, bir karakter dizisindeki herhangi bir karakterin geçerli dize örneğinde sıfır tabanlı bir dizin döndüren.</span><span class="sxs-lookup"><span data-stu-id="814e8-165"><xref:System.String.LastIndexOfAny%2A>, which returns a zero-based index in the current string instance of the last occurrence of any character in a character array.</span></span>

<span data-ttu-id="814e8-166">Aşağıdaki örnek, <xref:System.String.IndexOf%2A> bir dizedeki dönemleri bulmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="814e8-166">The following example uses the <xref:System.String.IndexOf%2A> method to find the periods in a string.</span></span> <span data-ttu-id="814e8-167">Ardından, <xref:System.String.Substring%2A> tam tümceler döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="814e8-167">It then uses the <xref:System.String.Substring%2A> method to return full sentences.</span></span>

:::code language="csharp" source="snippets/parse-strings/csharp/indexof.cs" id="1" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/indexof.vb" id="1":::

## <a name="see-also"></a><span data-ttu-id="814e8-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="814e8-168">See also</span></span>

- [<span data-ttu-id="814e8-169">.NET 'te temel dize işlemleri</span><span class="sxs-lookup"><span data-stu-id="814e8-169">Basic string operations in .NET</span></span>](basic-string-operations.md)
- [<span data-ttu-id="814e8-170">.NET normal ifadeleri</span><span class="sxs-lookup"><span data-stu-id="814e8-170">.NET regular expressions</span></span>](regular-expressions.md)
- [<span data-ttu-id="814e8-171">C 'de dize. Split kullanarak dizeleri ayrıştırma #</span><span class="sxs-lookup"><span data-stu-id="814e8-171">How to parse strings using String.Split in C#</span></span>](../../csharp/how-to/parse-strings-using-split.md)
