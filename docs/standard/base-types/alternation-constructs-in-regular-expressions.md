---
title: .NET normal Ifadelerinde değişim yapıları
description: Normal ifadelerde koşullu eşleme için değişim yapılarını nasıl kullanacağınızı öğrenin.
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
ms.custom: seodec18
ms.openlocfilehash: 560597770d667cf8c7668bf2338ac4bac3eb192f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968567"
---
# <a name="alternation-constructs-in-regular-expressions"></a>Normal İfadelerdeki Değişim Yapıları
<a name="top"></a>Değişim yapıları,/veya veya koşullu eşleştirmeyi etkinleştirmek için bir normal ifadeyi değiştirir. .NET üç değişim yapılarını destekler:  
  
- [İle eşleşen desenler&#124;](#Either_Or)  
  
- [(? () İle koşullu eşleme ifade) Evet&#124;Hayır)](#Conditional_Expr)  
  
- [Geçerli bir yakalanan gruba göre koşullu eşleme](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a>İle eşleşen desenler&#124;  
 Dikey çubuk (`|`) karakterini, bir dizi desenden eşleştirmek için kullanabilirsiniz, `|` burada karakter her bir deseni ayırır.  
  
 Pozitif karakter sınıfı gibi, `|` karakter, bir dizi tek karakterden biriyle eşleştirmek için de kullanılabilir. Aşağıdaki örnek, bir dizede "gri" veya "gri" kelimelerin tekrarlamalarını bulmak `|` için hem pozitif bir karakter sınıfını hem de karakteri ile eşleşen stili kullanır. Bu durumda, `|` karakter daha ayrıntılı olan bir normal ifade üretir.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 `|` Bu`\bgr(a|e)y\b`karakteri kullanan normal ifade, aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`gr`|"Gr" karakterlerini eşleştirin.|  
|<code>(a&#124;e)</code>|Bir "a" veya "e" ile eşleş.|  
|`y\b`|Bir sözcük sınırında "y" ile eşleşir.|  
  
 Karakter `|` , ya da karakter değişmez değerleri ve normal ifade dili öğelerinin herhangi bir birleşimini içerebilen birden çok karakterle veya alt ifadeyle eşleşme gerçekleştirmek için de kullanılabilir. (Karakter sınıfı bu işlevselliği sağlamaz.) Aşağıdaki örnek, bir ABD `|` 'yi ayıklamak için karakteri kullanır Bir 9 basamaklı bir sayı olan sosyal güvenlik numarası (SSN), *ddd*-*gg*-*gggg*veya ABD 7 basamaklı bir sayı-olan işveren kimlik numarası (EIN).  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 Normal ifade `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|Aşağıdakilerden birini eşleştirin: iki ondalık basamak ve sonra da yedi ondalık basamak gelen tire. ya da üç ondalık basamak, kısa çizgi, iki ondalık basamak, başka bir tire ve dört ondalık basamak.|  
|`\d`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 [Başa dön](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a>İfade Kullanarak Koşullu Eşleştirme  
 Bu dil öğesi, bir başlangıç deseniyle eşleşmediğine bağlı olarak iki desenden birini eşleştirmeye çalışır. Sözdizimi şöyledir:  
  
 `(?(`*ifade* *Evet* Hayır `)` `|``)`  
  
 Burada *ifadesi* eşleşmek üzere başlangıç düzensiyse, *Evet* *ifadesi* eşleşiyorsa eşleşen bir modeldir ve *hiçbir* değer *ifade* eşleşmezse eşleşen isteğe bağlı bir modeldir. Normal ifade altyapısı, *ifadeyi* sıfır genişlikli bir onaylama olarak değerlendirir; diğer bir deyişle, normal ifade altyapısı, *ifade*değerlendirdikten sonra giriş akışında ilerlemez. Bu nedenle, bu yapı aşağıdaki ile eşdeğerdir:  
  
 `(?(?=`*ifade* *Evet* Hayır `)` `|``)`  
  
 Burada `(?=` ifadesi`)` sıfır genişlikli bir onaylama yapısıdır. (Daha fazla bilgi için bkz. [yapıları gruplandırma](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Normal ifade altyapısı *ifadeyi* bir tutturucu (sıfır genişlikli bir onaylama) olarak yorumladığı için, *ifadenin* sıfır genişlikli bir onaylama (daha fazla bilgi Için, bkz. [Tutturucular](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) veya içinde de bulunan bir alt ifade olması gerekir. *Evet*. Aksi halde, *Evet* deseninin eşleştirilemez.  
  
> [!NOTE]
> *İfade*adlandırılmış veya numaralandırılmış yakalama grubsiyse, değişim yapısı yakalama testi olarak yorumlanır; daha fazla bilgi için, [geçerli bir yakalama grubuna göre koşullu eşleme](#Conditional_Group)başlıklı sonraki bölüme bakın. Diğer bir deyişle, normal ifade altyapısı yakalanan alt dizeyle eşleştirmeye çalışmaz, bunun yerine grubun varlığını veya yokluğunu sınar.  
  
 Aşağıdaki örnek, [ile &#124; eşleşen bir/veya desenli](#Either_Or) bir örnek çeşitlemesi olan bir örnektir. Bir sözcük sınırından sonraki ilk üç karakterin, kısa çizgi ve sonrasında iki basamak olup olmadığını anlamak için koşullu eşleştirmeyi kullanır. Varsa, bir ABD ile eşleştirmeye çalışır İşveren Kimlik numarası (EIN). Aksi takdirde, bir ABD ile eşleştirmeye çalışır Sosyal güvenlik numarası (SSK).  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 Normal ifade deseninin `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`(?(\d{2}-)`|Sonraki üç karakterin iki basamakla ve sonra bir tire ile olup olmadığını belirleme.|  
|`\d{2}-\d{7}`|Önceki kalıp eşleşiyorsa, iki basamakla ve sonra da yedi basamakla eşleşen bir tire ile eşleştirin.|  
|`\d{3}-\d{2}-\d{4}`|Önceki model eşleşmiyorsa üç ondalık basamağı, kısa çizgi, iki ondalık basamak, başka bir tire ve dört ondalık basamak eşleştirin.|  
|`\b`|Bir sözcük sınırıyla eşleş.|  
  
 [Başa dön](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a>Yakalanan Geçerli Bir Gruba Göre Koşullu Eşleştirme  
 Bu dil öğesi, belirtilen bir yakalama grubuyla eşleşip eşleşmediğine bağlı olarak iki desenden birini eşleştirmeye çalışır. Sözdizimi şöyledir:  
  
 `(?(`*ad* *Evet* Hayır `)` `|``)`  
  
 veya  
  
 `(?(`*sayı* *Evet* Hayır `)` `|``)`  
  
 Burada *ad* , ad ve *sayı* bir yakalama grubu numarasıdır, *Evet* , *ad* veya *sayı* bir eşleşme içeriyorsa ve *Hayır* ise eşleşmesi gereken isteğe bağlı ifadedir.  
  
 *Ad* , normal ifade modelinde kullanılan bir yakalama grubunun adına karşılık gelmiyorsa, değişim yapısı, önceki bölümde açıklandığı gibi bir ifade testi olarak yorumlanır. Genellikle, bu *ifade* olarak `false`değerlendirilir. *Sayı* , normal ifade deseninin kullandığı numaralandırılmış bir yakalama grubuna karşılık gelmiyorsa, normal ifade altyapısı bir <xref:System.ArgumentException>oluşturur.  
  
 Aşağıdaki örnek, [ile &#124; eşleşen bir/veya desenli](#Either_Or) bir örnek çeşitlemesi olan bir örnektir. İki basamaktan oluşan adlı `n2` bir yakalama grubu kullanır ve kısa çizgi gelir. Değişim yapısı, bu yakalama grubunun giriş dizesinde eşleştirilip eşleştirilmediğini test eder. Varsa, değişim yapısı dokuz basamaklı ABD 'nin son yedi basamağıyla eşleştirmeye çalışır İşveren Kimlik numarası (EIN). Bu yoksa dokuz basamaklı bir ABD ile eşleştirmeye çalışır Sosyal güvenlik numarası (SSK).  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 Normal ifade deseninin `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`(?<n2>\d{2}-)?`|Sıfır veya iki basamaklı bir oluşumu izleyen kısa çizgi ile eşleştirin. Bu yakalama grubunu `n2`adlandırın.|  
|`(?(n2)`|Giriş dizesinde `n2` eşleştirilip eşleştirilmediğini test edin.|  
|`\d{7}`|Eşleştiriliyorsa `n2` yedi ondalık basamağı eşleştirin.|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|`n2` Eşleştirilmedi, üç ondalık basamağı, kısa çizgi, iki ondalık basamak, başka bir tire ve dört ondalık basamak eşleştirin.|  
|`\b`|Bir sözcük sınırıyla eşleş.|  
  
 Bu örneğin, adlandırılmış bir grup yerine numaralandırılmış bir grup kullanan bir çeşitlemesi aşağıdaki örnekte gösterilmiştir. Normal ifade deseninin `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
