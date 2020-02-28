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
ms.openlocfilehash: 8956be3cf8f96a8dd255f378d4927404c172c908
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160007"
---
# <a name="the-regular-expression-object-model"></a>Normal İfade Nesnesi Modeli
<a name="introduction"></a>Bu konuda, .NET normal ifadelerle çalışırken kullanılan nesne modeli açıklanmaktadır. Aşağıdaki bölümleri içerir:  
  
- [Normal Ifade altyapısı](#Engine)  
  
- [MatchCollection ve Match nesneleri](#Match_and_MCollection)  
  
- [Grup koleksiyonu](#GroupCollection)  
  
- [Yakalanan grup](#the_captured_group)  
  
- [Yakalama koleksiyonu](#CaptureCollection)  
  
- [Tek yakalama](#the_individual_capture)  
  
<a name="Engine"></a>
## <a name="the-regular-expression-engine"></a>Normal Ifade altyapısı  
 .NET 'teki normal ifade altyapısı <xref:System.Text.RegularExpressions.Regex> sınıfı tarafından temsil edilir. Normal ifade altyapısı, bir normal ifadeyi ayrıştırma ve derleme ve bir giriş dizesiyle normal ifade düzeniyle eşleşen işlemler gerçekleştirme işlemlerinden sorumludur. Motor, .NET normal ifade nesne modelindeki merkezi bileşendir.  
  
 Normal ifade altyapısını iki şekilde kullanabilirsiniz:  
  
- <xref:System.Text.RegularExpressions.Regex> sınıfının statik yöntemlerini çağırarak. Yöntem parametreleri, giriş dizesini ve normal ifade düzenlerini içerir. Normal ifade altyapısı, statik yöntem çağrılarında kullanılan normal ifadeleri önbelleğe alır; bu nedenle, aynı normal ifadeyi kullanan statik normal ifade yöntemlerine yinelenen çağrılar görece iyi performans sunar.  
  
- Bir <xref:System.Text.RegularExpressions.Regex> nesnesini, sınıf oluşturucusuna normal bir ifade geçirerek örnekleyerek. Bu durumda <xref:System.Text.RegularExpressions.Regex> nesnesi sabittir (salt okunurdur) ve tek bir normal ifadeyle sıkı bir şekilde bağlanmış bir normal ifade altyapısını temsil eder. <xref:System.Text.RegularExpressions.Regex> örnekleri tarafından kullanılan normal ifadeler önbelleğe alınmadığı için, aynı normal ifadeyle bir <xref:System.Text.RegularExpressions.Regex> nesnesini birden çok kez örnekleyemezsiniz.  
  
 Aşağıdaki işlemleri gerçekleştirmek için <xref:System.Text.RegularExpressions.Regex> sınıfının yöntemlerini çağırabilirsiniz:  
  
- Bir dizenin bir normal ifade düzeniyle eşleşip eşleşmediğini belirleme.  
  
- Tek bir eşleşmeyi veya ilk eşleşmeyi ayıklayın.  
  
- Tüm eşleşmeleri ayıkla.  
  
- Eşleşen bir alt dizeyi değiştirin.  
  
- Tek bir dizeyi dizeler dizisine Böl.  
  
 Bu işlemler aşağıdaki bölümlerde açıklanmıştır.  
  
### <a name="matching-a-regular-expression-pattern"></a>Normal Ifade düzeniyle eşleştirme  
 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> yöntemi, dize düzeniyle eşleşiyorsa `true` döndürür veya `false` yoksa. <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> yöntemi genellikle dize girişini doğrulamak için kullanılır. Örneğin, aşağıdaki kod bir dizenin Birleşik Devletler geçerli bir sosyal güvenlik numarasıyla eşleşmesini sağlar.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/validate1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/validate1.vb#1)]  
  
 Normal ifade deseninin `^\d{3}-\d{2}-\d{4}$`, aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Giriş dizesinin başlangıcını eşleştirin.|  
|`\d{3}`|Üç ondalık basamakla eşleş.|  
|`-`|Bir kısa çizgi eşleştirin.|  
|`\d{2}`|İki ondalık basamağı eşleştirin.|  
|`-`|Bir kısa çizgi eşleştirin.|  
|`\d{4}`|Dört ondalık basamağı eşleştirin.|  
|`$`|Giriş dizesinin sonuyla eşleş.|  
  
### <a name="extracting-a-single-match-or-the-first-match"></a>Tek bir eşleşme veya Ilk eşleşme ayıklanıyor  
 <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> yöntemi, normal ifade düzeniyle eşleşen ilk alt dize hakkında bilgi içeren bir <xref:System.Text.RegularExpressions.Match> nesnesi döndürür. `Match.Success` özelliği, bir eşleşmenin bulunduğunu gösteren `true`döndürürse, <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> yöntemini çağırarak sonraki eşleşmeler hakkında bilgi alabilirsiniz. Bu yöntem çağrıları `Match.Success` özelliği `false`döndürdüğünden devam edebilir. Örneğin, aşağıdaki kod, bir dizedeki yinelenen bir sözcüğün ilk oluşumunu bulmak için <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> yöntemini kullanır. Daha sonra ek oluşumları bulmak için <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> yöntemini çağırır. Örnek, geçerli eşleşmenin başarılı olup olmadığını ve <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> yöntemine yönelik bir çağrının takip edilip edilmeyeceğini anlamak için her yöntem çağrısından sonra `Match.Success` özelliğini inceler.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match1.vb#2)]  
  
 Normal ifade deseninin `\b(\w+)\W+(\1)\b`, aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Eşleşmeyi bir sözcük sınırında başlatın.|  
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|  
|`\W+`|Bir veya daha fazla sözcük olmayan karakteri eşleştirin.|  
|`(\1)`|Yakalanan ilk dizeyle eşleştirin. Bu ikinci yakalama grubudur.|  
|`\b`|Eşleşmeyi bir sözcük sınırında sonlandır.|  
  
### <a name="extracting-all-matches"></a>Tüm eşleşmeler ayıklanıyor  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> yöntemi, normal ifade altyapısının giriş dizesinde bulduğu tüm eşleşmeler hakkında bilgi içeren bir <xref:System.Text.RegularExpressions.MatchCollection> nesnesi döndürür. Örneğin, önceki örnek, <xref:System.Text.RegularExpressions.Regex.Match%2A> ve <xref:System.Text.RegularExpressions.Match.NextMatch%2A> yöntemleri yerine <xref:System.Text.RegularExpressions.Regex.Matches%2A> yöntemi çağırmak için yeniden yazılabilir.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matches1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matches1.vb#3)]  
  
### <a name="replacing-a-matched-substring"></a>Eşleşen bir alt dizeyi değiştirme  
 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> yöntemi, normal ifade düzeniyle eşleşen her alt dizenin belirtilen dize veya normal ifade düzeniyle yerini alır ve tüm giriş dizesini değiştirme ile döndürür. Örneğin, aşağıdaki kod bir dizedeki ondalık sayıdan önce bir ABD para birimi simgesi ekler.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/replace1.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/replace1.vb#4)]  
  
 Normal ifade deseninin `\b\d+\.\d{2}\b`, aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`\.`|Bir noktayla eşleştirin.|  
|`\d{2}`|İki ondalık basamağı eşleştirin.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Değiştirme deseninin `$$$&`, aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Değiştirme dizesi|  
|-------------|------------------------|  
|`$$`|Dolar işareti ($) karakteri.|  
|`$&`|Eşleşen alt dizenin tamamı.|  
  
### <a name="splitting-a-single-string-into-an-array-of-strings"></a>Tek bir dizeyi dizeler dizisine bölme  
 <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> yöntemi, giriş dizesini normal ifade eşleşmesi tarafından tanımlanan konumlarda böler. Örneğin, aşağıdaki kod öğeleri numaralandırılmış bir liste içine dize dizisine koyar.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/split1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/split1.vb#5)]  
  
 Normal ifade deseninin `\b\d{1,2}\.\s`, aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\d{1,2}`|Bir veya iki ondalık basamağı eşleştirin.|  
|`\.`|Bir noktayla eşleştirin.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
  
<a name="Match_and_MCollection"></a>
## <a name="the-matchcollection-and-match-objects"></a>MatchCollection ve Match nesneleri  
 Regex yöntemleri, normal ifade nesne modelinin parçası olan iki nesne döndürür: <xref:System.Text.RegularExpressions.MatchCollection> nesnesi ve <xref:System.Text.RegularExpressions.Match> nesnesi.  
  
<a name="the_match_collection"></a>
### <a name="the-match-collection"></a>Eşleştirme koleksiyonu  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> yöntemi, normal ifade altyapısının bulduğu tüm eşleşmeleri temsil eden <xref:System.Text.RegularExpressions.Match> nesnelerini giriş dizesinde gerçekleştikleri sırada içeren bir <xref:System.Text.RegularExpressions.MatchCollection> nesnesi döndürür. Eşleşme yoksa, yöntemi üyesi olmayan bir <xref:System.Text.RegularExpressions.MatchCollection> nesnesi döndürür. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> özelliği, koleksiyona göre koleksiyonun tek üyelerine, <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> özelliğinin değerinden bir daha küçük bir değere erişmenizi sağlar. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A> koleksiyonun Dizin Oluşturucusu (içinde C#) ve varsayılan özelliktir (Visual Basic).  
  
 Varsayılan olarak, <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> yöntemine yapılan çağrı, <xref:System.Text.RegularExpressions.MatchCollection> nesnesini doldurmak için yavaş değerlendirmeyi kullanır. <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> özellikleri gibi tamamen doldurulmuş bir koleksiyon gerektiren özelliklere erişim, bir performans cezası içerebilir. Sonuç olarak, <xref:System.Text.RegularExpressions.MatchCollection.GetEnumerator%2A?displayProperty=nameWithType> yöntemi tarafından döndürülen <xref:System.Collections.IEnumerator> nesnesini kullanarak koleksiyona erişmenizi öneririz. Tek diller, Visual Basic ve içindeki C#`foreach` `For Each` gibi yapıları sağlar, bu da koleksiyonun <xref:System.Collections.IEnumerator> arabirimini sarmalıdır.  
  
 Aşağıdaki örnek, bir <xref:System.Text.RegularExpressions.MatchCollection> nesnesini bir giriş dizesinde bulunan tüm eşleştirmelerle doldurmak için <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%29?displayProperty=nameWithType> yöntemini kullanır. Örnek, koleksiyonu numaralandırır, eşleşmeleri bir dize dizisine kopyalar ve karakter konumlarını bir tamsayı dizisine kaydeder.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matchcollection1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matchcollection1.vb#6)]  
  
<a name="the_match"></a>
### <a name="the-match"></a>Eşleşme  
 <xref:System.Text.RegularExpressions.Match> sınıfı, tek bir normal ifade eşleşmesinden elde edilen sonucu temsil eder. <xref:System.Text.RegularExpressions.Match> nesnelerine iki şekilde erişebilirsiniz:  
  
- Bunları <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> yöntemi tarafından döndürülen <xref:System.Text.RegularExpressions.MatchCollection> nesnesinden alarak. Tek tek <xref:System.Text.RegularExpressions.Match> nesneleri almak için, koleksiyonu bir `foreach` (içinde C#) veya `For Each`...`Next` (Visual Basic) yapısında yineleyin ya da <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> özelliğini kullanarak belirli bir <xref:System.Text.RegularExpressions.Match> nesnesini dizine veya ada göre alın. Koleksiyonu dizine göre, koleksiyondaki nesne sayısının birinden daha az bir olacak şekilde yineleerek koleksiyondan tek tek <xref:System.Text.RegularExpressions.Match> nesneleri de alabilirsiniz. Ancak, bu yöntem, <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> özelliğine eriştiği için yavaş değerlendirmeden faydalanır.  
  
     Aşağıdaki örnek, `foreach` veya `For Each`...`Next` yapısını kullanarak koleksiyonu yineleerek bir <xref:System.Text.RegularExpressions.MatchCollection> nesnesinden bağımsız <xref:System.Text.RegularExpressions.Match> nesnelerini alır. Normal ifade yalnızca giriş dizesindeki "abc" dizesiyle eşleşir.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match2.vb#7)]  
  
- Bir dizedeki ilk eşleşmeyi temsil eden bir <xref:System.Text.RegularExpressions.Match> nesnesi döndüren <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> yöntemini çağırarak veya dizenin bir kısmı. `Match.Success` özelliğinin değerini alarak eşleşmenin bulunup bulunmadığını belirleyebilirsiniz. Sonraki eşleşmeleri temsil eden <xref:System.Text.RegularExpressions.Match> nesneleri almak için, döndürülen <xref:System.Text.RegularExpressions.Match> nesnesinin `Success` özelliği `false`kadar <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> yöntemini tekrar tekrar çağırın.  
  
     Aşağıdaki örnek, giriş dizesindeki "abc" dizesiyle eşleşen <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> yöntemlerini kullanır.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match3.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match3.vb#8)]  
  
 <xref:System.Text.RegularExpressions.Match> sınıfının iki özelliği koleksiyon nesneleri döndürüyor:  
  
- <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliği, normal ifade deseninin yakalama gruplarıyla eşleşen alt dizeler hakkında bilgi içeren bir <xref:System.Text.RegularExpressions.GroupCollection> nesnesi döndürür.  
  
- `Match.Captures` özelliği, sınırlı kullanım <xref:System.Text.RegularExpressions.CaptureCollection> bir nesne döndürür. Koleksiyon, `Success` özelliği `false`olan bir <xref:System.Text.RegularExpressions.Match> nesnesi için doldurulmadı. Aksi halde, <xref:System.Text.RegularExpressions.Match> nesnesiyle aynı bilgilere sahip tek bir <xref:System.Text.RegularExpressions.Capture> nesnesi içerir.  
  
 Bu nesneler hakkında daha fazla bilgi için bu konunun ilerleyen kısımlarında [grup koleksiyonu](#GroupCollection) ve [yakalama koleksiyonu](#CaptureCollection) bölümlerine bakın.  
  
 <xref:System.Text.RegularExpressions.Match> sınıfının iki ek özelliği eşleşme hakkında bilgi sağlar. `Match.Value` özelliği, giriş dizesindeki normal ifade düzeniyle eşleşen alt dizeyi döndürür. `Match.Index` özelliği, giriş dizesindeki eşleşen dizenin sıfır tabanlı başlangıç konumunu döndürür.  
  
 <xref:System.Text.RegularExpressions.Match> sınıfında Ayrıca iki kalıp eşleme yöntemi vardır:  
  
- <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> yöntemi, geçerli <xref:System.Text.RegularExpressions.Match> nesnesi tarafından temsil edilen eşleşmesinden sonra eşleşmeyi bulur ve bu eşleşmeyi temsil eden bir <xref:System.Text.RegularExpressions.Match> nesnesi döndürür.  
  
- <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemi, eşleşen dize üzerinde belirtilen bir değiştirme işlemi gerçekleştirir ve sonucu döndürür.  
  
 Aşağıdaki örnek, iki kesirli basamak içeren her sayıdan önce bir $ symbol ve bir boşluk eklemek için <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> yöntemini kullanır.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/result1.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/result1.vb#9)]  
  
 `\b\d+(,\d{3})*\.\d{2}\b` normal ifade deseninin aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`(,\d{3})*`|Bir virgülden sonra gelen sıfır veya daha fazla tekrarı ve ardından üç ondalık basamak eşleştirin.|  
|`\.`|Ondalık nokta karakteriyle eşleştirin.|  
|`\d{2}`|İki ondalık basamağı eşleştirin.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Değiştirme deseninin `$$ $&`, eşleşen alt dizenin bir dolar işareti ($) simgesiyle (`$$` düzeniyle), bir boşluk ve eşleşmenin (`$&` deseninin) değeri ile değiştirilmesi gerektiğini gösterir.  
  
 [Başa dön](#introduction)  
  
<a name="GroupCollection"></a>
## <a name="the-group-collection"></a>Grup koleksiyonu  
 <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliği, tek bir eşleşme halinde yakalanan grupları temsil eden <xref:System.Text.RegularExpressions.Group> nesneleri içeren bir <xref:System.Text.RegularExpressions.GroupCollection> nesnesi döndürür. Koleksiyondaki ilk <xref:System.Text.RegularExpressions.Group> nesnesi (Dizin 0 ' da) tüm eşleşmeyi temsil eder. Aşağıdaki her nesne tek bir yakalama grubunun sonuçlarını temsil eder.  
  
 <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> özelliğini kullanarak koleksiyondaki tek tek <xref:System.Text.RegularExpressions.Group> nesneleri alabilirsiniz. Adlandırılmamış grupları koleksiyonda sıra konumlarına göre alabilir ve adlandırılmış grupları ada veya sıralı konuma göre alabilir. Adlandırılmamış yakalamalar koleksiyonda önce görünür ve normal ifade modelinde göründükleri sırada soldan sağa dizinlenir. Adlandırılmış yakalamalar, adsız yakalamalardan sonra, normal ifade düzeninde göründükleri sırada, soldan sağa dizinlenir. Belirli bir normal ifade eşleştirme yöntemi için döndürülen koleksiyonda hangi numaralanmış grupların kullanılabildiğini belirlemek için örnek <xref:System.Text.RegularExpressions.Regex.GetGroupNumbers%2A?displayProperty=nameWithType> yöntemini çağırabilirsiniz. Koleksiyonda adlandırılmış grupların kullanılabildiğini belirlemek için örnek <xref:System.Text.RegularExpressions.Regex.GetGroupNames%2A?displayProperty=nameWithType> yöntemini çağırabilirsiniz. Her iki yöntem de özellikle herhangi bir normal ifade tarafından bulunan eşleşmeleri çözümleyen genel amaçlı yordamlar için yararlıdır.  
  
 <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> özelliği, içindeki C# koleksiyonun Dizin oluşturucudur ve koleksiyon nesnesinin varsayılan özelliği olan Visual Basic. Bu, bireysel <xref:System.Text.RegularExpressions.Group> nesnelerine dizin (veya adlandırılmış gruplar söz konusu olduğunda, ada göre) tarafından erişilebileceği anlamına gelir:  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupsyntax1.cs#13)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupsyntax1.vb#13)]  
  
 Aşağıdaki örnek, bir tarihin ay, gün ve yılını yakalamak için gruplandırma yapılarını kullanan bir normal ifade tanımlar.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupcollection1.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupcollection1.vb#10)]  
  
 `\b(\w+)\s(\d{1,2}),\s(\d{4})\b` normal ifade deseninin aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`(\d{1,2})`|Bir veya iki ondalık basamağı eşleştirin. Bu ikinci yakalama grubudur.|  
|`,`|Bir virgülü eşleştirin.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`(\d{4})`|Dört ondalık basamağı eşleştirin. Bu, üçüncü yakalama grubudur.|  
|`\b`|Eşleşmeyi bir sözcük sınırında sonlandır.|  
  
 [Başa dön](#introduction)  
  
<a name="the_captured_group"></a>
## <a name="the-captured-group"></a>Yakalanan grup  
 <xref:System.Text.RegularExpressions.Group> sınıfı, tek bir yakalama grubundan elde edilen sonucu temsil eder. Normal bir ifadede tanımlanan yakalama gruplarını temsil eden Grup nesneleri, <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliği tarafından döndürülen <xref:System.Text.RegularExpressions.GroupCollection> nesnesinin <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> özelliği tarafından döndürülür. <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> özelliği, <xref:System.Text.RegularExpressions.Group> sınıfının Dizin oluşturucudır C#(içinde) ve varsayılan özelliktir (Visual Basic). `foreach` veya `For Each` yapısını kullanarak koleksiyonu yineleerek tek tek üyeleri de alabilirsiniz. Bir örnek için önceki bölüme bakın.  
  
 Aşağıdaki örnek, alt dizeleri gruplar halinde yakalamak için iç içe gruplama yapılarını kullanır. Normal ifade deseninin `(a(b))c`, "abc" dizesiyle eşleşir. "AB" alt dizesini ilk yakalama grubuna ve "b" alt dizesini ikinci yakalama grubuna atar.  
  
 [!code-csharp[RegularExpressions.Classes#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#6)]
 [!code-vb[RegularExpressions.Classes#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#6)]  
  
 Aşağıdaki örnek, "DATANAME: VALUE" biçiminde veri içeren bir dizeden alt dizeleri yakalamak için adlandırılmış gruplandırma yapılarını kullanır, bu da normal ifadenin iki nokta üst üste (:) ayırır).  
  
 [!code-csharp[RegularExpressions.Classes#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#8)]
 [!code-vb[RegularExpressions.Classes#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#8)]  
  
 `^(?<name>\w+):(?<value>\w+)` normal ifade deseninin aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Giriş dizesinin başında eşleşmeye başla.|  
|`(?<name>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu yakalama grubunun adı `name`.|  
|`:`|İki nokta üst üste eşleştirin.|  
|`(?<value>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu yakalama grubunun adı `value`.|  
  
 <xref:System.Text.RegularExpressions.Group> sınıfının özellikleri yakalanan grup hakkında bilgi sağlar: `Group.Value` özelliği yakalanan alt dizeyi içerir. `Group.Index` özelliği, yakalanan grubun başlangıç konumunu giriş metninde gösterir, `Group.Length` özelliği yakalanan metnin uzunluğunu içerir ve `Group.Success` özelliği, bir alt dizenin yakalama grubu tarafından tanımlanan Düzenle eşleştiğini gösterir.  
  
 Bir gruba nicelik belirteçleri uygulama (daha fazla bilgi için, bkz. [nicelik belirteçleri](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)) yakalama grubu başına bir yakalamanın ilişkisini iki şekilde değiştirir:  
  
- Bir gruba uygulanmış `*` veya `*?` nicelik (sıfır veya daha fazla eşleşme belirten) varsa, bir yakalama grubunun giriş dizesinde eşleşmesi olmayabilir. Yakalanan metin olmadığında, <xref:System.Text.RegularExpressions.Group> nesnesinin özellikleri aşağıdaki tabloda gösterildiği gibi ayarlanır.  
  
    |Group özelliği|Değer|  
    |--------------------|-----------|  
    |`Success`|`false`|  
    |`Value`|<xref:System.String.Empty?displayProperty=nameWithType>|  
    |`Length`|0|  
  
     Aşağıdaki örnek, bir gösterim sağlar. Normal ifade deseninin `aaa(bbb)*ccc`, ilk yakalama grubu ("bbb" alt dizesi) sıfır veya daha fazla kez eşleştirilebilir. "Aaaccc" giriş dizesi düzeniyle eşleştiğinden, yakalama grubunun eşleşmesi yoktur.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/nocapture1.cs#11)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/nocapture1.vb#11)]  
  
- Nicelik belirteçleri, bir yakalama grubu tarafından tanımlanan bir düzenin birden çok tekrarı ile eşleştirebilir. Bu durumda, bir <xref:System.Text.RegularExpressions.Group> nesnesinin `Value` ve `Length` özellikleri yalnızca son yakalanan alt dizeyle ilgili bilgiler içerir. Örneğin, aşağıdaki normal ifade bir noktayla biten tek bir cümle ile eşleşir. İki gruplama yapısını kullanır: ilki tek tek kelimeleri bir boşluk karakteriyle birlikte yakalar; İkincisi tek tek kelimeleri yakalar. Örneğin çıkışının gösterdiği gibi, normal ifade bir tümcenin tamamını yakalamada başarılı olsa da, ikinci yakalama grubu yalnızca son sözcüğü yakalar.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/lastcapture1.cs#12)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/lastcapture1.vb#12)]  
  
 [Başa dön](#introduction)  
  
<a name="CaptureCollection"></a>
## <a name="the-capture-collection"></a>Yakalama koleksiyonu  
 <xref:System.Text.RegularExpressions.Group> nesnesi yalnızca son yakalama hakkındaki bilgileri içerir. Ancak, bir yakalama grubu tarafından yapılan tüm yakalama kümesi, <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> özelliği tarafından döndürülen <xref:System.Text.RegularExpressions.CaptureCollection> nesnesinden hala kullanılabilir. Koleksiyonun her üyesi, bu yakalama grubu tarafından, yakalandıkları sırada (ve bu nedenle, yakalanan dizelerin giriş dizesinde soldan sağa eşleştirildiği sırada) yapılan bir yakalamayı temsil eden bir <xref:System.Text.RegularExpressions.Capture> nesnesidir. Tek tek <xref:System.Text.RegularExpressions.Capture> nesneleri koleksiyondan iki şekilde alabilirsiniz:  
  
- Koleksiyon içinde `foreach` (in C#) veya `For Each` (Visual Basic) gibi bir yapı kullanarak yineleme yaparak.  
  
- Dizine göre belirli bir nesneyi almak için <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A?displayProperty=nameWithType> özelliğini kullanarak. <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A> özelliği, <xref:System.Text.RegularExpressions.CaptureCollection> nesnenin varsayılan özelliğidir (Visual Basic) veya dizin oluşturucuda (içinde C#).  
  
 Bir nicelik listesi bir yakalama grubuna uygulanmadığından, <xref:System.Text.RegularExpressions.CaptureCollection> nesnesi, <xref:System.Text.RegularExpressions.Group> nesnesiyle aynı eşleşme hakkında bilgi sağladığından, çok ilgi çekici olan tek bir <xref:System.Text.RegularExpressions.Capture> nesnesi içerir. Bir yakalama grubuna bir nicelik belirteci uygulanmışsa, <xref:System.Text.RegularExpressions.CaptureCollection> nesnesi yakalama grubu tarafından yapılan tüm yakalamaları içerir ve koleksiyonun son üyesi, <xref:System.Text.RegularExpressions.Group> nesnesi ile aynı yakalamayı temsil eder.  
  
 Örneğin, `((a(b))c)+` normal ifade deseninin (+ nicelik veya birden fazla eşleşme belirttiği), "abcabcabc" dizesinden gelen eşleşmeleri yakalamak için, her bir <xref:System.Text.RegularExpressions.Group> nesnesinin <xref:System.Text.RegularExpressions.CaptureCollection> nesnesi üç üye içerir.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capturecollection1.cs#14)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capturecollection1.vb#14)]  
  
 Aşağıdaki örnek, "XYZAbcAbcAbcXYZAbcAb" dizesinde "abc" dizesinin bir veya daha fazla art arda bir çalıştırmasını bulmak için `(Abc)+` normal ifade kullanır. Örnek, yakalanan alt dizelerin birden çok grubunu döndürmek için <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> özelliğinin kullanımını gösterir.  
  
 [!code-csharp[RegularExpressions.Classes#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#5)]
 [!code-vb[RegularExpressions.Classes#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#5)]  
  
 [Başa dön](#introduction)  
  
<a name="the_individual_capture"></a>
## <a name="the-individual-capture"></a>Tek yakalama  
 <xref:System.Text.RegularExpressions.Capture> sınıfı, tek bir alt ifade yakalamanın sonuçlarını içerir. <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType> özelliği eşleşen metni içerir ve <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType> özelliği, eşleşen alt dizenin başladığı giriş dizesindeki sıfır tabanlı konumu gösterir.  
  
 Aşağıdaki örnek seçilen şehirlerin sıcaklığı için bir giriş dizesi ayrıştırır. Bir şehri ve sıcaklığını ayırmak için virgül (","), her şehir verisini ayırmak için noktalı virgül (";") kullanılır. Giriş dizesinin tamamı tek bir eşleşmeyi temsil eder. Dizeyi ayrıştırmak için kullanılan normal ifade deseninin `((\w+(\s\w+)*),(\d+);)+`, şehir adı ikinci yakalama grubuna atanır ve sıcaklık dördüncü yakalama grubuna atanır.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capture1.cs#16)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capture1.vb#16)]  
  
 Normal ifade aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`(\s\w+)*`|Boşluk karakterinin sıfır veya daha fazla tekrarlamalarını ve ardından bir veya daha fazla sözcük karakterini eşleştirin. Bu model, çok sözcüklü şehir adlarıyla eşleşir. Bu, üçüncü yakalama grubudur.|  
|`(\w+(\s\w+)*)`|Bir veya daha fazla sözcük karakterini, ardından sıfır veya daha fazla boşluk karakteri ve bir veya daha fazla sözcük karakteri ile eşleştirin. Bu ikinci yakalama grubudur.|  
|`,`|Bir virgülü eşleştirin.|  
|`(\d+)`|Bir veya daha fazla rakam eşleştirin. Bu dördüncü yakalama grubudur.|  
|`;`|Noktalı virgülle eşleştirin.|  
|`((\w+(\s\w+)*),(\d+);)+`|Bir sözcüğün örüntüsünün ve ardından virgül, bir veya daha fazla rakam ve noktalı virgül, bir veya daha fazla sayıda ek sözcük ile eşleştirin. Bu ilk yakalama grubudur.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Text.RegularExpressions>
- [.NET normal Ifadeleri](../../../docs/standard/base-types/regular-expressions.md)
- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
