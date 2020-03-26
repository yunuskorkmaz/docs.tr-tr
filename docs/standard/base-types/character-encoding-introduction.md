---
title: .NET'te karakter kodlamasına giriş
description: .NET'te karakter kodlama ve kod çözme hakkında bilgi edinin.
ms.date: 03/09/2020
no-loc:
- Rune
- char
- string
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: 34b1577f8bcea80c1f41b6f9605bf47d132fdb4f
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134428"
---
# <a name="character-encoding-in-net"></a><span data-ttu-id="d143a-103">.NET'te karakter kodlaması</span><span class="sxs-lookup"><span data-stu-id="d143a-103">Character encoding in .NET</span></span>

<span data-ttu-id="d143a-104">Bu makalede, .NET tarafından kullanılan karakter kodlama sistemlerine giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="d143a-104">This article provides an introduction to character encoding systems that are used by .NET.</span></span> <span data-ttu-id="d143a-105">Makalede, <xref:System.Char>Unicode, <xref:System.Text.Rune>UTF-16 ve <xref:System.Globalization.StringInfo> UTF-8 ile nasıl çalıştığı açıklanmaktadır. <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="d143a-105">The article explains how the <xref:System.String>, <xref:System.Char>, <xref:System.Text.Rune>, and <xref:System.Globalization.StringInfo> types work with Unicode, UTF-16, and UTF-8.</span></span>

<span data-ttu-id="d143a-106">*Karakter* terimi *burada, okuyucunun tek bir görüntü öğesi olarak algıladığı*genel anlamda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d143a-106">The term *character* is used here in the general sense of *what a reader perceives as a single display element*.</span></span> <span data-ttu-id="d143a-107">Yaygın örnekler "a", sembol "@" ve emoji🐂" ".</span><span class="sxs-lookup"><span data-stu-id="d143a-107">Common examples are the letter "a", the symbol "@", and the emoji "🐂".</span></span> <span data-ttu-id="d143a-108">Bazen [grafme kümeleri](#grapheme-clusters) üzerindeki bölüm açıklandığı gibi, bir karakter gibi görünen şey aslında birden çok bağımsız görüntü öğesinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="d143a-108">Sometimes what looks like one character is actually composed of multiple independent display elements, as the section on [grapheme clusters](#grapheme-clusters) explains.</span></span>

## <a name="the-string-and-char-types"></a><span data-ttu-id="d143a-109">Dize ve char türleri</span><span class="sxs-lookup"><span data-stu-id="d143a-109">The string and char types</span></span>

<span data-ttu-id="d143a-110">[Dize](xref:System.String) sınıfının bir örneği bazı metni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d143a-110">An instance of the [string](xref:System.String) class represents some text.</span></span> <span data-ttu-id="d143a-111">A `string` mantıksal olarak 16 bitdeğerlerinden oluşan bir dizidir ve bunların her biri [char](xref:System.Char) struct'un bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="d143a-111">A `string` is logically a sequence of 16-bit values, each of which is an instance of the [char](xref:System.Char) struct.</span></span> <span data-ttu-id="d143a-112">[İp. Uzunluk](xref:System.String.Length) `char` `string` özelliği, örnekteki örneklerin sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="d143a-112">The [string.Length](xref:System.String.Length) property returns the number of `char` instances in the `string` instance.</span></span>

<span data-ttu-id="d143a-113">Aşağıdaki örnek işlevi, tüm örneklerin `char` heksadesit gösterimindeki değerleri `string`yazdırır:</span><span class="sxs-lookup"><span data-stu-id="d143a-113">The following sample function prints out the values in hexadecimal notation of all the `char` instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::

<span data-ttu-id="d143a-114">"Merhaba" dizesini bu işleve geçirin ve aşağıdaki çıktıyı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="d143a-114">Pass the string "Hello" to this function, and you get the following output:</span></span>

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

<span data-ttu-id="d143a-115">Her karakter tek `char` bir değerle temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="d143a-115">Each character is represented by a single `char` value.</span></span> <span data-ttu-id="d143a-116">Bu model dünya dillerinin çoğu için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d143a-116">That pattern holds true for most of the world's languages.</span></span> <span data-ttu-id="d143a-117">Örneğin, burada *nů hůo* ve ortalama *Merhaba*gibi ses iki Çince karakter için çıkış' s:</span><span class="sxs-lookup"><span data-stu-id="d143a-117">For example, here's the output for two Chinese characters that sound like *nǐ hǎo* and mean *Hello*:</span></span>

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

<span data-ttu-id="d143a-118">Ancak, bazı diller ve bazı semboller ve `char` emoji için, tek bir karakteri temsil etmek için iki örnek alır.</span><span class="sxs-lookup"><span data-stu-id="d143a-118">However, for some languages and for some symbols and emoji, it takes two `char` instances to represent a single character.</span></span> <span data-ttu-id="d143a-119">Örneğin, Osage dilinde `char` *Osage* anlamına gelen sözcükteki karakterleri ve örnekleri karşılaştırın:</span><span class="sxs-lookup"><span data-stu-id="d143a-119">For example, compare the characters and `char` instances in the word that means *Osage* in the Osage language:</span></span>

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

<span data-ttu-id="d143a-120">Önceki örnekte, boşluk dışındaki her karakter iki `char` örnekle temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="d143a-120">In the preceding example, each character except the space is represented by two `char` instances.</span></span>

<span data-ttu-id="d143a-121">Tek bir Unicode emoji de `char`iki s tarafından temsil edilir, bir öküz emoji gösteren aşağıdaki örnekte görüldüğü gibi:</span><span class="sxs-lookup"><span data-stu-id="d143a-121">A single Unicode emoji is also represented by two `char`s, as seen in the following example showing an ox emoji:</span></span>

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

<span data-ttu-id="d143a-122">Bu örnekler, `string.Length` `char` örnek sayısını gösteren değerin görüntülenen karakter sayısını göstermesi gerekmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d143a-122">These examples show that the value of `string.Length`, which indicates the number of `char` instances, doesn't necessarily indicate the number of displayed characters.</span></span> <span data-ttu-id="d143a-123">Tek `char` bir örnek tek başına mutlaka bir karakteri temsil etmez.</span><span class="sxs-lookup"><span data-stu-id="d143a-123">A single `char` instance by itself doesn't necessarily represent a character.</span></span>

<span data-ttu-id="d143a-124">Tek `char` bir karakterle eşleyen *çiftlere vekil çiftler*denir.</span><span class="sxs-lookup"><span data-stu-id="d143a-124">The `char` pairs that map to a single character are called *surrogate pairs*.</span></span> <span data-ttu-id="d143a-125">Nasıl çalıştıklarını anlamak için Unicode ve UTF-16 kodlamasını anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d143a-125">To understand how they work, you need to understand Unicode and UTF-16 encoding.</span></span>

## <a name="unicode-code-points"></a><span data-ttu-id="d143a-126">Unicode kod noktaları</span><span class="sxs-lookup"><span data-stu-id="d143a-126">Unicode code points</span></span>

