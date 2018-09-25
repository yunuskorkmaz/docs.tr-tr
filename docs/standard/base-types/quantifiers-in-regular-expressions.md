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
ms.openlocfilehash: a982082611760e4f901c427af25a0a49a4e243a1
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2018
ms.locfileid: "47027927"
---
# <a name="quantifiers-in-regular-expressions"></a>Normal İfadelerdeki Miktar Belirleyiciler
Bir karakter, Grup veya karakter sınıfı kaç tane giriş eşleşmenin bulunması mevcut olmalıdır, miktar belirleyiciler belirtin.  .NET tarafından desteklenen miktar belirleyiciler aşağıdaki tabloda listelenmektedir.  
  
|Doyumsuz niceleyici|Yavaş miktar belirleyici|Açıklama|  
|-----------------------|---------------------|-----------------|  
|`*`|`*?`|Sıfır veya daha fazla kez eşleştirin.|  
|`+`|`+?`|Bir veya daha fazla kez eşleştirin.|  
|`?`|`??`|Sıfır veya bir kez eşleştirin.|  
|`{` *N* `}`|`{` *N* `}?`|Tam olarak eşleşmesi *n* kez.|  
|`{` *N* `,}`|`{` *N* `,}?`|En az eşleşen *n* kez.|  
|`{` *n* `,` *m* `}`|`{` *n* `,` *m* `}?`|Gelen eşleşen *n* için *m* kez.|  
  
 Miktarları `n` ve `m` tamsayı sabit değerlerdir. Normalde, miktar belirleyiciler doyumsuz; Bunlar, mümkün olduğunca çok tekrarı belirli desenleri eşleştirilecek normal ifade altyapısı neden. Ekleme `?` karakter için bir miktar belirleyiciyi yapar, yavaş; mümkün olduğu kadar az oluşum eşleştirilecek normal ifade altyapısı sağlar. Doyumsuz ve yavaş miktar belirleyiciler arasındaki farkı eksiksiz bir açıklaması için konudaki [Greedy ve yavaş miktar belirleyiciler](#Greedy) bu konuda.  
  
> [!IMPORTANT]
>  İç içe miktar belirleyiciler (örneğin, normal ifade deseni olarak `(a*)*` yapar) normal ifade altyapısının giriş dizesindeki karakterlerin sayısının üstel işlev olarak gerçekleştirmelidir karşılaştırmalar sayısını artırabilirsiniz. Bu davranışı ve onun geçici çözümler hakkında daha fazla bilgi için bkz. [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).  
  
## <a name="regular-expression-quantifiers"></a>Normal ifade miktar belirleyiciler  
 .NET normal ifadeler tarafından desteklenen miktar belirleyiciler aşağıdaki bölümlerde listelenmiştir.  
  
> [!NOTE]
>  *, +,?, {, Ve} karakterleri bir normal ifade deseninde karşılaştı, sürece dahil edilir ve normal ifade altyapısının bunları miktar belirleyiciler veya niceleyici yapıları bir parçası yorumlar bir [karakter sınıfı](../../../docs/standard/base-types/character-classes-in-regular-expressions.md). Bu bir karakter sınıfı dışında değişmez karakter olarak yorumlanması için ters eğik çizgi ile koyarak çıkış gerekir. Örneğin, dize `\*` bir normal ifade deseni değişmez bir yıldız işareti yorumlanır ("\*") karakteri.  
  
### <a name="match-zero-or-more-times-"></a>Eşleşen sıfır veya daha fazla kez: *  
 `*` Niceleyici, önceki öğeyle sıfır veya daha fazla kez eşleşir. Eşdeğerdir `{0,}` nicelik belirteci. `*` doyumsuz bir miktar belirleyiciyi, yavaş bir eşdeğeri olan `*?`.  
  
 Bu normal ifade aşağıdaki örnekte gösterilmektedir. Düzenin ve dört giriş dizesinde dokuz basamak beş eşleşen (`95`, `929`, `9129`, ve `9919`) yapın.  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`91*`|Sıfır veya daha fazla "1" karakterlerinin izlediği bir "9" eşleşir.|  
|`9*`|Sıfır veya daha fazla "9" karakteriyle eşleş.|  
|`\b`|Bir sözcük sınırında bit.|  
  
### <a name="match-one-or-more-times-"></a>Bir veya daha fazla kez eşleştir: +  
 `+` Niceleyici, önceki öğeyle bir veya daha fazla kez eşleşir. Eşdeğerdir `{1,}`. `+` doyumsuz bir miktar belirleyiciyi, yavaş bir eşdeğeri olan `+?`.  
  
 Örneğin, normal ifade `\ban+\w*?\b` harfi ile başlayan tüm sözcükleri eşleştirmeyi dener `a` harfini bir veya daha fazla örneği tarafından izlenen `n`. Bu normal ifade aşağıdaki örnekte gösterilmektedir. Normal ifadeyle eşleşen sözcükler `an`, `annual`, `announcement`, ve `antique`ve eşleşecek şekilde doğru başarısız `autumn` ve `all`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`an+`|Eşleşme bir "a" bir veya daha fazla "n" karakterlerle devam eder.|  
|`\w*?`|Sıfır veya daha fazla kez, ancak en az bir kez mümkün olduğunca bir sözcük karakteriyle eşleş.|  
|`\b`|Bir sözcük sınırında bit.|  
  
### <a name="match-zero-or-one-time-"></a>Eşleşen sıfır veya bir kez:?  
 `?` Niceleyici, önceki öğesi sıfır veya bir zaman eşleşir. Eşdeğerdir `{0,1}`. `?` doyumsuz bir miktar belirleyiciyi, yavaş bir eşdeğeri olan `??`.  
  
 Örneğin, normal ifade `\ban?\b` harfi ile başlayan tüm sözcükleri eşleştirmeyi dener `a` harfi sıfır veya bir örneği tarafından izlenen `n`. Diğer bir deyişle, sözcükleri eşleştirmeye çalışır `a` ve `an`. Bu normal ifade aşağıdaki örnekte gösterilmektedir.  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`an?`|Eşleşme bir "a" sıfır veya bir "n" karakter.|  
|`\b`|Bir sözcük sınırında bit.|  
  
### <a name="match-exactly-n-times-n"></a>Tam olarak n kez eşleştir: {n}  
 `{` *n* `}` niceleyici önceki öğeyle tam olarak eşleşen *n* süreleri ve nerede *n* herhangi bir tamsayıdır. `{`*n* `}` yavaş olan eşdeğerdir doyumsuz bir miktar belirleyici olduğu `{` *n*`}?`.  
  
 Örneğin, normal ifade `\b\d+\,\d{3}\b` bir sözcük sınırı izleyen üç ondalık basamak tarafından izlenen bir veya daha fazla ondalık basamak arkasından bir sözcük sınırı eşleştirmeye çalışır. Bu normal ifade aşağıdaki örnekte gösterilmektedir.  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`\,`|Virgül karakteriyle eşleş.|  
|`\d{3}`|Üç ondalık basamakla eşleş.|  
|`\b`|Bir sözcük sınırında bit.|  
  
### <a name="match-at-least-n-times-n"></a>En az n kez eşleştir: {n,}  
 `{` *n* `,}` niceleyici eşleştirir önceki öğeyle en az *n* süreleri ve nerede *n* herhangi bir tamsayıdır. `{`*n* `,}` yavaş olan eşdeğerdir doyumsuz bir miktar belirleyici olduğu `{` *n*`,}?`.  
  
 Örneğin, normal ifade `\b\d{2,}\b\D+` ardından bir sözcük sınırı ve bir basamak olmayan karakterle en az iki basamak arkasından bir sözcük sınırı eşleştirmeye çalışır. Bu normal ifade aşağıdaki örnekte gösterilmektedir. Tümcecik eşleştirilecek normal ifade başarısız `"7 days"` yalnızca bir adet ondalık rakam içeriyor, ancak başarıyla tümcecikleri eşleşir çünkü `"10 weeks and 300 years"`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`\d{2,}`|En az iki ondalık basamağı eşleştirin.|  
|`\b`|Bir sözcük sınırıyla eşleş.|  
|`\D+`|En az bir ondalık olmayan basamak eşleştirin.|  
  
### <a name="match-between-n-and-m-times-nm"></a>N ile m zamanları arasında eşleşmiyor: {n, m}  
 `{` *n*`,`*m* `}` niceleyici eşleştirir önceki öğeyle en az *n* süreleri, ancak Hayır birden fazla *m*  süreleri ve nerede *n* ve *m* tamsayılardır. `{`*n*`,`*m* `}` yavaş olan eşdeğerdir doyumsuz bir miktar belirleyici olduğu `{` *n*`,`*m* `}?`.  
  
 Aşağıdaki örnekte, normal ifade `(00\s){2,4}` arasında iki ve dört oluşum iki sıfır basamak, ardından bir boşluk eşleştirmeye çalışır. Giriş dizesinin son kısmı bu düzen beş kez içerdiğini unutmayın yerine dört en fazla. Ancak, bu alt dize (en fazla alan ve sıfır beşinci çiftinin) yalnızca ilk bölümü normal ifade deseni ile eşleşir.  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### <a name="match-zero-or-more-times-lazy-match-"></a>Eşleşen sıfır veya daha fazla kez (Lazy eşleşme): *?  
 `*?` Niceleyici, önceki öğeyle sıfır veya daha fazla kez, ancak en az bir kez mümkün olduğunca eşleşir. Doyumsuz niceleyici yavaş karşılığı olan `*`.  
  
 Aşağıdaki örnekte, normal ifade `\b\w*?oo\w*?\b` dizesini içeren tüm sözcüklerle eşleşir `oo`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`\w*?`|Sıfır veya daha fazla sözcük karakterini, ancak mümkün olduğunca kadar az karakterle eşleştirin.|  
|`oo`|"Paylaşımlarınızda" dizesini eşleştirin.|  
|`\w*?`|Sıfır veya daha fazla sözcük karakterini, ancak mümkün olduğunca kadar az karakterle eşleştirin.|  
|`\b`|Bir sözcük sınırında sonlandır.|  
  
### <a name="match-one-or-more-times-lazy-match-"></a>Bir veya daha fazla kez (Lazy eşleşme) eşleşmesi: +?  
 `+?` Niceleyici, önceki öğeyle bir veya daha fazla kez, ancak en az bir kez mümkün olduğunca eşleşir. Doyumsuz niceleyici yavaş karşılığı olan `+`.  
  
 Örneğin, normal ifade `\b\w+?\b` sözcük sınırları tarafından ayrılmış bir veya daha fazla karakter ile eşleşir. Bu normal ifade aşağıdaki örnekte gösterilmektedir.  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### <a name="match-zero-or-one-time-lazy-match-"></a>Eşleşen sıfır veya bir kez (Lazy eşleşme):??  
 `??` Niceleyici, önceki öğesi sıfır veya bir zaman, ancak en az bir kez mümkün olduğunca eşleşir. Doyumsuz niceleyici yavaş karşılığı olan `?`.  
  
 Örneğin, normal ifade `^\s*(System.)??Console.Write(Line)??\(??` dizeleri "Console.Write" veya "Console.WriteLine" eşleştirmeyi dener. Dize, "Sistem" de içerebilir ardına bir sol ayraç "Konsol" ve izlenebilir önce. Dize, boşluk tarafından öncesinde olsa da satırın başında olması gerekir. Bu normal ifade aşağıdaki örnekte gösterilmektedir.  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Giriş akışı başlangıcını eşleştirin.|  
|`\s*`|Sıfır veya daha fazla boşluk karakteriyle eşleş.|  
|`(System.)??`|"Sistem" dizesi sıfır veya bir oluşumunu eşleştirin.|  
|`Console.Write`|"Console.Write" dizesini eşleştirin.|  
|`(Line)??`|"Satır" dizesi sıfır veya bir oluşumunu eşleştirin.|  
|`\(??`|Açma parantezinden sıfır veya bir oluşumunu eşleştirin.|  
  
### <a name="match-exactly-n-times-lazy-match-n"></a>Tam olarak n kez (Lazy eşleşme) eşleşmesi: {n}?  
 `{` *n* `}?` niceleyici önceki öğeyle tam olarak eşleşen `n` süreleri ve nerede *n* herhangi bir tamsayıdır. Doyumsuz niceleyici yavaş karşılığı olan `{` *n*`}+`.  
  
 Aşağıdaki örnekte, normal ifade `\b(\w{3,}?\.){2}?\w{3,}?\b` bir Web sitesi adresi tanımlamak için kullanılır. Bu "www.microsoft.com" ve "msdn.microsoft.com" ile eşleşir ancak "numaralı" veya "mycompany.com" eşleşmiyor unutmayın.  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`(\w{3,}?\.)`|En az 3 sözcük karakterini eşleştirin, ancak mümkün olduğunca az karakter ve ardından bir nokta veya nokta karakteri. Bu ilk yakalama grubudur.|  
|`(\w{3,}?\.){2}?`|İlk grubunda iki kez ancak mümkün olduğunca deseniyle eşleşen.|  
|`\b`|Eşleşme bir sözcük sınırında sonlandır.|  
  
### <a name="match-at-least-n-times-lazy-match-n"></a>En az n kez eşleştir (Lazy eşleşme): {n,}?  
 `{` *n* `,}?` niceleyici eşleştirir önceki öğeyle en az `n` süreleri ve nerede *n* herhangi bir tamsayı mümkün olduğunca ancak gibi birkaç kez gösterir. Doyumsuz niceleyici yavaş karşılığı olan `{` *n*`,}`.  
  
 Örneğin bakın `{` *n* `}?` niceleyici, önceki bölümde bir gösterim. Bu örnekte normal ifadeyi kullanan `{` *n* `,}` bir nokta en az üç karakter içeren bir dizeyle eşleştirme yapmayı nicelik belirteci.  
  
### <a name="match-between-n-and-m-times-lazy-match-nm"></a>N ile m (Lazy eşleşme) saatleri arasında eşleşme: {n, m}?  
 `{` *n*`,`*m* `}?` niceleyici, önceki öğe arasında eşleşen `n` ve `m` süreleri ve nerede *n* ve *m* tam, ancak en az bir kez mümkün olduğunca sayılardır. Doyumsuz niceleyici yavaş karşılığı olan `{` *n*`,`*m*`}`.  
  
 Aşağıdaki örnekte, normal ifade `\b[A-Z](\w*\s+){1,10}?[.!?]` arasında bir ve on sözcükler içeren cümleleri eşleşir. Bu, Giriş dizesinin 18 sözcükler içeren bir cümle hariç tüm cümleleri eşleşir.  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`[A-Z]`|A'dan Z'ye bir büyük harf karakteri eşleştirin.|  
|`(\w*\s+)`|Bir veya daha fazla boşluk karakterlerinin izlediği sıfır veya daha fazla sözcük karakterini eşleştirin. Bu ilk yakalama grubudur.|  
|`{1,10}?`|Önceki desenle arasında 1 ile 10 kez ancak mümkün olduğunca eşleştirin.|  
|`[.!?]`|Noktalama işaretleri herhangi biriyle eşleşmesi ".","!", veya "?".|  
  
<a name="Greedy"></a>   
## <a name="greedy-and-lazy-quantifiers"></a>Doyumsuz ve yavaş miktar belirleyiciler  
 Miktar belirleyiciler iki sürümü vardır:  
  
-   Doyumsuz bir sürümü.  
  
     Doyumsuz bir miktar belirleyiciyi, olası sayıda öğenin eşleştirmeyi dener.  
  
-   Doyumsuz olmayan (veya yavaş) sürümü.  
  
     Doyumsuz olmayan bir miktar belirleyiciyi, mümkün olduğunca bir öğe eşleştirmeyi dener. Basitçe ekleyerek bir yavaş belirleyici birlikte doyumsuz bir miktar belirleyiciyi kapatabilirsiniz bir `?`.  
  
 Son dört rakamı bir kredi kartı numarası gibi sayıdan oluşan bir dize ayıklamak için hedeflenen basit bir normal ifade düşünün. Kullanan normal ifade sürümünü `*` doyumsuz niceleyici olduğu `\b.*([0-9]{4})\b`. Ancak, bir dize iki sayı varsa, bu normal ifade aşağıdaki örnekte gösterildiği gibi yalnızca ikinci numarasının son dört rakamı eşleşir.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 İlk sayı olduğundan eşleştirmek normal ifade başarısız `*` niceleyici gerektiği kadar tüm dizeyi mümkün olduğunca önceki öğeyle eşleşen dener ve eşini dizenin sonuna kadar bulduğu.  
  
 İstediğiniz çalışma biçimini değil. Bunun yerine kullanabileceğiniz `*?`basamak aşağıdaki örnekte gösterildiği gibi her iki numarayı ayıklamak için bir yavaş belirleyici birlikte.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 Çoğu durumda, doyumsuz ve yavaş miktar belirleyiciler Normal ifadelerle aynı eşleşme döndürür. Joker karakter ile kullanıldığında, en yaygın olarak farklı sonuçlar döndürebilir (`.`) meta, herhangi bir karakterle eşleşir.  
  
## <a name="quantifiers-and-empty-matches"></a>Miktar belirleyiciler ve boş bir eşleşme  
 Miktar belirleyiciler `*`, `+`, ve `{` *n*`,`*m* `}` ve boş bir eşleşen sonra ne zaman yavaş karşılıkları hiçbir zaman yineleyin en düşük yakalamalar sayısını bulundu. Bu kural, miktar belirleyiciler olası grup yakalamalarını sayısı sonsuz olduğunda boş alt eşleşmeleri veya sınırsız neredeyse sonsuz döngüler girmesini engeller.  
  
 Örneğin, aşağıdaki kod bir çağrı sonucunu gösterir <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> yöntemi normal ifade deseni ile `(a?)*`, sıfır veya daha fazla kez sıfır veya bir "a" karakterle eşleşir. Tek bir yakalama grubu her "a" olarak yakalar, Not iyi <xref:System.String.Empty?displayProperty=nameWithType>, ancak ilk boş eşleşme yinelenen durdurmak niceleyici neden olduğundan ikinci boş eşleşme olduğundan.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 Pratik tanımlayan en az bir yakalama grubu ve en fazla sayısını yakalamalarına ve yakalamaları sabit sayıda tanımlayan bir farkı görmek için normal ifade desenleri göz önünde bulundurun. `(a\1|(?(1)\1)){0,2}` ve `(a\1|(?(1)\1)){2}`. Her iki normal ifade aşağıdaki tabloda gösterildiği gibi tanımlanmaktadır tek bir yakalama grubu oluşur.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`(a\1`|Ya da eşleşme yakalanan ilk grubun değeri birlikte "a"...|  
|<code>&#124;(?(1)</code>|… veya ilk yakalanan grubu tanımlı olup olmadığını test edin. (Unutmayın `(?(1)` yapısı bir yakalama grubunu tanımlamıyor.)|  
|`\1))`|İlk yakalanan grubu varsa, değeri eşleştirin. Grup mevcut değilse grubunu eşleştirir <xref:System.String.Empty?displayProperty=nameWithType>.|  
  
 Birinci normal ifadeyi sıfır ve iki zaman arasındaki bu desenle eşleşen çalışır; İkincisi, tam olarak iki kez. İlk desen, ilk yakalama ile çalışın, en az sayıda ulaştığında çünkü <xref:System.String.Empty?displayProperty=nameWithType>, hiçbir zaman eşleşecek şekilde denemek için yinelenen `a\1`; `{0,2}` niceleyici son yinelemede yalnızca boş bir eşleşme sağlar. İkinci normal ifade buna karşılık, eşleşen "a", değerlendirdiğinden `a\1` ikinci kez; yinelemeler, 2, en az sayıda sonra boş bir eşleşme yinelemek için altyapı zorlar.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
- [Geri Dönüş](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
