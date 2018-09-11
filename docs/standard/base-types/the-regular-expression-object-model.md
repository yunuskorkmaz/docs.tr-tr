---
title: Normal İfade Nesnesi Modeli
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, backreferences
- Regex class
- Match class
- pattern-matching with regular expressions, backreferences
- .NET Framework regular expressions, classes
- CaptureCollection class
- Group class
- characters [.NET Framework], backreferences
- substrings
- .NET Framework regular expressions, backreferences
- searching with regular expressions, classes
- backreferences
- Capture class
- repeating groups of characters
- MatchCollection class
- parsing text with regular expressions, backreferences
- regular expressions [.NET Framework]
- characters [.NET Framework], regular expressions
- classes [.NET Framework], regular expression
- regular expressions [.NET Framework], classes
- characters [.NET Framework], metacharacters
- metacharacters, regular expression classes
- metacharacters, backreferences
- parsing text with regular expressions, classes
- regular expressions [.NET Framework], backreferences
- strings [.NET Framework], regular expressions
- pattern-matching with regular expressions, classes
- GroupCollection class
ms.assetid: 49a21470-64ca-4b5a-a889-8e24e3c0af7e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 856b7c8a842b173fbf3e31323ce7224fc05a4f12
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44361715"
---
# <a name="the-regular-expression-object-model"></a>Normal İfade Nesnesi Modeli
<a name="introduction"></a> Bu konuda, .NET normal ifadeleriyle çalışan kullanılan nesne modelini açıklar. Aşağıdaki bölümleri içerir:  
  
