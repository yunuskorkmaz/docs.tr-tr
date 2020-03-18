---
title: .NET Düzenli İfadelerde Alternation Yapılar
description: Düzenli ifadelerde koşullu eşleştirme için alternasyon yapılarını nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- either/or matching
- alternative matching patterns
- regular expressions, alternation constructs
- alternation constructs
- optional matching patterns
- constructs, alternation
- .NET Framework regular expressions, alternation constructs
ms.assetid: 071e22e9-fbb0-4ecf-add1-8d2424f9f2d1
ms.openlocfilehash: 02664bd2812f89649ec933483161263bae530a75
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159695"
---
# <a name="alternation-constructs-in-regular-expressions"></a>Normal İfadelerdeki Değişim Yapıları

Alternation yapıları ya / veya koşullu eşleştirme etkinleştirmek için normal bir ifade değiştirmek. .NET üç değişim yapısını destekler:

- [&#124;ile eşleşen desen](#Either_Or)
- [Koşullu eşleştirme ile (?( ifade)evet&#124;hayır)](#Conditional_Expr)
- [Yakalanan geçerli bir gruba göre koşullu eşleştirme](#Conditional_Group)

<a name="Either_Or"></a>
## <a name="pattern-matching-with-124"></a>&#124; ile Örüntü Eşleştirme

Dikey çubuk (`|`) karakterini, `|` karakterin her deseni ayırdığı bir dizi desenle eşleştirmek için kullanabilirsiniz.

Pozitif karakter sınıfı gibi, `|` karakter de tek karakterden herhangi biriyle eşleşmek için kullanılabilir. Aşağıdaki örnekte, bir dizedeki "gri" veya `|` "gri" sözcüklerinin oluşumlarını bulmak için hem pozitif karakter sınıfı hem de karakterle eşleşen bir deseni kullanır. Bu durumda, `|` karakter daha ayrıntılı düzenli bir ifade üretir.

[!code-csharp[RegularExpressions.Language.Alternation#1](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
[!code-vb[RegularExpressions.Language.Alternation#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]

`|` Karakteri kullanan normal ifade, `\bgr(a|e)y\b`aşağıdaki tabloda gösterildiği gibi yorumlanır:

|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`gr`|"gr" karakterlerini eşleştirin.|  
|<code>(a&#124;e)</code>|Bir "a" veya "e" ile eşleş.|  
|`y\b`|Sözcük sınırında bir "y" ile eşleştirin.|  

`|` Karakter, karakter gerçek ve normal ifade dili öğelerinin herhangi bir birleşimini içerebilen birden çok karakter veya alt ifadeyle eşleştirme yapmak için de kullanılabilir. (Karakter sınıfı bu işlevselliği sağlamaz.) Aşağıdaki örnek, `|` *ddd*-*ddddd**dd*-biçimine sahip 9 basamaklı bir sayı olan ABD Sosyal Güvenlik Numarası (SSN) veya-*dddddd*biçimine sahip 9 basamaklı bir sayı *dd*olan ABD İşveren Kimlik Numarası (EIN) özelliğini ayıklamak için karakteri kullanır.

[!code-csharp[RegularExpressions.Language.Alternation#2](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
[!code-vb[RegularExpressions.Language.Alternation#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  

Normal ifade `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır:
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|Aşağıdakilerden birini eşleştirin: iki ondalık basamak ve ardından bir tire ve ardından yedi ondalık basamak; veya üç ondalık basamak, bir tire, iki ondalık basamak, başka bir tire ve dört ondalık basamak.|  
|`\d`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
<a name="Conditional_Expr"></a>
## <a name="conditional-matching-with-an-expression"></a>Bir ifadeyle koşullu eşleştirme

Bu dil öğesi, ilk desenle eşleşip eşleşmediğine bağlı olarak iki desenden birini eşleştirmeye çalışır. Sözdizimi:  

`(?(`*ifade* `)` *evet* `|` *hayır*`)`

*ifadenin* eşleşecek ilk desen olduğu yerde, *evet* *ifade* eşleşip eşleşmediği desendir ve *ifade* eşleşmiyorsa eşleşen isteğe bağlı desen *hayırdır.* Normal ifade altyapısı *ifadeyi* sıfır genişlikli bir tasnı olarak ele alar; diğer bir deyişle, normal ifade altyapısı *ifadeyi*değerlendirdikten sonra giriş akışında ilerlemez. Bu nedenle, bu yapı aşağıdakilere eşdeğerdir:

`(?(?=`*ifade* `)` *evet* `|` *hayır*`)`

`(?=` *ifadenin* `)` sıfır genişlikte bir tasnİf yapısı olduğu yerde. (Daha fazla bilgi için yapı [yı gruplandırma](grouping-constructs-in-regular-expressions.md)ya da gruplandırma 'ya bakın.) Normal ifade altyapısı *ifadeyi* bir bağlantı noktası (sıfır genişlikte bir iddia) olarak yorumladığı için, *ifade* nin sıfır genişlikte bir tasnİf (daha fazla bilgi için, [Bkz. Çapalar)](anchors-in-regular-expressions.md)veya *evet'te*de bulunan bir alt ifade olması gerekir. Aksi takdirde, *evet* deseni eşleşemez.  
  
> [!NOTE]
> *İfade* adlandırılmış veya numaralandırılmış bir yakalama grubuysa, değiştirme yapısı bir yakalama testi olarak yorumlanır; daha fazla bilgi için, [geçerli bir yakalama grubuna dayalı koşullu eşleştirme](#Conditional_Group)sonraki bölüme bakın. Başka bir deyişle, normal ifade altyapısı yakalanan alt dizeyle eşleşmeye çalışmaz, bunun yerine grubun varlığı veya yokluğu için test eder.  
  
Aşağıdaki örnek, [ya/veya desen eşleştirmesinde &#124;bölümüyle](#Either_Or) görünen örneğin bir varyasyonudur. Bir sözcük sınırından sonraki ilk üç karakterin iki basamaklı olup olmadığını belirlemek için koşullu eşleştirmeyi kullanır. Varsa, bir ABD İşveren Kimlik Numarası (EIN) eşleşmeye çalışır. Değilse, bir ABD Sosyal Güvenlik Numarası (SSN) eşleşmeye çalışır.

[!code-csharp[RegularExpressions.Language.Alternation#3](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
[!code-vb[RegularExpressions.Language.Alternation#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]

Normal ifade `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` deseni aşağıdaki tabloda gösterildiği gibi yorumlanır:

|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`(?(\d{2}-)`|Sonraki üç karakterin iki basamaktan oluşup oluşmadığını ve ardından tireyi belirleyin.|  
|`\d{2}-\d{7}`|Önceki desen eşleşirse, iki basamak ve ardından bir tire ve ardından yedi basamak eşleştirin.|  
|`\d{3}-\d{2}-\d{4}`|Önceki desen eşleşmiyorsa, üç ondalık basamak, bir tire, iki ondalık basamak, başka bir tire ve dört ondalık basamak eşleştirin.|  
|`\b`|Bir sözcük sınırıyla eşleş.|  

<a name="Conditional_Group"></a>
## <a name="conditional-matching-based-on-a-valid-captured-group"></a>Yakalanan geçerli bir gruba göre koşullu eşleştirme

Bu dil öğesi, belirli bir yakalama grubuyla eşleşip eşleşmediğine bağlı olarak iki desenden birini eşleştirmeye çalışır. Sözdizimi:

`(?(`*isim* `)` *evet* `|` *hayır*`)`

or

`(?(`*numara* `)` *evet* `|` *hayır*`)`

*adı* nisisim ve *sayı* bir yakalama grubunun numarasıdır, *evet* *ad* veya *sayı* eşleşip eşleşmediği ifadedir ve *hayır,* yoksa eşleşecek isteğe bağlı ifadedir.

*Ad,* normal ifade deseninde kullanılan bir yakalama grubunun adıile uyuşmuyorsa, değiştirme yapısı önceki bölümde açıklandığı gibi bir ifade testi olarak yorumlanır. Genellikle, bu *ifadenin* `false`. *Sayı,* normal ifade deseninde kullanılan numaralanmış bir yakalama grubuna karşılık gelmiyorsa, normal ifade motoru . <xref:System.ArgumentException>

Aşağıdaki örnek, [ya/veya desen eşleştirmesinde &#124;bölümüyle](#Either_Or) görünen örneğin bir varyasyonudur. İki basamaktan oluşan `n2` ve ardından tire yi izleyen bir yakalama grubu kullanır. Alternation yapı, bu yakalama grubunun giriş dizesinde eşleşip eşleşmediğini sınar. Varsa, alternation yapı dokuz basamaklı BIR ABD İşveren Kimlik Numarası (EIN) son yedi basamak eşleşmeye çalışır. Değilse, dokuz basamaklı bir ABD Sosyal Güvenlik Numarası (SSN) eşleştirmeye çalışır.

[!code-csharp[RegularExpressions.Language.Alternation#4](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
[!code-vb[RegularExpressions.Language.Alternation#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]

Normal ifade `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` deseni aşağıdaki tabloda gösterildiği gibi yorumlanır:

|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`(?<n2>\d{2}-)?`|Eşleştirme sıfır veya iki basamaklı bir olay ardından bir tire. Bu yakalama grubunu `n2`adlandırın.|  
|`(?(n2)`|Giriş `n2` dizesinde eşleşip eşleşmediğini test edin.|  
|`\d{7}`|Eşleştirildiyse, `n2` yedi ondalık basamakeşleştirin.|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|Eşleşmediyse, `n2` üç ondalık basamak, bir tire, iki ondalık basamak, başka bir tire ve dört ondalık basamak eşleştirin.|  
|`\b`|Bir sözcük sınırıyla eşleş.|  

Bu örneğin, adlandırılmış bir grup yerine numaralandırılmış bir grup kullanan bir varyasyonu aşağıdaki örnekte gösterilmiştir. Onun düzenli ifade `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`deseni .

[!code-csharp[RegularExpressions.Language.Alternation#5](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
[!code-vb[RegularExpressions.Language.Alternation#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]

## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](regular-expression-language-quick-reference.md)
