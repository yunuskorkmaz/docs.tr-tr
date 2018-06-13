---
title: Normal İfadelerdeki Miktar Belirleyiciler
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, quantifiers
- metacharacters, quantifiers
- minimal matching quantifiers
- quantifiers in regular expressions
- .NET Framework regular expressions, quantifiers
- quantifiers
- lazy quantifiers
ms.assetid: 36b81212-6511-49ed-a8f1-ff080415312f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 374ef3e015ee477c5979e2e31574aabfdd03dd1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579099"
---
# <a name="quantifiers-in-regular-expressions"></a>Normal İfadelerdeki Miktar Belirleyiciler
Miktar belirleyiciler kaç tane karakter, Grup veya karakter sınıfı örneğinin bulunması bir eşleşme için giriş bulunmalıdır belirtin.  Aşağıdaki tabloda .NET tarafından desteklenen nicelik listeler.  
  
|Doyumsuz niceleyici|Yavaş niceleyici|Açıklama|  
|-----------------------|---------------------|-----------------|  
|`*`|`*?`|Sıfır veya daha fazla kez eşleşir.|  
|`+`|`+?`|Bir veya birden çok kez eşleşir.|  
|`?`|`??`|Sıfır veya bir kez eşleşir.|  
|`{` *N* `}`|`{` *N* `}?`|Tam olarak eşleştiğinden *n* kez.|  
|`{` *N* `,}`|`{` *N* `,}?`|En az eşleşen *n* kez.|  
|`{` *n* `,` *m* `}`|`{` *n* `,` *m* `}?`|Gelen eşleşen *n* için *m* kez.|  
  
 Miktarları `n` ve `m` tamsayı sabittir. Normalde, nicelik doyumsuz; Bunlar, mümkün olduğunca belirli modelleri sayıda oluşumları eşleştirilecek normal ifade altyapısı neden. Sonuna ekleme `?` bir niceleyici karakter kılar yavaş; mümkün olduğunca en az yinelenme eşleştirilecek normal ifade alt neden olur. Doyumsuz ve yavaş miktar belirleyiciler arasındaki farkı tam bir açıklaması için bkz [Greedy ve yavaş miktar belirleyiciler](#Greedy) bu konuda daha sonra.  
  
> [!IMPORTANT]
>  İç içe geçme nicelik (örneğin, normal ifade deseni olarak `(a*)*` yapar) normal ifade altyapısı giriş dizedeki karakter sayısını üstel bir işlevi olarak gerçekleştirmelisiniz karşılaştırmaları sayısını artırabilirsiniz. Bu davranış ve kendi geçici çözümler hakkında daha fazla bilgi için bkz: [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).  
  
## <a name="regular-expression-quantifiers"></a>Normal ifade miktar belirleyiciler  
 Aşağıdaki bölümlerde .NET normal ifadeleri tarafından desteklenen nicelik listelenmektedir.  
  
> [!NOTE]
>  *, +,?, {, Ve} bir normal ifade deseni karakteri ile karşılaşıldı, yer alan sürece normal ifade altyapısı bunları nicelik veya niceleyici yapıları bir parçası olarak yorumlar bir [karakter sınıfı](../../../docs/standard/base-types/character-classes-in-regular-expressions.md). Bu karakter sınıf dışındaki değişmez karakter olarak yorumlamak için ters bölü işareti koyarak çıkış gerekir. Örneğin, dize `\*` bir normal ifade deseni değişmez değer bir yıldız işareti olarak yorumlanır ("\*") karakter.  
  
### <a name="match-zero-or-more-times-"></a>Eşleşen sıfır veya daha fazla kez: *  
 `*` Niceleyici önceki öğesi sıfır veya daha fazla kez eşleştirir. Eşdeğer olan `{0,}` niceleyici. `*` yavaş olan eşdeğerdir doyumsuz niceleyici olan `*?`.  
  
 Aşağıdaki örnek, bu normal ifade gösterilmektedir. Modeli ve dört giriş dizisinde dokuz basamak beş eşleşen (`95`, `929`, `9129`, ve `9919`) desteklemez.  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`91*`|"Sıfır veya daha fazla"1"karakterle devam etmelidir 9" eşleşir.|  
|`9*`|Sıfır veya daha fazla "9" karakter eşleşmesi.|  
|`\b`|Bir sözcük sınırında bit.|  
  
### <a name="match-one-or-more-times-"></a>Bir veya birden çok kez eşleşen: +  
 `+` Niceleyici önceki öğesi bir veya birden çok kez eşleştirir. Eşdeğer olan `{1,}`. `+` yavaş olan eşdeğerdir doyumsuz niceleyici olan `+?`.  
  
 Örneğin, normal ifade `\ban+\w*?\b` harfiyle başlayan tüm sözcükleri eşleştirmeyi dener `a` harf bir veya daha fazla örnekleri tarafından izlenen `n`. Aşağıdaki örnek, bu normal ifade gösterilmektedir. Sözcükleri normal ifadeyle eşleşen `an`, `annual`, `announcement`, ve `antique`ve eşleşecek şekilde doğru başarısız `autumn` ve `all`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`an+`|Eşleşen bir "a" bir veya daha fazla "n" karakterle devam etmelidir.|  
|`\w*?`|Bir sözcük karakteriyle sıfır veya daha fazla kez, ancak gibi birkaç kez mümkün olduğunca aynı.|  
|`\b`|Bir sözcük sınırında bit.|  
  
### <a name="match-zero-or-one-time-"></a>Eşleşen sıfır veya bir kez:?  
 `?` Niceleyici önceki öğesi sıfır veya bir zaman eşleşir. Eşdeğer olan `{0,1}`. `?` yavaş olan eşdeğerdir doyumsuz niceleyici olan `??`.  
  
 Örneğin, normal ifade `\ban?\b` harfiyle başlayan tüm sözcükleri eşleştirmeyi dener `a` harf sıfır veya bir örnekleri tarafından izlenen `n`. Diğer bir deyişle, sözcükleri eşleştirmeye çalışır `a` ve `an`. Aşağıdaki örnek, bu normal ifade gösterilmektedir.  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`an?`|Eşleşen bir "a" sıfır veya bir "n" karakter.|  
|`\b`|Bir sözcük sınırında bit.|  
  
### <a name="match-exactly-n-times-n"></a>Tam olarak n kez eşleşen: {n}  
 `{` *n* `}` niceleyici önceki öğesi tam olarak eşleşen *n* zaman, nerede *n* herhangi bir tamsayıdır. `{`*n* `}` yavaş olan eşdeğerdir doyumsuz niceleyici olan `{` *n*`}?`.  
  
 Örneğin, normal ifade `\b\d+\,\d{3}\b` word sınır tarafından izlenen üç ondalık basamak ve ardından bir veya daha fazla ondalık basamak arkasından bir word sınır eşleştirmeye çalışır. Aşağıdaki örnek, bu normal ifade gösterilmektedir.  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`\,`|Virgül karakteriyle eşleşmesi.|  
|`\d{3}`|Üç ondalık basamakla eşleş.|  
|`\b`|Bir sözcük sınırında bit.|  
  
### <a name="match-at-least-n-times-n"></a>En az n kez eşleşen: {n}  
 `{` *n* `,}` niceleyici eşleşen önceki öğesi en az *n* zaman, nerede *n* herhangi bir tamsayıdır. `{`*n* `,}` yavaş olan eşdeğerdir doyumsuz niceleyici olan `{` *n*`}?`.  
  
 Örneğin, normal ifade `\b\d{2,}\b\D+` en az iki basamak ardından word sınır ve sayı olmayan karakter ve ardından word sınır eşleştirmeye çalışır. Aşağıdaki örnek, bu normal ifade gösterilmektedir. Tümcecik eşleştirilecek normal ifade başarısız `"7 days"` tek bir ondalık basamak içeriyor, ancak başarılı bir şekilde tümcecikleri eşleşen çünkü `"10 weeks and 300 years"`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`\d{2,}`|En az iki ondalık basamak eşleşir.|  
|`\b`|Bir sözcük sınırıyla eşleş.|  
|`\D+`|En az bir olmayan ondalık basamak eşleşir.|  
  
### <a name="match-between-n-and-m-times-nm"></a>N ve m zamanları arasında eşleştirme: {n, m}  
 `{` *n*`,`*m* `}` niceleyici eşleşen önceki öğesi en az *n* kez ancak hiçbir birden fazla *m*  zaman, nerede *n* ve *m* tamsayı olduğunu. `{`*n*`,`*m* `}` yavaş olan eşdeğerdir doyumsuz niceleyici olan `{` *n*`,`*m* `}?`.  
  
 Aşağıdaki örnekte, normal ifade `(00\s){2,4}` iki ve dört oluşumları iki arasında bir boşluk bırakarak sıfır basamak eşleştirmeye çalışır. Giriş dizesi'nın son kısmı bu deseni beş kez içerdiğini unutmayın yerine en fazla dört. Ancak, bu alt dizeyi (kadar boşluk ve sıfır beşinci çiftinin) yalnızca ilk bölümü normal ifade deseni eşleştirir.  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### <a name="match-zero-or-more-times-lazy-match-"></a>Eşleşen sıfır veya daha fazla kez (yavaş eşleşme): *?  
 `*?` Niceleyici önceki öğesi sıfır veya daha fazla kez, mümkün olduğunca ancak gibi birkaç kez eşleştirir. Doyumsuz nicelik, yavaş karşılık gelen olan `*`.  
  
 Aşağıdaki örnekte, normal ifade `\b\w*?oo\w*?\b` dizesini içeren tüm sözcükleri eşleşen `oo`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`\w*?`|Sıfır veya daha fazla sözcük karakterleri, mümkün olduğunca az karakter ancak aynı.|  
|`oo`|"Oo" dize eşleşmesi.|  
|`\w*?`|Sıfır veya daha fazla sözcük karakterleri, mümkün olduğunca az karakter ancak aynı.|  
|`\b`|Word sınırında sonlandırın.|  
  
### <a name="match-one-or-more-times-lazy-match-"></a>Bir veya daha fazla kez (yavaş eşleşme) eşleşmesi: +?  
 `+?` Niceleyici önceki öğesi bir veya birden çok kez, mümkün olduğunca ancak gibi birkaç kez eşleştirir. Doyumsuz nicelik, yavaş karşılık gelen olan `+`.  
  
 Örneğin, normal ifade `\b\w+?\b` word sınırları tarafından ayrılmış bir veya daha fazla karakter ile eşleşir. Aşağıdaki örnek, bu normal ifade gösterilmektedir.  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### <a name="match-zero-or-one-time-lazy-match-"></a>Eşleşen sıfır veya bir kez (yavaş eşleşme):??  
 `??` Niceleyici önceki öğesi sıfır veya bir zaman mümkün olduğunca ancak gibi birkaç kez eşleştirir. Doyumsuz nicelik, yavaş karşılık gelen olan `?`.  
  
 Örneğin, normal ifade `^\s*(System.)??Console.Write(Line)??\(??` "Console.Write" veya "Console.WriteLine" dizeleri eşleştirmeye çalışır. "Sistem" dizesini de içerir "Konsol" ve onu bir açma parantezi izlenebilir önce. Dize, boşluk tarafından öncesinde rağmen bir satır başında olması gerekir. Aşağıdaki örnek, bu normal ifade gösterilmektedir.  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Giriş akışı başlangıcı eşleşir.|  
|`\s*`|Sıfır veya daha fazla boşluk karakteriyle eşleş.|  
|`(System.)??`|"Sistem" dizenin sıfır veya bir örneğinin aynı.|  
|`Console.Write`|"Console.Write" dize eşleşmesi.|  
|`(Line)??`|"Satır" dizenin sıfır veya bir örneğinin aynı.|  
|`\(??`|Sıfır veya bir geçişi parantez ile eşleşir.|  
  
### <a name="match-exactly-n-times-lazy-match-n"></a>N kez (yavaş eşleşme) tam olarak eşleşen: {n}?  
 `{` *n* `}?` niceleyici önceki öğesi tam olarak eşleşen `n` zaman, nerede *n* herhangi bir tamsayıdır. Doyumsuz nicelik, yavaş karşılık gelen olan `{` *n*`}+`.  
  
 Aşağıdaki örnekte, normal ifade `\b(\w{3,}?\.){2}?\w{3,}?\b` bir Web sitesi adresi tanımlamak için kullanılır. Bu "www.microsoft.com" ve "msdn.microsoft.com" eşleştirir ancak "numaralı" veya "mycompany.com" eşleşmiyor unutmayın.  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`(\w{3,}?\.)`|En az 3 word karakterlerle eşleşen ancak mümkün olduğunca az karakter, nokta veya nokta karakteri tarafından izlenen. Bu ilk yakalama grubudur.|  
|`(\w{3,}?\.){2}?`|İki kez ilk grubundaki ancak mümkün olduğunca birkaç kez desenle eşleşen.|  
|`\b`|Son bir word sınırında eşleşmiyor.|  
  
### <a name="match-at-least-n-times-lazy-match-n"></a>En az n kez eşleşen (yavaş eşleşme): {n}?  
 `{` *n* `,}?` niceleyici eşleşen önceki öğesi en az `n` zaman, nerede *n* mümkün olduğunca ancak gibi birkaç kez herhangi bir tamsayı değil. Doyumsuz nicelik, yavaş karşılık gelen olan `{` *n*`,}`.  
  
 Örneğin bkz `{` *n* `}?` niceleyici bir çizim için önceki bölümdeki. Bu örnekte normal ifade kullanan `{` *n* `,}` ardından bir noktayla en az üç karakterden uzun bir dize eşleşmesi için niceleyici.  
  
### <a name="match-between-n-and-m-times-lazy-match-nm"></a>N ve m (yavaş eşleşme) saatleri arasında eşleşme: {n, m}?  
 `{` *n*`,`*m* `}?` niceleyici eşleşir önceki arasında `n` ve `m` zaman, nerede *n* ve *m* tamsayılar, mümkün olduğunca ancak gibi birkaç kez olur. Doyumsuz nicelik, yavaş karşılık gelen olan `{` *n*`,`*m*`}`.  
  
 Aşağıdaki örnekte, normal ifade `\b[A-Z](\w*\s+){1,10}?[.!?]` arasında bir ve on sözcükler içeren tümceler eşleşir. Giriş dizesi 18 sözcükler içeren bir cümle hariç tüm cümlelerde eşleşir.  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`[A-Z]`|Bir büyük harf karakter A'dan Z'ye eşleşmesi.|  
|`(\w*\s+)`|Bir veya daha fazla boşluk karakterlerinin ardından sıfır veya daha fazla word karakterlerle eşleşen. Bu ilk yakalama grubudur.|  
|`{1,10}?`|1 ile 10 zamanları arasında ancak mümkün olduğunca birkaç kez olarak önceki desenle eşleşen.|  
|`[.!?]`|Herhangi bir noktalama karakter eşleşmesi ".","!", veya "?".|  
  
<a name="Greedy"></a>   
## <a name="greedy-and-lazy-quantifiers"></a>Doyumsuz ve yavaş miktar belirleyiciler  
 Miktar belirleyiciler iki sürümü vardır:  
  
-   Doyumsuz bir sürümü.  
  
     Doyumsuz niceleyici öğenin olası sayıda eşleştirmeyi dener.  
  
-   Doyumsuz olmayan (veya yavaş) sürümü.  
  
     Doyumsuz olmayan niceleyici öğenin mümkün olduğunca birkaç kez eşleştirmeyi dener. Basitçe ekleyerek yavaş niceleyici doyumsuz niceleyici kapatabilirsiniz bir `?`.  
  
 Kredi kartı numarası gibi sayıların bir dizeden son dört rakamı ayıklamak için tasarlanmıştır basit bir normal ifade göz önünde bulundurun. Kullanan normal ifade sürümü `*` doyumsuz niceleyici olan `\b.*([0-9]{4})\b`. Ancak, bir dize iki sayı içeriyorsa, bu normal ifade aşağıdaki örnekte gösterildiği gibi ikinci sayı yalnızca, son dört rakamı eşleşir.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 İlk sayı çünkü eşleştirmek normal ifade başarısız `*` niceleyici çalışırsa önceki öğesi tüm dizeyi mümkün olduğunca çok kez olarak eşleşecek şekilde ve eşini dizesi sonunda bulduğu şekilde.  
  
 Bu istediğiniz davranış değildir. Bunun yerine, kullanabileceğiniz `*?`basamak aşağıdaki örnekte gösterildiği gibi her iki numarayı ayıklamak için yavaş niceleyici.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 Çoğu durumda, aynı eşleşmeleri doyumsuz ve yavaş miktar belirleyiciler Normal ifadelerle döndür. Joker karakterle kullanıldığında bunlar en yaygın olarak farklı sonuçlar döndürür (`.`) meta karakteri, herhangi bir karakter ile eşleşir.  
  
## <a name="quantifiers-and-empty-matches"></a>Miktar belirleyiciler ve boş eşleşiyor  
 Miktar belirleyiciler `*`, `+`, ve `{` *n*`,`*m* `}` ve boş bir eşledikten sonra ne zaman yavaş dekiler hiçbir zaman yineleyin en düşük yakalamaları sayısı bulundu. Bu kural, olası grup yakalamaları maksimum sayısı sonsuz olduğunda boş alt eşleşmeleri ya da sonsuz yanına sonsuz döngüler girişini nicelik engeller.  
  
 Örneğin, aşağıdaki kod bir çağrı sonucunu gösterir <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> normal ifade deseni yöntemiyle `(a?)*`, sıfır veya daha fazla kez sıfır veya bir "a" karakter eşleşir. Tek bir yakalama Grup her "a" olarak yakalamalarına Not hem de <xref:System.String.Empty?displayProperty=nameWithType>, ancak bu ilk boş eşleşme yinelenen durdurmak niceleyici neden olduğundan ikinci boş eşleşme olduğunu.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 En az tanımlayan bir yakalama grubunu ve maksimum sayısını yakalar ve yakalamaları sabit sayıda tanımlayan bir pratik birbirinden görmek için normal ifade desenleri göz önünde bulundurun. `(a\1|(?(1)\1)){0,2}` ve `(a\1|(?(1)\1)){2}`. Her iki normal ifadeler aşağıdaki tabloda gösterildiği gibi tanımlanan tek bir yakalama grubunu oluşur.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`(a\1`|Ya da eşleşme ilk yakalanan grubunun değeri birlikte "a"...|  
|<code>&#124;(?(1)</code>|… veya ilk yakalanan Grup tanımlı olup olmadığını test etme. (Unutmayın `(?(1)` yapı bir yakalama grubunu tanımlamak değil.)|  
|`\1))`|İlk yakalanan grup varsa değerini eşleşmesi. Grup mevcut değilse Grup eşleşir <xref:System.String.Empty?displayProperty=nameWithType>.|  
  
 İlk normal ifade bu deseni ve iki kez arasındaki eşleştirmeyi dener; İkincisi, tam olarak iki kez. İlk desen yakalamaları ilk yakalanmasını ile en az sayıda ulaştığında çünkü <xref:System.String.Empty?displayProperty=nameWithType>, hiçbir zaman eşleşecek şekilde denemek için yinelenen `a\1`; `{0,2}` niceleyici son yinelemede yalnızca boş eşleşmeleri sağlar. Buna karşılık, ikinci normal ifadeyle eşleşir "a", değerlendirildiği `a\1` ikinci kez; yineleme, 2, en az sayıda sonra boş bir eşleşme yinelenecek altyapısı zorlar.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [Geri Dönüş](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
