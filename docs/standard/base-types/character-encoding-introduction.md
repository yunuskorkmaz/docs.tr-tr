---
title: :::no-loc(char):::.Net ' te acter kodlamaya giriş
description: :::no-loc(char):::.Net 'te acter kodlama ve kod çözme hakkında bilgi edinin.
ms.date: 03/09/2020
no-loc:
- ':::no-loc(Rune):::'
- ':::no-loc(char):::'
- ':::no-loc(string):::'
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: 572fcd289eea720873d94e7fc71f3b4a030d1d70
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282315"
---
# <a name="character-encoding-in-net"></a><span data-ttu-id="f1c41-103">.NET içinde karakter kodlaması</span><span class="sxs-lookup"><span data-stu-id="f1c41-103">Character encoding in .NET</span></span>

<span data-ttu-id="f1c41-104">Bu makalede :::no-loc(char)::: , .NET tarafından kullanılan kodlama sistemlerine yönelik bir giriş sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f1c41-104">This article provides an introduction to :::no-loc(char):::acter encoding systems that are used by .NET.</span></span> <span data-ttu-id="f1c41-105">Makalesinde,,, <xref:System.String> <xref:System.Char> <xref:System.Text.:::no-loc(Rune):::> ve <xref:System.Globalization.StringInfo> türlerinin Unicode, UTF-16 ve UTF-8 ile nasıl çalıştığı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f1c41-105">The article explains how the <xref:System.String>, <xref:System.Char>, <xref:System.Text.:::no-loc(Rune):::>, and <xref:System.Globalization.StringInfo> types work with Unicode, UTF-16, and UTF-8.</span></span>

<span data-ttu-id="f1c41-106">*:::no-loc(char)::: Acter* terimi, *bir okuyucunun tek bir görüntüleme öğesi olarak beyin bir* genel anlamda burada kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f1c41-106">The term *:::no-loc(char):::acter* is used here in the general sense of *what a reader perceives as a single display element*.</span></span> <span data-ttu-id="f1c41-107">Ortak örnekler, "a", "@" simgesi ve Emoji "" harftir 🐂 .</span><span class="sxs-lookup"><span data-stu-id="f1c41-107">Common examples are the letter "a", the symbol "@", and the emoji "🐂".</span></span> <span data-ttu-id="f1c41-108">Bazı durumlarda :::no-loc(char)::: , [grafem kümelerindeki](#grapheme-clusters) bölümünde açıklandığı gibi, bir acter aslında birden çok bağımsız görüntüleme öğelerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="f1c41-108">Sometimes what looks like one :::no-loc(char):::acter is actually composed of multiple independent display elements, as the section on [grapheme clusters](#grapheme-clusters) explains.</span></span>

## <a name="the-no-locstring-and-no-locchar-types"></a><span data-ttu-id="f1c41-109">:::no-loc(string):::Ve :::no-loc(char)::: türleri</span><span class="sxs-lookup"><span data-stu-id="f1c41-109">The :::no-loc(string)::: and :::no-loc(char)::: types</span></span>

<span data-ttu-id="f1c41-110">Sınıfının bir örneği [:::no-loc(string):::](xref:System.String) bazı metinleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f1c41-110">An instance of the [:::no-loc(string):::](xref:System.String) class represents some text.</span></span> <span data-ttu-id="f1c41-111">`:::no-loc(string):::`, Her biri yapının bir örneği olan 16 bit değerlerden oluşan bir dizidir [:::no-loc(char):::](xref:System.Char) .</span><span class="sxs-lookup"><span data-stu-id="f1c41-111">A `:::no-loc(string):::` is logically a sequence of 16-bit values, each of which is an instance of the [:::no-loc(char):::](xref:System.Char) struct.</span></span> <span data-ttu-id="f1c41-112">[ :::no-loc(string)::: . Length](xref:System.String.Length) özelliği `:::no-loc(char):::` , örnekteki örneklerin sayısını döndürür `:::no-loc(string):::` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-112">The [:::no-loc(string):::.Length](xref:System.String.Length) property returns the number of `:::no-loc(char):::` instances in the `:::no-loc(string):::` instance.</span></span>

<span data-ttu-id="f1c41-113">Aşağıdaki örnek işlev, içindeki tüm örneklerin onaltılı gösterimindeki değerleri yazdırır `:::no-loc(char):::` `:::no-loc(string):::` :</span><span class="sxs-lookup"><span data-stu-id="f1c41-113">The following sample function prints out the values in hexadecimal notation of all the `:::no-loc(char):::` instances in a `:::no-loc(string):::`:</span></span>

<span data-ttu-id="f1c41-114">::: Code Language = "CSharp" Source = "parçacıklar/ :::no-loc(char)::: acter-Encoding-tanıtımı/CSharp/PrintStringChars. cs" id = "SnippetPrintChars":::</span><span class="sxs-lookup"><span data-stu-id="f1c41-114">:::code language="csharp" source="snippets/:::no-loc(char):::acter-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::</span></span>

<span data-ttu-id="f1c41-115">:::no-loc(string):::"Hello" ifadesini bu işleve geçirin ve aşağıdaki çıktıyı alın:</span><span class="sxs-lookup"><span data-stu-id="f1c41-115">Pass the :::no-loc(string)::: "Hello" to this function, and you get the following output:</span></span>

```csharp
PrintChars("Hello");
```

```output
"Hello".Length = 5
s[0] = 'H' ('\u0048')
s[1] = 'e' ('\u0065')
s[2] = 'l' ('\u006c')
s[3] = 'l' ('\u006c')
s[4] = 'o' ('\u006f')
```

<span data-ttu-id="f1c41-116">Her :::no-loc(char)::: bir acter tek bir değer ile temsil edilir `:::no-loc(char):::` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-116">Each :::no-loc(char):::acter is represented by a single `:::no-loc(char):::` value.</span></span> <span data-ttu-id="f1c41-117">Bu kalıp, dünyanın çoğu dili için geçerli bir değer içerir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-117">That pattern holds true for most of the world's languages.</span></span> <span data-ttu-id="f1c41-118">Örneğin, :::no-loc(char)::: *nǐ hǎo* ve " *Hello* " gibi sesli iki Çince acters çıkışı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f1c41-118">For example, here's the output for two Chinese :::no-loc(char):::acters that sound like *nǐ hǎo* and mean *Hello* :</span></span>

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

<span data-ttu-id="f1c41-119">Ancak bazı dillerde ve bazı semboller ve Emoji için `:::no-loc(char):::` tek bir acter temsil eden iki örnek sürer :::no-loc(char)::: .</span><span class="sxs-lookup"><span data-stu-id="f1c41-119">However, for some languages and for some symbols and emoji, it takes two `:::no-loc(char):::` instances to represent a single :::no-loc(char):::acter.</span></span> <span data-ttu-id="f1c41-120">Örneğin, :::no-loc(char)::: sözcük içindeki acters ve `:::no-loc(char):::` örnekleri, Ozu dilinde *Ozu* anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="f1c41-120">For example, compare the :::no-loc(char):::acters and `:::no-loc(char):::` instances in the word that means *Osage* in the Osage language:</span></span>

```csharp
PrintChars("𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟");
```

```output
"𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟".Length = 17
s[0] = '�' ('\ud801')
s[1] = '�' ('\udccf')
s[2] = '�' ('\ud801')
s[3] = '�' ('\udcd8')
s[4] = '�' ('\ud801')
s[5] = '�' ('\udcfb')
s[6] = '�' ('\ud801')
s[7] = '�' ('\udcd8')
s[8] = '�' ('\ud801')
s[9] = '�' ('\udcfb')
s[10] = '�' ('\ud801')
s[11] = '�' ('\udcdf')
s[12] = ' ' ('\u0020')
s[13] = '�' ('\ud801')
s[14] = '�' ('\udcbb')
s[15] = '�' ('\ud801')
s[16] = '�' ('\udcdf')
```

<span data-ttu-id="f1c41-121">Yukarıdaki örnekte, :::no-loc(char)::: boşluk hariç her bir acter iki örnekle temsil edilir `:::no-loc(char):::` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-121">In the preceding example, each :::no-loc(char):::acter except the space is represented by two `:::no-loc(char):::` instances.</span></span>

<span data-ttu-id="f1c41-122">Tek bir Unicode emoji Ayrıca `:::no-loc(char):::` , aşağıdaki örnekte görüldüğü gibi bir Ox emoji gösterildiği gibi iki s tarafından da temsil edilir:</span><span class="sxs-lookup"><span data-stu-id="f1c41-122">A single Unicode emoji is also represented by two `:::no-loc(char):::`s, as seen in the following example showing an ox emoji:</span></span>