<span data-ttu-id="d143a-127">Unicode çeşitli platformlarda ve çeşitli dillerde ve komut dosyaları ile kullanılmak üzere uluslararası bir kodlama standardıdır.</span><span class="sxs-lookup"><span data-stu-id="d143a-127">Unicode is an international encoding standard for use on various platforms and with various languages and scripts.</span></span>

<span data-ttu-id="d143a-128">Unicode Standardı 1,1 milyondan fazla [kod noktası](https://www.unicode.org/glossary/#code_point)tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d143a-128">The Unicode Standard defines over 1.1 million [code points](https://www.unicode.org/glossary/#code_point).</span></span> <span data-ttu-id="d143a-129">Kod noktası, 0 ile `U+10FFFF` (ondalık 1.114.111) arasında değişen bir tamsayı değeridir.</span><span class="sxs-lookup"><span data-stu-id="d143a-129">A code point is an integer value that can range from 0 to `U+10FFFF` (decimal 1,114,111).</span></span> <span data-ttu-id="d143a-130">Bazı kod noktaları harflere, sembollere veya emojilere atanır.</span><span class="sxs-lookup"><span data-stu-id="d143a-130">Some code points are assigned to letters, symbols, or emoji.</span></span> <span data-ttu-id="d143a-131">Diğerleri, yeni bir satıra ilerlemek gibi metin veya karakterlerin nasıl görüntüleneceğini denetleyen eylemlere atanır.</span><span class="sxs-lookup"><span data-stu-id="d143a-131">Others are assigned to actions that control how text or characters are displayed, such as advance to a new line.</span></span> <span data-ttu-id="d143a-132">Birçok kod noktası henüz atanmamış.</span><span class="sxs-lookup"><span data-stu-id="d143a-132">Many code points are not yet assigned.</span></span>

<span data-ttu-id="d143a-133">Aşağıda, göründükleri Unicode grafiklerine bağlantılar içeren kod noktası atamalarına bazı örnekler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d143a-133">Here are some examples of code point assignments, with links to Unicode charts in which they appear:</span></span>

|<span data-ttu-id="d143a-134">Ondalık</span><span class="sxs-lookup"><span data-stu-id="d143a-134">Decimal</span></span>|<span data-ttu-id="d143a-135">Onaltılık</span><span class="sxs-lookup"><span data-stu-id="d143a-135">Hex</span></span>       |<span data-ttu-id="d143a-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="d143a-136">Example</span></span>|<span data-ttu-id="d143a-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d143a-137">Description</span></span>|
|------:|----------|-------|-----------|
|<span data-ttu-id="d143a-138">10</span><span class="sxs-lookup"><span data-stu-id="d143a-138">10</span></span>     | `U+000A` |<span data-ttu-id="d143a-139">Yok</span><span class="sxs-lookup"><span data-stu-id="d143a-139">N/A</span></span>| [<span data-ttu-id="d143a-140">HAT BESLEMESI</span><span class="sxs-lookup"><span data-stu-id="d143a-140">LINE FEED</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="d143a-141">65</span><span class="sxs-lookup"><span data-stu-id="d143a-141">65</span></span>     | `U+0061` | <span data-ttu-id="d143a-142">a</span><span class="sxs-lookup"><span data-stu-id="d143a-142">a</span></span> | [<span data-ttu-id="d143a-143">LATIN KÜÇÜK HARF A</span><span class="sxs-lookup"><span data-stu-id="d143a-143">LATIN SMALL LETTER A</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="d143a-144">562</span><span class="sxs-lookup"><span data-stu-id="d143a-144">562</span></span>    | `U+0232` | <span data-ttu-id="d143a-145">A.B.D</span><span class="sxs-lookup"><span data-stu-id="d143a-145">Ȳ</span></span> | [<span data-ttu-id="d143a-146">MACRON İlE LATIN SERMAYE MEKTUBU Y</span><span class="sxs-lookup"><span data-stu-id="d143a-146">LATIN CAPITAL LETTER Y WITH MACRON</span></span>](https://www.unicode.org/charts/PDF/U0180.pdf) |
|<span data-ttu-id="d143a-147">68,675</span><span class="sxs-lookup"><span data-stu-id="d143a-147">68,675</span></span> | `U+10C43`| <span data-ttu-id="d143a-148">𐱃</span><span class="sxs-lookup"><span data-stu-id="d143a-148">𐱃</span></span> | [<span data-ttu-id="d143a-149">ESKI TÜRK HARFI ORKHON AT</span><span class="sxs-lookup"><span data-stu-id="d143a-149">OLD TURKIC LETTER ORKHON AT</span></span>](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|<span data-ttu-id="d143a-150">127,801</span><span class="sxs-lookup"><span data-stu-id="d143a-150">127,801</span></span>| `U+1F339`| <span data-ttu-id="d143a-151">🌹</span><span class="sxs-lookup"><span data-stu-id="d143a-151">🌹</span></span> | [<span data-ttu-id="d143a-152">GÜL emoji</span><span class="sxs-lookup"><span data-stu-id="d143a-152">ROSE emoji</span></span>](https://www.unicode.org/charts/PDF/U1F300.pdf) |

<span data-ttu-id="d143a-153">Kod noktaları, hex kodlanmış tamsayı `U+xxxx`değerinin `xxxx` bulunduğu sözdizimi kullanılarak özel olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d143a-153">Code points are customarily referred to by using the syntax `U+xxxx`, where `xxxx` is the hex-encoded integer value.</span></span>

<span data-ttu-id="d143a-154">Tüm kod noktaları aralığında iki alt aralık vardır:</span><span class="sxs-lookup"><span data-stu-id="d143a-154">Within the full range of code points there are two subranges:</span></span>

* <span data-ttu-id="d143a-155">**Temel Çok Dilli Düzlem (BMP)** aralığında. `U+0000..U+FFFF`</span><span class="sxs-lookup"><span data-stu-id="d143a-155">The **Basic Multilingual Plane (BMP)** in the range `U+0000..U+FFFF`.</span></span> <span data-ttu-id="d143a-156">Bu 16 bitlik aralık, dünyanın yazı sistemlerinin çoğunu kapsayacak kadar 65.536 kod puanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d143a-156">This 16-bit range provides 65,536 code points, enough to cover the majority of the world's writing systems.</span></span>
* <span data-ttu-id="d143a-157">Aralıktaki `U+10000..U+10FFFF` **tamamlayıcı kod noktaları.**</span><span class="sxs-lookup"><span data-stu-id="d143a-157">**Supplementary code points** in the range `U+10000..U+10FFFF`.</span></span> <span data-ttu-id="d143a-158">Bu 21 bit aralık, daha az bilinen diller ve emojiler gibi diğer amaçlar için kullanılabilecek bir milyondan fazla ek kod noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="d143a-158">This 21-bit range provides more than a million additional code points that can be used for less well-known languages and other purposes such as emojis.</span></span>

<span data-ttu-id="d143a-159">Aşağıdaki diyagram, BMP ve ek kod noktaları arasındaki ilişkiyi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d143a-159">The following diagram illustrates the relationship between the BMP and the supplementary code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP ve ek kod noktaları":::

## <a name="utf-16-code-units"></a><span data-ttu-id="d143a-161">UTF-16 kod birimleri</span><span class="sxs-lookup"><span data-stu-id="d143a-161">UTF-16 code units</span></span>

<span data-ttu-id="d143a-162">16 bit Unicode Dönüşüm Biçimi[(UTF-16),](https://www.unicode.org/faq/utf_bom.html#UTF16)Unicode kod noktalarını temsil etmek için 16 bit *kod birimleri* kullanan bir karakter kodlama sistemidir.</span><span class="sxs-lookup"><span data-stu-id="d143a-162">16-bit Unicode Transformation Format ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) is a character encoding system that uses 16-bit *code units* to represent Unicode code points.</span></span> <span data-ttu-id="d143a-163">.NET, metni kodlamak için UTF-16'yı `string`kullanır.</span><span class="sxs-lookup"><span data-stu-id="d143a-163">.NET uses UTF-16 to encode the text in a `string`.</span></span> <span data-ttu-id="d143a-164">Bir `char` örnek 16 bitkodlu kod birimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d143a-164">A `char` instance represents a 16-bit code unit.</span></span>

<span data-ttu-id="d143a-165">Tek bir 16 bit kod birimi, Temel Çok Dilli Düzlemin 16 bit aralığındaki herhangi bir kod noktasını temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="d143a-165">A single 16-bit code unit can represent any code point in the 16-bit range of the Basic Multilingual Plane.</span></span> <span data-ttu-id="d143a-166">Ancak ek aralıktaki bir kod noktası `char` için iki örnek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d143a-166">But for a code point in the supplementary range, two `char` instances are needed.</span></span>

## <a name="surrogate-pairs"></a><span data-ttu-id="d143a-167">Vekil çiftleri</span><span class="sxs-lookup"><span data-stu-id="d143a-167">Surrogate pairs</span></span>

<span data-ttu-id="d143a-168">İki 16 bit değerin tek bir 21 bit değerine çevrilme, vekil kod noktaları `U+D800` `U+DFFF` olarak adlandırılan özel bir aralıkla (ondalık 55.296 ile 57.343), dahil olmak üzere, (ondalık kod *noktaları)* ile kolaylaştırılır.</span><span class="sxs-lookup"><span data-stu-id="d143a-168">The translation of two 16-bit values to a single 21-bit value is facilitated by a special range called the *surrogate code points*, from `U+D800` to `U+DFFF` (decimal 55,296 to 57,343), inclusive.</span></span>

<span data-ttu-id="d143a-169">Aşağıdaki diyagram, BMP ve vekil kod noktaları arasındaki ilişkiyi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d143a-169">The following diagram illustrates the relationship between the BMP and the surrogate code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="BMP ve vekil kod noktaları":::

<span data-ttu-id="d143a-171">Yüksek *vekil* kod noktası`U+D800..U+DBFF`( ) hemen *düşük* bir`U+DC00..U+DFFF`vekil kod noktası ( ) tarafından takip edildiğinde, çifti aşağıdaki formül kullanılarak tamamlayıcı bir kod noktası olarak yorumlanır:</span><span class="sxs-lookup"><span data-stu-id="d143a-171">When a *high surrogate* code point (`U+D800..U+DBFF`) is immediately followed by a *low surrogate* code point (`U+DC00..U+DFFF`), the pair is interpreted as a supplementary code point by using the following formula:</span></span>

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

<span data-ttu-id="d143a-172">Ondalık gösterimi kullanan aynı formül aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d143a-172">Here's the same formula using decimal notation:</span></span>

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

<span data-ttu-id="d143a-173">*Yüksek* vekil kod noktası, *düşük* bir vekil kod noktasından daha yüksek bir sayı değerine sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="d143a-173">A *high* surrogate code point doesn't have a higher number value than a *low* surrogate code point.</span></span> <span data-ttu-id="d143a-174">Tam 21 bit kod noktası aralığının üst düzey 11 bitini hesaplamak için kullanıldığından, yüksek vekil kod noktası "yüksek" olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d143a-174">The high surrogate code point is called "high" because it's used to calculate the higher-order 11 bits of the full 21-bit code point range.</span></span> <span data-ttu-id="d143a-175">Düşük vekil kod noktası, alt sıra 10 bitini hesaplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d143a-175">The low surrogate code point is used to calculate the lower-order 10 bits.</span></span>

<span data-ttu-id="d143a-176">Örneğin, vekil çifte `0xD83C` karşılık gelen ve `0xDF39` aşağıdaki gibi hesaplanan gerçek kod noktası:</span><span class="sxs-lookup"><span data-stu-id="d143a-176">For example, the actual code point that corresponds to the surrogate pair `0xD83C` and `0xDF39`  is computed as follows:</span></span>

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

<span data-ttu-id="d143a-177">Ondalık gösterimi kullanarak aynı hesaplama aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d143a-177">Here's the same calculation using decimal notation:</span></span>

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

<span data-ttu-id="d143a-178">Yukarıdaki örnek, daha `"\ud83c\udf39"` önce bahsedilen kod noktasının `U+1F339 ROSE ('🌹')` UTF-16 kodlaması olduğunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d143a-178">The preceding example demonstrates that `"\ud83c\udf39"` is the UTF-16 encoding of the `U+1F339 ROSE ('🌹')` code point mentioned earlier.</span></span>

## <a name="unicode-scalar-values"></a><span data-ttu-id="d143a-179">Unicode skaler değerler</span><span class="sxs-lookup"><span data-stu-id="d143a-179">Unicode scalar values</span></span>

<span data-ttu-id="d143a-180">[Unicode skaler değeri](https://www.unicode.org/glossary/#unicode_scalar_value) terimi, vekil kod noktaları dışındaki tüm kod noktalarını ifade eder.</span><span class="sxs-lookup"><span data-stu-id="d143a-180">The term [Unicode scalar value](https://www.unicode.org/glossary/#unicode_scalar_value) refers to all code points other than the surrogate code points.</span></span> <span data-ttu-id="d143a-181">Başka bir deyişle, skaler değer, bir karakter atanan veya gelecekte bir karakter atanabilir herhangi bir kod noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="d143a-181">In other words, a scalar value is any code point that is assigned a character or can be assigned a character in the future.</span></span> <span data-ttu-id="d143a-182">Buradaki "Karakter" kod noktasına atanabilen ve metnin veya karakterlerin nasıl görüntüleneceğini denetleyen eylemler gibi şeyleri içeren herhangi bir şeyi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="d143a-182">"Character" here refers to anything that can be assigned to a code point, which includes such things as actions that control how text or characters are displayed.</span></span>

<span data-ttu-id="d143a-183">Aşağıdaki diyagramskalar değer kodu noktalarını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d143a-183">The following diagram illustrates the scalar value code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="Skaler değerler":::

### <a name="the-opno-locrune-type-as-a-scalar-value"></a><span data-ttu-id="d143a-185">Skaler değer olarak Rune türü</span><span class="sxs-lookup"><span data-stu-id="d143a-185">The Rune type as a scalar value</span></span>

<span data-ttu-id="d143a-186">.NET Core 3.0 ile <xref:System.Text.Rune?displayProperty=fullName> başlayarak, tür Unicode skaler değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d143a-186">Beginning with .NET Core 3.0, the <xref:System.Text.Rune?displayProperty=fullName> type represents a Unicode scalar value.</span></span> <span data-ttu-id="d143a-187">**`Rune`.NET Core 2.x veya .NET Framework 4.x'te kullanılamaz.**</span><span class="sxs-lookup"><span data-stu-id="d143a-187">**`Rune` is not available in .NET Core 2.x or .NET Framework 4.x.**</span></span>

<span data-ttu-id="d143a-188">Kurucular, `Rune` ortaya çıkan örneğin geçerli bir Unicode skaler değer olduğunu doğrular, aksi takdirde bir özel durum atarlar.</span><span class="sxs-lookup"><span data-stu-id="d143a-188">The `Rune` constructors validate that the resulting instance is a valid Unicode scalar value, otherwise they throw an exception.</span></span> <span data-ttu-id="d143a-189">Aşağıdaki örnek, giriş geçerli skaler `Rune` değerleri temsil ettiği için örnekleri başarıyla anında gösteren kodu gösterir:</span><span class="sxs-lookup"><span data-stu-id="d143a-189">The following example shows code that successfully instantiates `Rune` instances because the input represents valid scalar values:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::

<span data-ttu-id="d143a-190">Kod noktası vekil aralığında olduğundan ve bir vekil çiftinin parçası olmadığından aşağıdaki örnek bir özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="d143a-190">The following example throws an exception because the code point is in the surrogate range and isn't part of a surrogate pair:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::

<span data-ttu-id="d143a-191">Kod noktası ek aralığın dışında olduğundan aşağıdaki örnek bir özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="d143a-191">The following example throws an exception because the code point is beyond the supplementary range:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::

### <a name="opno-locrune-usage-example-changing-letter-case"></a>Rune<span data-ttu-id="d143a-192">kullanım örneği: harf örneği değiştirme</span><span class="sxs-lookup"><span data-stu-id="d143a-192"> usage example: changing letter case</span></span>

<span data-ttu-id="d143a-193">Bir api `char` alır ve skaler bir değer bir kod noktası ile çalıştığını varsayar bir `char` API bir vekil çifti ise doğru çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="d143a-193">An API that takes a `char` and assumes it is working with a code point that is a scalar value doesn't work correctly if the `char` is from a surrogate pair.</span></span> <span data-ttu-id="d143a-194">Örneğin, aşağıdaki <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> char yöntemi göz önünde bulundurun stringher biri çağırır:</span><span class="sxs-lookup"><span data-stu-id="d143a-194">For example, consider the following method that calls <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> on each char in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::

<span data-ttu-id="d143a-195">`input` string Küçük Deseret harfi `er` ()`𐑉`içeriyorsa, bu kod onu büyük`𐐡`harfe dönüştürmez ( ).</span><span class="sxs-lookup"><span data-stu-id="d143a-195">If the `input` string contains the lowercase Deseret letter `er` (`𐑉`), this code won't convert it to uppercase (`𐐡`).</span></span> <span data-ttu-id="d143a-196">Kod, `char.ToUpperInvariant` her vekil kod noktasında `U+D801` ayrı `U+DC49`ayrı çağırır ve .</span><span class="sxs-lookup"><span data-stu-id="d143a-196">The code calls `char.ToUpperInvariant` separately on each surrogate code point, `U+D801` and `U+DC49`.</span></span> <span data-ttu-id="d143a-197">Ama `U+D801` tek başına küçük bir mektup olarak tanımlamak için yeterli `char.ToUpperInvariant` bilgiye sahip değil, bu yüzden yalnız bırakır.</span><span class="sxs-lookup"><span data-stu-id="d143a-197">But `U+D801` doesn't have enough information by itself to identify it as a lowercase letter, so `char.ToUpperInvariant` leaves it alone.</span></span> <span data-ttu-id="d143a-198">Ve aynı `U+DC49` şekilde işliyor.</span><span class="sxs-lookup"><span data-stu-id="d143a-198">And it handles `U+DC49` the same way.</span></span> <span data-ttu-id="d143a-199">Sonuç olarak küçük harf ''' `input` string büyük harf ''' dönüştürülür almaz.</span><span class="sxs-lookup"><span data-stu-id="d143a-199">The result is that lowercase '𐑉' in the `input` string doesn't get converted to uppercase '𐐡'.</span></span>

<span data-ttu-id="d143a-200">A'yı büyük string harfe doğru dönüştürmek için iki seçenek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d143a-200">Here are two options for correctly converting a string to uppercase:</span></span>

* <span data-ttu-id="d143a-201">-by-`char`. `char` <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> string</span><span class="sxs-lookup"><span data-stu-id="d143a-201">Call <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> on the input string rather than iterating `char`-by-`char`.</span></span> <span data-ttu-id="d143a-202">Yöntem, `string.ToUpperInvariant` her vekil çiftinin her iki bölümüne de erişebilir, böylece tüm Unicode kod noktalarını doğru şekilde işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="d143a-202">The `string.ToUpperInvariant` method has access to both parts of each surrogate pair, so it can handle all Unicode code points correctly.</span></span>
* <span data-ttu-id="d143a-203">Aşağıdaki örnekte gösterildiği gibi, `Rune` `char` örnek yerine Örnek olarak Unicode skaler değerleri üzerinden yineleyin.</span><span class="sxs-lookup"><span data-stu-id="d143a-203">Iterate through the Unicode scalar values as `Rune` instances instead of `char` instances, as shown in the following example.</span></span> <span data-ttu-id="d143a-204">Bir `Rune` örnek geçerli bir Unicode skaler değer olduğundan, skaler bir değer üzerinde çalışmayı bekleyen API'lere geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d143a-204">Since a `Rune` instance is a valid Unicode scalar value, it can be passed to APIs that expect to operate on a scalar value.</span></span> <span data-ttu-id="d143a-205">Örneğin, aşağıdaki <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> örnekte gösterildiği gibi arama doğru sonuçlar verir:</span><span class="sxs-lookup"><span data-stu-id="d143a-205">For example, calling <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> as shown in the following example gives correct results:</span></span>

  :::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::

### <a name="other-opno-locrune-apis"></a><span data-ttu-id="d143a-206">Diğer Rune API'ler</span><span class="sxs-lookup"><span data-stu-id="d143a-206">Other Rune APIs</span></span>

<span data-ttu-id="d143a-207">Bu `Rune` `char` tür, API'lerin çoğunun analoglarını ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="d143a-207">The `Rune` type exposes analogs of many of the `char` APIs.</span></span> <span data-ttu-id="d143a-208">Örneğin, aşağıdaki yöntemler statik API'leri türe `char` yansıtmaktadır:</span><span class="sxs-lookup"><span data-stu-id="d143a-208">For example, the following methods mirror static APIs on the `char` type:</span></span>

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

<span data-ttu-id="d143a-209">Bir `Rune` örnekten ham skaler değeri elde <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> etmek için özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="d143a-209">To get the raw scalar value from a `Rune` instance, use the <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="d143a-210">Bir `Rune` örneği `char`s, kullanım <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> veya <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> yöntem dizisine dönüştürmek için.</span><span class="sxs-lookup"><span data-stu-id="d143a-210">To convert a `Rune` instance back to a sequence of `char`s, use <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> or the <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="d143a-211">Herhangi bir Unicode skaler değer tek `char` bir veya bir vekil `Rune` çifti tarafından temsil edilebilir `char` olduğundan, herhangi bir örnek en fazla 2 örnek tarafından temsil edilebilir.</span><span class="sxs-lookup"><span data-stu-id="d143a-211">Since any Unicode scalar value is representable by a single `char` or by a surrogate pair, any `Rune` instance can be represented by at most 2 `char` instances.</span></span> <span data-ttu-id="d143a-212">Bir <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> `Rune` örneği temsil `char` etmek için kaç örnek gerektiğini görmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="d143a-212">Use <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> to see how many `char` instances are required to represent a `Rune` instance.</span></span>

<span data-ttu-id="d143a-213">.NET `Rune` türü hakkında daha fazla bilgi için [ `Rune` API başvurusuna](xref:System.Text.Rune)bakın.</span><span class="sxs-lookup"><span data-stu-id="d143a-213">For more information about the .NET `Rune` type, see the [`Rune` API reference](xref:System.Text.Rune).</span></span>

## <a name="grapheme-clusters"></a><span data-ttu-id="d143a-214">Grapheme kümeleri</span><span class="sxs-lookup"><span data-stu-id="d143a-214">Grapheme clusters</span></span>

<span data-ttu-id="d143a-215">Bir karakter gibi görünen şey, birden çok kod noktasının birleşiminden kaynaklanabilir, bu nedenle genellikle "karakter" yerine kullanılan daha açıklayıcı bir terim [grafme kümesidir.](https://www.unicode.org/glossary/#grapheme_cluster)</span><span class="sxs-lookup"><span data-stu-id="d143a-215">What looks like one character might result from a combination of multiple code points, so a more descriptive term that is often used in place of "character" is [grapheme cluster](https://www.unicode.org/glossary/#grapheme_cluster).</span></span> <span data-ttu-id="d143a-216">.NET'teki eşdeğer terim [metin öğesidir.](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A)</span><span class="sxs-lookup"><span data-stu-id="d143a-216">The equivalent term in .NET is [text element](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span></span>

<span data-ttu-id="d143a-217">`string` "a", "á" örneklerini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="d143a-217">Consider the `string` instances "a", "á".</span></span> <span data-ttu-id="d143a-218">"á", ve`👩🏽‍🚒`" ".</span><span class="sxs-lookup"><span data-stu-id="d143a-218">"á", and "`👩🏽‍🚒`".</span></span> <span data-ttu-id="d143a-219">İşletim sisteminiz bunları Unicode standardında belirtildiği şekilde işlerse, bu `string` örneklerin her biri tek bir metin öğesi veya grafi kümesi olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="d143a-219">If your operating system handles them as specified by the Unicode standard, each of these `string` instances appears as a single text element or grapheme cluster.</span></span> <span data-ttu-id="d143a-220">Ancak son ikisi birden fazla skaler değer kodu noktasıyla temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="d143a-220">But the last two are represented by more than one scalar value code point.</span></span>

* <span data-ttu-id="d143a-221">string "A" bir skaler değerle temsil edilir `char` ve bir örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="d143a-221">The string "a" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+0061 LATIN SMALL LETTER A`

* <span data-ttu-id="d143a-222">string "Á" bir skaler değerle temsil edilir `char` ve bir örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="d143a-222">The string "á" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+00E1 LATIN SMALL LETTER E WITH ACUTE`

* <span data-ttu-id="d143a-223">string "Á" "á" ile aynı görünür, ancak iki skaler değerle `char` temsil edilir ve iki örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="d143a-223">The string "á" looks the same as "á" but is represented by two scalar values and contains two `char` instances.</span></span>

  * `U+0065 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* <span data-ttu-id="d143a-224">Son string olarak,`👩🏽‍🚒`" " " dört skaler değerle temsil edilir ve yedi `char` örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="d143a-224">Finally, the string "`👩🏽‍🚒`" is represented by four scalar values and contains seven `char` instances.</span></span>

  * <span data-ttu-id="d143a-225">`U+1F469 WOMAN`(ek aralığı, bir vekil çifti gerektirir)</span><span class="sxs-lookup"><span data-stu-id="d143a-225">`U+1F469 WOMAN` (supplementary range, requires a surrogate pair)</span></span>
  * <span data-ttu-id="d143a-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4`(ek aralığı, bir vekil çifti gerektirir)</span><span class="sxs-lookup"><span data-stu-id="d143a-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (supplementary range, requires a surrogate pair)</span></span>
  * `U+200D ZERO WIDTH JOINER`
  * <span data-ttu-id="d143a-227">`U+1F692 FIRE ENGINE`(ek aralığı, bir vekil çifti gerektirir)</span><span class="sxs-lookup"><span data-stu-id="d143a-227">`U+1F692 FIRE ENGINE` (supplementary range, requires a surrogate pair)</span></span>

<span data-ttu-id="d143a-228">Önceki örneklerin bazılarında - vurgu değiştirici veya cilt tonu değiştirici birleştirme gibi - kod noktası ekranda bağımsız bir öğe olarak görüntülenmiyor.</span><span class="sxs-lookup"><span data-stu-id="d143a-228">In some of the preceding examples - such as the combining accent modifier or the skin tone modifier - the code point does not display as a standalone element on the screen.</span></span> <span data-ttu-id="d143a-229">Bunun yerine, ondan önce gelen bir metin öğesigörünümünü değiştirmek için hizmet vermektedir.</span><span class="sxs-lookup"><span data-stu-id="d143a-229">Rather, it serves to modify the appearance of a text element that came before it.</span></span> <span data-ttu-id="d143a-230">Bu örnekler, tek bir "karakter" veya "grafeme kümesi" olarak düşündüğümüz şeyi uydurmak için birden çok skaler değer gerektirebileceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d143a-230">These examples show that it might take multiple scalar values to make up what we think of as a single "character," or "grapheme cluster."</span></span>

<span data-ttu-id="d143a-231">Bir `string`grapheme kümelerini sıralamak için aşağıdaki <xref:System.Globalization.StringInfo> örnekte gösterildiği gibi sınıfı kullanın.</span><span class="sxs-lookup"><span data-stu-id="d143a-231">To enumerate the grapheme clusters of a `string`, use the <xref:System.Globalization.StringInfo> class as shown in the following example.</span></span> <span data-ttu-id="d143a-232">Swift'i tanıyorsanız,.NET `StringInfo` türü kavramsal olarak [ `character` Swift'in türüne](https://developer.apple.com/documentation/swift/character)benzer.</span><span class="sxs-lookup"><span data-stu-id="d143a-232">If you're familiar with Swift, the .NET `StringInfo` type is conceptually similar to [Swift's `character` type](https://developer.apple.com/documentation/swift/character).</span></span>

### <a name="example-count-opno-locchar-opno-locrune-and-text-element-instances"></a><span data-ttu-id="d143a-233">Örnek: charsaymak , Runeve metin öğesi örnekleri</span><span class="sxs-lookup"><span data-stu-id="d143a-233">Example: count char, Rune, and text element instances</span></span>

<span data-ttu-id="d143a-234">.NET API'lerinde grafme kümesine *metin öğesi*denir.</span><span class="sxs-lookup"><span data-stu-id="d143a-234">In .NET APIs, a grapheme cluster is called a *text element*.</span></span> <span data-ttu-id="d143a-235">Aşağıdaki yöntem, metin `char` `Rune`öğesi örnekleri arasındaki farkları gösterir: `string`</span><span class="sxs-lookup"><span data-stu-id="d143a-235">The following method demonstrates the differences between `char`, `Rune`, and text element instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::

<span data-ttu-id="d143a-236">Bu kodu .NET Framework veya .NET Core 3.1 veya daha önce çalıştırDıysanız, emoji için metin öğesi sayısı gösterir. `4`</span><span class="sxs-lookup"><span data-stu-id="d143a-236">If you run this code in .NET Framework or .NET Core 3.1 or earlier, the text element count for the emoji shows `4`.</span></span> <span data-ttu-id="d143a-237">Bunun nedeni, `StringInfo` sınıftaki .NET 5'te sabitlenmiş bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="d143a-237">That is due to a bug in the `StringInfo` class that is fixed in .NET 5.</span></span>

### <a name="example-splitting-opno-locstring-instances"></a><span data-ttu-id="d143a-238">Örnek: string örnekleri bölme</span><span class="sxs-lookup"><span data-stu-id="d143a-238">Example: splitting string instances</span></span>

<span data-ttu-id="d143a-239">Örnekleri `string` bölerken, vekil çiftleri ve grafme kümelerini bölmekten kaçının.</span><span class="sxs-lookup"><span data-stu-id="d143a-239">When splitting `string` instances, avoid splitting surrogate pairs and grapheme clusters.</span></span> <span data-ttu-id="d143a-240">Satır sonları eklemek niyetinde yanlış kod, aşağıdaki örnek stringdüşünün:</span><span class="sxs-lookup"><span data-stu-id="d143a-240">Consider the following example of incorrect code, which intends to insert line breaks every 10 characters in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::

<span data-ttu-id="d143a-241">Bu kod örnekleri sıraladığı `char` için, 10-sınıra`char` binen bir vekil çifti bölünür ve aralarında yeni bir satır enjekte edilir.</span><span class="sxs-lookup"><span data-stu-id="d143a-241">Because this code enumerates `char` instances, a surrogate pair that happens to straddle a 10-`char` boundary will be split and a newline injected between them.</span></span> <span data-ttu-id="d143a-242">Bu ekleme, vekil kod noktaları yalnızca çiftler olarak anlamlı olduğundan, veri bozulması nı tanıtır.</span><span class="sxs-lookup"><span data-stu-id="d143a-242">This insertion introduces data corruption, because surrogate code points are meaningful only as pairs.</span></span>

<span data-ttu-id="d143a-243">Örnekler yerine örnekleri (skaler değerler) sayısalad `Rune` ederseniz, veri bozulması potansiyeli ortadan kaldırılmaz. `char`</span><span class="sxs-lookup"><span data-stu-id="d143a-243">The potential for data corruption isn't eliminated if you enumerate `Rune` instances (scalar values) instead of `char` instances.</span></span> <span data-ttu-id="d143a-244">Bir dizi `Rune` örnek,`char` 10-sınıra bağlı bir grafme kümesini kapsaabilir.</span><span class="sxs-lookup"><span data-stu-id="d143a-244">A set of `Rune` instances might make up a grapheme cluster that straddles a 10-`char` boundary.</span></span> <span data-ttu-id="d143a-245">Grafme küme kümesi bölünürse, doğru yorumlanamaz.</span><span class="sxs-lookup"><span data-stu-id="d143a-245">If the grapheme cluster set is split up, it can't be interpreted correctly.</span></span>

<span data-ttu-id="d143a-246">Daha iyi bir yaklaşım, aşağıdaki örnekte olduğu gibi grafeme kümelerini veya metin öğelerini sayarak kırmaktır: string</span><span class="sxs-lookup"><span data-stu-id="d143a-246">A better approach is to break the string by counting grapheme clusters, or text elements, as in the following example:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::

<span data-ttu-id="d143a-247">Ancak daha önce de belirtildiği gibi, .NET 5 dışındaki `StringInfo` .NET uygulamalarında, sınıf bazı grafme kümelerini yanlış işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="d143a-247">As noted earlier, however, in implementations of .NET other than .NET 5, the `StringInfo` class might handle some grapheme clusters incorrectly.</span></span>

## <a name="utf-8-and-utf-32"></a><span data-ttu-id="d143a-248">UTF-8 ve UTF-32</span><span class="sxs-lookup"><span data-stu-id="d143a-248">UTF-8 and UTF-32</span></span>

<span data-ttu-id="d143a-249">Önceki bölümler UTF-16'ya odaklanmıştır, çünkü .NET örnekleri `string` kodlamak için bunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="d143a-249">The preceding sections focused on UTF-16 because that's what .NET uses to encode `string` instances.</span></span> <span data-ttu-id="d143a-250">Utf-8 ve [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32)- Unicode için diğer kodlama sistemleri vardır. [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8)</span><span class="sxs-lookup"><span data-stu-id="d143a-250">There are other encoding systems for Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) and [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span></span> <span data-ttu-id="d143a-251">Bu kodlamalar sırasıyla 8-bit kod birimleri ve 32-bit kod birimleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d143a-251">These encodings use 8-bit code units and 32-bit code units, respectively.</span></span>

<span data-ttu-id="d143a-252">UTF-16 gibi UTF-8 de bazı Unicode skaler değerlerini temsil etmek için birden çok kod birimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d143a-252">Like UTF-16, UTF-8 requires multiple code units to represent some Unicode scalar values.</span></span> <span data-ttu-id="d143a-253">UTF-32, tek bir 32 bitkodlu kod birimindeki herhangi bir skaler değeri temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="d143a-253">UTF-32 can represent any scalar value in a single 32-bit code unit.</span></span>

<span data-ttu-id="d143a-254">Bu üç Unicode kodlama sisteminin her birinde aynı Unicode kod noktasının nasıl temsil edildiğini gösteren bazı örnekler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d143a-254">Here are some examples showing how the same Unicode code point is represented in each of these three Unicode encoding systems:</span></span>

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

<span data-ttu-id="d143a-255">Daha önce belirtildiği gibi, bir [vekil çifti](#surrogate-pairs) tek bir UTF-16 kod birimi kendisi tarafından anlamsızdır.</span><span class="sxs-lookup"><span data-stu-id="d143a-255">As noted earlier, a single UTF-16 code unit from a [surrogate pair](#surrogate-pairs) is meaningless by itself.</span></span> <span data-ttu-id="d143a-256">Aynı şekilde, tek bir UTF-8 kod birimi, skaler bir değeri hesaplamak için kullanılan iki, üç veya dört sırahalindeyse tek başına anlamsızdır.</span><span class="sxs-lookup"><span data-stu-id="d143a-256">In the same way, a single UTF-8 code unit is meaningless by itself if it's in a sequence of two, three, or four used to calculate a scalar value.</span></span>

### <a name="endianness"></a><span data-ttu-id="d143a-257">Endianness</span><span class="sxs-lookup"><span data-stu-id="d143a-257">Endianness</span></span>

<span data-ttu-id="d143a-258">.NET'te, a'nın string UTF-16 kod birimleri bitişik bellekte 16 bittamsedi (örnekler)`char` dizisi olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="d143a-258">In .NET, the UTF-16 code units of a string are stored in contiguous memory as a sequence of 16-bit integers (`char` instances).</span></span> <span data-ttu-id="d143a-259">Tek tek kod birimlerinin bitleri, geçerli mimarinin [sonluluğuna](https://en.wikipedia.org/wiki/Endianness) göre düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="d143a-259">The bits of individual code units are laid out according to the [endianness](https://en.wikipedia.org/wiki/Endianness) of the current architecture.</span></span>

<span data-ttu-id="d143a-260">Biraz endian mimarisinde, string UTF-16 kod noktalarından `[ D801 DCCC ]` oluşan bayt olarak bellekte ortaya `[ 0x01, 0xD8, 0xCC, 0xDC ]`konulacaktır.</span><span class="sxs-lookup"><span data-stu-id="d143a-260">On a little-endian architecture, the string consisting of the UTF-16 code points `[ D801 DCCC ]` would be laid out in memory as the bytes `[ 0x01, 0xD8, 0xCC, 0xDC ]`.</span></span> <span data-ttu-id="d143a-261">Büyük-endian mimarisinde aynı string bayt `[ 0xD8, 0x01, 0xDC, 0xCC ]`olarak bellekte ortaya konulmuş olurdu.</span><span class="sxs-lookup"><span data-stu-id="d143a-261">On a big-endian architecture that same string would be laid out in memory as the bytes `[ 0xD8, 0x01, 0xDC, 0xCC ]`.</span></span>

<span data-ttu-id="d143a-262">Birbiriyle iletişim kurandaki bilgisayar sistemleri, kabloyu geçen verilerin temsili üzerinde anlaşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d143a-262">Computer systems that communicate with each other must agree on the representation of data crossing the wire.</span></span> <span data-ttu-id="d143a-263">Çoğu ağ protokolü, kısmen küçük endian makinesiyle iletişim kuran büyük endian makinesinden kaynaklanabilir sorunları önlemek için, metin aktarırken UTF-8'i standart olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="d143a-263">Most network protocols use UTF-8 as a standard when transmitting text, partly to avoid issues that might result from a big-endian machine communicating with a little-endian machine.</span></span> <span data-ttu-id="d143a-264">UTF-8 kod noktalarından string `[ F0 90 93 8C ]` oluşan her zaman endianness `[ 0xF0, 0x90, 0x93, 0x8C ]` ne olursa olsun bayt olarak temsil edilecektir.</span><span class="sxs-lookup"><span data-stu-id="d143a-264">The string consisting of the UTF-8 code points `[ F0 90 93 8C ]` will always be represented as the bytes `[ 0xF0, 0x90, 0x93, 0x8C ]` regardless of endianness.</span></span>

<span data-ttu-id="d143a-265">Metin iletmek için UTF-8 kullanmak için ,NET uygulamaları genellikle aşağıdaki örnekgibi kod kullanır:</span><span class="sxs-lookup"><span data-stu-id="d143a-265">To use UTF-8 for transmitting text, .NET applications often use code like the following example:</span></span>

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

<span data-ttu-id="d143a-266">Önceki örnekte, Yöntem [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) unicode skaler `string` değerleri bir dizi geri UTF-16 deşifre, sonra UTF-8 içine bu skaler değerleri yeniden kodlar ve bir `byte` dizi içine ortaya çıkan sırayı yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="d143a-266">In the preceding example, the method [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) decodes the UTF-16 `string` back into a series of Unicode scalar values, then it re-encodes those scalar values into UTF-8 and places the resulting sequence into a `byte` array.</span></span> <span data-ttu-id="d143a-267">Yöntem [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) bir UTF-8 `byte` dizi bir UTF-16 `string`dönüştürerek, ters dönüşüm gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d143a-267">The method [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) performs the opposite transformation, converting a UTF-8 `byte` array to a UTF-16 `string`.</span></span>

> [!WARNING]
> <span data-ttu-id="d143a-268">UTF-8 internet üzerinde olağan olduğundan, tel ham bayt okumak ve UTF-8 sanki verileri tedavi etmek cazip olabilir.</span><span class="sxs-lookup"><span data-stu-id="d143a-268">Since UTF-8 is commonplace on the internet, it may be tempting to read raw bytes from the wire and to treat the data as if it were UTF-8.</span></span> <span data-ttu-id="d143a-269">Ancak, gerçekten iyi biçimlendirilmiş olduğunu doğrulamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="d143a-269">However, you should validate that it is indeed well-formed.</span></span> <span data-ttu-id="d143a-270">Kötü niyetli bir istemci kötü biçimlendirilmiş UTF-8'i hizmetinize gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="d143a-270">A malicious client might submit ill-formed UTF-8 to your service.</span></span> <span data-ttu-id="d143a-271">Bu verileri iyi biçimlendirilmiş gibi çalıştırArsanız, uygulamanızda hatalara veya güvenlik açıklarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="d143a-271">If you operate on that data as if it were well-formed, it could cause errors or security holes in your application.</span></span> <span data-ttu-id="d143a-272">UTF-8 verilerini doğrulamak için, `Encoding.UTF8.GetString`gelen verileri bir . `string`</span><span class="sxs-lookup"><span data-stu-id="d143a-272">To validate UTF-8 data, you can use a method like `Encoding.UTF8.GetString`, which will perform validation while converting the incoming data to a `string`.</span></span>

### <a name="well-formed-encoding"></a><span data-ttu-id="d143a-273">İyi biçimlendirilmiş kodlama</span><span class="sxs-lookup"><span data-stu-id="d143a-273">Well-formed encoding</span></span>

<span data-ttu-id="d143a-274">İyi biçimlendirilmiş Unicode kodlaması, string unicode skaler değerleri dizisine hatasız ve hatasız olarak çözülebilen kod birimlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="d143a-274">A well-formed Unicode encoding is a string of code units that can be decoded unambiguously and without error into a sequence of Unicode scalar values.</span></span> <span data-ttu-id="d143a-275">İyi biçimlendirilmiş veriler UTF-8, UTF-16 ve UTF-32 arasında serbestçe ileri geri kodlanabilir.</span><span class="sxs-lookup"><span data-stu-id="d143a-275">Well-formed data can be transcoded freely back and forth between UTF-8, UTF-16, and UTF-32.</span></span>

<span data-ttu-id="d143a-276">Kodlama dizisinin iyi oluşup oluşmadığı sorusu, bir makinenin mimarisinin sonilişkisiyle ilgisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d143a-276">The question of whether an encoding sequence is well-formed or not is unrelated to the endianness of a machine's architecture.</span></span> <span data-ttu-id="d143a-277">Kötü biçimlendirilmiş bir UTF-8 dizisi hem büyük endian hem de küçük endian makinelerde aynı şekilde kötü biçimlendirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d143a-277">An ill-formed UTF-8 sequence is ill-formed in the same way on both big-endian and little-endian machines.</span></span>

<span data-ttu-id="d143a-278">Aşağıda, yanlış biçimlendirilmiş kodlamalara bazı örnekler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d143a-278">Here are some examples of ill-formed encodings:</span></span>

* <span data-ttu-id="d143a-279">UTF-8'de, `[ 6C C2 61 ]` dizi kötü biçimlendirilmiştir `C2` çünkü `61`takip edilemez.</span><span class="sxs-lookup"><span data-stu-id="d143a-279">In UTF-8, the sequence `[ 6C C2 61 ]` is ill-formed because `C2` cannot be followed by `61`.</span></span>

* <span data-ttu-id="d143a-280">UTF-16'da, `[ DC00 DD00 ]` düşük vekil başka bir string `"\udc00\udd00"`düşük vekil `DC00` `DD00`tarafından takip edilemediği için dizi (veya C#, the) kötü biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d143a-280">In UTF-16, the sequence `[ DC00 DD00 ]` (or, in C#, the string `"\udc00\udd00"`) is ill-formed because the low surrogate `DC00` cannot be followed by another low surrogate `DD00`.</span></span>

* <span data-ttu-id="d143a-281">UTF-32'de, `[ 0011ABCD ]` Unicode skaler değerlerinin aralığının dışında `0011ABCD` olduğu için dizi kötü biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d143a-281">In UTF-32, the sequence `[ 0011ABCD ]` is ill-formed because `0011ABCD` is outside the range of Unicode scalar values.</span></span>

<span data-ttu-id="d143a-282">.NET'te, `string` örnekler hemen hemen her zaman iyi biçimlendirilmiş UTF-16 verileri içerir, ancak bu garanti değildir.</span><span class="sxs-lookup"><span data-stu-id="d143a-282">In .NET, `string` instances almost always contain well-formed UTF-16 data, but that isn't guaranteed.</span></span> <span data-ttu-id="d143a-283">Aşağıdaki örnekler, kötü biçimlendirilmiş UTF-16 verilerini örneklerde `string` oluşturan geçerli C# kodunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d143a-283">The following examples show valid C# code that creates ill-formed UTF-16 data in `string` instances.</span></span>

* <span data-ttu-id="d143a-284">Kötü biçimli bir edebi:</span><span class="sxs-lookup"><span data-stu-id="d143a-284">An ill-formed literal:</span></span>

  ```csharp
  const string s = "\ud800";
  ```

* <span data-ttu-id="d143a-285">Bir vekil çifti ayıran bir alt dize:</span><span class="sxs-lookup"><span data-stu-id="d143a-285">A substring that splits up a surrogate pair:</span></span>

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

<span data-ttu-id="d143a-286">API'ler kötü biçimlendirilmiş [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) `string` örnekleri asla iade etmek gibi.</span><span class="sxs-lookup"><span data-stu-id="d143a-286">APIs like [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) never return ill-formed `string` instances.</span></span> <span data-ttu-id="d143a-287">`Encoding.GetString`ve `Encoding.GetBytes` yöntemler girişte yanlış biçimlendirilmiş dizileri algılar ve çıktıyı oluştururken karakter ikamesi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d143a-287">`Encoding.GetString` and `Encoding.GetBytes` methods detect ill-formed sequences in the input and perform character substitution when generating the output.</span></span> <span data-ttu-id="d143a-288">Örneğin, girişte ASCII olmayan bir bayt [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) görürse (U+0000..U+007F aralığının dışında), döndürülen `string` örneğe bir '?' ekler.</span><span class="sxs-lookup"><span data-stu-id="d143a-288">For example, if [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) sees a non-ASCII byte in the input (outside the range U+0000..U+007F), it inserts a '?' into the returned `string` instance.</span></span> <span data-ttu-id="d143a-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A)kötü biçimlendirilmiş UTF-8 dizilerini `U+FFFD REPLACEMENT CHARACTER ('�')` döndürülen `string` örnekte değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d143a-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) replaces ill-formed UTF-8 sequences with `U+FFFD REPLACEMENT CHARACTER ('�')` in the returned `string` instance.</span></span> <span data-ttu-id="d143a-290">Daha fazla bilgi için [Unicode Standardı,](https://www.unicode.org/versions/latest/)Bölüm 5.22 ve 3.9'a bakın.</span><span class="sxs-lookup"><span data-stu-id="d143a-290">For more information, see [the Unicode Standard](https://www.unicode.org/versions/latest/), Sections 5.22 and 3.9.</span></span>

<span data-ttu-id="d143a-291">Yerleşik `Encoding` sınıflar, yanlış biçimlendirilmiş diziler görüldüğünde karakter ikamesi gerçekleştirmek yerine bir özel durum atmak için de yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="d143a-291">The built-in `Encoding` classes can also be configured to throw an exception rather than perform character substitution when ill-formed sequences are seen.</span></span> <span data-ttu-id="d143a-292">Bu yaklaşım genellikle karakter değiştirmenin kabul edilemeyebildiği güvenliğe duyarlı uygulamalarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d143a-292">This approach is often used in security-sensitive applications where character substitution might not be acceptable.</span></span>

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

<span data-ttu-id="d143a-293">Yerleşik `Encoding` sınıfların nasıl kullanılacağı hakkında bilgi için [.NET'te karakter kodlama sınıfları nasıl kullanılır.](character-encoding.md)</span><span class="sxs-lookup"><span data-stu-id="d143a-293">For information about how to use the built-in `Encoding` classes, see [How to use character encoding classes in .NET](character-encoding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d143a-294">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d143a-294">See also</span></span>

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [<span data-ttu-id="d143a-295">Küreselleşme ve Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="d143a-295">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
