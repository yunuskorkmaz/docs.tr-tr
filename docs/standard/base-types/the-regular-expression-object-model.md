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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160007"
---
# <a name="the-regular-expression-object-model"></a>Normal İfade Nesnesi Modeli
<a name="introduction"></a>Bu konu,.NET düzenli ifadeleri ile çalışırken kullanılan nesne modelini açıklar. Aşağıdaki bölümleri içerir:  
  
- [Normal İfade Motoru](#Engine)  
  
- [MatchCollection ve Match Nesneleri](#Match_and_MCollection)  
  
- [Grup Koleksiyonu](#GroupCollection)  
  
- [Yakalanan Grup](#the_captured_group)  
  
- [Yakalama Koleksiyonu](#CaptureCollection)  
  
- [Bireysel Yakalama](#the_individual_capture)  
  
<a name="Engine"></a>
## <a name="the-regular-expression-engine"></a>Normal İfade Motoru  
 .NET'teki normal ifade altyapısı <xref:System.Text.RegularExpressions.Regex> sınıf tarafından temsil edilir. Normal ifade altyapısı, normal bir ifadeyi ayrıştırma ve derlemekten ve normal ifade deseniyle bir giriş dizesiyle eşleşen işlemleri gerçekleştirmekten sorumludur. Motor,.NET normal ifade nesnesi modelinin merkezi bileşenidir.  
  
 Normal ifade altyapısını iki şekilde de kullanabilirsiniz:  
  
- Sınıfın statik yöntemlerini <xref:System.Text.RegularExpressions.Regex> çağırarak. Yöntem parametreleri giriş dizesi ve normal ifade deseni içerir. Normal ifade altyapısı statik yöntem çağrılarında kullanılan normal ifadeleri önbelleğe alır, bu nedenle aynı normal ifadeyi kullanan statik normal ifade yöntemlerine tekrarlanan çağrılar nispeten iyi performans sunar.  
  
- Bir <xref:System.Text.RegularExpressions.Regex> nesneyi anında, sınıf oluşturucuya normal bir ifade geçirerek. Bu durumda, <xref:System.Text.RegularExpressions.Regex> nesne değişmez (salt okunur) ve tek bir normal ifadeyle sıkıca birleşen normal bir ifade altyapısını temsil eder. Örnekler tarafından <xref:System.Text.RegularExpressions.Regex> kullanılan normal ifadeler önbelleğe alınmadığından, bir <xref:System.Text.RegularExpressions.Regex> nesneyi aynı normal ifadeyle birden çok kez anında kullanmamalısınız.  
  
 Aşağıdaki işlemleri gerçekleştirmek için <xref:System.Text.RegularExpressions.Regex> sınıfın yöntemlerini arayabilirsiniz:  
  
- Dize normal bir ifade deseniyle eşleşip eşleşmediğini belirleyin.  
  
- Tek bir eşleşme yi veya ilk eşleşmeyi ayıklayın.  
  
- Tüm kibritleri ayıklayın.  
  
- Eşleşen bir alt dize değiştirin.  
  
- Tek bir dizeyi bir dizi dize olarak bölün.  
  
 Bu işlemler aşağıdaki bölümlerde açıklanmıştır.  
  
### <a name="matching-a-regular-expression-pattern"></a>Normal İfade Deseni Eşleştirme  
 Dize <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> `true` desenle eşleşirse `false` veya eşleşmiyorsa yöntem döndürür. Yöntem <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> genellikle dize girişini doğrulamak için kullanılır. Örneğin, aşağıdaki kod, bir dize abd'de geçerli bir sosyal güvenlik numarası eşleşen sağlar.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/validate1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/validate1.vb#1)]  
  
 Normal ifade `^\d{3}-\d{2}-\d{4}$` deseni aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Giriş dizesinin başlangıcını eşleştirin.|  
|`\d{3}`|Üç ondalık basamakla eşleş.|  
|`-`|Bir tireeşleştirin.|  
|`\d{2}`|İki ondalık basamak eşleştirin.|  
|`-`|Bir tireeşleştirin.|  
|`\d{4}`|Dört ondalık basamakeşleştirin.|  
|`$`|Giriş dizesinin sonuyla eşleş.|  
  
### <a name="extracting-a-single-match-or-the-first-match"></a>Tek Bir Eşleşme yi veya İlk Eşleşmeyi Ayıklama  
 Yöntem, <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> normal <xref:System.Text.RegularExpressions.Match> bir ifade deseniyle eşleşen ilk alt dize hakkında bilgi içeren bir nesne döndürür. `Match.Success` Özellik döndürürse, `true`eşleşme bulunduğunu gösterirse, <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> yöntemi arayarak sonraki eşleşmeler hakkında bilgi alabilirsiniz. Bu yöntem çağrıları özellik `Match.Success` dönene `false`kadar devam edebilir. Örneğin, aşağıdaki kod, <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> bir dize içinde yinelenen bir sözcüğün ilk oluşumunu bulmak için yöntemi kullanır. Daha sonra <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> herhangi bir ek oluşumları bulmak için yöntemi çağırır. Örnek, geçerli `Match.Success` eşleşmenin başarılı olup olmadığını ve yönteme yapılan bir çağrının <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> takip edilip edilmemesi gerektiğini belirlemek için her yöntem çağrısından sonra özelliği inceler.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match1.vb#2)]  
  
 Normal ifade `\b(\w+)\W+(\1)\b` deseni aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Eşleşmeyi sözcük sınırında başlatın.|  
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|  
|`\W+`|Bir veya daha fazla sözcük olmayan karakteri eşleştirin.|  
|`(\1)`|Yakalanan ilk dizeyle eşleştirin. Bu ikinci yakalama grubudur.|  
|`\b`|Eşleşmeyi sözcük sınırında sonla.|  
  
### <a name="extracting-all-matches"></a>Tüm Eşleşmeleri Ayıklama  
 Yöntem, <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> giriş <xref:System.Text.RegularExpressions.MatchCollection> dizesinde bulunan normal ifade altyapısının bulduğu tüm eşleşmeler hakkında bilgi içeren bir nesne döndürür. Örneğin, önceki örnek yöntem <xref:System.Text.RegularExpressions.Regex.Matches%2A> <xref:System.Text.RegularExpressions.Regex.Match%2A> ve <xref:System.Text.RegularExpressions.Match.NextMatch%2A> yöntemler yerine aramak için yeniden yazılabilir.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matches1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matches1.vb#3)]  
  
### <a name="replacing-a-matched-substring"></a>Eşleşen Substring değiştirme  
 Yöntem, <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> normal ifade deseniyle eşleşen her alt dizeyi belirli bir dize veya normal ifade deseniyle değiştirir ve tüm giriş dizesini yedeklerle döndürür. Örneğin, aşağıdaki kod, bir dizedeki ondalık sayıdan önce bir ABD para birimi simgesi ekler.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/replace1.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/replace1.vb#4)]  
  
 Normal ifade `\b\d+\.\d{2}\b` deseni aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`\.`|Bir periyodu eşleştirin.|  
|`\d{2}`|İki ondalık basamak eşleştirin.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Değiştirme deseni `$$$&` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Yedek dize|  
|-------------|------------------------|  
|`$$`|Dolar işareti ($) karakter.|  
|`$&`|Tüm eşleşen substring.|  
  
### <a name="splitting-a-single-string-into-an-array-of-strings"></a>Tek Bir Dizeyi Bir Dize Dizisine Bölme  
 Yöntem, <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> normal bir ifade eşleşmesi ile tanımlanan konumlardaki giriş dizesini böler. Örneğin, aşağıdaki kod, numaralanmış bir listedeki öğeleri bir dize dizisine yerleştirir.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/split1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/split1.vb#5)]  
  
 Normal ifade `\b\d{1,2}\.\s` deseni aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\d{1,2}`|Bir veya iki ondalık basamak eşleştirin.|  
|`\.`|Bir periyodu eşleştirin.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
  
<a name="Match_and_MCollection"></a>
## <a name="the-matchcollection-and-match-objects"></a>MatchCollection ve Match Nesneleri  
 Regex yöntemleri normal ifade nesnesi modelinin bir <xref:System.Text.RegularExpressions.MatchCollection> parçası olan <xref:System.Text.RegularExpressions.Match> iki nesne döndürür: nesne ve nesne.  
  
<a name="the_match_collection"></a>
### <a name="the-match-collection"></a>Maç Koleksiyonu  
 Yöntem, <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> normal <xref:System.Text.RegularExpressions.MatchCollection> ifade <xref:System.Text.RegularExpressions.Match> altyapısının bulduğu tüm eşleşmeleri, giriş dizesinde oluştukları sırada temsil eden nesneleri içeren bir nesne döndürür. Eşleşme yoksa, yöntem üyesi olmayan <xref:System.Text.RegularExpressions.MatchCollection> bir nesneyi döndürür. Özellik, <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> koleksiyonun tek tek üyelerine, mülkün değerinden sıfırdan bire kadar dizin olarak erişmenizi <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> sağlar. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A>koleksiyonun dizinleyicisidir (C#' da) ve varsayılan özelliktir (Visual Basic'te).  
  
 Varsayılan olarak, <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> yönteme çağrı <xref:System.Text.RegularExpressions.MatchCollection> nesneyi doldurmak için tembel değerlendirme kullanır. Bunlar <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> özellikler gibi tam doldurulmuş bir koleksiyon gerektiren özelliklere erişim, bir performans cezası içerebilir. Sonuç olarak, yöntem tarafından döndürülen <xref:System.Collections.IEnumerator> nesneyi kullanarak koleksiyona <xref:System.Text.RegularExpressions.MatchCollection.GetEnumerator%2A?displayProperty=nameWithType> erişmenizi öneririz. Tek tek diller, Visual `For Each` Basic ve `foreach` C# gibi koleksiyonun <xref:System.Collections.IEnumerator> arabirimini saran yapılar sağlar.  
  
 Aşağıdaki örnek, <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%29?displayProperty=nameWithType> bir <xref:System.Text.RegularExpressions.MatchCollection> giriş dizesinde bulunan tüm eşleşmeleri bir nesneyi doldurmak için yöntemi kullanır. Örnek, koleksiyonu numaralandırır, eşleşmeleri bir dize dizisiyle kopyalar ve bir tamsayı dizisinde karakter konumlarını kaydeder.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matchcollection1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matchcollection1.vb#6)]  
  
<a name="the_match"></a>
### <a name="the-match"></a>Maç  
 Sınıf, <xref:System.Text.RegularExpressions.Match> tek bir normal ifade eşleşmesinin sonucunu temsil eder. Nesnelere <xref:System.Text.RegularExpressions.Match> iki şekilde erişebilirsiniz:  
  
- <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> Yöntemle döndürülen <xref:System.Text.RegularExpressions.MatchCollection> nesneden alarak. Tek tek <xref:System.Text.RegularExpressions.Match> nesneleri almak için, (C#) `foreach` veya `For Each`... kullanarak koleksiyonu yineleyin `Next` (Visual Basic'te) belirli <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> bir <xref:System.Text.RegularExpressions.Match> nesneyi dizin veya ada göre almak için özelliği oluşturveya kullanın. Ayrıca, koleksiyondaki <xref:System.Text.RegularExpressions.Match> nesne sayısını sıfırdan bire doğru, dizin olarak yineleyerek koleksiyondan tek tek nesneleri alabilirsiniz. Ancak, bu yöntem, <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> özelliğe erişir, çünkü tembel değerlendirme yararlanmaz.  
  
     Aşağıdaki örnek, bir <xref:System.Text.RegularExpressions.Match> <xref:System.Text.RegularExpressions.MatchCollection> nesneden tek tek nesneleri kullanarak koleksiyonu `foreach` `For Each`yineleyerek alır ... `Next` inşa etmek. Normal ifade, giriş dizesindeki "abc" dizeyle eşleşir.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match2.vb#7)]  
  
- Bir dize <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> veya bir <xref:System.Text.RegularExpressions.Match> dize bir bölümünde ilk eşleşmeyi temsil eden bir nesne döndürür yöntemi çağırarak. Özelliğin değerini `Match.Success` alarak eşleşmenin bulunup bulunmadığını belirleyebilirsiniz. Sonraki <xref:System.Text.RegularExpressions.Match> eşleşmeleri temsil eden nesneleri <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> almak için, `Success` döndürülen <xref:System.Text.RegularExpressions.Match> nesnenin özelliği `false`olana kadar yöntemi tekrar tekrar çağırın.  
  
     Aşağıdaki örnek, <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> giriş <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> dizesinde "abc" dizesini eşleştirmek için ve yöntemleri kullanır.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match3.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match3.vb#8)]  
  
 Sınıf iade <xref:System.Text.RegularExpressions.Match> toplama nesnelerinin iki özelliği:  
  
- Özellik, <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> normal <xref:System.Text.RegularExpressions.GroupCollection> ifade desenindeki yakalama gruplarıyla eşleşen alt dizeleri hakkında bilgi içeren bir nesne döndürür.  
  
- Özellik `Match.Captures` sınırlı <xref:System.Text.RegularExpressions.CaptureCollection> kullanımda olan bir nesne döndürür. Koleksiyon, <xref:System.Text.RegularExpressions.Match> özelliği `Success` `false`. Aksi takdirde, <xref:System.Text.RegularExpressions.Capture> <xref:System.Text.RegularExpressions.Match> nesneyle aynı bilgiye sahip tek bir nesne içerir.  
  
 Bu nesneler hakkında daha fazla bilgi için, bu konunun ilerleyen bölümlerinde [Grup Koleksiyonu](#GroupCollection) ve [Yakalama Koleksiyonu](#CaptureCollection) bölümlerine bakın.  
  
 <xref:System.Text.RegularExpressions.Match> Sınıfın iki ek özelliği eşleşme hakkında bilgi sağlar. Özellik, `Match.Value` normal ifade deseniyle eşleşen giriş dizesinde alt dizeyi döndürür. Özellik, `Match.Index` giriş dizesinde eşleşen dizenin sıfır tabanlı başlangıç konumunu döndürür.  
  
 Sınıfın <xref:System.Text.RegularExpressions.Match> da iki desen eşleştirme yöntemi vardır:  
  
- Yöntem, <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> geçerli <xref:System.Text.RegularExpressions.Match> nesne tarafından temsil edilen eşleşmeyi eşleştirmeden <xref:System.Text.RegularExpressions.Match> sonra bulur ve bu eşleşmeyi temsil eden bir nesneyi döndürür.  
  
- Yöntem <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> eşleşen dize üzerinde belirtilen bir değiştirme işlemi gerçekleştirir ve sonucu döndürür.  
  
 Aşağıdaki örnek, <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> bir $ sembolü ve iki kesirli basamak içeren her sayının önce bir boşluk prepend yöntemikullanır.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/result1.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/result1.vb#9)]  
  
 Normal ifade `\b\d+(,\d{3})*\.\d{2}\b` deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`(,\d{3})*`|Virgüldeki sıfır veya daha fazla oluşumları ve ardından üç ondalık basamakla eşleştirin.|  
|`\.`|Ondalık nokta karakterini eşleştirin.|  
|`\d{2}`|İki ondalık basamak eşleştirin.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Değiştirme deseni, `$$ $&` eşleşen alt dizenin bir dolar işareti ($) `$$` simgesi (desen), boşluk ve eşleşmenin `$&` değeri (desen) ile değiştirilmesi gerektiğini gösterir.  
  
 [Başa dön](#introduction)  
  
<a name="GroupCollection"></a>
## <a name="the-group-collection"></a>Grup Koleksiyonu  
 Özellik, <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> yakalanan <xref:System.Text.RegularExpressions.GroupCollection> grupları <xref:System.Text.RegularExpressions.Group> tek bir eşleşmede temsil eden nesneleri içeren bir nesne döndürür. Koleksiyondaki <xref:System.Text.RegularExpressions.Group> ilk nesne (dizin0'de) tüm eşleşmeyi temsil eder. İzleyen her nesne tek bir yakalama grubunun sonuçlarını temsil eder.  
  
 Özelliği kullanarak <xref:System.Text.RegularExpressions.Group> koleksiyondaki tek tek nesneleri alabilirsiniz. <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> Adı açıklanmayan grupları koleksiyondaki konumlarına göre alabilir ve adlandırılmış grupları ada göre veya sıraya göre alabilirsiniz. Adsız yakalamalar önce koleksiyonda görünür ve normal ifade deseninde göründükleri sırada soldan sağa dizine dizine alınır. Adlandırılmış yakalamalar, normal ifade deseninde göründükleri sırada soldan sağa, adlandırılmış yakalamalardan sonra dizine dizine alınır. Belirli bir normal ifade eşleştirme yöntemi için döndürülen koleksiyonda hangi numaralanmış <xref:System.Text.RegularExpressions.Regex.GetGroupNumbers%2A?displayProperty=nameWithType> grupların kullanılabillerini belirlemek için örnek yöntemini arayabilirsiniz. Koleksiyonda hangi adlandırılmış grupların kullanılabileni belirlemek <xref:System.Text.RegularExpressions.Regex.GetGroupNames%2A?displayProperty=nameWithType> için örnek yöntemini çağırabilirsiniz. Her iki yöntem de, herhangi bir normal ifade yle bulunan eşleşmeleri analiz eden genel amaçlı yordamlarda özellikle yararlıdır.  
  
 Özellik, <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> C#'daki koleksiyonun dizinleyicisidir ve Visual Basic'teki koleksiyon nesnesinin varsayılan özelliğidir. Bu, tek <xref:System.Text.RegularExpressions.Group> tek nesnelere dizin (veya adlandırılmış gruplar durumunda adla) aşağıdaki gibi erişilebildiği anlamına gelir:  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupsyntax1.cs#13)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupsyntax1.vb#13)]  
  
 Aşağıdaki örnek, bir tarihin ayını, gününü ve yılını yakalamak için gruplandırma yapılarını kullanan normal bir ifade tanımlar.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupcollection1.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupcollection1.vb#10)]  
  
 Normal ifade `\b(\w+)\s(\d{1,2}),\s(\d{4})\b` deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`(\d{1,2})`|Bir veya iki ondalık basamak eşleştirin. Bu ikinci yakalama grubudur.|  
|`,`|Bir virgülü eşleştirin.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`(\d{4})`|Dört ondalık basamakeşleştirin. Bu, üçüncü yakalama grubudur.|  
|`\b`|Eşleşmeyi sözcük sınırında sonla.|  
  
 [Başa dön](#introduction)  
  
<a name="the_captured_group"></a>
## <a name="the-captured-group"></a>Yakalanan Grup  
 Sınıf, <xref:System.Text.RegularExpressions.Group> tek bir yakalama grubunun sonucunu temsil eder. Normal bir ifadede tanımlanan yakalama gruplarını temsil eden <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> grup nesneleri, <xref:System.Text.RegularExpressions.GroupCollection> <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özellik tarafından döndürülen nesnenin özelliği tarafından döndürülür. Özellik <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> dizinleyici (C#) ve varsayılan özelliği (Visual Basic) <xref:System.Text.RegularExpressions.Group> sınıfın. Ayrıca, koleksiyonu kullanarak `foreach` veya `For Each` yapıyı kullanarak tek tek üyeleri de alabilirsiniz. Örneğin, önceki bölüme bakın.  
  
 Aşağıdaki örnek, alt dizeleri gruplara yakalamak için iç içe gruplandırma yapılarını kullanır. Normal ifade `(a(b))c` deseni "abc" dizesi ile eşleşir. İlk yakalama grubuna "ab" alt dizesini, ikinci yakalama grubuna "b" alt dizesini atar.  
  
 [!code-csharp[RegularExpressions.Classes#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#6)]
 [!code-vb[RegularExpressions.Classes#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#6)]  
  
 Aşağıdaki örnekte, normal ifadenin iki nokta üst üste (:) bölündüğü "DATANAME:VALUE" biçiminde veri içeren bir dizeden alt dizeleri yakalamak için adlandırılmış gruplandırma yapıları kullanılır.  
  
 [!code-csharp[RegularExpressions.Classes#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#8)]
 [!code-vb[RegularExpressions.Classes#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#8)]  
  
 Normal ifade `^(?<name>\w+):(?<value>\w+)` deseni aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Giriş dizesinin başında eşleşmeye başla.|  
|`(?<name>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu yakalama grubunun `name`adı.|  
|`:`|Bir kolon maç.|  
|`(?<value>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu yakalama grubunun `value`adı.|  
  
 <xref:System.Text.RegularExpressions.Group> Sınıfın `Group.Value` özellikleri yakalanan grup hakkında bilgi sağlar: Özellik yakalanan alt `Group.Index` dizeyi içerir, özellik giriş metninde yakalanan `Group.Length` grubun başlangıç konumunu gösterir, özellik `Group.Success` yakalanan metnin uzunluğunu içerir ve özellik, bir alt dizenin yakalama grubu tarafından tanımlanan desenle eşleşip eşleşmediğini gösterir.  
  
 Bir gruba niceleyiciler uygulamak (daha fazla bilgi için [bkz. Ölçütler)](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)yakalama grubu başına bir yakalamanın ilişkisini iki şekilde değiştirir:  
  
- `*` Bir gruba `*?` (sıfır veya daha fazla eşleşme belirtir) veya niceleyici uygulanırsa, bir yakalama grubunun giriş dizesinde eşleşme olmayabilir. Yakalanan metin olmadığında, nesnenin <xref:System.Text.RegularExpressions.Group> özellikleri aşağıdaki tabloda gösterildiği gibi ayarlanır.  
  
    |Grup özelliği|Değer|  
    |--------------------|-----------|  
    |`Success`|`false`|  
    |`Value`|<xref:System.String.Empty?displayProperty=nameWithType>|  
    |`Length`|0|  
  
     Aşağıdaki örnek, bir gösterim sağlar. Normal ifade deseninde, `aaa(bbb)*ccc`ilk yakalama grubu (alt dize "bbb") sıfır veya daha fazla kez eşleşebilir. Giriş dizesi "aaaccc" desenle eşleştiğinden, yakalama grubunun eşleşmesi yoktur.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/nocapture1.cs#11)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/nocapture1.vb#11)]  
  
- Niceleyiciler, yakalama grubu tarafından tanımlanan bir desenin birden çok oluşumunu eşleyebilir. Bu durumda, `Value` bir `Length` <xref:System.Text.RegularExpressions.Group> nesnenin özellikleri yalnızca yakalanan son alt dize hakkında bilgi içerir. Örneğin, aşağıdaki normal ifade, bir dönemde biten tek bir tümceyle eşleşir. İki gruplama yapısı kullanır: İlk ibare, beyaz alan karakteriyle birlikte tek tek sözcükleri yakalar; ikincisi tek tek sözcükleri yakalar. Örnekteki çıktının gösterdiği gibi, normal ifade tüm cümleyi yakalamayı başarsa da, ikinci yakalama grubu yalnızca son sözcüğü yakalar.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/lastcapture1.cs#12)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/lastcapture1.vb#12)]  
  
 [Başa dön](#introduction)  
  
<a name="CaptureCollection"></a>
## <a name="the-capture-collection"></a>Yakalama Koleksiyonu  
 Nesne <xref:System.Text.RegularExpressions.Group> yalnızca son yakalama hakkında bilgi içerir. Ancak, bir yakalama grubu tarafından yapılan tüm yakalama kümesi, <xref:System.Text.RegularExpressions.CaptureCollection> <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> özellik tarafından döndürülen nesneden hala kullanılabilir. Koleksiyonun her üyesi, <xref:System.Text.RegularExpressions.Capture> yakalanan grup tarafından çekilen sırayla (ve bu nedenle, yakalanan dizelerin giriş dizesinde soldan sağa eşleştir) tarafından yapılan bir yakalamayı temsil eden bir nesnedir. Koleksiyondan tek <xref:System.Text.RegularExpressions.Capture> tek nesneleri iki şekilde alabilirsiniz:  
  
- (C#' da) veya `foreach` `For Each` (Visual Basic) gibi bir yapıyı kullanarak koleksiyonda yineleyerek.  
  
- Dizin <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A?displayProperty=nameWithType> tarafından belirli bir nesne almak için özelliği kullanarak. Özellik <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A> nesnenin <xref:System.Text.RegularExpressions.CaptureCollection> varsayılan özelliğidir (Visual Basic'te) veya dizinleyicidir (C#'da).  
  
 Bir ölçme grubuna bir niceleyici uygulanmazsa, <xref:System.Text.RegularExpressions.CaptureCollection> <xref:System.Text.RegularExpressions.Capture> <xref:System.Text.RegularExpressions.Group> nesne, nesnesi ile aynı eşleşme hakkında bilgi sağladığından, çok az ilgi çeken tek bir nesne içerir. Bir ölçme grubu için bir niceleyici uygulanırsa, <xref:System.Text.RegularExpressions.CaptureCollection> nesne yakalama grubu tarafından yapılan tüm yakalamaları içerir ve koleksiyonun <xref:System.Text.RegularExpressions.Group> son üyesi nesneyle aynı yakalamayı temsil eder.  
  
 Örneğin, "abcabcabc" dizesinden eşleşmeleri yakalamak için normal ifade deseni `((a(b))c)+` (+ nicelemenin bir veya daha <xref:System.Text.RegularExpressions.CaptureCollection> fazla <xref:System.Text.RegularExpressions.Group> eşleşme belirttiği) kullanırsanız, her nesne için nesne üç üye içerir.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capturecollection1.cs#14)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capturecollection1.vb#14)]  
  
 Aşağıdaki örnek, "XYZAbcAbcAbcAbcXYZAbcAb" dizesinde "Abc" dizesinin bir veya daha fazla ardışık çalışır bulmak için normal ifadeyi `(Abc)+` kullanır. Örnek, yakalanan alt dizeleri birden çok grup döndürmek için <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> özelliğin kullanımını göstermektedir.  
  
 [!code-csharp[RegularExpressions.Classes#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#5)]
 [!code-vb[RegularExpressions.Classes#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#5)]  
  
 [Başa dön](#introduction)  
  
<a name="the_individual_capture"></a>
## <a name="the-individual-capture"></a>Bireysel Yakalama  
 Sınıf, <xref:System.Text.RegularExpressions.Capture> tek bir alt ifade yakalamanın sonuçlarını içerir. Özellik <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType> eşleşen metni içerir ve <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType> özellik, eşleşen alt dizenin başladığı giriş dizesinde sıfır tabanlı konumu gösterir.  
  
 Aşağıdaki örnek, seçili şehirlerin sıcaklığı için bir giriş dizesini ayrıştirır. Virgül (",") bir şehri ve sıcaklığını ayırmak için kullanılır ve her şehrin verilerini ayırmak için bir yarı kolon (";") kullanılır. Tüm giriş dizesi tek bir eşleşmeyi temsil eder. Dize ayrıştırmak için kullanılan normal ifade deseninde, `((\w+(\s\w+)*),(\d+);)+`şehir adı ikinci yakalama grubuna, sıcaklık ise dördüncü yakalama grubuna atanır.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capture1.cs#16)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capture1.vb#16)]  
  
 Normal ifade aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`(\s\w+)*`|Bir veya daha fazla sözcük karakteri tarafından izlenen bir beyaz boşluk karakterinin sıfır veya daha fazla oluşumlarını eşleştirin. Bu desen, çok kelimeli şehir adlarıyla eşleşir. Bu, üçüncü yakalama grubudur.|  
|`(\w+(\s\w+)*)`|Bir veya daha fazla sözcük karakterini, ardından bir beyaz boşluk karakterinin ve bir veya daha fazla sözcük karakterinin sıfır veya daha fazla oluşumunu eşleştirin. Bu ikinci yakalama grubudur.|  
|`,`|Bir virgülü eşleştirin.|  
|`(\d+)`|Bir veya daha fazla basamak eşleştirin. Bu dördüncü yakalama grubudur.|  
|`;`|Bir yarı kolon maç.|  
|`((\w+(\s\w+)*),(\d+);)+`|Virgül, bir veya daha fazla basamak ve bir yarı kolon, bir veya daha fazla kez takip herhangi bir ek kelime takip bir sözcük deseni eşleştirin. Bu ilk yakalama grubudur.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Text.RegularExpressions>
- [.NET Düzenli İfadeler](../../../docs/standard/base-types/regular-expressions.md)
- [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
