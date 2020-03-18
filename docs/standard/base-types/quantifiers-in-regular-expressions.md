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
ms.openlocfilehash: f1627248cbed0f03c6fb76ce660f9b2bf7764781
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160020"
---
# <a name="quantifiers-in-regular-expressions"></a>Normal İfadelerdeki Miktar Niceleyiciler
Niceleyiciler, eşleşmenin bulunabilmesi için girişte bir karakter, grup veya karakter sınıfının kaç örneğinin bulunması gerektiğini belirtir.  Aşağıdaki tabloda .NET tarafından desteklenen niceleyiciler listelenir.  
  
|Açgözlü niceleyici|Tembel niceleyici|Açıklama|  
|-----------------------|---------------------|-----------------|  
|`*`|`*?`|Sıfır veya daha fazla kez eşleştirin.|  
|`+`|`+?`|Bir veya daha fazla kez eşleştirin.|  
|`?`|`??`|Sıfırı ya da bir kez eşleştirin.|  
|`{`*n*`}`|`{`*n*`}?`|Tam olarak *n* kez maç.|  
|`{`*n*`,}`|`{`*n*`,}?`|En az *n* kez eşleştirin.|  
|`{`*n* `,` *m*`}`|`{`*n* `,` *m*`}?`|*N'den* *m'ye* kadar olan zamanları eşleştirin.|  
  
 Miktarları `n` `m` ve onsa sabitleri vardır. Normalde, niceleyiciler açgözlüdür; normal ifade altyapısının belirli desenlerdeki birçok olayla mümkün olduğunca eşleşmesine neden olurlar. `?` Karakteri bir niceleyiciye eklemek onu tembelleştirir; normal ifade altyapısının mümkün olduğunca az olayla eşleşmesine neden olur. Açgözlü ve tembel niceleyiciler arasındaki farkın tam bir açıklaması için, bu konuda daha sonra bölüm [Açgözlü ve Tembel Quantifiers](#Greedy) bakın.  
  
> [!IMPORTANT]
> İç içe niceleyiciler (örneğin, normal ifade `(a*)*` deseni gibi) giriş dizesinde karakter sayısının üstel bir işlevi olarak, normal ifade altyapısının gerçekleştirmesi gereken karşılaştırma sayısını artırabilir. Bu davranış ve geçici geçici işleri hakkında daha fazla bilgi için [Geri İzleme'ye](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)bakın.  
  
## <a name="regular-expression-quantifiers"></a>Düzenli İfade Niceleyicileri  
 Aşağıdaki bölümlerde .NET düzenli ifadeleri tarafından desteklenen niceleyiciler listelenir.  
  
> [!NOTE]
> *, +, ?, {, ve } karakterleri normal bir ifade deseninde karşılaşılırsa, normal ifade altyapısı bunları bir [karakter sınıfına](../../../docs/standard/base-types/character-classes-in-regular-expressions.md)dahil edilmedikçe niceleyici veya niceleyici yapılarının bir parçası olarak yorumlar. Bunları bir karakter sınıfının dışındaki gerçek karakterler olarak yorumlamak için, onlardan önce bir ters eğik çizgi ile kaçmalısınız. Örneğin, normal `\*` bir ifade desenindeki dize, gerçek bir yıldız\*işareti (" ") karakter olarak yorumlanır.  
  
### <a name="match-zero-or-more-times-"></a>Match Zero veya More Times: *  
 `*` Niceleyici, önceki öğe sıfır veya daha fazla kez eşleşir. `{0,}` Niceleyiciye eşdeğerdir. `*`tembel eşdeğeri olan açgözlü bir niceleyicidir. `*?`  
  
 Aşağıdaki örnekte bu normal ifade gösteriş. Giriş dizesinde dokuz basamak, beş eşler desen`95`ve `929` `9219`dört `9919`( , , , ve ) yok.  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`91*`|Bir "9"u sıfır veya daha fazla "1" karakterle eşleştirin.|  
|`9*`|Sıfır veya daha fazla "9" karakteri eşleştirin.|  
|`\b`|Bir sözcük sınırında bit.|  
  
### <a name="match-one-or-more-times-"></a>Bir veya Daha Fazla Kez Eşleştir: +  
 `+` Niceleyici, önceki öğeyle bir veya daha fazla kez eşleşir. Bu eşdeğerdir `{1,}`. `+`tembel eşdeğeri olan açgözlü bir niceleyicidir. `+?`  
  
 Örneğin, normal ifade `\ban+\w*?\b` harfi `n`bir veya daha fazla `a` örnek ardından harf ile başlayan tüm sözcükleri eşleştirmeye çalışır. Aşağıdaki örnekte bu normal ifade gösteriş. Normal ifade, , `an` `annual`, `announcement`, `antique`ve , kelimeleri `autumn` eşleşir ve doğru bir şekilde eşleşmiyor ve `all`.  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`an+`|Bir "a" ve ardından bir veya daha fazla "n" karakterini eşleştirin.|  
|`\w*?`|Bir sözcük karakterini sıfır veya daha fazla kez, ancak mümkün olduğunca az kez eşleştirin.|  
|`\b`|Bir sözcük sınırında bit.|  
  
### <a name="match-zero-or-one-time-"></a>Maç Sıfır veya One Time: ?  
 `?` Niceleyici, bir önceki öğe sıfır veya bir kez eşleşir. Bu eşdeğerdir `{0,1}`. `?`tembel eşdeğeri olan açgözlü bir niceleyicidir. `??`  
  
 Örneğin, normal ifade `\ban?\b` harfi sıfır veya harfin `a` `n`bir örneği ardından gelen harfle başlayan tüm sözcükleri eşleştirmeye çalışır. Başka bir deyişle, kelimeleri `a` eşleştirmeye `an`çalışır ve . Aşağıdaki örnekte bu normal ifade gösteriş.  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`an?`|Bir "a" ve ardından sıfır veya bir "n" karakterini eşleştirin.|  
|`\b`|Bir sözcük sınırında bit.|  
  
### <a name="match-exactly-n-times-n"></a>Tam olarak n Times maç: {n}  
 `{` *n* n`}` ölçüleyicisi, *n'nin* herhangi bir tamsayı olduğu önceki öğeyle tam olarak *n* kez eşleşir. `{`*n* `}` olan tembel eşdeğer `{` *n*`}?`açgözlü bir niceleyici olduğunu .  
  
 Örneğin, normal ifade `\b\d+\,\d{3}\b` bir sözcük sınırını eşleştirmeye çalışır ve ardından bir veya daha fazla ondalık basamak ve ardından üç ondalık basamak ve ardından bir sözcük sınırı nı takip eder. Aşağıdaki örnekte bu normal ifade gösteriş.  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`\,`|Virgül karakterini eşleştirin.|  
|`\d{3}`|Üç ondalık basamakla eşleş.|  
|`\b`|Bir sözcük sınırında bit.|  
  
### <a name="match-at-least-n-times-n"></a>En Az n Kez Maç: {n,}  
 `{` *n* n`,}` ölçüleyicisi, *n'nin* herhangi bir karşıcı olduğu önceki öğeyle en az *n* kez eşleşir. `{`*n* `,}` olan tembel eşdeğer `{` *n*`,}?`açgözlü bir niceleyici olduğunu .  
  
 Örneğin, normal ifade, `\b\d{2,}\b\D+` bir sözcük sınırı ve ardından en az iki basamak la eşleşmeye çalışır ve ardından bir sözcük sınırı ve basamaksız bir karakter. Aşağıdaki örnekte bu normal ifade gösteriş. Normal ifade, yalnızca bir `"7 days"` ondalık basamak içerdiğinden tümcecikle eşleşmiyor, ancak tümceciklerle `"10 weeks and 300 years"`başarıyla eşleşiyor.  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`\d{2,}`|En az iki ondalık basamak eşleştirin.|  
|`\b`|Bir sözcük sınırıyla eşleş.|  
|`\D+`|En az bir ondalık olmayan basamak eşleştirin.|  
  
### <a name="match-between-n-and-m-times-nm"></a>n ve m Saatleri Arasındaki Eşleşme: {n,m}  
 `{` *n*n`,`*m* `}` m niceleyici, bir önceki elemanla en az *n* kez eşleşir, ancak *n* ve *m'nin* sayılattığı *m* kereden fazla olamaz. `{`*n*`,`*m* `}` olan tembel eşdeğer `{` *n*`,`*m*`}?`olan açgözlü bir niceleyici olduğunu .  
  
 Aşağıdaki örnekte, normal `(00\s){2,4}` ifade iki sıfır basamak iki ve dört oluşumları arasında eşleşmeye çalışır ve ardından bir boşluk. Giriş dizesinin son bölümünün bu deseni en fazla dört yerine beş kez içerdiğini unutmayın. Ancak, bu alt dizenin yalnızca ilk bölümü (boşluk ve beşinci sıfır çifti) normal ifade deseniyle eşleşir.  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### <a name="match-zero-or-more-times-lazy-match-"></a>Match Zero or More Times (Lazy Match): *?  
 `*?` Niceleyici, önceki öğe sıfır veya daha fazla kez eşleşir, ancak mümkün olduğunca az kez. Bu açgözlü niceleyici tembel `*`meslektaşıdır.  
  
 Aşağıdaki örnekte, normal `\b\w*?oo\w*?\b` ifade dize `oo`içeren tüm sözcükleri eşleşir.  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`\w*?`|Sıfır veya daha fazla sözcük karakterini eşleştirin, ancak mümkün olduğunca az karakter.|  
|`oo`|"oo" dizesini eşleştirin.|  
|`\w*?`|Sıfır veya daha fazla sözcük karakterini eşleştirin, ancak mümkün olduğunca az karakter.|  
|`\b`|Bir sözcük sınırında sona erdirin.|  
  
### <a name="match-one-or-more-times-lazy-match-"></a>Bir veya Daha Fazla Kez Maç (Lazy Match): +?  
 `+?` Niceleyici, önceki öğeyle bir veya daha fazla kez, ancak mümkün olduğunca az kez eşleşir. Bu açgözlü niceleyici tembel `+`meslektaşıdır.  
  
 Örneğin, normal ifade, `\b\w+?\b` sözcük sınırlarına göre ayrılmış bir veya daha fazla karakterle eşleşir. Aşağıdaki örnekte bu normal ifade gösteriş.  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### <a name="match-zero-or-one-time-lazy-match-"></a>Maç Sıfır veya Bir Kez (Tembel Maç): ??  
 `??` Niceleyici, bir önceki öğe sıfır veya bir kez eşleşir, ancak mümkün olduğunca az kez. Bu açgözlü niceleyici tembel `?`meslektaşıdır.  
  
 Örneğin, normal ifade `^\s*(System.)??Console.Write(Line)??\(??` "Console.Write" veya "Console.WriteLine" dizelerini eşleştirmeye çalışır. Dize "Sistem" de içerebilir. önce "Konsol", ve bir açılış parantez tarafından takip edilebilir. Dize bir çizginin başında olmalıdır, ancak beyaz boşluk tan önce gelebilir. Aşağıdaki örnekte bu normal ifade gösteriş.  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Giriş akışının başlangıcını eşleştirin.|  
|`\s*`|Sıfır veya daha fazla boşluk karakteriyle eşleş.|  
|`(System.)??`|"Sistem" dizesinin sıfır veya bir oluşumunu eşleştirin.|  
|`Console.Write`|"Console.Write" dizesini eşleştirin.|  
|`(Line)??`|"Line" dizesinin sıfır veya bir oluşumunu eşleştirin.|  
|`\(??`|Açılış parantezinin sıfır veya bir oluşumunu eşleştirin.|  
  
### <a name="match-exactly-n-times-lazy-match-n"></a>Tam olarak n Times (Lazy Match): {n}?  
 `{` *n* n`}?` ölçüleyicisi, n'nin `n` herhangi bir tamsayı *olduğu* önceki öğeyle tam olarak kez eşleşir. Bu açgözlü niceleyici `{` *n*`}`tembel meslektaşıdır.  
  
 Aşağıdaki örnekte, normal `\b(\w{3,}?\.){2}?\w{3,}?\b` ifade bir Web sitesi adresini tanımlamak için kullanılır. "www.microsoft.com" ve "msdn.microsoft.com" ile eşleştiğini, ancak "web sitem" veya "mycompany.com" ile eşleşmediğini unutmayın.  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`(\w{3,}?\.)`|Maç en az 3 kelime karakterleri, ancak mümkün olduğunca az karakter, bir nokta veya nokta karakteri takip. Bu ilk yakalama grubudur.|  
|`(\w{3,}?\.){2}?`|İlk gruptaki deseni iki kez, ancak mümkün olduğunca az kez eşleştirin.|  
|`\b`|Eşleşmeyi sözcük sınırında sonla.|  
  
### <a name="match-at-least-n-times-lazy-match-n"></a>Maç en az n Kez (Tembel Maç): {n,}?  
 `{` *n* n`,}?` nicelleyici, *n'nin* herhangi `n` bir karşıcı olduğu, ancak mümkün olduğunca az kez önceki öğeyle en az eşleşir. Bu açgözlü niceleyici `{` *n*`,}`tembel meslektaşıdır.  
  
 Bir resim için `{`önceki bölümdeki *n* `}?` niceleyici örneğine bakın. Bu örnekteki normal ifade, bir dönemin ardından en az üç karaktere sahip bir dizeyle eşleştirmek için `{` *n* `,}` nicelini kullanır.  
  
### <a name="match-between-n-and-m-times-lazy-match-nm"></a>N ve m Times Arasındaki Eşleşme (Tembel Maç): {n,m}?  
 `{` *n*`}?` `n` `m` *n* *m* *m* m niceleyici, n ve m'nin hemdemeger olduğu, ancak mümkün olduğunca az kez olduğu zaman ile arasındaki önceki öğeyle eşleşir.`,` Bu açgözlü `{`niceleyici *n*`,`*m*`}`tembel meslektaşıdır.  
  
 Aşağıdaki örnekte, normal `\b[A-Z](\w*?\s*?){1,10}[.!?]` ifade, bir ile on arasında sözcük içeren tümcelerle eşleşir. 18 sözcük içeren bir tümce dışında giriş dizesindeki tüm tüm cümlelerle eşleşir.  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 Normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında başla.|  
|`[A-Z]`|A'dan Z'ye bir büyük harf karakteri eşleştirin.|  
|`(\w*?\s*?)`|Sıfır veya daha fazla sözcük karakterini eşleştirin, ardından bir veya daha fazla boşluk karakteri, ancak mümkün olduğunca az kez. Bu ilk yakalama grubu.|  
|`{1,10}`|Önceki deseni 1 ile 10 kez eşleştirin.|  
|`[.!?]`|Noktalama işaretlerinden herhangi birini ".", "!", veya "?".|  
  
<a name="Greedy"></a>
## <a name="greedy-and-lazy-quantifiers"></a>Açgözlü ve Tembel Niceleyiciler  
 Niceleyicilerin bir dizi iki sürümü vardır:  
  
- Açgözlü bir versiyonu.  
  
     Açgözlü bir niceleyici mümkün olduğunca çok kez bir öğe eşleşmeye çalışır.  
  
- Açgözlü olmayan (veya tembel) bir sürüm.  
  
     Açgözlü olmayan bir nicel, bir öğeyi mümkün olduğunca az kez eşleştirmeye çalışır. Açgözlü bir niceleyiciyi sadece bir `?`.  
  
 Kredi kartı numarası gibi bir sayı dizesinden son dört rakamı ayıklamak için tasarlanmış basit bir normal ifade düşünün. `*` Açgözlü niceleyici kullanan normal ifade sürümü . `\b.*([0-9]{4})\b` Ancak, bir dize iki sayı içeriyorsa, bu normal ifade aşağıdaki örnekte görüldüğü gibi yalnızca ikinci sayının son dört basamağıyla eşleşir.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 `*` Niceleyici önceki öğeyi tüm dizede mümkün olduğunca çok kez eşleştirmeye çalıştığından ve böylece dize sonunda eşleşmesini bulduğundan, normal ifade ilk sayıyla eşleşmez.  
  
 Bu istenilen davranış değildir. Bunun yerine, aşağıdaki `*?`örnekte görüldüğü gibi, her iki sayıdan da basamak ayıklamak için tembel niceleyiciyi kullanabilirsiniz.  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 Çoğu durumda, açgözlü ve tembel niceleyiciler ile düzenli ifadeler aynı eşleşmeleri döndürün. Onlar en sık herhangi bir karakter eşleşen joker`.`( ) metakarakter ile kullanıldığında farklı sonuçlar verir.  
  
## <a name="quantifiers-and-empty-matches"></a>Niceleyiciler ve Boş Eşleşmeler  
 Ölçüleyiciler `*` `+`, ve `{` *n*`,`*m* `}` ve onların tembel meslektaşları yakalamalar minimum sayıda bulunduğunda boş bir maç sonra tekrarlamak asla. Bu kural, olası grup yakalama sayısı sonsuz veya sonsuza yakın olduğunda, niceleyicilerin boş alt ifade eşleşmelerine sonsuz döngüler girmesini önler.  
  
 Örneğin, aşağıdaki kod, sıfır veya bir <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> "a" karakteri `(a?)*`sıfır veya daha fazla kez eşleşen normal ifade deseni ile yönteme yapılan çağrının sonucunu gösterir. Tek yakalama grubunun her "a"yı ve <xref:System.String.Empty?displayProperty=nameWithType>ikinci boş eşleşmeyi yakaladığını, çünkü ilk boş eşleşmenin niceleyicinin yinelemeyi durdurmasına neden olduğunu unutmayın.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 En az ve maksimum sayıda yakalama yı tanımlayan bir yakalama grubu ile sabit sayıda yakalama tanımlayan grup arasındaki pratik farkı `(a\1|(?(1)\1)){0,2}` `(a\1|(?(1)\1)){2}`görmek için, normal ifade modellerini düşünün ve . Her iki normal ifade de aşağıdaki tabloda gösterildiği gibi tanımlanan tek bir yakalama grubundan oluşur.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`(a\1`|Ya maç "a" ilk yakalanan grubun değeri ile birlikte ...|  
|<code>&#124;(?(1)</code>|… veya yakalanan ilk grubun tanımlanıp tanımlanmadığını test edin. (Yapının `(?(1)` bir yakalama grubu tanımlamadığını unutmayın.)|  
|`\1))`|Yakalanan ilk grup varsa, değerini eşleştirin. Grup yoksa, grup eşleşir. <xref:System.String.Empty?displayProperty=nameWithType>|  
  
 İlk normal ifade bu deseni sıfır ile iki kez eşleştirmeye çalışır; ikincisi, tam olarak iki kez. İlk desen ilk yakalama ile yakalama en az <xref:System.String.Empty?displayProperty=nameWithType>sayıda ulaştığından, o maç `a\1`denemek için tekrarasla ; `{0,2}` niceleyici son yinelemede yalnızca boş eşleşmeler sağlar. Buna karşılık, ikinci kez değerlendirir `a\1` çünkü ikinci normal ifade "a" eşleşir; en az yineleme sayısı, 2, motoru boş bir eşleşmeden sonra yinelemeye zorlar.  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
- [Geri Dönüş](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