```output
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

<span data-ttu-id="f1c41-123">Bu örnekler `:::no-loc(string):::.Length` , örneklerinin sayısını gösteren değerinin, `:::no-loc(char):::` görüntülenen acters sayısını belirtmesinin gerekli olmadığını gösterir :::no-loc(char)::: .</span><span class="sxs-lookup"><span data-stu-id="f1c41-123">These examples show that the value of `:::no-loc(string):::.Length`, which indicates the number of `:::no-loc(char):::` instances, doesn't necessarily indicate the number of displayed :::no-loc(char):::acters.</span></span> <span data-ttu-id="f1c41-124">Tek bir `:::no-loc(char):::` örnek bir acter temsil etmesi gereken değildir :::no-loc(char)::: .</span><span class="sxs-lookup"><span data-stu-id="f1c41-124">A single `:::no-loc(char):::` instance by itself doesn't necessarily represent a :::no-loc(char):::acter.</span></span>

<span data-ttu-id="f1c41-125">`:::no-loc(char):::`Tek bir acter ile eşlenen çiftler :::no-loc(char)::: *vekil çiftleri* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f1c41-125">The `:::no-loc(char):::` pairs that map to a single :::no-loc(char):::acter are called *surrogate pairs*.</span></span> <span data-ttu-id="f1c41-126">Nasıl çalıştığını anlamak için Unicode ve UTF-16 kodlamasını anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-126">To understand how they work, you need to understand Unicode and UTF-16 encoding.</span></span>

## <a name="unicode-code-points"></a><span data-ttu-id="f1c41-127">Unicode kod noktaları</span><span class="sxs-lookup"><span data-stu-id="f1c41-127">Unicode code points</span></span>

<span data-ttu-id="f1c41-128">Unicode, çeşitli platformlarda ve çeşitli diller ve betiklerle kullanım için uluslararası bir kodlama standardıdır.</span><span class="sxs-lookup"><span data-stu-id="f1c41-128">Unicode is an international encoding standard for use on various platforms and with various languages and scripts.</span></span>

<span data-ttu-id="f1c41-129">Unicode standart 1.100.000 ' den fazla [kod noktasını](https://www.unicode.org/glossary/#code_point)tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f1c41-129">The Unicode Standard defines over 1.1 million [code points](https://www.unicode.org/glossary/#code_point).</span></span> <span data-ttu-id="f1c41-130">Kod noktası, 0 ile `U+10FFFF` (ondalık 1.114.111) arasında değişebilir bir tamsayı değeridir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-130">A code point is an integer value that can range from 0 to `U+10FFFF` (decimal 1,114,111).</span></span> <span data-ttu-id="f1c41-131">Bazı kod noktaları harflere, simgelere veya emoji 'ye atanır.</span><span class="sxs-lookup"><span data-stu-id="f1c41-131">Some code points are assigned to letters, symbols, or emoji.</span></span> <span data-ttu-id="f1c41-132">Diğer :::no-loc(char)::: bir deyişle, yeni bir satıra ilerlemek gibi metin veya acters 'nin nasıl görüntülendiğini denetleyen eylemlere atanır.</span><span class="sxs-lookup"><span data-stu-id="f1c41-132">Others are assigned to actions that control how text or :::no-loc(char):::acters are displayed, such as advance to a new line.</span></span> <span data-ttu-id="f1c41-133">Birçok kod noktası henüz atanmadı.</span><span class="sxs-lookup"><span data-stu-id="f1c41-133">Many code points are not yet assigned.</span></span>

<span data-ttu-id="f1c41-134">Aşağıda göründükleri Unicode TS bağlantıları ile kod noktası atamalarının bazı örnekleri verilmiştir :::no-loc(char)::: :</span><span class="sxs-lookup"><span data-stu-id="f1c41-134">Here are some examples of code point assignments, with links to Unicode :::no-loc(char):::ts in which they appear:</span></span>

|<span data-ttu-id="f1c41-135">Ondalık</span><span class="sxs-lookup"><span data-stu-id="f1c41-135">Decimal</span></span>|<span data-ttu-id="f1c41-136">Onaltılık</span><span class="sxs-lookup"><span data-stu-id="f1c41-136">Hex</span></span>       |<span data-ttu-id="f1c41-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1c41-137">Example</span></span>|<span data-ttu-id="f1c41-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1c41-138">Description</span></span>|
|------:|----------|-------|-----------|
|<span data-ttu-id="f1c41-139">10</span><span class="sxs-lookup"><span data-stu-id="f1c41-139">10</span></span>     | `U+000A` |<span data-ttu-id="f1c41-140">Yok</span><span class="sxs-lookup"><span data-stu-id="f1c41-140">N/A</span></span>| <span data-ttu-id="f1c41-141">[SATıR BESLEME](https://www.unicode.org/:::no-loc(char):::ts/PDF/U0000.pdf)</span><span class="sxs-lookup"><span data-stu-id="f1c41-141">[LINE FEED](https://www.unicode.org/:::no-loc(char):::ts/PDF/U0000.pdf)</span></span> |
|<span data-ttu-id="f1c41-142">97</span><span class="sxs-lookup"><span data-stu-id="f1c41-142">97</span></span>     | `U+0061` | <span data-ttu-id="f1c41-143">a</span><span class="sxs-lookup"><span data-stu-id="f1c41-143">a</span></span> | <span data-ttu-id="f1c41-144">[LATIN KÜÇÜK HARF A](https://www.unicode.org/:::no-loc(char):::ts/PDF/U0000.pdf)</span><span class="sxs-lookup"><span data-stu-id="f1c41-144">[LATIN SMALL LETTER A](https://www.unicode.org/:::no-loc(char):::ts/PDF/U0000.pdf)</span></span> |
|<span data-ttu-id="f1c41-145">562</span><span class="sxs-lookup"><span data-stu-id="f1c41-145">562</span></span>    | `U+0232` | <span data-ttu-id="f1c41-146">Ȳ</span><span class="sxs-lookup"><span data-stu-id="f1c41-146">Ȳ</span></span> | <span data-ttu-id="f1c41-147">[LATIN BÜYÜK HARF Y WITH MACRON](https://www.unicode.org/:::no-loc(char):::ts/PDF/U0180.pdf)</span><span class="sxs-lookup"><span data-stu-id="f1c41-147">[LATIN CAPITAL LETTER Y WITH MACRON](https://www.unicode.org/:::no-loc(char):::ts/PDF/U0180.pdf)</span></span> |
|<span data-ttu-id="f1c41-148">68.675</span><span class="sxs-lookup"><span data-stu-id="f1c41-148">68,675</span></span> | `U+10C43`| <span data-ttu-id="f1c41-149">𐱃</span><span class="sxs-lookup"><span data-stu-id="f1c41-149">𐱃</span></span> | <span data-ttu-id="f1c41-150">[ESKI TÜRKIC LETTER ORKHON](https://www.unicode.org/:::no-loc(char):::ts/PDF/U10C00.pdf)</span><span class="sxs-lookup"><span data-stu-id="f1c41-150">[OLD TURKIC LETTER ORKHON AT](https://www.unicode.org/:::no-loc(char):::ts/PDF/U10C00.pdf)</span></span> |
|<span data-ttu-id="f1c41-151">127.801</span><span class="sxs-lookup"><span data-stu-id="f1c41-151">127,801</span></span>| `U+1F339`| <span data-ttu-id="f1c41-152">🌹</span><span class="sxs-lookup"><span data-stu-id="f1c41-152">🌹</span></span> | <span data-ttu-id="f1c41-153">[GÜL emoji](https://www.unicode.org/:::no-loc(char):::ts/PDF/U1F300.pdf)</span><span class="sxs-lookup"><span data-stu-id="f1c41-153">[ROSE emoji](https://www.unicode.org/:::no-loc(char):::ts/PDF/U1F300.pdf)</span></span> |

<span data-ttu-id="f1c41-154">Kod noktaları, sözdizimi kullanılarak geleneksel adlandırılır `U+xxxx` ; burada `xxxx` onaltılık kodlanmış tamsayı değeridir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-154">Code points are customarily referred to by using the syntax `U+xxxx`, where `xxxx` is the hex-encoded integer value.</span></span>

<span data-ttu-id="f1c41-155">Kod noktalarının tam aralığı içinde iki alt Aralık vardır:</span><span class="sxs-lookup"><span data-stu-id="f1c41-155">Within the full range of code points there are two subranges:</span></span>

* <span data-ttu-id="f1c41-156">Aralıktaki **temel çok dilli düzlem (BMP)** `U+0000..U+FFFF` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-156">The **Basic Multilingual Plane (BMP)** in the range `U+0000..U+FFFF`.</span></span> <span data-ttu-id="f1c41-157">Bu 16 bit Aralık, dünyanın yazma sistemlerinin çoğunluğunu kapsayacak kadar 65.536 kod noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1c41-157">This 16-bit range provides 65,536 code points, enough to cover the majority of the world's writing systems.</span></span>
* <span data-ttu-id="f1c41-158">Aralıktaki **tamamlayıcı kod noktaları** `U+10000..U+10FFFF` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-158">**Supplementary code points** in the range `U+10000..U+10FFFF`.</span></span> <span data-ttu-id="f1c41-159">Bu 21 bitlik Aralık, daha az bilinen diller ve emojıs gibi diğer amaçlar için kullanılabilen bir milyon ek kod noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1c41-159">This 21-bit range provides more than a million additional code points that can be used for less well-known languages and other purposes such as emojis.</span></span>

<span data-ttu-id="f1c41-160">Aşağıdaki diyagramda, BMP ve ek kod noktaları arasındaki ilişki gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-160">The following diagram illustrates the relationship between the BMP and the supplementary code points.</span></span>

:::image type="content" source="media/:::No-Loc (Char)::: acter-Encoding-introduction/BMP-and-Supplementary. SVG "alt-text =" BMP ve ek kod noktaları ":::

## <a name="utf-16-code-units"></a><span data-ttu-id="f1c41-162">UTF-16 kod birimleri</span><span class="sxs-lookup"><span data-stu-id="f1c41-162">UTF-16 code units</span></span>

<span data-ttu-id="f1c41-163">16 bit Unicode dönüştürme biçimi ( [UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)), :::no-loc(char)::: Unicode kod noktalarını temsil etmek için 16 bit *kod birimi* kullanan bir acter kodlama sistemidir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-163">16-bit Unicode Transformation Format ( [UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) is a :::no-loc(char):::acter encoding system that uses 16-bit *code units* to represent Unicode code points.</span></span> <span data-ttu-id="f1c41-164">.NET, içindeki metni kodlamak için UTF-16 kullanır `:::no-loc(string):::` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-164">.NET uses UTF-16 to encode the text in a `:::no-loc(string):::`.</span></span> <span data-ttu-id="f1c41-165">`:::no-loc(char):::`Örnek, 16 bit kod birimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f1c41-165">A `:::no-loc(char):::` instance represents a 16-bit code unit.</span></span>

<span data-ttu-id="f1c41-166">Tek bir 16 bit kod birimi, temel çok dilli düzlemin 16 bit aralığında herhangi bir kod noktasını temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-166">A single 16-bit code unit can represent any code point in the 16-bit range of the Basic Multilingual Plane.</span></span> <span data-ttu-id="f1c41-167">Ancak, tamamlayıcı aralıktaki bir kod noktası için iki `:::no-loc(char):::` örnek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-167">But for a code point in the supplementary range, two `:::no-loc(char):::` instances are needed.</span></span>

## <a name="surrogate-pairs"></a><span data-ttu-id="f1c41-168">Vekil çiftleri</span><span class="sxs-lookup"><span data-stu-id="f1c41-168">Surrogate pairs</span></span>

<span data-ttu-id="f1c41-169">2 16 bitlik değerlerin tek 21 bitlik bir değere çevrilmesi, ' den *surrogate code points* `U+D800` `U+DFFF` (Decimal 55.296-57.343), dahil olmak üzere, vekil kod noktaları adlı özel bir Aralık tarafından kolaylaştırılacaktır.</span><span class="sxs-lookup"><span data-stu-id="f1c41-169">The translation of two 16-bit values to a single 21-bit value is facilitated by a special range called the *surrogate code points* , from `U+D800` to `U+DFFF` (decimal 55,296 to 57,343), inclusive.</span></span>

<span data-ttu-id="f1c41-170">Aşağıdaki diyagramda, BMP ve vekil kod noktaları arasındaki ilişki gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-170">The following diagram illustrates the relationship between the BMP and the surrogate code points.</span></span>

:::image type="content" source="media/:::No-Loc (Char)::: acter-Encoding-introduction/BMP-and-Surrogate. SVG "alt-text =" BMP ve vekil kod noktaları ":::

<span data-ttu-id="f1c41-172">Yüksek bir *yedek* kod noktası ( `U+D800..U+DBFF` ) hemen sonrasında *düşük bir yedek* kod noktası () olduğunda `U+DC00..U+DFFF` , Çift, aşağıdaki formül kullanılarak bir ek kod noktası olarak yorumlanır:</span><span class="sxs-lookup"><span data-stu-id="f1c41-172">When a *high surrogate* code point (`U+D800..U+DBFF`) is immediately followed by a *low surrogate* code point (`U+DC00..U+DFFF`), the pair is interpreted as a supplementary code point by using the following formula:</span></span>

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

<span data-ttu-id="f1c41-173">Ondalık gösterimi kullanan aynı formül aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f1c41-173">Here's the same formula using decimal notation:</span></span>

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

<span data-ttu-id="f1c41-174">*Üst* yedek kod noktası, *düşük* bir vekil kod noktasına göre daha yüksek bir sayı değerine sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-174">A *high* surrogate code point doesn't have a higher number value than a *low* surrogate code point.</span></span> <span data-ttu-id="f1c41-175">Yüksek yedek kod noktası, tam 21 bit kod noktası aralığının daha yüksek sıralı 11 bitini hesaplamak için kullanıldığından, "yüksek" olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f1c41-175">The high surrogate code point is called "high" because it's used to calculate the higher-order 11 bits of the full 21-bit code point range.</span></span> <span data-ttu-id="f1c41-176">Düşük yedek kod noktası, alt sıra 10 bitlerini hesaplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f1c41-176">The low surrogate code point is used to calculate the lower-order 10 bits.</span></span>

<span data-ttu-id="f1c41-177">Örneğin, yedek çiftine karşılık gelen gerçek kod noktası `0xD83C` `0xDF39`  aşağıdaki şekilde hesaplanır:</span><span class="sxs-lookup"><span data-stu-id="f1c41-177">For example, the actual code point that corresponds to the surrogate pair `0xD83C` and `0xDF39`  is computed as follows:</span></span>

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

<span data-ttu-id="f1c41-178">Ondalık gösterimi kullanılarak aynı hesaplama aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f1c41-178">Here's the same calculation using decimal notation:</span></span>

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

<span data-ttu-id="f1c41-179">Yukarıdaki örnek, `"\ud83c\udf39"` `U+1F339 ROSE ('🌹')` daha önce bahsedilen kod noktasının UTF-16 kodlaması olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-179">The preceding example demonstrates that `"\ud83c\udf39"` is the UTF-16 encoding of the `U+1F339 ROSE ('🌹')` code point mentioned earlier.</span></span>

## <a name="unicode-scalar-values"></a><span data-ttu-id="f1c41-180">Unicode skaler değerleri</span><span class="sxs-lookup"><span data-stu-id="f1c41-180">Unicode scalar values</span></span>

<span data-ttu-id="f1c41-181">[Unicode skaler değeri](https://www.unicode.org/glossary/#unicode_scalar_value) , yedek kod noktalarından başka tüm kod noktalarına başvurur.</span><span class="sxs-lookup"><span data-stu-id="f1c41-181">The term [Unicode scalar value](https://www.unicode.org/glossary/#unicode_scalar_value) refers to all code points other than the surrogate code points.</span></span> <span data-ttu-id="f1c41-182">Diğer bir deyişle, skaler bir değer, bir :::no-loc(char)::: acter atanmış veya gelecekte bir acter atanabilir olan herhangi bir kod noktasıdır :::no-loc(char)::: .</span><span class="sxs-lookup"><span data-stu-id="f1c41-182">In other words, a scalar value is any code point that is assigned a :::no-loc(char):::acter or can be assigned a :::no-loc(char):::acter in the future.</span></span> <span data-ttu-id="f1c41-183">Burada "character", metin veya acters 'nin nasıl görüntülendiğini denetleyen eylemler gibi şeyler içeren bir kod noktasına atanabilecek her şeyi ifade eder :::no-loc(char)::: .</span><span class="sxs-lookup"><span data-stu-id="f1c41-183">"Character" here refers to anything that can be assigned to a code point, which includes such things as actions that control how text or :::no-loc(char):::acters are displayed.</span></span>

<span data-ttu-id="f1c41-184">Aşağıdaki diyagramda skaler değer kod noktaları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-184">The following diagram illustrates the scalar value code points.</span></span>

:::image type="content" source="media/:::No-Loc (Char)::: acter-Encoding-introduction/scalar-values. SVG "alt-text =" skaler değerler ":::

### <a name="the-no-locrune-type-as-a-scalar-value"></a><span data-ttu-id="f1c41-186">:::no-loc(Rune):::Skalar değer olarak tür</span><span class="sxs-lookup"><span data-stu-id="f1c41-186">The :::no-loc(Rune)::: type as a scalar value</span></span>

<span data-ttu-id="f1c41-187">.NET Core 3,0 ile başlayarak, <xref:System.Text.:::no-loc(Rune):::?displayProperty=fullName> tür bir Unicode skaler değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f1c41-187">Beginning with .NET Core 3.0, the <xref:System.Text.:::no-loc(Rune):::?displayProperty=fullName> type represents a Unicode scalar value.</span></span> <span data-ttu-id="f1c41-188">**`:::no-loc(Rune):::` .NET Core 2. x veya .NET Framework 4. x sürümünde kullanılamaz.**</span><span class="sxs-lookup"><span data-stu-id="f1c41-188">**`:::no-loc(Rune):::` is not available in .NET Core 2.x or .NET Framework 4.x.**</span></span>

<span data-ttu-id="f1c41-189">`:::no-loc(Rune):::`Oluşturucular, sonuçta elde edilen örneğin geçerli bir Unicode skaler değeri olduğunu doğrular, aksi takdirde bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1c41-189">The `:::no-loc(Rune):::` constructors validate that the resulting instance is a valid Unicode scalar value, otherwise they throw an exception.</span></span> <span data-ttu-id="f1c41-190">Aşağıdaki örnek, `:::no-loc(Rune):::` giriş geçerli skaler değerleri temsil ettiğinden örnekleri başarıyla örnekleyen kodu gösterir:</span><span class="sxs-lookup"><span data-stu-id="f1c41-190">The following example shows code that successfully instantiates `:::no-loc(Rune):::` instances because the input represents valid scalar values:</span></span>

<span data-ttu-id="f1c41-191">::: Code Language = "CSharp" Source = "parçacıklar/ :::no-loc(char)::: acter-Encoding-giriş/CSharp/örnek oluştur :::no-loc(Rune)::: s.cs" id = "SnippetValid":::</span><span class="sxs-lookup"><span data-stu-id="f1c41-191">:::code language="csharp" source="snippets/:::no-loc(char):::acter-encoding-introduction/csharp/Instantiate:::no-loc(Rune):::s.cs" id="SnippetValid":::</span></span>

<span data-ttu-id="f1c41-192">Aşağıdaki örnek, bir özel durum oluşturur çünkü kod noktası vekil aralıkta ve bir yedek çiftinin parçası değil:</span><span class="sxs-lookup"><span data-stu-id="f1c41-192">The following example throws an exception because the code point is in the surrogate range and isn't part of a surrogate pair:</span></span>

<span data-ttu-id="f1c41-193">::: Code Language = "CSharp" Source = "parçacıklar/ :::no-loc(char)::: acter-Encoding-giriş/CSharp/örnek oluştur :::no-loc(Rune)::: s.cs" id = "SnippetInvalidSurrogate":::</span><span class="sxs-lookup"><span data-stu-id="f1c41-193">:::code language="csharp" source="snippets/:::no-loc(char):::acter-encoding-introduction/csharp/Instantiate:::no-loc(Rune):::s.cs" id="SnippetInvalidSurrogate":::</span></span>

<span data-ttu-id="f1c41-194">Aşağıdaki örnek bir özel durum oluşturur çünkü kod noktası, tamamlayıcı aralığın ötesinde:</span><span class="sxs-lookup"><span data-stu-id="f1c41-194">The following example throws an exception because the code point is beyond the supplementary range:</span></span>

<span data-ttu-id="f1c41-195">::: Code Language = "CSharp" Source = "parçacıklar/ :::no-loc(char)::: acter-Encoding-giriş/CSharp/örnek oluştur :::no-loc(Rune)::: s.cs" id = "SnippetInvalidHigh":::</span><span class="sxs-lookup"><span data-stu-id="f1c41-195">:::code language="csharp" source="snippets/:::no-loc(char):::acter-encoding-introduction/csharp/Instantiate:::no-loc(Rune):::s.cs" id="SnippetInvalidHigh":::</span></span>

### <a name="no-locrune-usage-example-changing-letter-case"></a><span data-ttu-id="f1c41-196">:::no-loc(Rune)::: Kullanım örneği: harf durumunu değiştirme</span><span class="sxs-lookup"><span data-stu-id="f1c41-196">:::no-loc(Rune)::: usage example: changing letter case</span></span>

<span data-ttu-id="f1c41-197">Bir ' a sahip olan `:::no-loc(char):::` ve bir vekil çiftten ise, skaler bir değer olan bir kod noktasıyla çalıştığını varsayan BIR API `:::no-loc(char):::` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-197">An API that takes a `:::no-loc(char):::` and assumes it is working with a code point that is a scalar value doesn't work correctly if the `:::no-loc(char):::` is from a surrogate pair.</span></span> <span data-ttu-id="f1c41-198">Örneğin, her birinde ' de çağıran aşağıdaki yöntemi göz önünde bulundurun <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> :::no-loc(char)::: :::no-loc(string)::: :</span><span class="sxs-lookup"><span data-stu-id="f1c41-198">For example, consider the following method that calls <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> on each :::no-loc(char)::: in a :::no-loc(string)::::</span></span>

<span data-ttu-id="f1c41-199">::: Code Language = "CSharp" Source = "parçacıklar/ :::no-loc(char)::: acter-Encoding-tanıtımı/CSharp/ConvertToUpper. cs" ID = "SnippetBadExample":::</span><span class="sxs-lookup"><span data-stu-id="f1c41-199">:::code language="csharp" source="snippets/:::no-loc(char):::acter-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::</span></span>

<span data-ttu-id="f1c41-200">`input` :::no-loc(string)::: Küçük harfli Deseret harfini içeriyorsa `er` ( `𐑉` ), bu kod bunu büyük harfe ( `𐐡` ) dönüştürmez.</span><span class="sxs-lookup"><span data-stu-id="f1c41-200">If the `input` :::no-loc(string)::: contains the lowercase Deseret letter `er` (`𐑉`), this code won't convert it to uppercase (`𐐡`).</span></span> <span data-ttu-id="f1c41-201">Kod `:::no-loc(char):::.ToUpperInvariant` , her yedek kod noktasında ayrı olarak çağırır `U+D801` `U+DC49` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-201">The code calls `:::no-loc(char):::.ToUpperInvariant` separately on each surrogate code point, `U+D801` and `U+DC49`.</span></span> <span data-ttu-id="f1c41-202">Ancak `U+D801` kendi kendine küçük harf olarak tanımlamak için yeterli bilgi yok, `:::no-loc(char):::.ToUpperInvariant` Bu nedenle tek başına çıkar.</span><span class="sxs-lookup"><span data-stu-id="f1c41-202">But `U+D801` doesn't have enough information by itself to identify it as a lowercase letter, so `:::no-loc(char):::.ToUpperInvariant` leaves it alone.</span></span> <span data-ttu-id="f1c41-203">`U+DC49`Aynı şekilde işler.</span><span class="sxs-lookup"><span data-stu-id="f1c41-203">And it handles `U+DC49` the same way.</span></span> <span data-ttu-id="f1c41-204">Sonuç, içindeki küçük harfli ' 𐑉 ' `input` :::no-loc(string)::: ' 𐑉 ' değerine dönüştürülmez.</span><span class="sxs-lookup"><span data-stu-id="f1c41-204">The result is that lowercase '𐑉' in the `input` :::no-loc(string)::: doesn't get converted to uppercase '𐐡'.</span></span>

<span data-ttu-id="f1c41-205">Doğru bir şekilde büyük harfe dönüştürmek için iki seçenek vardır :::no-loc(string)::: :</span><span class="sxs-lookup"><span data-stu-id="f1c41-205">Here are two options for correctly converting a :::no-loc(string)::: to uppercase:</span></span>

* <span data-ttu-id="f1c41-206"><xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType>Giriş üzerinde, yineleme yerine çağırın :::no-loc(string)::: `:::no-loc(char):::` `:::no-loc(char):::` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-206">Call <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> on the input :::no-loc(string)::: rather than iterating `:::no-loc(char):::`-by-`:::no-loc(char):::`.</span></span> <span data-ttu-id="f1c41-207">`:::no-loc(string):::.ToUpperInvariant`Yöntemi her bir yedek çiftinin her iki bölümüne erişebilir, bu nedenle tüm Unicode kod noktalarını doğru bir şekilde işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-207">The `:::no-loc(string):::.ToUpperInvariant` method has access to both parts of each surrogate pair, so it can handle all Unicode code points correctly.</span></span>
* <span data-ttu-id="f1c41-208">`:::no-loc(Rune):::` `:::no-loc(char):::` Aşağıdaki örnekte gösterildiği gibi, UNICODE skaler değerlerini örnekler yerine örnekler olarak yineleyin.</span><span class="sxs-lookup"><span data-stu-id="f1c41-208">Iterate through the Unicode scalar values as `:::no-loc(Rune):::` instances instead of `:::no-loc(char):::` instances, as shown in the following example.</span></span> <span data-ttu-id="f1c41-209">`:::no-loc(Rune):::`Örnek geçerli bir Unicode skaler değeri olduğundan, skaler bir değer üzerinde çalışmasını bekleyen API 'lere geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-209">Since a `:::no-loc(Rune):::` instance is a valid Unicode scalar value, it can be passed to APIs that expect to operate on a scalar value.</span></span> <span data-ttu-id="f1c41-210">Örneğin, <xref:System.Text.:::no-loc(Rune):::.ToUpperInvariant%2A?displayProperty=nameWithType> Aşağıdaki örnekte gösterildiği gibi çağırmak doğru sonuçlar verir:</span><span class="sxs-lookup"><span data-stu-id="f1c41-210">For example, calling <xref:System.Text.:::no-loc(Rune):::.ToUpperInvariant%2A?displayProperty=nameWithType> as shown in the following example gives correct results:</span></span>

  <span data-ttu-id="f1c41-211">::: Code Language = "CSharp" Source = "parçacıklar/ :::no-loc(char)::: acter-Encoding-tanıtımı/CSharp/ConvertToUpper. cs" ID = "SnippetGoodExample":::</span><span class="sxs-lookup"><span data-stu-id="f1c41-211">:::code language="csharp" source="snippets/:::no-loc(char):::acter-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::</span></span>

### <a name="other-no-locrune-apis"></a><span data-ttu-id="f1c41-212">Diğer :::no-loc(Rune)::: API 'ler</span><span class="sxs-lookup"><span data-stu-id="f1c41-212">Other :::no-loc(Rune)::: APIs</span></span>

<span data-ttu-id="f1c41-213">`:::no-loc(Rune):::`Tür, API 'lerin çoğunun analoglarından sunar `:::no-loc(char):::` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-213">The `:::no-loc(Rune):::` type exposes analogs of many of the `:::no-loc(char):::` APIs.</span></span> <span data-ttu-id="f1c41-214">Örneğin, aşağıdaki yöntemler tür üzerinde statik API 'Leri yansıtır `:::no-loc(char):::` :</span><span class="sxs-lookup"><span data-stu-id="f1c41-214">For example, the following methods mirror static APIs on the `:::no-loc(char):::` type:</span></span>

* <xref:System.Text.:::no-loc(Rune):::.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.:::no-loc(Rune):::.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.:::no-loc(Rune):::.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.:::no-loc(Rune):::.GetUnicodeCategory%2A?displayProperty=nameWithType>

<span data-ttu-id="f1c41-215">Bir örnekten ham skaler değer almak için `:::no-loc(Rune):::` <xref:System.Text.:::no-loc(Rune):::.Value%2A?displayProperty=nameWithType> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f1c41-215">To get the raw scalar value from a `:::no-loc(Rune):::` instance, use the <xref:System.Text.:::no-loc(Rune):::.Value%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="f1c41-216">Bir örneği bir `:::no-loc(Rune):::` dizi için geri dönüştürmek için `:::no-loc(char):::` <xref:System.Text.:::no-loc(Rune):::.ToString%2A?displayProperty=nameWithType> veya <xref:System.Text.:::no-loc(Rune):::.EncodeToUtf16%2A?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f1c41-216">To convert a `:::no-loc(Rune):::` instance back to a sequence of `:::no-loc(char):::`s, use <xref:System.Text.:::no-loc(Rune):::.ToString%2A?displayProperty=nameWithType> or the <xref:System.Text.:::no-loc(Rune):::.EncodeToUtf16%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="f1c41-217">Herhangi bir Unicode skaler değeri tek `:::no-loc(char):::` veya bir vekil çifti tarafından gösterilebilir olduğundan, herhangi bir `:::no-loc(Rune):::` örnek en fazla 2 örnek tarafından temsil edilebilir `:::no-loc(char):::` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-217">Since any Unicode scalar value is representable by a single `:::no-loc(char):::` or by a surrogate pair, any `:::no-loc(Rune):::` instance can be represented by at most 2 `:::no-loc(char):::` instances.</span></span> <span data-ttu-id="f1c41-218"><xref:System.Text.:::no-loc(Rune):::.Utf16SequenceLength%2A?displayProperty=nameWithType> `:::no-loc(char):::` Bir örneği göstermek için kaç örnek gerektiğini görmek için kullanın `:::no-loc(Rune):::` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-218">Use <xref:System.Text.:::no-loc(Rune):::.Utf16SequenceLength%2A?displayProperty=nameWithType> to see how many `:::no-loc(char):::` instances are required to represent a `:::no-loc(Rune):::` instance.</span></span>

<span data-ttu-id="f1c41-219">.NET türü hakkında daha fazla bilgi için `:::no-loc(Rune):::` bkz. [ `:::no-loc(Rune):::` API başvurusu](xref:System.Text.:::no-loc(Rune):::).</span><span class="sxs-lookup"><span data-stu-id="f1c41-219">For more information about the .NET `:::no-loc(Rune):::` type, see the [`:::no-loc(Rune):::` API reference](xref:System.Text.:::no-loc(Rune):::).</span></span>

## <a name="grapheme-clusters"></a><span data-ttu-id="f1c41-220">Grapheme kümeleri</span><span class="sxs-lookup"><span data-stu-id="f1c41-220">Grapheme clusters</span></span>

<span data-ttu-id="f1c41-221">Bir :::no-loc(char)::: acter, birden çok kod noktasının birleşiminden kaynaklanabilir. bu nedenle, genellikle "acter" yerine kullanılan daha açıklayıcı bir terim, :::no-loc(char)::: [grafem](https://www.unicode.org/glossary/#grapheme_cluster)kümesidir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-221">What looks like one :::no-loc(char):::acter might result from a combination of multiple code points, so a more descriptive term that is often used in place of ":::no-loc(char):::acter" is [grapheme cluster](https://www.unicode.org/glossary/#grapheme_cluster).</span></span> <span data-ttu-id="f1c41-222">.NET 'teki denk terim [metin öğesidir](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span><span class="sxs-lookup"><span data-stu-id="f1c41-222">The equivalent term in .NET is [text element](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span></span>

<span data-ttu-id="f1c41-223">`:::no-loc(string):::`"A", "á", "á" ve "" örneklerini göz önünde bulundurun `👩🏽‍🚒` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-223">Consider the `:::no-loc(string):::` instances "a", "á", "á", and "`👩🏽‍🚒`".</span></span> <span data-ttu-id="f1c41-224">İşletim sisteminiz, Unicode standardı tarafından belirtildiği gibi bunları işlediğinde, bu örneklerin her biri `:::no-loc(string):::` tek bir metin öğesi veya grafem kümesi olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="f1c41-224">If your operating system handles them as specified by the Unicode standard, each of these `:::no-loc(string):::` instances appears as a single text element or grapheme cluster.</span></span> <span data-ttu-id="f1c41-225">Ancak son ikisi birden fazla skaler değer kod noktasıyla temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-225">But the last two are represented by more than one scalar value code point.</span></span>

* <span data-ttu-id="f1c41-226">:::no-loc(string):::"A", bir skaler değerle temsil edilir ve bir örnek içerir `:::no-loc(char):::` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-226">The :::no-loc(string)::: "a" is represented by one scalar value and contains one `:::no-loc(char):::` instance.</span></span>

  * `U+0061 LATIN SMALL LETTER A`

* <span data-ttu-id="f1c41-227">:::no-loc(string):::"Á", bir skaler değerle temsil edilir ve bir örnek içerir `:::no-loc(char):::` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-227">The :::no-loc(string)::: "á" is represented by one scalar value and contains one `:::no-loc(char):::` instance.</span></span>

  * `U+00E1 LATIN SMALL LETTER A WITH ACUTE`

* <span data-ttu-id="f1c41-228">:::no-loc(string):::"Á", "á" ile aynı görünür, ancak iki skaler değerle temsil edilir ve iki örnek içerir `:::no-loc(char):::` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-228">The :::no-loc(string)::: "á" looks the same as "á" but is represented by two scalar values and contains two `:::no-loc(char):::` instances.</span></span>

  * `U+0061 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* <span data-ttu-id="f1c41-229">Son olarak, :::no-loc(string)::: " `👩🏽‍🚒` " dört skaler değer ile temsil edilir ve yedi `:::no-loc(char):::` örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-229">Finally, the :::no-loc(string)::: "`👩🏽‍🚒`" is represented by four scalar values and contains seven `:::no-loc(char):::` instances.</span></span>

  * <span data-ttu-id="f1c41-230">`U+1F469 WOMAN` (tamamlayıcı Aralık, yedek çifti gerektirir)</span><span class="sxs-lookup"><span data-stu-id="f1c41-230">`U+1F469 WOMAN` (supplementary range, requires a surrogate pair)</span></span>
  * <span data-ttu-id="f1c41-231">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (tamamlayıcı Aralık, yedek çifti gerektirir)</span><span class="sxs-lookup"><span data-stu-id="f1c41-231">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (supplementary range, requires a surrogate pair)</span></span>
  * `U+200D ZERO WIDTH JOINER`
  * <span data-ttu-id="f1c41-232">`U+1F692 FIRE ENGINE` (tamamlayıcı Aralık, yedek çifti gerektirir)</span><span class="sxs-lookup"><span data-stu-id="f1c41-232">`U+1F692 FIRE ENGINE` (supplementary range, requires a surrogate pair)</span></span>

