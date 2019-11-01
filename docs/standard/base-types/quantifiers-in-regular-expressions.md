---
title: Normal İfadelerdeki Miktar Niceleyiciler
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
ms.openlocfilehash: a7a870ac32385bf5015f1a95c0246fed6a5c9c05
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084243"
---
# <a name="quantifiers-in-regular-expressions"></a>Normal İfadelerdeki Miktar Niceleyiciler
Nicelik belirteçleri, bir eşleşmenin bulunması için girişte kaç tane karakter, Grup veya karakter sınıfının olması gerektiğini belirtir.  Aşağıdaki tabloda .NET tarafından desteklenen nicelik belirteçleri listelenmektedir.  
  
|Greedy nicelik belirteci|Geç nicelik belirteci|Açıklama|  
|-----------------------|---------------------|-----------------|  
|`*`|`*?`|Sıfır veya daha fazla kez eşleştirin.|  
|`+`|`+?`|Bir veya daha fazla kez eşleştirin.|  
|`?`|`??`|Sıfır veya bir kez eşleştirin.|  
|`{` *n* `}`|`{` *n* `}?`|Tam *n* kez Eşleştir.|  
|`{` *n* `,}`|`{` *n* `,}?`|En az *n* kez Eşleştir.|  
|`{` *n* `,` *e* `}`|`{` *n* `,` *e* `}?`|*N* ile *k* arasında bir kez eşleştirin.|  
  
 `n` ve `m` miktarları tamsayı sabitleridir. Normalde, nicelik belirteçleri DOYUMLAR; normal ifade altyapısının mümkün olduğunca çok sayıda tekrarla eşleşmesini sağlar. `?` karakteri bir nicelik sonuna eklemek yavaş olur; normal ifade altyapısının mümkün olduğunca az oluşum ile eşleşmesini sağlar. Doyumsuz ve yavaş nicelik belirteçleri arasındaki fark hakkında açıklayıcı bir açıklama için, bu konunun ilerleyen kısımlarında bulunan [doyumsuz ve geç nicelik belirteçleri](#Greedy) bölümüne bakın.  
  
> [!IMPORTANT]
> Nicelik belirteçleri iç içe (örneğin, normal ifade deseninin `(a*)*` olduğu gibi), giriş dizesindeki karakter sayısının üstel bir işlevi olarak, normal ifade altyapısının gerçekleştirmesi gereken karşılaştırmalar sayısını artırabilir. Bu davranış ve geçici çözümleri hakkında daha fazla bilgi için bkz. [geri izleme](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).  
  
## <a name="regular-expression-quantifiers"></a>Normal Ifade nicelik belirteçleri  
 Aşağıdaki bölümlerde .NET normal ifadeleri tarafından desteklenen nicelik belirteçleri listelenmektedir.  
  
> [!NOTE]
> Normal ifade düzeninde *, +,?, {, ve} karakter ile karşılaşılırsa, normal ifade altyapısı onları nicelik belirteçleri veya bir [karakter sınıfına](../../../docs/standard/base-types/character-classes-in-regular-expressions.md)dahil olmadıkları sürece belirleyici yapıların bir parçası olarak yorumlar. Bunları bir karakter sınıfı dışında değişmez karakterler olarak yorumlamak için, üzerlerine ters eğik çizgi koyarak kaçış yapmanız gerekir. Örneğin, bir normal ifade deseninin `\*` dize, sabit bir yıldız işareti ("\*") karakteri olarak yorumlanır.  
  
### <a name="match-zero-or-more-times-"></a>Sıfır veya daha fazla kez eşleştir: *  
 `*` nicelik belirteci önceki öğeyle sıfır veya daha fazla kez eşleşir. `{0,}` nicelik toplamına eşdeğerdir. `*`, geç eşdeğerini `*?`olan doyumsuz nicelik belirleyicgidir.  
  
 Aşağıdaki örnekte bu normal ifade gösterilmektedir. Giriş dizesindeki dokuz basamak, bu Düzenle ve dört (`95`, `929`, `9219`ve `9919`) ile aynıdır.  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 Normal ifade deseninin, aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`91*`|"9" öğesini ve ardından sıfır veya daha fazla "1" karakteri eşleştirin.|  
|`9*`|Sıfır veya daha fazla "9" karakteri eşleştirin.|  
|`\b`|Bir sözcük sınırında bit.|  
  
### <a name="match-one-or-more-times-"></a>Bir veya daha fazla kez eşleştir: +  
 `+` nicelik belirteci önceki öğeyle bir veya daha fazla kez eşleşir. `{1,}`eşdeğerdir. `+`, geç eşdeğerini `+?`olan doyumsuz nicelik belirleyicgidir.  
  
 Örneğin, normal ifade `\ban+\w*?\b`, harf `a` ile başlayan tüm kelimeleri eşleştirmeyi dener ve sonra bir veya daha fazla harf `n`örneği gelir. Aşağıdaki örnekte bu normal ifade gösterilmektedir. Normal ifade `an`, `annual`, `announcement`ve `antique`sözcüklerle eşleşir ve doğru şekilde `autumn` ve `all`eşleşemez.  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 Normal ifade deseninin, aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`an+`|Bir "a" ve arkasından bir veya daha fazla "n" karakteri eşleştirin.|  
|`\w*?`|Bir sözcük karakterini sıfır veya daha fazla kez ve mümkün olduğunca az eşleştirin.|  
|`\b`|Bir sözcük sınırında bit.|  
  
### <a name="match-zero-or-one-time-"></a>Sıfır veya bir kez eşleştir:?  
 `?` nicelik belirteci, önceki öğeyle sıfır veya bir kez eşleşir. `{0,1}`eşdeğerdir. `?`, geç eşdeğerini `??`olan doyumsuz nicelik belirleyicgidir.  
  
 Örneğin, normal ifade `\ban?\b`, harf `a` ile başlayan tüm kelimeleri eşleştirmeyi dener ve ardından sıfır veya harf `n`bir örneği. Diğer bir deyişle, `a` ve `an`kelimeleri eşleştirmeye çalışır. Aşağıdaki örnekte bu normal ifade gösterilmektedir.  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 Normal ifade deseninin, aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`an?`|Bir "a" ve arkasından sıfır veya bir "n" karakteri ile eşleştirin.|  
|`\b`|Bir sözcük sınırında bit.|  
  
### <a name="match-exactly-n-times-n"></a>Tam n kez eşleştir: {n}  
 `{`*n*`}` nicelik belirteci önceki öğeyle tam olarak *n* kez eşleşir, burada *n* herhangi bir tamsayıdır. `{`*n*`}`, yavaş eşdeğeri `{`*n*`}?`olan doyumsuz nicelik belirleyicisimleridir.  
  
 Örneğin, normal ifade `\b\d+\,\d{3}\b` bir sözcük sınırını, ardından bir veya daha fazla ondalık basamağı ve ardından bir sözcük sınırının ardından üç ondalık basamak ile eşleştirmeye çalışır. Aşağıdaki örnekte bu normal ifade gösterilmektedir.  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 Normal ifade deseninin, aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`\,`|Virgül karakteriyle eşleştirin.|  
|`\d{3}`|Üç ondalık basamakla eşleş.|  
|`\b`|Bir sözcük sınırında bit.|  
  
### <a name="match-at-least-n-times-n"></a>En az n kez eşleştir: {n,}  
 `{`*n*`,}` nicelik belirteci önceki öğeyle en az *n* kez eşleşir, burada *n* herhangi bir tamsayıdır. `{`*n*`,}`, yavaş eşdeğeri `{`*n*`,}?`olan doyumsuz nicelik belirleyicisimleridir.  
  
 Örneğin, normal ifade `\b\d{2,}\b\D+` bir sözcük sınırını ve ardından bir sözcük sınırı ve basamaklı bir karakter tarafından izlenen en az iki basamakla eşleştirmeye çalışır. Aşağıdaki örnekte bu normal ifade gösterilmektedir. Normal ifade, yalnızca bir ondalık basamak içerdiğinden `"7 days"` tümcecik ile eşleşemez, ancak `"10 weeks and 300 years"`tümcecikleriyle başarıyla eşleşiyor.  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 Normal ifade deseninin, aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`\d{2,}`|En az iki ondalık basamakla eşleştirin.|  
|`\b`|Bir sözcük sınırıyla eşleş.|  
|`\D+`|En az bir ondalık olmayan basamakla eşleştirin.|  
  
### <a name="match-between-n-and-m-times-nm"></a>N ve y zamanları arasında eşleştir: {n, d}  
 `{`*n*`,`h`}` nicelik belirteci, önceki öğeyle en az *n* kez, ancak *n* *ve 5* ' *in* tamsayı olduğu bir kez eşleşir. `{`*n*`,`*d*`}`, geç eşdeğeri `{`*n*`,`*d*`}?`olan doyumsuz nicelik belirleyicgidir.  
  
 Aşağıdaki örnekte, normal ifade `(00\s){2,4}` iki sıfır basamağının iki ve dört tekrarıyla ve ardından bir boşluk ile eşleştirmeye çalışır. Giriş dizesinin son bölümünün, en fazla dört kez bu kalıbı içerdiğini unutmayın. Ancak, bu alt dizenin yalnızca başlangıç kısmı (alana kadar ve sıfır ikilisi) normal ifade düzeniyle eşleşir.  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### <a name="match-zero-or-more-times-lazy-match-"></a>Sıfır veya daha fazla kez Eşleştir (geç eşleşme): *?  
 `*?` nicelik belirteci önceki öğeyle sıfır veya daha fazla kez eşleşir, ancak mümkün olduğunca az. `*`doyumsuz nicelik sayısının geç karşılığı.  
  
 Aşağıdaki örnekte, normal ifade `\b\w*?oo\w*?\b` dize `oo`içeren tüm sözcüklerle eşleşir.  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 Normal ifade deseninin, aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`\w*?`|Sıfır veya daha fazla sözcük karakteri ile mümkün olduğunca az karakter eşleştirin.|  
|`oo`|"Oo" dizesiyle eşleşir.|  
|`\w*?`|Sıfır veya daha fazla sözcük karakteri ile mümkün olduğunca az karakter eşleştirin.|  
|`\b`|Bir sözcük sınırında sonlandır.|  
  
### <a name="match-one-or-more-times-lazy-match-"></a>Bir veya daha fazla kez Eşleştir (geç eşleşme): +?  
 `+?` nicelik belirteci önceki öğeyle bir veya daha fazla kez eşleşir, ancak mümkün olduğunca az. `+`doyumsuz nicelik sayısının geç karşılığı.  
  
 Örneğin, normal ifade `\b\w+?\b` sözcük sınırlarıyla ayrılmış bir veya daha fazla karakterle eşleşir. Aşağıdaki örnekte bu normal ifade gösterilmektedir.  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### <a name="match-zero-or-one-time-lazy-match-"></a>Sıfır veya bir kez Eşleştir (geç eşleşme):??  
 `??` nicelik belirteci, önceki öğeyle sıfır veya bir kez, ancak mümkün olduğunca az eşleşir. `?`doyumsuz nicelik sayısının geç karşılığı.  
  
 Örneğin, normal ifade `^\s*(System.)??Console.Write(Line)??\(??` "Console. Write" veya "Console. WriteLine" dizeleriyle eşleştirmeye çalışır. Dize Ayrıca "sistem" i içerebilir. "konsolundan" ve ardından bir açılış ayracı gelebilir. Dize bir satırın başında olmalıdır, ancak önünde boşluk olabilir. Aşağıdaki örnekte bu normal ifade gösterilmektedir.  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 Normal ifade deseninin, aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Giriş akışının başlangıcını eşleştirin.|  
|`\s*`|Sıfır veya daha fazla boşluk karakteriyle eşleş.|  
|`(System.)??`|"System." dizesinin sıfır veya bir oluşumunu eşleştirin.|  
|`Console.Write`|"Console. Write" dizesiyle eşleştirin.|  
|`(Line)??`|"Line" dizesinin sıfır veya bir oluşumunu eşleştirin.|  
|`\(??`|Açma parantezinin sıfır veya bir oluşumunu eşleştirin.|  
  
### <a name="match-exactly-n-times-lazy-match-n"></a>Tam n kez Eşleştir (geç eşleşme): {n}?  
 `{`*n*`}?` nicelik belirteci, yukarıdaki öğeyle tam olarak `n` sürelerle eşleşir, burada *n* herhangi bir tamsayıdır. `{`*n*`}`doyumsuz nicelik sayısının geç karşılığı.  
  
 Aşağıdaki örnekte, `\b(\w{3,}?\.){2}?\w{3,}?\b` normal ifade bir Web sitesi adresini belirlemek için kullanılır. "Www.microsoft.com" ve "msdn.microsoft.com" ile eşleşir, ancak "mywebsite" veya "mycompany.com" ile eşleşmez.  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 Normal ifade deseninin, aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`(\w{3,}?\.)`|En az 3 sözcük karakteri, ancak mümkün olduğunca az karakter ve nokta veya nokta karakteriyle eşleştirin. Bu ilk yakalama grubudur.|  
|`(\w{3,}?\.){2}?`|İlk gruptaki stili iki kez, ancak mümkün olduğunca az eşleştirin.|  
|`\b`|Eşleşmeyi bir sözcük sınırında sonlandır.|  
  
### <a name="match-at-least-n-times-lazy-match-n"></a>En az n kez Eşleştir (geç eşleşme): {n,}?  
 `{`*n*`,}?` nicelik belirteci önceki öğeyle en az `n` kez eşleşir, burada *n* herhangi bir tamsayıdır, ancak mümkün olduğunca az. `{`*n*`,}`doyumsuz nicelik sayısının geç karşılığı.  
  
 Bir çizim için önceki bölümdeki `{`*n*`}?` nicelik için örneğe bakın. Bu örnekteki normal ifade, en az üç karakteri ve ardından bir nokta gelen bir dizeyle eşleştirmek için `{`*n*`,}` nicelik belirteci kullanır.  
  
### <a name="match-between-n-and-m-times-lazy-match-nm"></a>N ve k kez Eşleştir (geç eşleşme): {n, d}?  
 `{`*n*`,`h`}?` nicelik belirteci, yukarıdaki öğeyle `n` ve `m` süreleriyle eşleşir, burada *n* ve *b* , mümkün olduğunca az sayılardır. Bu, *n*`,`*d*`}``{`doyumsuz nicelik belirleyicisinin geç karşılığından oluşur.  
  
 Aşağıdaki örnekte, normal ifade `\b[A-Z](\w*?\s*?){1,10}[.!?]` bir ve on sözcükten oluşan cümlelere eşler. 18 sözcük içeren bir cümle hariç giriş dizesindeki tüm cümlelere eşleşir.  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 Normal ifade deseninin, aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`[A-Z]`|A 'dan Z 'ye büyük harfli bir karakter eşleştirin.|  
|`(\w*?\s*?)`|Sıfır veya daha fazla sözcük karakterini, ardından bir veya daha fazla boşluk karakterini ve mümkün olduğunca az kez eşleştirin. Bu ilk yakalama grubudur.|  
|`{1,10}`|Önceki Düzenle 1 ila 10 kez eşleştirin.|  
|`[.!?]`|".", "!" Veya "?" noktalama karakterlerinden birini eşleştirin.|  
  
<a name="Greedy"></a>   
## <a name="greedy-and-lazy-quantifiers"></a>Greedy ve yavaş nicelik belirteçleri  
 Nicelik belirteçleri sayısının iki sürümü vardır:  
  
- Doyumsuz sürümü.  
  
     Doyumsuz nicelik sayısı bir öğeyi mümkün olduğunca çok kez eşleştirmeyi dener.  
  
- Doyumsuz olmayan (veya geç) bir sürüm.  
  
     Doyumsuz olmayan nicelik süreleri, bir öğeyi mümkün olduğunca az eşleştirmeyi dener. Yalnızca bir `?`ekleyerek doyumsuz nicelik sayısını yavaş bir nicelik ya dönüştürebilirsiniz.  
  
 Kredi kartı numarası gibi bir sayı dizesinden son dört basamağı çıkarmak amaçlanan basit bir normal ifade düşünün. `*` doyumsuz nicelik sayısını kullanan normal ifade sürümü `\b.*([0-9]{4})\b`. Ancak, bir dize iki sayı içeriyorsa, bu normal ifade yalnızca ikinci sayının son dört basamağıyla eşleşir, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 `*` nicelik süresi tüm dizede olabildiğince çok kez eşleşmesi ve bu nedenle dizenin sonunda eşleşmesini bulduğundan, normal ifade ilk sayıyla eşleşemez.  
  
 Bu, istenen davranış değildir. Bunun yerine, aşağıdaki örnekte gösterildiği gibi, her iki sayıdan de basamak çıkarmak için `*?`yavaş nicelik sayısını kullanabilirsiniz.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 Çoğu durumda, doyumsuz ve yavaş nicelik belirteçleri olan normal ifadeler aynı eşleşmeleri döndürür. Bunlar, herhangi bir karakterle eşleşen joker karakter (`.`) metakarakteriyle birlikte kullanıldıkları zaman genellikle farklı sonuçlar döndürür.  
  
## <a name="quantifiers-and-empty-matches"></a>Nicelik belirteçleri ve boş eşleşmeler  
 `*`, `+`ve `{`*n`,`h*`}`, en az sayıda yakalama bulunduğunda boş bir eşleşmesinden sonra bunların yavaş karşılıkları hiçbir zaman tekrarlamamıştır. Bu kural, olası grup sayısı en fazla sonsuz veya sonsuz olduğunda, nicelik belirteçleri boş alt ifade üzerinde sonsuz döngüler girmesini engeller.  
  
 Örneğin, aşağıdaki kod, sıfıra veya bir "a" karakteriyle veya daha fazla kez eşleşen normal ifade düzeniyle `(a?)*`<xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> yöntemi çağrısının sonucunu gösterir. Tek yakalama grubunun her bir "a" ve <xref:System.String.Empty?displayProperty=nameWithType>olduğunu, ancak ilk boş eşleşme nicelik belirleyicinin yinelemeyi durdurmasına neden olduğu için ikinci boş eşleşme olmadığını unutmayın.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 En düşük ve en yüksek sayıda yakalama tanımlayan bir yakalama grubu arasındaki pratik farkı görmek için ve sabit sayıda yakalama tanımlayan bir tane, `(a\1|(?(1)\1)){0,2}` ve `(a\1|(?(1)\1)){2}`normal ifade desenlerini göz önünde bulundurun. Her iki normal ifade de, aşağıdaki tabloda gösterildiği gibi tanımlanan tek bir yakalama grubundan oluşur.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`(a\1`|"A" ile birlikte yakalanan ilk grubun değerini eşleştirin...|  
|<code>&#124;(?(1)</code>|… ya da ilk yakalanan grubun tanımlanıp tanımlanmadığını test edin. (`(?(1)` yapısının bir yakalama grubu tanımlamadığını unutmayın.)|  
|`\1))`|Yakalanan ilk grup varsa, değeriyle eşleştirin. Grup yoksa, Grup <xref:System.String.Empty?displayProperty=nameWithType>eşleşmeyecektir.|  
  
 İlk normal ifade, bu kalıbı sıfır ve iki kez eşleştirmeye çalışır; İkincisi, tam olarak iki kez. İlk model, ilk <xref:System.String.Empty?displayProperty=nameWithType>yakalamasına sahip en az sayıda yakalamaya ulaştığından, `a\1`eşleşmeyi denemeye hiçbir şekilde tekrarlamamalıdır; `{0,2}` nicelik belirteci, son yinelemede yalnızca boş eşleşmelerin kullanılmasına izin verir. Buna karşılık ikinci normal ifade, `a\1` ikinci bir kez değerlendirirken, "a" ile eşleşir; yineleme sayısı alt sınırı olan 2, altyapının boş bir eşleşmesinden sonra tekrarlanmasını zorlar.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Geri Dönüş](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
