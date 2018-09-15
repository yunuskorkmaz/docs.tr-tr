---
title: Normal İfadelerdeki Değişim Yapıları
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b653972fad71ce3a89c35598513b94f71fb4bf0
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45648375"
---
# <a name="alternation-constructs-in-regular-expressions"></a>Normal İfadelerdeki Değişim Yapıları
<a name="top"></a> Değişim yapıları etkinleştirmek üzere bir normal ifade değiştirmek / veya veya koşullu eşleştirme. .NET üç değişim yapıları destekler:  
  
-   [İle desen eşleştirme&#124;](#Either_Or)  
  
-   [Koşullu eşleşen (? () ifade) Evet&#124;yok)](#Conditional_Expr)  
  
-   [Yakalanan geçerli bir gruba bağlı koşullu eşleştirme](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a>İle desen eşleştirme&#124;  
 Dikey çubuk kullanabilirsiniz (`|`) herhangi bir desen, bir dizi karakter burada `|` karakter her desen ayırır.  
  
 Pozitif karakter sınıfı gibi `|` karakteri, herhangi bir tek karakteri eşleştirmek için kullanılabilir. Aşağıdaki örnek, bir pozitif karakter sınıfını hem ya da kullanır. / veya deseni ile eşleşen `|` bir dizede sözcükler "gri" veya "gri" oluşumlarını bulmak için kullanılan karakter. Bu durumda, `|` karakter daha ayrıntılıdır normal bir ifade oluşturur.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 Kullanan normal ifade `|` karakter `\bgr(a|e)y\b`, aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`gr`|"Gr" karakteriyle eşleş.|  
|<code>(a&#124;e)</code>|Bir "a" veya "e" ile eşleş.|  
|`y\b`|Bir sözcük sınırında bir "y" eşleşir.|  
  
 `|` Karakter de kullanılabilir ya da gerçekleştirmek için / veya birden çok karakter veya alt ifadeler karakter değişmez değerleri ve normal ifade dil öğesi herhangi bir birleşimini içerebilir. (Karakter sınıfı, bu işlevsellik sağlamaz.) Aşağıdaki örnekte `|` ya da bir ABD ayıklanacak karakter Sosyal Güvenlik numarası (9 basamaklı bir sayı biçiminde olan SSN), *ddd*-*GG*-*dddd*, veya bir ABD 9 basamaklı sayı biçimiyle İşveren Kimlik Numaranız'ne (EIN) *GG*-*ddddddd*.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 Normal ifade `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|Aşağıdakilerden birini eşleşen: yedi ondalık basamak; ardından gelen bir tirenin ardından iki ondalık basamak veya üç ondalık basamak, tire, iki ondalık basamak, başka bir kısa çizgi ve dört ondalık basamak.|  
|`\d`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 [Başa dön](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a>İfade Kullanarak Koşullu Eşleştirme  
 Bu dil öğesi, bir ilk desen olup eşleşebilir bağlı olarak iki desenlerden birini eşleştirmeyi dener. Kendi sözdizimi aşağıdaki gibidir:  
  
 `(?(` *ifade* `)` *Evet* `|` *yok* `)`  
  
 Burada *ifade* eşleştirmek için ilk desen *Evet* deseni eşleşiyorsa *ifade* eşleştirilir, ve *hiçbir* isteğe bağlıdır deseni eşleşiyorsa *ifade* eşlenemiyor. Normal ifade altyapısı işler *ifade* değerlendirir, sonra sıfır genişlikli onaylama olarak; diğer bir deyişle, normal ifade motoru giriş akışında ilerleyin değil *ifade*. Bu nedenle, bu yapı aşağıdakine eşdeğerdir:  
  
 `(?(?=` *ifade* `)` *Evet* `|` *yok* `)`  
  
 Burada `(?=` *ifade* `)` Sıfır genişlikli onaylama yapıdır. (Daha fazla bilgi için [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Normal ifade altyapısı yorumladığından *ifade* bir bağlantı (bir sıfır genişlikli onaylama) olarak *ifade* ya da Sıfır genişlikli onaylama olmalıdır (daha fazla bilgi için [ Yer işaretleri](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) ya da bulunan bir alt ifade *Evet*. Aksi takdirde, *Evet* deseni olamaz eşleşti.  
  
> [!NOTE]
>  Varsa *ifade*bir adlandırışmış veya numaralandırılmış yakalama grubu, değişim yapısı yorumlanır yakalama test olarak; daha fazla bilgi için sonraki bölüme bakın [koşullu eşleştirme dayalı olarak bir geçerli bir yakalama grubundaki](#Conditional_Group). Diğer bir deyişle, normal ifade altyapısı yakalanan alt dizeyi eşleştirmek çalışmaz ancak bunun yerine, varlığı veya yokluğu grubunun için test eder.  
  
 Aşağıdaki örnekte gösterildiği örnek bir çeşididir [ya da / veya desen eşleştirme ile &#124; ](#Either_Or) bölümü. Bir sözcük sınırı sonra ilk üç karakter, kısa çizgi ve ardından iki basamak olup olmadığını belirlemek için koşullu eşleştirme kullanır. Böyle bir durumda, bir ABD eşleştirmeye çalışır İşveren Kimlik numarası (EIN). Aksi halde, bir ABD eşleştirmeyi dener Sosyal Güvenlik numarası (SSN).  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 Normal ifade deseni `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`(?(\d{2}-)`|Sonraki üç karakter tireyle izleyen iki basamak oluşur olup olmadığını belirler.|  
|`\d{2}-\d{7}`|Önceki desenle eşleşiyorsa bir tire yedi haneli ve ardından iki basamak eşleştirin.|  
|`\d{3}-\d{2}-\d{4}`|Önceki desenle eşleşmez, üç ondalık basamak, tire, iki ondalık basamak, başka bir tire ve dört ondalık basamağı eşleştirin.|  
|`\b`|Bir sözcük sınırıyla eşleş.|  
  
 [Başa dön](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a>Yakalanan Geçerli Bir Gruba Göre Koşullu Eşleştirme  
 Bu dil öğesi, belirtilen bir yakalama grubu olup olmadığını eşleşti bağlı olarak iki desenlerden birini eşleştirmeyi dener. Kendi sözdizimi aşağıdaki gibidir:  
  
 `(?(` *adı* `)` *Evet* `|` *yok* `)`  
  
 veya  
  
 `(?(` *sayı* `)` *Evet* `|` *yok* `)`  
  
 Burada *adı* adıdır ve *numarası* bir yakalama grubu sayısı *Evet* eşleşiyorsa ifadesidir *adı* veya *numarası* bir eşleşmeye sahip ve *hiçbir* kullanmıyorsa eşleştirmek için isteğe bağlı ifade.  
  
 Varsa *adı* gelmediğinden normal ifade deseninde kullanılan bir yakalama grubunun adına, değişim yapısı bir ifade testi olarak önceki bölümde açıklandığı gibi yorumlanır. Genellikle, yani *ifade* değerlendiren `false`. Varsa *numarası* normal ifade deseni, normal ifade motoru oluşturur kullanılan numaralandırılmış bir tutma grubu gelmiyor bir <xref:System.ArgumentException>.  
  
 Aşağıdaki örnekte gösterildiği örnek bir çeşididir [ya da / veya desen eşleştirme ile &#124; ](#Either_Or) bölümü. Adlı bir yakalama grubunu kullanan `n2` tireyle izleyen iki basamak içerir. Değişim, giriş dizesinde Bu yakalama grubuyla eşleşen olup olmadığını testler oluşturun. Varsa, değişim oluşturmak dokuz basamak ABD son yedi rakamı eşleşmeyi dener İşveren Kimlik numarası (EIN). Sahip değil, dokuz basamak ABD eşleştirmeye çalışır Sosyal Güvenlik numarası (SSN).  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 Normal ifade deseni `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`(?<n2>\d{2}-)?`|İki basamaklı bir tire işaretiyle ardından sıfır veya bir oluşumunu eşleştirin. Bu yakalama grubu adı `n2`.|  
|`(?(n2)`|Test olmadığını `n2` giriş dizesinde eşleştirildi.|  
|`)\d{7}`|Varsa `n2` olan yedi ondalık basamak eşleşen, eşleşen.|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|Varsa `n2` eşleşmeyen, eşleşen üç ondalık basamak, tire, iki ondalık basamak, başka bir kısa çizgi ve dört ondalık basamak.|  
|`\b`|Bir sözcük sınırıyla eşleş.|  
  
 Bu örnek yerine adlandırılmış bir grubu numaralandırılmış bir grubu kullanan bir çeşitlemesi, aşağıdaki örnekte gösterilir. Normal ifade desenine olan `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
