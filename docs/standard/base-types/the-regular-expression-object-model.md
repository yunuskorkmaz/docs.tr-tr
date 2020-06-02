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
ms.openlocfilehash: ad7957fd555c1de8fe47c092d3eb399a803fb1fb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290908"
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
 .NET 'teki normal ifade altyapısı sınıfı tarafından temsil edilir <xref:System.Text.RegularExpressions.Regex> . Normal ifade altyapısı, bir normal ifadeyi ayrıştırma ve derleme ve bir giriş dizesiyle normal ifade düzeniyle eşleşen işlemler gerçekleştirme işlemlerinden sorumludur. Motor, .NET normal ifade nesne modelindeki merkezi bileşendir.  
  
 Normal ifade altyapısını iki şekilde kullanabilirsiniz:  
  
- Sınıfının statik yöntemlerini çağırarak <xref:System.Text.RegularExpressions.Regex> . Yöntem parametreleri, giriş dizesini ve normal ifade düzenlerini içerir. Normal ifade altyapısı, statik yöntem çağrılarında kullanılan normal ifadeleri önbelleğe alır; bu nedenle, aynı normal ifadeyi kullanan statik normal ifade yöntemlerine yinelenen çağrılar görece iyi performans sunar.  
  
- Bir nesneyi örnekleyerek <xref:System.Text.RegularExpressions.Regex> , sınıf oluşturucusuna normal bir ifade geçirerek. Bu durumda, <xref:System.Text.RegularExpressions.Regex> nesne sabittir (salt okunurdur) ve tek bir normal ifadeyle sıkı bir şekilde bağlanmış bir normal ifade altyapısını temsil eder. Örnekler tarafından kullanılan normal ifadeler <xref:System.Text.RegularExpressions.Regex> önbelleğe alınmadığı <xref:System.Text.RegularExpressions.Regex> için, aynı normal ifadeyle bir nesneyi birden çok kez örnekleyemezsiniz.  
  
 <xref:System.Text.RegularExpressions.Regex>Aşağıdaki işlemleri gerçekleştirmek için sınıfının yöntemlerini çağırabilirsiniz:  
  
- Bir dizenin bir normal ifade düzeniyle eşleşip eşleşmediğini belirleme.  
  
- Tek bir eşleşmeyi veya ilk eşleşmeyi ayıklayın.  
  
- Tüm eşleşmeleri ayıkla.  
  
- Eşleşen bir alt dizeyi değiştirin.  
  
- Tek bir dizeyi dizeler dizisine Böl.  
  
 Bu işlemler aşağıdaki bölümlerde açıklanmıştır.  
  
### <a name="matching-a-regular-expression-pattern"></a>Normal Ifade düzeniyle eşleştirme  
 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType>Yöntemi, `true` dize düzeniyle eşleşiyorsa veya içermiyorsa döndürür `false` . <xref:System.Text.RegularExpressions.Regex.IsMatch%2A>Yöntemi genellikle dize girişini doğrulamak için kullanılır. Örneğin, aşağıdaki kod bir dizenin Birleşik Devletler geçerli bir sosyal güvenlik numarasıyla eşleşmesini sağlar.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/validate1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/validate1.vb#1)]  
  
 Normal ifade deseninin `^\d{3}-\d{2}-\d{4}$` Aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Description|  
|-------------|-----------------|  
|`^`|Giriş dizesinin başlangıcını eşleştirin.|  
|`\d{3}`|Üç ondalık basamakla eşleş.|  
|`-`|Bir kısa çizgi eşleştirin.|  
|`\d{2}`|İki ondalık basamağı eşleştirin.|  
|`-`|Bir kısa çizgi eşleştirin.|  
|`\d{4}`|Dört ondalık basamağı eşleştirin.|  
|`$`|Giriş dizesinin sonuyla eşleş.|  
  