-   [Normal ifade altyapısı](#Engine)  
  
-   [MatchCollection ve nesneleri eşleştir](#Match_and_MCollection)  
  
-   [Grup koleksiyonu](#GroupCollection)  
  
-   [Yakalanan grubu](#the_captured_group)  
  
-   [Yakalama toplama](#CaptureCollection)  
  
-   [Tek tek yakalama](#the_individual_capture)  
  
<a name="Engine"></a>   
## <a name="the-regular-expression-engine"></a>Normal ifade altyapısı  
 .NET içinde normal ifade motoru tarafından temsil edilen <xref:System.Text.RegularExpressions.Regex> sınıfı. Normal ifade altyapısı, ayrıştırma ve normal bir ifadeyi derlemek ve bir Giriş dizesinin normal ifade deseniyle eşleşen işlemleri gerçekleştirmek için sorumludur. .NET normal ifade nesnesi modeli merkezi bileşeni altyapısıdır.  
  
 Normal ifade altyapısı iki yoldan birini kullanabilirsiniz:  
  
-   Statik yöntemleri çağırarak <xref:System.Text.RegularExpressions.Regex> sınıfı. Yöntem parametreleri, giriş dizesi ve normal ifade deseni içerir. Normal ifade altyapısı, statik yöntem çağrılarında aynı normal ifadeyi kullanan statik normal ifade yöntemleri yinelenen çağrıları oldukça iyi bir performans sunmak için kullanılan normal ifadeler önbelleğe alır.  
  
-   Örnekleme tarafından bir <xref:System.Text.RegularExpressions.Regex> sınıf yapıcısına bir normal ifade geçirerek nesnesi. Bu durumda, <xref:System.Text.RegularExpressions.Regex> nesne değişmez (salt okunur) ve tek bir normal ifade ile sıkı şekilde bağlı bir normal ifade motorunu temsil eder. Normal ifadeler tarafından kullanıldığından <xref:System.Text.RegularExpressions.Regex> örnekleri önbelleğe alınmaz, değil örneğini oluşturmalıdır bir <xref:System.Text.RegularExpressions.Regex> birden çok kez aynı normal ifadeyi içeren nesne.  
  
 Yöntemlerini çağırabilirsiniz <xref:System.Text.RegularExpressions.Regex> sınıfı aşağıdaki işlemleri gerçekleştirmek için:  
  
-   Bir dizeyi bir normal ifade deseni ile eşleşip eşleşmediğini belirler.  
  
-   Tek bir eşleştirme veya ilk eşleşme ayıklayın.  
  
-   Tüm eşleşmeleri ayıklayın.  
  
-   Eşleşen bir alt dizenin yerini alır.  
  
-   Tek bir dize, dize dizisi bölün.  
  
 Bu işlemleri aşağıdaki bölümlerde açıklanmıştır.  
  
### <a name="matching-a-regular-expression-pattern"></a>Bir normal ifade deseni eşleştirme  
 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> Yöntemi döndürür `true` dize deseni eşleşiyorsa veya `false` Aksi takdirde. <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> Yöntemi genellikle dize girişi doğrulamak için kullanılır. Örneğin, aşağıdaki kodu bir dize geçerli bir sosyal güvenlik numarası Amerika Birleşik Devletleri'nde bulunan eşleşmesini sağlar.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/validate1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/validate1.vb#1)]  
  
 Normal ifade deseni `^\d{3}-\d{2}-\d{4}$` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Giriş dizesinin başında eşleştirin.|  
|`\d{3}`|Üç ondalık basamakla eşleş.|  
|`-`|Bir tire eşleştirin.|  
|`\d{2}`|İki ondalık basamağı eşleştirin.|  
|`-`|Bir tire eşleştirin.|  
|`\d{4}`|Dört ondalık basamağı eşleştirin.|  
|`$`|Giriş dizesinin sonuyla eşleş.|  
  
### <a name="extracting-a-single-match-or-the-first-match"></a>Tek bir eşleştirme veya ilk eşleşme ayıklanıyor  
 <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> Yöntemi döndürür bir <xref:System.Text.RegularExpressions.Match> bir normal ifade deseniyle eşleşen ilk alt dizeyi hakkında bilgi içeren nesne. Varsa `Match.Success` özelliği döndürür `true`, belirten bir eşleşme bulunamadı, çağırarak sonraki eşleşme hakkında bilgi alabilirsiniz <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> yöntemi. Bu yöntem çağrılarının kadar devam edebilirsiniz `Match.Success` özelliği döndürür `false`. Örneğin, aşağıdaki kullanan kod <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> yinelenen sözcüklerin ilk geçtiği bir dizeyi bulmak için yöntemi. Ardından <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> ek oluşumların bulmak için yöntemi. Örnek inceler `Match.Success` özelliği geçerli eşleşmenin başarılı olup olmadığını ve bir çağrı olup olmadığını belirlemek için her yöntem çağrısının sonra <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> yöntemi izlemelidir.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match1.vb#2)]  
  
 Normal ifade deseni `\b(\w+)\W+(\1)\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|  
|`\W+`|Bir veya daha fazla sözcük olmayan karakterle eşleş.|  
|`(\1)`|İlk yakalanan dize eşleşmesi. Bu ikinci yakalama grubudur.|  
|`\b`|Eşleşme bir sözcük sınırında sonlandır.|  
  
### <a name="extracting-all-matches"></a>Tüm eşleşmeleri ayıklanıyor  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> Yöntemi döndürür bir <xref:System.Text.RegularExpressions.MatchCollection> normal ifade altyapısı giriş dizesinde bulunan tüm eşleşmeleri hakkında bilgi içeren nesne. Örneğin, önceki örnekte çağrılacak yazılması <xref:System.Text.RegularExpressions.Regex.Matches%2A> yöntemi yerine <xref:System.Text.RegularExpressions.Regex.Match%2A> ve <xref:System.Text.RegularExpressions.Match.NextMatch%2A> yöntemleri.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matches1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matches1.vb#3)]  
  
### <a name="replacing-a-matched-substring"></a>Eşleşen bir alt dizenin değiştirme  
 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> Yöntemi belirtilen dizenin veya normal ifade deseni ile normal ifade deseniyle eşleşen ve değişiklik tüm giriş dizesiyle döndüren her alt dizenin yerini alır. Örneğin, aşağıdaki kod bir ABD para birimi simgesini bir ondalık sayı önce bir dize ekler.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/replace1.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/replace1.vb#4)]  
  
 Normal ifade deseni `\b\d+\.\d{2}\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`\.`|Bir noktayı eşleştirin.|  
|`\d{2}`|İki ondalık basamağı eşleştirin.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Değiştirme deseni `$$$&` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Değiştirme dizesi|  
|-------------|------------------------|  
|`$$`|Dolar işareti ($) karakterini.|  
|`$&`|Eşleşen alt dizenin tamamı.|  
  
### <a name="splitting-a-single-string-into-an-array-of-strings"></a>Tek bir dize dize dizisi olarak bölme  
 <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> Yöntemi, Giriş dizesinin bir normal ifade eşleştirmesi tarafından tanımlanan konumlarda böler. Örneğin, aşağıdaki kod bir dize dizisine numaralanmış bir liste öğeleri yerleştirir.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/split1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/split1.vb#5)]  
  
 Normal ifade deseni `\b\d{1,2}\.\s` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\d{1,2}`|Bir veya iki ondalık basamağı eşleştirin.|  
|`\.`|Bir noktayı eşleştirin.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
  
<a name="Match_and_MCollection"></a>   
## <a name="the-matchcollection-and-match-objects"></a>MatchCollection ve nesneleri eşleştir  
 Normal ifade yöntemleri, normal ifade nesnesi modelinin bir parçası olan iki nesneleri döndürür: <xref:System.Text.RegularExpressions.MatchCollection> nesnesi ve <xref:System.Text.RegularExpressions.Match> nesne.  
  
<a name="the_match_collection"></a>   
### <a name="the-match-collection"></a>Eşleşme topluluğu  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> Yöntemi döndürür bir <xref:System.Text.RegularExpressions.MatchCollection> içeren nesne <xref:System.Text.RegularExpressions.Match> bulunan normal ifade motoru, giriş dizesinde gerçekleştikleri sırada tüm eşleşmeleri temsil eden nesneleri. Herhangi bir eşleşme varsa vardır, yöntem döndürür bir <xref:System.Text.RegularExpressions.MatchCollection> nesneyle üye yok. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> Size erişim koleksiyonun tek tek üyeleri dizine göre gelen özellik sağlar sıfır bir değerinden daha az <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> özelliği. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A> koleksiyonun dizin oluşturucu (C#) ve varsayılan özelliği (Visual Basic'te) var.  
  
 Varsayılan olarak, çağrı <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> yöntemi doldurmak için geç değerlendirme kullanır <xref:System.Text.RegularExpressions.MatchCollection> nesne. Tam olarak doldurulan bir koleksiyonu gibi gereken özelliklerine erişimi <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> özellikleri, bir performans cezası gerektirebilir. Sonuç olarak, koleksiyon kullanarak erişim öneririz <xref:System.Collections.IEnumerator> tarafından döndürülen nesne <xref:System.Text.RegularExpressions.MatchCollection.GetEnumerator%2A?displayProperty=nameWithType> yöntemi. Tek tek dillerin yapıları, aşağıdaki gibi sağlayın `For Each` Visual Basic'te ve `foreach` C# ' ta, sarmalama koleksiyonunun <xref:System.Collections.IEnumerator> arabirimi.  
  
 Aşağıdaki örnekte <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%29?displayProperty=nameWithType> doldurmak için yöntemi bir <xref:System.Text.RegularExpressions.MatchCollection> bir Giriş dizesinin içinde bulunan tüm eşleşmeler nesne. Örnek koleksiyonu sıralar, eşleşen bir dize dizisine kopyalar ve bir tamsayı dizisinde karakter konumlarının kaydeder.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matchcollection1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matchcollection1.vb#6)]  
  
<a name="the_match"></a>   
### <a name="the-match"></a>Eşleşme  
 <xref:System.Text.RegularExpressions.Match> Sınıfı, bir tek normal ifade eşleştirmesi sonucunu temsil eder. Erişebildiğiniz <xref:System.Text.RegularExpressions.Match> iki yolla nesneler:  
  
-   Bunları alarak <xref:System.Text.RegularExpressions.MatchCollection> tarafından döndürülen nesne <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> yöntemi. Tek tek almak için <xref:System.Text.RegularExpressions.Match> nesnelerini yinelemek koleksiyonu kullanarak bir `foreach` (C# ' de) veya `For Each`... `Next` (Visual Basic'te) oluşturun veya kullanın <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> belirli bir almak için özellik <xref:System.Text.RegularExpressions.Match> nesne dizini veya adı. Ayrıca tek tek alabilirsiniz <xref:System.Text.RegularExpressions.Match> nesnelerini koleksiyondan gelen dizine göre koleksiyon yineleme tarafından sıfır için daha az, koleksiyondaki nesne sayısı. Eriştiğinden, ancak bu yöntem geç değerlendirme avantajlarından almaz <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> özelliği.  
  
     Aşağıdaki örnek, tek tek alır. <xref:System.Text.RegularExpressions.Match> nesnelerin bir <xref:System.Text.RegularExpressions.MatchCollection> koleksiyonunu kullanarak yineleme nesne `foreach` veya `For Each`... `Next` oluşturun. Normal ifade yalnızca giriş dizesindeki "abc" dizesini eşleştirir.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match2.vb#7)]  
  
-   Çağırarak <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> döndüren yöntemi bir <xref:System.Text.RegularExpressions.Match> bir dize veya bir dizenin bir kısmını ilk eşleşmeyi temsil eden nesne. Değerini alarak eşleşme bulundu olup olmadığını belirlemek `Match.Success` özelliği. Alınacak <xref:System.Text.RegularExpressions.Match> sonraki eşleşmeleri temsil eden nesneleri çağrı <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> yöntemi kadar sürekli olarak, `Success` özelliği döndürülen <xref:System.Text.RegularExpressions.Match> nesnedir `false`.  
  
     Aşağıdaki örnekte <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> ' % s'dizesi "abc" giriş dizesinde eşleştirilecek yöntemleri.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match3.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match3.vb#8)]  
  
 İki özelliklerini <xref:System.Text.RegularExpressions.Match> dönüş koleksiyon nesnelerini sınıfı:  
  
-   <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> Özelliği döndürür bir <xref:System.Text.RegularExpressions.GroupCollection> yakalama eşleşen alt dizeler hakkında bilgi içeren nesne grupları normal ifade deseni.  
  
-   `Match.Captures` Özelliği döndürür bir <xref:System.Text.RegularExpressions.CaptureCollection> sınırlı kullanımı olan nesne. Koleksiyon için doldurulmamış bir <xref:System.Text.RegularExpressions.Match> nesnesi `Success` özelliği `false`. Aksi takdirde, tek bir içerdiği <xref:System.Text.RegularExpressions.Capture> aynı bilgileri nesnesi <xref:System.Text.RegularExpressions.Match> nesne.  
  
 Bu nesneler hakkında daha fazla bilgi için bkz: [Grup koleksiyon](#GroupCollection) ve [yakalama toplama](#CaptureCollection) daha sonra bu konudaki bölümler.  
  
 İki ek özelliklerini <xref:System.Text.RegularExpressions.Match> sınıfı eşleşme hakkında bilgi sağlar. `Match.Value` Özelliği, normal ifade deseni ile eşleşen girdi dizesindeki alt dizeyi döndürür. `Match.Index` Özelliği, giriş dizesinde eşleşen dizeyi sıfır tabanlı başlangıç konumunu döndürür.  
  
 <xref:System.Text.RegularExpressions.Match> Sınıfı ayrıca iki deseni eşleştirme yöntemlerine sahiptir:  
  
-   <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> Yöntemi geçerli tarafından temsil edilen eşleşmenin sonrasına eşleşme bulur <xref:System.Text.RegularExpressions.Match> nesne ve döndürür bir <xref:System.Text.RegularExpressions.Match> eşleşen temsil eden nesne.  
  
-   <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> Yöntemi, eşleştirilen dizeyi bir belirtilen değiştirme işlemi gerçekleştirir ve sonucu döndürür.  
  
 Aşağıdaki örnekte <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemi $ simgesi ve iki kesirli basamaklar içeren tüm sayıları öncesinde bir boşluk önüne ekleyin.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/result1.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/result1.vb#9)]  
  
 Normal ifade deseni `\b\d+(,\d{3})*\.\d{2}\b` aşağıdaki tabloda gösterildiği gibi tanımlanmaktadır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`(,\d{3})*`|Üç ondalık basamak gelen bir virgül sıfır veya daha fazla oluşumunu eşleyin.|  
|`\.`|Ondalık nokta karakteri Eşleştir.|  
|`\d{2}`|İki ondalık basamağı eşleştirin.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Değiştirme deseni `$$ $&` eşleşen alt dizenin bir dolar işareti ($) simgesi değiştirilmesi gerektiğini belirtir ( `$$` deseni), boşluk ve eşleşme değerini ( `$&` deseni).  
  
 [Başa dön](#introduction)  
  
<a name="GroupCollection"></a>   
## <a name="the-group-collection"></a>Grup koleksiyonu  
 <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> Özelliği döndürür bir <xref:System.Text.RegularExpressions.GroupCollection> içeren nesne <xref:System.Text.RegularExpressions.Group> yakalanan tek bir eşleştirme grubunda temsil eden nesneleri. İlk <xref:System.Text.RegularExpressions.Group> (0 dizininde) koleksiyon nesnesinde tüm eşleşmeyi temsil eder. Aşağıdaki her nesnenin sonuçlarını tek bir yakalama grubunu temsil eder.  
  
 Tek tek almak <xref:System.Text.RegularExpressions.Group> kullanarak koleksiyonundaki nesneleri <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> özelliği. Adsız grupları koleksiyondaki sıralı konumlarına göre alabilir ve adlandırılmış gruplara adı veya sıra konumu alınamıyor. Adlandırılmamış yakalamaları koleksiyondaki ilk görünür ve soldan sağa dizinlenir normal ifade deseninde göründükleri sırayla. Adlandırılmış yakalamalar dizin haline getirilir, soldan sağa doğru adlandırılmamış yakalamaları sonra normal ifade deseninde göründükleri sırayla. Hangi numaralandırılmış gruplar eşleştirme yöntemi bir özel normal ifade için döndürülen koleksiyon kullanılabilir belirlemek için örnek çağırabilirsiniz <xref:System.Text.RegularExpressions.Regex.GetGroupNumbers%2A?displayProperty=nameWithType> yöntemi. Hangi adlandırılmış gruplar koleksiyonunda kullanılabilir olduğunu belirlemek için örnek çağırabileceğiniz <xref:System.Text.RegularExpressions.Regex.GetGroupNames%2A?displayProperty=nameWithType> yöntemi. Her iki yöntem tarafından herhangi bir normal ifade eşleştirmeler analiz genel amaçlı yordamlarını özellikle yararlıdır.  
  
 <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> Koleksiyon C# ve Visual Basic koleksiyon nesnesinin varsayılan özellik Oluşturucusu bir özelliktir. Bu kişi anlamına gelir <xref:System.Text.RegularExpressions.Group> nesneleri erişilebilir diziniyle (veya adlandırılmış gruplar söz konusu olduğunda, ada göre) gibi:  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupsyntax1.cs#13)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupsyntax1.vb#13)]  
  
 Aşağıdaki örnek, ay, gün ve tarihin yıl değerini yakalamak için gruplama yapıları kullanan bir normal ifade tanımlar.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupcollection1.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupcollection1.vb#10)]  
  
 Normal ifade deseni `\b(\w+)\s(\d{1,2}),\s(\d{4})\b` aşağıdaki tabloda gösterildiği gibi tanımlanmaktadır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`(\d{1,2})`|Bir veya iki ondalık basamağı eşleştirin. Bu ikinci yakalama grubudur.|  
|`,`|Bir virgülü eşleştirin.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`(\d{4})`|Dört ondalık basamağı eşleştirin. Bu, üçüncü yakalama grubudur.|  
|`\b`|Eşleşme bir sözcük sınırında sonlandır.|  
  
 [Başa dön](#introduction)  
  
<a name="the_captured_group"></a>   
## <a name="the-captured-group"></a>Yakalanan grubu  
 <xref:System.Text.RegularExpressions.Group> Sınıfı tek bir yakalama grubu sonucu temsil eder. Normal bir ifade ile tanımlanan yakalama grupları temsil eden grubu nesneleri tarafından döndürülen <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> özelliği <xref:System.Text.RegularExpressions.GroupCollection> tarafından döndürülen nesne <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliği. <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> Özelliği oluşturucuda (C#) ve (Visual Basic'te) için varsayılan özelliği <xref:System.Text.RegularExpressions.Group> sınıfı. Koleksiyonunu kullanarak Yinelem yaparak tek tek üyeleri alabilirsiniz `foreach` veya `For Each` oluşturun. Örneğin, önceki bölüme bakın.  
  
 Aşağıdaki örnekte, iç içe gruplama yapıları grupları dizelere yakalamak için kullanır. Normal ifade deseni `(a(b))c` "abc" dizesini eşleştirir. "Ab" alt dizenin ilk yakalama grubu ve alt dizeyi "b" için ikinci yakalama grubu atar.  
  
 [!code-csharp[RegularExpressions.Classes#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#6)]
 [!code-vb[RegularExpressions.Classes#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#6)]  
  
 Aşağıdaki örnek, adlandırılmış gruplama yapıları alt dizelerin noktalı virgül (;) normal ifade böler "DATANAME:VALUE" biçimindeki verileri içeren bir dizeden yakalamak için kullanır.  
  
 [!code-csharp[RegularExpressions.Classes#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#8)]
 [!code-vb[RegularExpressions.Classes#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#8)]  
  
 Normal ifade deseni `^(?<name>\w+):(?<value>\w+)` aşağıdaki tabloda gösterildiği gibi tanımlanmaktadır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Giriş dizesinin başında eşleşmeye başla.|  
|`(?<name>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu yakalama grubunun adıdır `name`.|  
|`:`|Bir iki nokta üst üste eşleştirin.|  
|`(?<value>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu yakalama grubunun adıdır `value`.|  
  
 Özelliklerini <xref:System.Text.RegularExpressions.Group> sınıfı yakalanan grubu hakkında bilgi sağlar: `Group.Value` özelliği, yakalanan alt dizeyi içerir `Group.Index` özelliği Girişmetnindekiyakalanangrububaşlangıçkonumunugösterir`Group.Length` yakalanan metnin uzunluğunu özelliği içerir ve `Group.Success` özelliği, bir alt dizesi yakalama grubu tarafından tanımlanan örnekle eşleşen olup olmadığını gösterir.  
  
 Bir gruba miktar Belirleyicileri uygulamak (daha fazla bilgi için [miktar belirleyiciler](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)) yakalama grubu iki yolla başına bir yakalama arasındaki ilişkiyi değiştirir:  
  
-   Varsa `*` veya `*?` (Bu, sıfır veya daha fazla eşleşme belirtir) nicelik, bir gruba uygulandığında, bir yakalama grubunu, giriş dizesinde bir eşleşme olmayabilir. Yakalanan metin özelliklerini olduğunda <xref:System.Text.RegularExpressions.Group> nesne, aşağıdaki tabloda gösterildiği gibi ayarlanır.  
  
    |Grup özelliği|Değer|  
    |--------------------|-----------|  
    |`Success`|`false`|  
    |`Value`|<xref:System.String.Empty?displayProperty=nameWithType>|  
    |`Length`|0|  
  
     Aşağıdaki örnek, bir gösterim sağlar. Normal ifade deseninde `aaa(bbb)*ccc`, sıfır veya daha fazla kez ilk yakalama grubu ("bbb" alt) ile eşleştirilebilir. "Aaaccc" Giriş dizesinin desenle eşleşir çünkü yakalama grubu bir eşleşme yok.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/nocapture1.cs#11)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/nocapture1.vb#11)]  
  
-   Nicelik, bir yakalama grubu tarafından tanımlanan bir desenle birden çok defa geçmelerine eşleşebilir. Bu durumda, `Value` ve `Length` özelliklerini bir <xref:System.Text.RegularExpressions.Group> nesne yalnızca son yakalanan alt dizeyi hakkında bilgiler içerir. Örneğin, aşağıdaki normal ifade, nokta ile biten tek bir cümle ile eşleşir. Yapıları gruplandırma iki kullanır: ilk bir boşluk karakteri; birlikte kelimeler yakalar. İkinci kelimeler yakalar. Normal ifadenin tamamını bir cümle yakalanırken başarılı olsa da örnekteki çıktının gösterdiği gibi ikinci yakalama grubu yalnızca son sözcüğü yakalar.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/lastcapture1.cs#12)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/lastcapture1.vb#12)]  
  
 [Başa dön](#introduction)  
  
<a name="CaptureCollection"></a>   
## <a name="the-capture-collection"></a>Yakalama toplama  
 <xref:System.Text.RegularExpressions.Group> Nesne yalnızca son yakalama hakkında bilgi içerir. Ancak, bir yakalama grubu tarafından yapılan yakalamaları kümesinin tamamını hala kullanılabilir <xref:System.Text.RegularExpressions.CaptureCollection> tarafından döndürülen nesne <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> özelliği. Her bir koleksiyonun üyesi olduğundan bir <xref:System.Text.RegularExpressions.Capture> bunlar yakalanan sırada Bu yakalama grubu tarafından yapılan bir yakalama temsil eden nesne (ve bu nedenle, yakalanan dizeleri eşleşti soldan sağa doğru sırayla giriş dizesinde). Tek tek almak <xref:System.Text.RegularExpressions.Capture> nesnelerini koleksiyondan iki yöntemden biriyle:  
  
-   Bir yapı gibi kullanarak koleksiyon aracılığıyla yineleme tarafından `foreach` (C# ' de) veya `For Each` (Visual Basic'te).  
  
-   Kullanarak <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A?displayProperty=nameWithType> dizine göre belirli bir nesneye almak için özellik. <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A> Özelliği <xref:System.Text.RegularExpressions.CaptureCollection> nesnenin (Visual Basic'te) varsayılan özellik veya dizin oluşturucu (C#).  
  
 Bir miktar belirleyici bir yakalama grubunu uygulanmazsa <xref:System.Text.RegularExpressions.CaptureCollection> nesnesini içeren tek bir <xref:System.Text.RegularExpressions.Capture> aynı eşleşme hakkında bilgi sağladığından, çok az ilgi nesne kendi <xref:System.Text.RegularExpressions.Group> nesne. Bir yakalama grubu için bir miktar belirleyiciyi uygulanırsa <xref:System.Text.RegularExpressions.CaptureCollection> nesnesi yakalama grubu tarafından yapılan tüm öğeleri içerir ve olarak aynı yakalama koleksiyonun son üyesini temsil <xref:System.Text.RegularExpressions.Group> nesne.  
  
 Örneğin, normal ifade deseni kullanırsanız `((a(b))c)+` (burada + nicelik, bir veya daha fazla eşleşme belirtir) yakalamak için "abcabcabc" dizesi ile eşleşen <xref:System.Text.RegularExpressions.CaptureCollection> her nesne <xref:System.Text.RegularExpressions.Group> nesne üç üye içerir.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capturecollection1.cs#14)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capturecollection1.vb#14)]  
  
 Aşağıdaki örnek normal ifadeyi kullanan `(Abc)+` "XYZAbcAbcAbcXYZAbcAb" dizesinde "Abc" dizesinin bir veya daha fazla ardışık çalıştırmaları bulunacak. Bu örnek kullanımını gösterir <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> birden fazla grubundan dönmesini yakalanan alt dizeler.  
  
 [!code-csharp[RegularExpressions.Classes#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#5)]
 [!code-vb[RegularExpressions.Classes#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#5)]  
  
 [Başa dön](#introduction)  
  
<a name="the_individual_capture"></a>   
## <a name="the-individual-capture"></a>Tek tek yakalama  
 <xref:System.Text.RegularExpressions.Capture> Sonuçlarını tek bir alt ifade yakalama sınıfı içerir. <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType> Eşleşen metin özelliği içerir ve <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType> özelliği, eşleşen alt dizenin başlar giriş dizesindeki sıfır tabanlı konumu gösterir.  
  
 Aşağıdaki örnek, seçili şehirlerin sıcaklık için bir Giriş dizesinin ayrıştırır. Virgül (",") bir şehir ve kendi sıcaklık ve noktalı virgül ayırmak için kullanılan (";") her şehre ait verileri ayırmak için kullanılır. Giriş dizesinin tamamını tek bir eşleşmeyi temsil eder. Normal ifade deseninde `((\w+(\s\w+)*),(\d+);)+`, dizeyi ayrıştırmak için kullanılan, şehir adı ikinci yakalama grubuna atanır ve sıcaklık dördüncü yakalama gruba atanır.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capture1.cs#16)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capture1.vb#16)]  
  
 Normal ifade aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`(\s\w+)*`|Bir veya daha fazla sözcük karakteri ve ardından bir boşluk karakterin sıfır veya daha fazla oluşumunu eşleyin. Bu düzen, birden çok sözcük Şehir adları eşleşir. Bu, üçüncü yakalama grubudur.|  
|`(\w+(\s\w+)*)`|Ardından bir boşluk karakterin sıfır veya daha çok tekrarı ve bir veya daha fazla sözcük karakteri bir veya daha fazla sözcük karakterini eşleştirin. Bu ikinci yakalama grubudur.|  
|`,`|Bir virgülü eşleştirin.|  
|`(\d+)`|Bir veya daha çok basamağı eşleştirin. Bu dördüncü yakalama grubudur.|  
|`;`|Bir noktalı virgülü eşleştirin.|  
|`((\w+(\s\w+)*),(\d+);)+`|Herhangi bir ek sözcük bir veya daha fazla kez ardından virgül, bir veya daha fazla basamak ve bir noktalı virgül tarafından izlenen bir sözcük desenini eşleştirin. Bu ilk yakalama grubudur.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Text.RegularExpressions>  
- [.NET normal ifadeler](../../../docs/standard/base-types/regular-expressions.md)  
- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
