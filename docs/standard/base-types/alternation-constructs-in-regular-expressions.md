---
title: "Normal İfadelerdeki Değişim Yapıları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cea67e0309bccac7d21d7e8db659a55d34d4959a
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2018
---
# <a name="alternation-constructs-in-regular-expressions"></a>Normal İfadelerdeki Değişim Yapıları
<a name="top"></a> Değişim yapıları değiştirin ya da etkinleştirmek için normal bir ifade / veya veya koşullu eşleştirme. .NET üç değişim yapıları destekler:  
  
-   [Desen ile eşleştirme&#124;](#Either_Or)  
  
-   [Koşullu ile eşleşen (? () ifade) Evet&#124;yok)](#Conditional_Expr)  
  
-   [Koşullu eşleşen bir geçerli yakalanan grubuna bağlı](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a>Desen ile eşleştirme&#124;  
 Dikey çubuğu'nu kullanabilirsiniz (`|`) karakter düzenleri, bir dizi herhangi biri eşleştirmek için burada `|` karakter her düzeni ayırır.  
  
 Pozitif karakter sınıfı gibi `|` karakteri, herhangi bir tek karakteri eşleştirmek için kullanılabilir. Aşağıdaki örnek, bir pozitif karakter sınıfını hem ya da kullanır / veya desen ile eşleşen `|` karakter dizesi içinde sözcükleri "gri" veya "gri" oluşumları bulun. Bu durumda, `|` karakter daha ayrıntılı bir normal ifade üretir.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 Kullanan normal ifade `|` karakter `\bgr(a|e)y\b`, aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`gr`|"Gr" karakteri eşleştirmek.|  
|<code>(a&#124;e)</code>|Bir "a" veya "e" ile eşleş.|  
|`y\b`|Word sınırında "y" eşleşir.|  
  
 `|` Karakter de kullanılabilir ya da gerçekleştirmek için / veya birden çok karakter veya karakter değişmez değerleri ve normal ifade dil öğeleri herhangi bir birleşimini içerebilir alt ifadelerin ile eşleşiyor. (Karakter sınıfı bu işlevselliği sağlamaz.) Aşağıdaki örnek kullanır `|` karakter ya da bir ABD ayıklamak için Sosyal Güvenlik numarası (9 basamaklı bir sayı biçiminde olan SSN), *ddd*-*GG*-*dddd*, veya bir ABD 9 basamaklı sayı biçiminde İşveren Kimlik Numaranız'ne (EIN) *GG*-*ddddddd*.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 Normal ifade `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|Aşağıdakilerden birini eşleşen: tarafından yedi ondalık basamak; tire arkasından iki ondalık basamak veya üç ondalık basamak, tire, iki ondalık basamak, başka bir tire ve dört ondalık basamak.|  
|`\d`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 [Başa dön](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a>İfade Kullanarak Koşullu Eşleştirme  
 Bu dil öğe olup bir ilk desen eşleştirebilirsiniz bağlı olarak iki desenleri birini eşleştirmeyi dener. Sözdizimi aşağıdaki gibidir:  
  
 `(?(` *ifade* `)` *Evet* `|` *yok* `)`  
  
 Burada *ifade* eşleştirmek için ilk deseni *Evet* eşleşiyorsa deseni *ifade* eşleştirildiği, ve *hiçbir* isteğe bağlıdır eşleşiyorsa için desen *ifade* eşlenemiyor. Normal ifade altyapısı değerlendirir *ifade* bu hesaplar sonra sıfır genişlik onaylama; diğer bir deyişle, normal ifade altyapısı Giriş akışı ilerletmesi değil *ifade*. Bu nedenle, bu yapıyı şuna eşdeğerdir:  
  
 `(?(?=` *ifade* `)` *Evet* `|` *yok* `)`  
  
 Burada `(?=` *ifade* `)` Sıfır Genişlik onaylama yapısıdır. (Daha fazla bilgi için bkz: [gruplandırma yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Normal ifade altyapısı yorumlaması nedeniyle *ifade* bir bağlantı (bir sıfır genişlik onaylama) olarak *ifade* ya da Sıfır Genişlik onaylama olmalıdır (daha fazla bilgi için bkz: [ Tutturur](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) ya da bulunan bir alt *Evet*. Aksi takdirde, *Evet* deseni olamaz eşleştirilemedi.  
  
> [!NOTE]
>  Varsa *ifade*bir adlandırılmış ya da numaralı yakalama grup, değişim yapı yorumlanır yakalama test olarak; daha fazla bilgi için sonraki bölüme bakın [koşullu eşleşen bir geçerli yakalama grubu temelinde](#Conditional_Group). Diğer bir deyişle, normal ifade altyapısı yakalanan alt dizeyi eşleştirmek çalışmaz, ancak bunun yerine varlığının veya yokluğunun grubunun için sınar.  
  
 Aşağıdaki örnekte gösterildiği örnek bir çeşididir [ya da / veya desen eşleştirme ile &#124; ](#Either_Or) bölümü. Bu koşullu eşleşen word sınır sonra ilk üç karakter kısa çizgi ve ardından iki basamak olup olmadığını belirlemek için kullanır. Böyle bir durumda, bir ABD eşleştirmeye çalışır İşveren Kimlik numarası (EIN). Aksi durumda, bir ABD eşleştirmeye çalışır Sosyal Güvenlik numarası (SSN).  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 Normal ifade deseni `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`(?(\d{2}-)`|Sonraki üç karakter kısa çizgi ve ardından iki basamak oluşur olup olmadığını belirler.|  
|`\d{2}-\d{7}`|Önceki desen eşleşirse, bir tire yedi rakam ve ardından iki basamak eşleşmesi.|  
|`\d{3}-\d{2}-\d{4}`|Önceki düzeni eşleşmiyorsa, üç ondalık basamak, tire, iki ondalık basamak, başka bir tire ve dört ondalık basamak eşleşir.|  
|`\b`|Bir sözcük sınırıyla eşleş.|  
  
 [Başa dön](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a>Yakalanan Geçerli Bir Gruba Göre Koşullu Eşleştirme  
 Bu dil öğe olup belirtilen bir yakalama grubunu eşleşti bağlı olarak iki desenleri birini eşleştirmeyi dener. Sözdizimi aşağıdaki gibidir:  
  
 `(?(` *ad* `)` *Evet* `|` *yok* `)`  
  
 veya  
  
 `(?(` *sayı* `)` *Evet* `|` *yok* `)`  
  
 Burada *adı* adıdır ve *numarası* bir yakalama grubunu sayısı *Evet* eşleşiyorsa ifadesidir *adı* veya *numarası* bir eşleşmeye sahip ve *hiçbir* mevcut değilse eşleştirilecek isteğe bağlı ifadesidir.  
  
 Varsa *adı* karşılık gelmediğinden normal ifade deseni kullanılan yakalama bir grup adına değişim yapı ifade sınama olarak, önceki bölümde açıklandığı gibi yorumlanır. Genellikle, bunun anlamı *ifade* değerlendiren `false`. Varsa *numarası* normal ifade deseni, normal ifade altyapısı atar kullanılan numaralandırılmış bir yakalama grubuna karşılık gelmiyor bir <xref:System.ArgumentException>.  
  
 Aşağıdaki örnekte gösterildiği örnek bir çeşididir [ya da / veya desen eşleştirme ile &#124; ](#Either_Or) bölümü. Adlı bir yakalama grubunu kullanan `n2` tireyle ve ardından iki basamak oluşur. Değişim Bu yakalama grubunu giriş dizesini eşleşen olup olmadığını testleri oluşturun. Varsa, değişim oluşturmak dokuz basamaklı ABD son yedi rakamı eşleştirmeyi dener İşveren Kimlik numarası (EIN). Henüz gelmemiş dokuz basamaklı ABD eşleştirmeye çalışır Sosyal Güvenlik numarası (SSN).  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 Normal ifade deseni `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`(?<n2>\d{2}-)?`|İki basamaklı çizgi ile ardından sıfır veya bir örneğini Bul. Bu yakalama grubunu adlandırın `n2`.|  
|`(?(n2)`|Test olup olmadığını `n2` giriş dizesini eşleşti.|  
|`)\d{7}`|Varsa `n2` olan yedi ondalık basamak eşleşen eşleşiyor.|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|Varsa `n2` eşleşmeyen, eşleşen üç ondalık basamak, tire, iki ondalık basamak, başka bir tire ve dört ondalık basamak.|  
|`\b`|Bir sözcük sınırıyla eşleş.|  
  
 Değişim numaralandırılmış bir Grup yerine adlandırılmış bir grup kullanan bu örnekte, aşağıdaki örnekte gösterilir. Normal ifade deseni `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