### <a name="extracting-a-single-match-or-the-first-match"></a>Tek bir eşleşme veya Ilk eşleşme ayıklanıyor  
 <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType>Yöntemi, <xref:System.Text.RegularExpressions.Match> normal ifade düzeniyle eşleşen ilk alt dize hakkında bilgi içeren bir nesnesi döndürür. `Match.Success`Özelliği döndürürse `true` , bir eşleşmenin bulunduğunu belirten, yöntemi çağırarak sonraki eşleşmeler hakkında bilgi alabilirsiniz <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> . Bu yöntem çağrıları, `Match.Success` özellik dönene kadar devam edebilir `false` . Örneğin, aşağıdaki kod, <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> bir dizedeki yinelenen bir sözcüğün ilk oluşumunu bulmak için yöntemini kullanır. Daha sonra <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> ek oluşumları bulmak için yöntemini çağırır. Örnek, `Match.Success` her yöntem çağrısından sonra özelliği inceleyerek geçerli eşleşmenin başarılı olup olmadığını ve yöntemin bir çağrısının izlenmesi gerekip gerekmediğini belirlemektir <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> .  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match1.vb#2)]  
  
 Normal ifade deseninin `\b(\w+)\W+(\1)\b` Aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Description|  
|-------------|-----------------|  
|`\b`|Eşleşmeyi bir sözcük sınırında başlatın.|  
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|  
|`\W+`|Bir veya daha fazla sözcük olmayan karakteri eşleştirin.|  
|`(\1)`|Yakalanan ilk dizeyle eşleştirin. Bu ikinci yakalama grubudur.|  
|`\b`|Eşleşmeyi bir sözcük sınırında sonlandır.|  
  
### <a name="extracting-all-matches"></a>Tüm eşleşmeler ayıklanıyor  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType>Yöntemi, <xref:System.Text.RegularExpressions.MatchCollection> normal ifade altyapısının giriş dizesinde bulduğu tüm eşleşmeler hakkında bilgi içeren bir nesnesi döndürür. Örneğin, <xref:System.Text.RegularExpressions.Regex.Matches%2A> ve yöntemleri yerine yöntemi çağırmak için önceki örnek <xref:System.Text.RegularExpressions.Regex.Match%2A> yeniden yazılabilir <xref:System.Text.RegularExpressions.Match.NextMatch%2A> .  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matches1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matches1.vb#3)]  
  
### <a name="replacing-a-matched-substring"></a>Eşleşen bir alt dizeyi değiştirme  
 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType>Yöntemi, normal ifade düzeniyle eşleşen her alt dizenin belirtilen bir dize veya normal ifade düzeniyle yerini alır ve tüm giriş dizesini değiştirme ile döndürür. Örneğin, aşağıdaki kod bir dizedeki ondalık sayıdan önce bir ABD para birimi simgesi ekler.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/replace1.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/replace1.vb#4)]  
  
 Normal ifade deseninin `\b\d+\.\d{2}\b` Aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Description|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`\.`|Bir noktayla eşleştirin.|  
|`\d{2}`|İki ondalık basamağı eşleştirin.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Değiştirme kalıbı `$$$&` Aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Değiştirme dizesi|  
|-------------|------------------------|  
|`$$`|Dolar işareti ($) karakteri.|  
|`$&`|Eşleşen alt dizenin tamamı.|  
  