<span data-ttu-id="f1c41-233">Önceki örneklerde, örneğin, vurgulu vurgu değiştiricisi veya kaplama tonu değiştiricisi gibi-kod noktası ekranda tek başına bir öğe olarak görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="f1c41-233">In some of the preceding examples - such as the combining accent modifier or the skin tone modifier - the code point does not display as a standalone element on the screen.</span></span> <span data-ttu-id="f1c41-234">Bunun yerine, daha önce gelen bir metin öğesinin görünümünü değiştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f1c41-234">Rather, it serves to modify the appearance of a text element that came before it.</span></span> <span data-ttu-id="f1c41-235">Bu örnekler, tek bir " :::no-loc(char)::: acter," veya "grapheme kümesi" olarak düşündüğimizi oluşturmak için birden çok skalar değer alıp verebileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-235">These examples show that it might take multiple scalar values to make up what we think of as a single ":::no-loc(char):::acter," or "grapheme cluster."</span></span>

<span data-ttu-id="f1c41-236">Bir a 'nın grafem kümelerini numaralandırmak için `:::no-loc(string):::` <xref:System.Globalization.StringInfo> Aşağıdaki örnekte gösterildiği gibi sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="f1c41-236">To enumerate the grapheme clusters of a `:::no-loc(string):::`, use the <xref:System.Globalization.StringInfo> class as shown in the following example.</span></span> <span data-ttu-id="f1c41-237">Swift hakkında bilginiz varsa, .NET `StringInfo` türü [Swift 'ın `:::no-loc(char):::acter` tipine](https://developer.apple.com/documentation/swift/:::no-loc(char):::acter)benzer.</span><span class="sxs-lookup"><span data-stu-id="f1c41-237">If you're familiar with Swift, the .NET `StringInfo` type is conceptually similar to [Swift's `:::no-loc(char):::acter` type](https://developer.apple.com/documentation/swift/:::no-loc(char):::acter).</span></span>

### <a name="example-count-no-locchar-no-locrune-and-text-element-instances"></a><span data-ttu-id="f1c41-238">Örnek: Count :::no-loc(char)::: , :::no-loc(Rune)::: , ve metin öğesi örnekleri</span><span class="sxs-lookup"><span data-stu-id="f1c41-238">Example: count :::no-loc(char):::, :::no-loc(Rune):::, and text element instances</span></span>

<span data-ttu-id="f1c41-239">.NET API 'lerinde, bir grafem kümesine *metin öğesi* denir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-239">In .NET APIs, a grapheme cluster is called a *text element*.</span></span> <span data-ttu-id="f1c41-240">Aşağıdaki yöntem `:::no-loc(char):::` ,, `:::no-loc(Rune):::` ve içindeki metin öğesi örnekleri arasındaki farkları göstermektedir `:::no-loc(string):::` :</span><span class="sxs-lookup"><span data-stu-id="f1c41-240">The following method demonstrates the differences between `:::no-loc(char):::`, `:::no-loc(Rune):::`, and text element instances in a `:::no-loc(string):::`:</span></span>

<span data-ttu-id="f1c41-241">::: Code Language = "CSharp" Source = "parçacıklar/ :::no-loc(char)::: acter-Encoding-tanıtımı/CSharp/CountTextElements. cs" ID = "SnippetCountMethod":::</span><span class="sxs-lookup"><span data-stu-id="f1c41-241">:::code language="csharp" source="snippets/:::no-loc(char):::acter-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::</span></span>

<span data-ttu-id="f1c41-242">::: Code Language = "CSharp" Source = "parçacıklar/ :::no-loc(char)::: acter-Encoding-tanıtımı/CSharp/CountTextElements. cs" ID = "SnippetCallCountMethod":::</span><span class="sxs-lookup"><span data-stu-id="f1c41-242">:::code language="csharp" source="snippets/:::no-loc(char):::acter-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::</span></span>

<span data-ttu-id="f1c41-243">Bu kodu .NET Framework veya .NET Core 3,1 veya önceki sürümlerde çalıştırırsanız, emoji için metin öğesi sayısı gösterilir `4` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-243">If you run this code in .NET Framework or .NET Core 3.1 or earlier, the text element count for the emoji shows `4`.</span></span> <span data-ttu-id="f1c41-244">Bunun nedeni, `StringInfo` .NET 5 ' te düzeltilen sınıftaki bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="f1c41-244">That is due to a bug in the `StringInfo` class that is fixed in .NET 5.</span></span>

### <a name="example-splitting-no-locstring-instances"></a><span data-ttu-id="f1c41-245">Örnek: :::no-loc(string)::: örnekleri bölme</span><span class="sxs-lookup"><span data-stu-id="f1c41-245">Example: splitting :::no-loc(string)::: instances</span></span>

<span data-ttu-id="f1c41-246">Örnekleri bölrken `:::no-loc(string):::` , vekil çiftleri ve grafem kümelerini bölmemeye özen gösterin.</span><span class="sxs-lookup"><span data-stu-id="f1c41-246">When splitting `:::no-loc(string):::` instances, avoid splitting surrogate pairs and grapheme clusters.</span></span> <span data-ttu-id="f1c41-247">Aşağıdaki hatalı kod örneğini göz önünde bulundurun: her 10 acters satır sonu eklemeyi amaçlayan :::no-loc(char)::: :::no-loc(string):::</span><span class="sxs-lookup"><span data-stu-id="f1c41-247">Consider the following example of incorrect code, which intends to insert line breaks every 10 :::no-loc(char):::acters in a :::no-loc(string)::::</span></span>

<span data-ttu-id="f1c41-248">::: Code Language = "CSharp" Source = "parçacıklar/ :::no-loc(char)::: acter-Encoding-tanıtım/CSharp/ınsertnewlines. cs" ID = "SnippetBadExample":::</span><span class="sxs-lookup"><span data-stu-id="f1c41-248">:::code language="csharp" source="snippets/:::no-loc(char):::acter-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::</span></span>

<span data-ttu-id="f1c41-249">Bu kod örnekleri numaralandırdığından `:::no-loc(char):::` , Straddle bir 10 sınır olarak gerçekleşen bir yedek çift `:::no-loc(char):::` bölünecektir ve aralarında bir yeni satır eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-249">Because this code enumerates `:::no-loc(char):::` instances, a surrogate pair that happens to straddle a 10-`:::no-loc(char):::` boundary will be split and a newline injected between them.</span></span> <span data-ttu-id="f1c41-250">Bu ekleme veri bozulması sunarak, vekil kod noktaları yalnızca çiftler olarak anlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="f1c41-250">This insertion introduces data corruption, because surrogate code points are meaningful only as pairs.</span></span>

<span data-ttu-id="f1c41-251">Örnekler `:::no-loc(Rune):::` yerine örnekleri (skaler değerler) numaralandırdıysanız veri bozulması olasılığı ortadan kalkar `:::no-loc(char):::` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-251">The potential for data corruption isn't eliminated if you enumerate `:::no-loc(Rune):::` instances (scalar values) instead of `:::no-loc(char):::` instances.</span></span> <span data-ttu-id="f1c41-252">Bir dizi `:::no-loc(Rune):::` örnek, 10 sınırını izleyen bir grafem kümesi oluşturur `:::no-loc(char):::` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-252">A set of `:::no-loc(Rune):::` instances might make up a grapheme cluster that straddles a 10-`:::no-loc(char):::` boundary.</span></span> <span data-ttu-id="f1c41-253">Grafem kümesi ayarlandıysa, doğru yorumlanamaz.</span><span class="sxs-lookup"><span data-stu-id="f1c41-253">If the grapheme cluster set is split up, it can't be interpreted correctly.</span></span>

<span data-ttu-id="f1c41-254">:::no-loc(string):::Aşağıdaki örnekte olduğu gibi, grafem kümelerini veya metin öğelerini sayarak daha iyi bir yaklaşım vardır:</span><span class="sxs-lookup"><span data-stu-id="f1c41-254">A better approach is to break the :::no-loc(string)::: by counting grapheme clusters, or text elements, as in the following example:</span></span>

<span data-ttu-id="f1c41-255">::: Code Language = "CSharp" Source = "parçacıklar/ :::no-loc(char)::: acter-Encoding-tanıtım/CSharp/ınsertnewlines. cs" ID = "SnippetGoodExample":::</span><span class="sxs-lookup"><span data-stu-id="f1c41-255">:::code language="csharp" source="snippets/:::no-loc(char):::acter-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::</span></span>

<span data-ttu-id="f1c41-256">Ancak daha önce belirtildiği gibi, .NET 5 dışındaki .NET uygulamalarında, `StringInfo` sınıfı bazı grafem kümelerini yanlış işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-256">As noted earlier, however, in implementations of .NET other than .NET 5, the `StringInfo` class might handle some grapheme clusters incorrectly.</span></span>

## <a name="utf-8-and-utf-32"></a><span data-ttu-id="f1c41-257">UTF-8 ve UTF-32</span><span class="sxs-lookup"><span data-stu-id="f1c41-257">UTF-8 and UTF-32</span></span>

<span data-ttu-id="f1c41-258">Önceki bölümlerde, .NET 'in örnekleri kodlamak için kullandığı, UTF-16 ' a odaklanan bölümler vardır `:::no-loc(string):::` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-258">The preceding sections focused on UTF-16 because that's what .NET uses to encode `:::no-loc(string):::` instances.</span></span> <span data-ttu-id="f1c41-259">Unicode- [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) ve [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32)için başka kodlama sistemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="f1c41-259">There are other encoding systems for Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) and [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span></span> <span data-ttu-id="f1c41-260">Bu kodlamalar sırasıyla 8 bit kod birimleri ve 32 bit kod birimleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1c41-260">These encodings use 8-bit code units and 32-bit code units, respectively.</span></span>

<span data-ttu-id="f1c41-261">UTF-16 gibi, UTF-8, bazı Unicode skaler değerleri temsil etmek için birden çok kod birimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-261">Like UTF-16, UTF-8 requires multiple code units to represent some Unicode scalar values.</span></span> <span data-ttu-id="f1c41-262">UTF-32, tek bir 32 bit kod biriminde herhangi bir skaler değeri temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-262">UTF-32 can represent any scalar value in a single 32-bit code unit.</span></span>

<span data-ttu-id="f1c41-263">Bu üç Unicode kodlama sisteminin her birinde aynı Unicode kod noktasının nasıl temsil edileceğini gösteren bazı örnekler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f1c41-263">Here are some examples showing how the same Unicode code point is represented in each of these three Unicode encoding systems:</span></span>

```
Scalar: U+0061 LATIN SMALL LETTER A ('a')
UTF-8 : [ 61 ]           (1x  8-bit code unit  = 8 bits total)
UTF-16: [ 0061 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000061 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+0429 CYRILLIC CAPITAL LETTER SHCHA ('Щ')
UTF-8 : [ D0 A9 ]        (2x  8-bit code units = 16 bits total)
UTF-16: [ 0429 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000429 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+A992 JAVANESE LETTER GA ('ꦒ')
UTF-8 : [ EA A6 92 ]     (3x  8-bit code units = 24 bits total)
UTF-16: [ A992 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 0000A992 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+104CC OSAGE CAPITAL LETTER TSHA ('𐓌')
UTF-8 : [ F0 90 93 8C ]  (4x  8-bit code units = 32 bits total)
UTF-16: [ D801 DCCC ]    (2x 16-bit code units = 32 bits total)
UTF-32: [ 000104CC ]     (1x 32-bit code unit  = 32 bits total)
```

<span data-ttu-id="f1c41-264">Daha önce belirtildiği gibi, bir [vekil çiftin](#surrogate-pairs) tek bir UTF-16 kod birimi kendi kendine daha az anlamlı olur.</span><span class="sxs-lookup"><span data-stu-id="f1c41-264">As noted earlier, a single UTF-16 code unit from a [surrogate pair](#surrogate-pairs) is meaningless by itself.</span></span> <span data-ttu-id="f1c41-265">Aynı şekilde, tek bir UTF-8 kod birimi, skalar bir değeri hesaplamak için kullanılan iki, üç veya dört dizilirse, kendisini anlamlı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-265">In the same way, a single UTF-8 code unit is meaningless by itself if it's in a sequence of two, three, or four used to calculate a scalar value.</span></span>

### <a name="endianness"></a><span data-ttu-id="f1c41-266">Endian</span><span class="sxs-lookup"><span data-stu-id="f1c41-266">Endianness</span></span>

<span data-ttu-id="f1c41-267">.NET ' te, UTF-16 kod birimleri, :::no-loc(string)::: 16 bit tamsayılar (örnekler) dizisi olarak bitişik bellekte depolanır `:::no-loc(char):::` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-267">In .NET, the UTF-16 code units of a :::no-loc(string)::: are stored in contiguous memory as a sequence of 16-bit integers (`:::no-loc(char):::` instances).</span></span> <span data-ttu-id="f1c41-268">Bağımsız kod birimlerinin bitleri geçerli mimarinin [bitimcisine](https://en.wikipedia.org/wiki/Endianness) göre düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-268">The bits of individual code units are laid out according to the [endianness](https://en.wikipedia.org/wiki/Endianness) of the current architecture.</span></span>

<span data-ttu-id="f1c41-269">Küçük endian mimarisinde, :::no-loc(string)::: UTF-16 kod noktalarından oluşan bir tanesi `[ D801 DCCC ]` bayt olarak bellekte düzenlenir `[ 0x01, 0xD8, 0xCC, 0xDC ]` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-269">On a little-endian architecture, the :::no-loc(string)::: consisting of the UTF-16 code points `[ D801 DCCC ]` would be laid out in memory as the bytes `[ 0x01, 0xD8, 0xCC, 0xDC ]`.</span></span> <span data-ttu-id="f1c41-270">Aynı büyüklükte bir mimaride :::no-loc(string)::: , bayt olarak bellekte aynı şekilde düzenlenir `[ 0xD8, 0x01, 0xDC, 0xCC ]` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-270">On a big-endian architecture that same :::no-loc(string)::: would be laid out in memory as the bytes `[ 0xD8, 0x01, 0xDC, 0xCC ]`.</span></span>

<span data-ttu-id="f1c41-271">Birbirleriyle iletişim kuran bilgisayar sistemleri, kablo ile kesişen verilerin gösterimini kabul etmelidir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-271">Computer systems that communicate with each other must agree on the representation of data crossing the wire.</span></span> <span data-ttu-id="f1c41-272">Çoğu ağ protokolü, metin aktarırken bir standart olarak UTF-8 kullanır, kısmen de az endian bir makineyle iletişim kuran büyük endian makinesinden kaynaklanan sorunlardan kaçınmaktır.</span><span class="sxs-lookup"><span data-stu-id="f1c41-272">Most network protocols use UTF-8 as a standard when transmitting text, partly to avoid issues that might result from a big-endian machine communicating with a little-endian machine.</span></span> <span data-ttu-id="f1c41-273">:::no-loc(string):::UTF-8 kod noktalarından oluşan bir işlem, `[ F0 90 93 8C ]` her zaman bitime yönteminden bağımsız olarak bayt olarak temsil edilir `[ 0xF0, 0x90, 0x93, 0x8C ]` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-273">The :::no-loc(string)::: consisting of the UTF-8 code points `[ F0 90 93 8C ]` will always be represented as the bytes `[ 0xF0, 0x90, 0x93, 0x8C ]` regardless of endianness.</span></span>

<span data-ttu-id="f1c41-274">Metin aktarmak için UTF-8 ' i kullanmak için, .NET uygulamaları genellikle aşağıdaki örnek gibi bir kod kullanır:</span><span class="sxs-lookup"><span data-stu-id="f1c41-274">To use UTF-8 for transmitting text, .NET applications often use code like the following example:</span></span>

```csharp
:::no-loc(string)::: :::no-loc(string):::ToWrite = GetString();
byte[] :::no-loc(string):::AsUtf8Bytes = Encoding.UTF8.GetBytes(:::no-loc(string):::ToWrite);
await outputStream.WriteAsync(:::no-loc(string):::AsUtf8Bytes, 0, :::no-loc(string):::AsUtf8Bytes.Length);
```

<span data-ttu-id="f1c41-275">Önceki örnekte, [. UTF8. GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) YÖNTEMI, UTF-16 `:::no-loc(string):::` ' ı bir dizi Unicode skaler değere geri çözer, ardından bu skaler değerleri UTF-8 ' e yeniden kodlar ve sonuç sırasını bir `byte` diziye koyar.</span><span class="sxs-lookup"><span data-stu-id="f1c41-275">In the preceding example, the method [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) decodes the UTF-16 `:::no-loc(string):::` back into a series of Unicode scalar values, then it re-encodes those scalar values into UTF-8 and places the resulting sequence into a `byte` array.</span></span> <span data-ttu-id="f1c41-276">[Encoding. UTF8. GetString](xref:System.Text.UTF8Encoding.GetString%2A) yöntemi, bir UTF-8 `byte` dizisini UTF-16 ' a dönüştürerek ters dönüştürmeyi gerçekleştirir `:::no-loc(string):::` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-276">The method [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) performs the opposite transformation, converting a UTF-8 `byte` array to a UTF-16 `:::no-loc(string):::`.</span></span>

> [!WARNING]
> <span data-ttu-id="f1c41-277">UTF-8 internet 'te ortak olduğundan, ham baytları kablolu olarak okumak ve verileri UTF-8 gibi değerlendirmek mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-277">Since UTF-8 is commonplace on the internet, it may be tempting to read raw bytes from the wire and to treat the data as if it were UTF-8.</span></span> <span data-ttu-id="f1c41-278">Ancak, gerçekten doğru biçimlendirildiğini doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-278">However, you should validate that it is indeed well-formed.</span></span> <span data-ttu-id="f1c41-279">Kötü amaçlı bir istemci, hizmetinize hatalı biçimlendirilmiş UTF-8 gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-279">A malicious client might submit ill-formed UTF-8 to your service.</span></span> <span data-ttu-id="f1c41-280">Doğru biçimlendirilmiş gibi bu veriler üzerinde işlem yaparsanız, uygulamanızda hatalara veya güvenlik delikleri oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-280">If you operate on that data as if it were well-formed, it could cause errors or security holes in your application.</span></span> <span data-ttu-id="f1c41-281">UTF-8 verilerini doğrulamak için, gibi bir yöntemi kullanabilirsiniz `Encoding.UTF8.GetString` . Bu, gelen verileri bir öğesine dönüştürürken doğrulama işlemi gerçekleştirecek `:::no-loc(string):::` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-281">To validate UTF-8 data, you can use a method like `Encoding.UTF8.GetString`, which will perform validation while converting the incoming data to a `:::no-loc(string):::`.</span></span>

### <a name="well-formed-encoding"></a><span data-ttu-id="f1c41-282">İyi biçimlendirilmiş kodlama</span><span class="sxs-lookup"><span data-stu-id="f1c41-282">Well-formed encoding</span></span>

<span data-ttu-id="f1c41-283">İyi biçimlendirilmiş bir Unicode kodlaması, belirsiz bir :::no-loc(string)::: şekilde çözülemeyen ve bir Unicode skaler değerler dizisine hatasız bir şekilde kodu oluşturulan kod birimleridir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-283">A well-formed Unicode encoding is a :::no-loc(string)::: of code units that can be decoded unambiguously and without error into a sequence of Unicode scalar values.</span></span> <span data-ttu-id="f1c41-284">İyi biçimlendirilmiş veriler UTF-8, UTF-16 ve UTF-32 arasında serbestçe dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-284">Well-formed data can be transcoded freely back and forth between UTF-8, UTF-16, and UTF-32.</span></span>

<span data-ttu-id="f1c41-285">Bir kodlama sırasının doğru biçimlendirilmiş olup olmadığı ve bir makinenin mimarisinin BİTİLMESİ ile ilgisi olmadığı hakkında soru.</span><span class="sxs-lookup"><span data-stu-id="f1c41-285">The question of whether an encoding sequence is well-formed or not is unrelated to the endianness of a machine's architecture.</span></span> <span data-ttu-id="f1c41-286">Hatalı biçimlendirilmiş bir UTF-8 sırası, büyük endian ve az endian makinelerde aynı şekilde hatalı biçimlendirilmiş bir dizelerdir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-286">An ill-formed UTF-8 sequence is ill-formed in the same way on both big-endian and little-endian machines.</span></span>

<span data-ttu-id="f1c41-287">Hatalı biçimlendirilmiş kodlamalar örnekleri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f1c41-287">Here are some examples of ill-formed encodings:</span></span>

* <span data-ttu-id="f1c41-288">UTF-8 ' de, `[ 6C C2 61 ]` izleyen sıra hatalı biçimlendirilmiş `C2` `61` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-288">In UTF-8, the sequence `[ 6C C2 61 ]` is ill-formed because `C2` cannot be followed by `61`.</span></span>

* <span data-ttu-id="f1c41-289">UTF-16 ' da, dizi `[ DC00 DD00 ]` (veya C# ' ta :::no-loc(string)::: `"\udc00\udd00"` ) hatalı biçimlendirilmiş olduğundan düşük vekil `DC00` başka bir düşük yedek tarafından izlenemiyor `DD00` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-289">In UTF-16, the sequence `[ DC00 DD00 ]` (or, in C#, the :::no-loc(string)::: `"\udc00\udd00"`) is ill-formed because the low surrogate `DC00` cannot be followed by another low surrogate `DD00`.</span></span>

* <span data-ttu-id="f1c41-290">UTF-32 ' de, dizi, `[ 0011ABCD ]` `0011ABCD` Unicode skaler değerler aralığının dışında olduğundan, sıra hatalı biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="f1c41-290">In UTF-32, the sequence `[ 0011ABCD ]` is ill-formed because `0011ABCD` is outside the range of Unicode scalar values.</span></span>

<span data-ttu-id="f1c41-291">.NET sürümünde `:::no-loc(string):::` örnekler neredeyse her zaman iyi BIÇIMLENDIRILMIŞ UTF-16 verileri içerir, ancak bu garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="f1c41-291">In .NET, `:::no-loc(string):::` instances almost always contain well-formed UTF-16 data, but that isn't guaranteed.</span></span> <span data-ttu-id="f1c41-292">Aşağıdaki örneklerde, örneklerde hatalı biçimlendirilmiş UTF-16 verileri oluşturan geçerli C# kodu gösterilmektedir `:::no-loc(string):::` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-292">The following examples show valid C# code that creates ill-formed UTF-16 data in `:::no-loc(string):::` instances.</span></span>

* <span data-ttu-id="f1c41-293">Hatalı biçimlendirilmiş değişmez değer:</span><span class="sxs-lookup"><span data-stu-id="f1c41-293">An ill-formed literal:</span></span>

  ```csharp
  const :::no-loc(string)::: s = "\ud800";
  ```

* <span data-ttu-id="f1c41-294">:::no-loc(string):::Bir vekil çifti ayıran Sub:</span><span class="sxs-lookup"><span data-stu-id="f1c41-294">A sub:::no-loc(string)::: that splits up a surrogate pair:</span></span>

  ```csharp
  :::no-loc(string)::: x = "\ud83e\udd70"; // "🥰"
  :::no-loc(string)::: y = x.Sub:::no-loc(string):::(1, 1); // "\udd70" standalone low surrogate
  ```

<span data-ttu-id="f1c41-295">Hiçbir şekilde [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) hatalı oluşturulmuş örnekler döndürmeyen API 'ler `:::no-loc(string):::` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-295">APIs like [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) never return ill-formed `:::no-loc(string):::` instances.</span></span> <span data-ttu-id="f1c41-296">`Encoding.GetString` ve `Encoding.GetBytes` yöntemleri, girişte hatalı biçimlendirilmiş dizileri tespit ediyor ve çıkış oluştururken :::no-loc(char)::: acter değiştirme işlemi gerçekleştirmiyor.</span><span class="sxs-lookup"><span data-stu-id="f1c41-296">`Encoding.GetString` and `Encoding.GetBytes` methods detect ill-formed sequences in the input and perform :::no-loc(char):::acter substitution when generating the output.</span></span> <span data-ttu-id="f1c41-297">Örneğin, [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) GIRIŞTE ASCII olmayan bir bayt görürseniz (U + 0000.. U + 007F aralığı dışında), döndürülen örneğe bir '? ' ekler `:::no-loc(string):::` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-297">For example, if [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) sees a non-ASCII byte in the input (outside the range U+0000..U+007F), it inserts a '?' into the returned `:::no-loc(string):::` instance.</span></span> <span data-ttu-id="f1c41-298">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) Hatalı biçimlendirilmiş UTF-8 dizilerini `U+FFFD REPLACEMENT CHARACTER ('�')` döndürülen örnekteki ile değiştirir `:::no-loc(string):::` .</span><span class="sxs-lookup"><span data-stu-id="f1c41-298">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) replaces ill-formed UTF-8 sequences with `U+FFFD REPLACEMENT CHARACTER ('�')` in the returned `:::no-loc(string):::` instance.</span></span> <span data-ttu-id="f1c41-299">Daha fazla bilgi için bkz. [Unicode standart](https://www.unicode.org/versions/latest/), Bölüm 5,22 ve 3,9.</span><span class="sxs-lookup"><span data-stu-id="f1c41-299">For more information, see [the Unicode Standard](https://www.unicode.org/versions/latest/), Sections 5.22 and 3.9.</span></span>

<span data-ttu-id="f1c41-300">Yerleşik `Encoding` sınıflar, :::no-loc(char)::: Hatalı biçimlendirilmiş diziler görüldüğünde, acter değiştirme yerine özel bir durum oluşturmak için de yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="f1c41-300">The built-in `Encoding` classes can also be configured to throw an exception rather than perform :::no-loc(char):::acter substitution when ill-formed sequences are seen.</span></span> <span data-ttu-id="f1c41-301">Bu yaklaşım, genellikle :::no-loc(char)::: acter değiştirme 'nin kabul edilebilir olabileceği güvenlik duyarlı uygulamalarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f1c41-301">This approach is often used in security-sensitive applications where :::no-loc(char):::acter substitution might not be acceptable.</span></span>

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
:::no-loc(string)::: asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

<span data-ttu-id="f1c41-302">Yerleşik sınıfların nasıl kullanılacağı hakkında daha fazla bilgi için `Encoding` bkz. [ :::no-loc(char)::: .net 'te acter kodlama sınıfları kullanma](:::no-loc(char):::acter-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="f1c41-302">For information about how to use the built-in `Encoding` classes, see [How to use :::no-loc(char):::acter encoding classes in .NET](:::no-loc(char):::acter-encoding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f1c41-303">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1c41-303">See also</span></span>

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.:::no-loc(Rune):::>
- [<span data-ttu-id="f1c41-304">Genelleştirme ve yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="f1c41-304">Globalization and Localization</span></span>](../globalization-localization/index.md)