### <a name="splitting-a-single-string-into-an-array-of-strings"></a>Tek bir dizeyi dizeler dizisine bölme  
 <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType>Yöntemi, giriş dizesini normal ifade eşleşmesi tarafından tanımlanan konumlarda böler. Örneğin, aşağıdaki kod öğeleri numaralandırılmış bir liste içine dize dizisine koyar.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/split1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/split1.vb#5)]  
  
 Normal ifade deseninin `\b\d{1,2}\.\s` Aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Description|  
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
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType>Yöntemi, <xref:System.Text.RegularExpressions.MatchCollection> <xref:System.Text.RegularExpressions.Match> normal ifade altyapısının bulduğu tüm eşleşmeleri temsil eden nesneleri, giriş dizesinde gerçekleştikleri sırayla içeren bir nesne döndürür. Eşleşme yoksa, yöntem <xref:System.Text.RegularExpressions.MatchCollection> üye içermeyen bir nesne döndürür. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType>Özelliği, koleksiyonun tek tek üyelerine, sıfırdan, özelliğin değerinden daha küçük bir değere erişmenizi sağlar <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> . <xref:System.Text.RegularExpressions.MatchCollection.Item%2A>koleksiyonun Dizin Oluşturucusu (C# ' de) ve varsayılan Özellik (Visual Basic).  
  
 Varsayılan olarak, yöntemine yapılan çağrı <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> nesneyi doldurmak için yavaş değerlendirmeyi kullanır <xref:System.Text.RegularExpressions.MatchCollection> . Ve özellikleri gibi tamamen doldurulmuş bir koleksiyon gerektiren özelliklere erişim <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> , bir performans cezası içerebilir. Sonuç olarak, <xref:System.Collections.IEnumerator> yöntemi tarafından döndürülen nesnesini kullanarak koleksiyona erişmenizi öneririz <xref:System.Text.RegularExpressions.MatchCollection.GetEnumerator%2A?displayProperty=nameWithType> . Tek tek diller, Visual Basic ve C# ' deki gibi, `For Each` `foreach` koleksiyonun arabirimini kaydırabilen yapılar sağlar <xref:System.Collections.IEnumerator> .  
  
 Aşağıdaki örnek, bir <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%29?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.MatchCollection> nesneyi giriş dizesinde bulunan tüm eşleştirmelerle doldurmak için yöntemini kullanır. Örnek, koleksiyonu numaralandırır, eşleşmeleri bir dize dizisine kopyalar ve karakter konumlarını bir tamsayı dizisine kaydeder.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matchcollection1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matchcollection1.vb#6)]  
  
<a name="the_match"></a>
### <a name="the-match"></a>Eşleşme  
 <xref:System.Text.RegularExpressions.Match>Sınıfı, tek bir normal ifade eşleşmesinden elde edilen sonucu temsil eder. <xref:System.Text.RegularExpressions.Match>Nesnelere iki şekilde erişebilirsiniz:  
  
- <xref:System.Text.RegularExpressions.MatchCollection>Metodu, yöntemi tarafından döndürülen nesneden alarak <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> . Tek tek nesneleri almak için <xref:System.Text.RegularExpressions.Match> , `foreach` (C# ' de) veya `For Each` ... `Next` (Visual Basic) yapısı kullanarak koleksiyonu yineleyin veya <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> belirli bir <xref:System.Text.RegularExpressions.Match> nesneyi dizine veya ada göre almak için özelliğini kullanın. Koleksiyonu <xref:System.Text.RegularExpressions.Match> dizine göre, koleksiyondaki nesne sayısından bir değerden daha az bir olacak şekilde yineleerek koleksiyondan tek tek nesneleri de alabilirsiniz. Ancak, bu yöntem, özelliğine eriştiği için yavaş değerlendirmeden faydalanır <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> .  
  
     Aşağıdaki örnek, <xref:System.Text.RegularExpressions.Match> <xref:System.Text.RegularExpressions.MatchCollection> `foreach` veya `For Each` ... yapısını kullanarak koleksiyonu yineleerek bir nesneden tek nesneleri alır `Next` . Normal ifade yalnızca giriş dizesindeki "abc" dizesiyle eşleşir.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match2.vb#7)]  
  
- <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType>Yöntemini çağırarak, <xref:System.Text.RegularExpressions.Match> bir dizedeki ilk eşleşmeyi temsil eden bir nesne veya bir dizenin bir kısmı döndürür. Özelliğin değerini alarak eşleşmenin bulunup bulunmadığını belirleyebilirsiniz `Match.Success` . <xref:System.Text.RegularExpressions.Match>Sonraki eşleşmeleri temsil eden nesneleri almak için <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> `Success` döndürülen nesnenin özelliği olana kadar yöntemi tekrar tekrar çağırın <xref:System.Text.RegularExpressions.Match> `false` .  
  
     Aşağıdaki örnek, <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> Giriş dizesindeki "abc" dizesiyle eşleşmesi için ve yöntemlerini kullanır.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match3.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match3.vb#8)]  
  
 Sınıfın iki özelliği, <xref:System.Text.RegularExpressions.Match> koleksiyon nesneleri döndürüyor:  
  
- <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>Özelliği, <xref:System.Text.RegularExpressions.GroupCollection> normal ifade deseninin yakalama gruplarıyla eşleşen alt dizeler hakkında bilgi içeren bir nesnesi döndürür.  
  
- `Match.Captures`Özelliği, <xref:System.Text.RegularExpressions.CaptureCollection> sınırlı kullanım olan bir nesne döndürür. Koleksiyonu, <xref:System.Text.RegularExpressions.Match> özelliği olan bir nesne için doldurulmamış `Success` `false` . Aksi halde, <xref:System.Text.RegularExpressions.Capture> nesnesiyle aynı bilgilere sahip tek bir nesnesi içerir <xref:System.Text.RegularExpressions.Match> .  
  
 Bu nesneler hakkında daha fazla bilgi için bu konunun ilerleyen kısımlarında [grup koleksiyonu](#GroupCollection) ve [yakalama koleksiyonu](#CaptureCollection) bölümlerine bakın.  
  
 Sınıfının iki ek özelliği <xref:System.Text.RegularExpressions.Match> eşleşme hakkında bilgi sağlar. `Match.Value`Özelliği, giriş dizesindeki normal ifade düzeniyle eşleşen alt dizeyi döndürür. `Match.Index`Özelliği, giriş dizesindeki eşleşen dizenin sıfır tabanlı başlangıç konumunu döndürür.  
  
 <xref:System.Text.RegularExpressions.Match>Sınıfta Ayrıca iki kalıp eşleme yöntemi vardır:  
  
- <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType>Yöntemi, geçerli nesnenin gösterdiği eşleşmesinden sonra eşleşmeyi bulur <xref:System.Text.RegularExpressions.Match> ve <xref:System.Text.RegularExpressions.Match> Bu eşleşmeyi temsil eden bir nesne döndürür.  
  
- <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType>Yöntemi, eşleşen dize üzerinde belirtilen bir değiştirme işlemi gerçekleştirir ve sonucu döndürür.  
  
 Aşağıdaki örnek, <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> iki kesirli basamak içeren her sayıdan önce bir $ symbol ve bir boşluk eklemek için yöntemini kullanır.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/result1.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/result1.vb#9)]  
  
 Normal ifade deseninin, `\b\d+(,\d{3})*\.\d{2}\b` Aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Description|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`(,\d{3})*`|Bir virgülden sonra gelen sıfır veya daha fazla tekrarı ve ardından üç ondalık basamak eşleştirin.|  
|`\.`|Ondalık nokta karakteriyle eşleştirin.|  
|`\d{2}`|İki ondalık basamağı eşleştirin.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Değiştirme stili, `$$ $&` eşleşen alt dizenin bir dolar işareti ($) simgesiyle ( `$$` desenler), bir boşluk ve eşleşmenin (model) değeri ile değiştirilmesi gerektiğini gösterir `$&` .  
  
 [Başa dön](#introduction)  
  
<a name="GroupCollection"></a>
## <a name="the-group-collection"></a>Grup koleksiyonu  
 <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>Özelliği, <xref:System.Text.RegularExpressions.GroupCollection> <xref:System.Text.RegularExpressions.Group> tek bir eşleşme halinde yakalanan grupları temsil eden nesneler içeren bir nesne döndürür. Koleksiyondaki ilk <xref:System.Text.RegularExpressions.Group> nesne (0 dizininde) tüm eşleşmeyi temsil eder. Aşağıdaki her nesne tek bir yakalama grubunun sonuçlarını temsil eder.  
  
 <xref:System.Text.RegularExpressions.Group>Özelliğini kullanarak koleksiyondaki nesneleri tek tek alabilirsiniz <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> . Adlandırılmamış grupları koleksiyonda sıra konumlarına göre alabilir ve adlandırılmış grupları ada veya sıralı konuma göre alabilir. Adlandırılmamış yakalamalar koleksiyonda önce görünür ve normal ifade modelinde göründükleri sırada soldan sağa dizinlenir. Adlandırılmış yakalamalar, adsız yakalamalardan sonra, normal ifade düzeninde göründükleri sırada, soldan sağa dizinlenir. Belirli bir normal ifade eşleştirme yöntemi için döndürülen koleksiyonda hangi numaralanmış grupların kullanılabildiğini belirlemek için örnek <xref:System.Text.RegularExpressions.Regex.GetGroupNumbers%2A?displayProperty=nameWithType> yöntemini çağırabilirsiniz. Koleksiyonda bulunan adlandırılmış grupları belirlemek için örnek <xref:System.Text.RegularExpressions.Regex.GetGroupNames%2A?displayProperty=nameWithType> yöntemini çağırabilirsiniz. Her iki yöntem de özellikle herhangi bir normal ifade tarafından bulunan eşleşmeleri çözümleyen genel amaçlı yordamlar için yararlıdır.  
  
 <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType>Özelliği, C# ve koleksiyon nesnesinin varsayılan özelliği olan Visual Basic koleksiyonun Dizin oluşturucudur. Bu, tek tek <xref:System.Text.RegularExpressions.Group> nesnelere dizin (veya adlandırılmış gruplar söz konusu olduğunda, ada göre) tarafından erişilebileceği anlamına gelir:  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupsyntax1.cs#13)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupsyntax1.vb#13)]  
  
 Aşağıdaki örnek, bir tarihin ay, gün ve yılını yakalamak için gruplandırma yapılarını kullanan bir normal ifade tanımlar.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupcollection1.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupcollection1.vb#10)]  
  
 Normal ifade deseninin, `\b(\w+)\s(\d{1,2}),\s(\d{4})\b` Aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Description|  
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
 <xref:System.Text.RegularExpressions.Group>Sınıfı, tek bir yakalama grubundan elde edilen sonucu temsil eder. Normal bir ifadede tanımlanan yakalama gruplarını temsil eden Grup nesneleri <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> <xref:System.Text.RegularExpressions.GroupCollection> , özelliği tarafından döndürülen nesnenin özelliği tarafından döndürülür <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> . <xref:System.Text.RegularExpressions.GroupCollection.Item%2A>Özelliği, sınıfının Indexer (C# ' de) ve varsayılan özelliği (Visual Basic) <xref:System.Text.RegularExpressions.Group> . Veya yapısını kullanarak koleksiyonu yineleerek tek tek üyeleri de alabilirsiniz `foreach` `For Each` . Bir örnek için önceki bölüme bakın.  
  
 Aşağıdaki örnek, alt dizeleri gruplar halinde yakalamak için iç içe gruplama yapılarını kullanır. Normal ifade deseninin `(a(b))c` "abc" dizesiyle eşleşmesi. "AB" alt dizesini ilk yakalama grubuna ve "b" alt dizesini ikinci yakalama grubuna atar.  
  
 [!code-csharp[RegularExpressions.Classes#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#6)]
 [!code-vb[RegularExpressions.Classes#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#6)]  
  
 Aşağıdaki örnek, "DATANAME: VALUE" biçiminde veri içeren bir dizeden alt dizeleri yakalamak için adlandırılmış gruplandırma yapılarını kullanır, bu da normal ifadenin iki nokta üst üste (:) ayırır).  
  
 [!code-csharp[RegularExpressions.Classes#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#8)]
 [!code-vb[RegularExpressions.Classes#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#8)]  
  
 Normal ifade deseninin, `^(?<name>\w+):(?<value>\w+)` Aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Description|  
|-------------|-----------------|  
|`^`|Giriş dizesinin başında eşleşmeye başla.|  
|`(?<name>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu yakalama grubunun adı `name` .|  
|`:`|İki nokta üst üste eşleştirin.|  
|`(?<value>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu yakalama grubunun adı `value` .|  
  
 <xref:System.Text.RegularExpressions.Group>Sınıfının özellikleri yakalanan grup hakkında bilgi sağlar: `Group.Value` özelliği yakalanan alt dizeyi içerir, özelliği, yakalanan `Group.Index` grubun başlangıç konumunu giriş metninde gösterir, `Group.Length` özelliği yakalanan metnin uzunluğunu içerir ve `Group.Success` özellik, bir alt dizenin yakalama grubu tarafından tanımlanan bir Düzenle eşleştiğini gösterir.  
  
 Bir gruba nicelik belirteçleri uygulama (daha fazla bilgi için, bkz. [nicelik belirteçleri](quantifiers-in-regular-expressions.md)) yakalama grubu başına bir yakalamanın ilişkisini iki şekilde değiştirir:  
  
- `*` `*?` Bir gruba uygulanmış veya nicelik (sıfır veya daha fazla eşleşme belirten) varsa, bir yakalama grubunun giriş dizesinde eşleşmesi olmayabilir. Yakalanan metin olmadığında <xref:System.Text.RegularExpressions.Group> nesnenin özellikleri aşağıdaki tabloda gösterildiği gibi ayarlanır.  
  
    |Group özelliği|Değer|  
    |--------------------|-----------|  
    |`Success`|`false`|  
    |`Value`|<xref:System.String.Empty?displayProperty=nameWithType>|  
    |`Length`|0|  
  
     Aşağıdaki örnek, bir gösterim sağlar. Normal ifade modelinde `aaa(bbb)*ccc` , ilk yakalama grubu ("bbb" alt dizesi) sıfır veya daha fazla kez eşleştirilebilir. "Aaaccc" giriş dizesi düzeniyle eşleştiğinden, yakalama grubunun eşleşmesi yoktur.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/nocapture1.cs#11)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/nocapture1.vb#11)]  
  
- Nicelik belirteçleri, bir yakalama grubu tarafından tanımlanan bir düzenin birden çok tekrarı ile eşleştirebilir. Bu durumda, `Value` `Length` bir nesnenin ve özellikleri <xref:System.Text.RegularExpressions.Group> yalnızca son yakalanan alt dizeyle ilgili bilgiler içerir. Örneğin, aşağıdaki normal ifade bir noktayla biten tek bir cümle ile eşleşir. İki gruplama yapısını kullanır: ilki tek tek kelimeleri bir boşluk karakteriyle birlikte yakalar; İkincisi tek tek kelimeleri yakalar. Örneğin çıkışının gösterdiği gibi, normal ifade bir tümcenin tamamını yakalamada başarılı olsa da, ikinci yakalama grubu yalnızca son sözcüğü yakalar.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/lastcapture1.cs#12)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/lastcapture1.vb#12)]  
  
 [Başa dön](#introduction)  
  
<a name="CaptureCollection"></a>
## <a name="the-capture-collection"></a>Yakalama koleksiyonu  
 <xref:System.Text.RegularExpressions.Group>Nesne yalnızca son yakalama hakkındaki bilgileri içerir. Ancak, bir yakalama grubu tarafından yapılan tüm yakalama kümesi, <xref:System.Text.RegularExpressions.CaptureCollection> özelliği tarafından döndürülen nesneden hala kullanılabilir <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> . Koleksiyonun her üyesi <xref:System.Text.RegularExpressions.Capture> , bu yakalama grubu tarafından, yakalandıkları sırada (ve bu nedenle, yakalanan dizelerin giriş dizesinde soldan sağa eşleştirildiği sırada) yapılan yakalamayı temsil eden bir nesnedir. Koleksiyondan tek tek <xref:System.Text.RegularExpressions.Capture> nesneleri iki şekilde de alabilirsiniz:  
  
- Koleksiyon içinde `foreach` (C# ' de) veya (Visual Basic) gibi bir yapı kullanarak yineleme yaparak `For Each` .  
  
- <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A?displayProperty=nameWithType>Belirli bir nesneyi dizine göre almak için özelliğini kullanarak. <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A>Özelliği <xref:System.Text.RegularExpressions.CaptureCollection> nesnenin varsayılan özelliğidir (Visual Basic) veya dizin oluşturucuda (C# dilinde).  
  
 Bir nicelik listesi bir yakalama grubuna uygulanmadığından, nesnesi, <xref:System.Text.RegularExpressions.CaptureCollection> <xref:System.Text.RegularExpressions.Capture> nesnesiyle aynı eşleşme hakkında bilgi sağladığından çok az ilgi çekici tek bir nesne içerir <xref:System.Text.RegularExpressions.Group> . Bir yakalama grubuna bir nicelik belirteci uygulanmışsa, <xref:System.Text.RegularExpressions.CaptureCollection> nesne yakalama grubu tarafından yapılan tüm yakalamaları içerir ve koleksiyonun son üyesi nesneyle aynı yakalamayı temsil eder <xref:System.Text.RegularExpressions.Group> .  
  
 Örneğin, normal ifade deseninin `((a(b))c)+` (+ nicelik belirteci bir veya daha fazla eşleşme belirttiğinde) kullanırsanız, <xref:System.Text.RegularExpressions.CaptureCollection> her nesne için nesne <xref:System.Text.RegularExpressions.Group> üç üye içerir.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capturecollection1.cs#14)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capturecollection1.vb#14)]  
  
 Aşağıdaki örnek, `(Abc)+` "XYZAbcAbcAbcXYZAbcAb" dizesinde "abc" dizesinin bir veya daha fazla art arda çalışmasını bulmak için normal ifadeyi kullanmaktadır. Örnek, <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> birden fazla yakalanan alt dize grubunu döndürmek için özelliğinin kullanımını gösterir.  
  
 [!code-csharp[RegularExpressions.Classes#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#5)]
 [!code-vb[RegularExpressions.Classes#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#5)]  
  
 [Başa dön](#introduction)  
  
<a name="the_individual_capture"></a>
## <a name="the-individual-capture"></a>Tek yakalama  
 <xref:System.Text.RegularExpressions.Capture>Sınıfı, tek bir alt ifade yakalamanın sonuçlarını içerir. <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType>Özelliği eşleşen metni içerir ve özelliği, eşleşen alt <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType> dizenin başladığı giriş dizesindeki sıfır tabanlı konumu gösterir.  
  
 Aşağıdaki örnek seçilen şehirlerin sıcaklığı için bir giriş dizesi ayrıştırır. Bir şehri ve sıcaklığını ayırmak için virgül (","), her şehir verisini ayırmak için noktalı virgül (";") kullanılır. Giriş dizesinin tamamı tek bir eşleşmeyi temsil eder. `((\w+(\s\w+)*),(\d+);)+`Dizeyi ayrıştırmak için kullanılan normal ifade modelinde, şehir adı ikinci yakalama grubuna atanır ve sıcaklık dördüncü yakalama grubuna atanır.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capture1.cs#16)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capture1.vb#16)]  
  
 Normal ifade aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Description|  
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
- [.NET normal Ifadeleri](regular-expressions.md)
- [Normal İfade Dili - Hızlı Başvuru](regular-expression-language-quick-reference.md)
