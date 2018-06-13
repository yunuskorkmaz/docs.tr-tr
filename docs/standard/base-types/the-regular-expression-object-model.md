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
ms.openlocfilehash: 14402b56a765fc8fe57f40e9c5c44f500267e266
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579866"
---
# <a name="the-regular-expression-object-model"></a>Normal İfade Nesnesi Modeli
<a name="introduction"></a> Bu konu içinde .NET Normal ifadelerle çalışma kullanılan nesne modeli açıklar. Aşağıdaki bölümleri içerir:  
  
-   [Normal ifade altyapısı](#Engine)  
  
-   [MatchCollection ve eşleşen nesneleri](#Match_and_MCollection)  
  
-   [Grup koleksiyonu](#GroupCollection)  
  
-   [Yakalanan grubu](#the_captured_group)  
  
-   [Yakalama toplama](#CaptureCollection)  
  
-   [Tek tek yakalama](#the_individual_capture)  
  
<a name="Engine"></a>   
## <a name="the-regular-expression-engine"></a>Normal ifade altyapısı  
 .NET normal ifade altyapısında tarafından temsil edilen <xref:System.Text.RegularExpressions.Regex> sınıfı. Normal ifade altyapısı, ayrıştırma ve normal bir ifade derleme ve giriş dizesi ile normal ifade ile eşleşen işlemleri gerçekleştirmek için sorumludur. .NET normal ifade nesnesi modeli merkezi bileşeni altyapısıdır.  
  
 Normal ifade altyapısı iki yöntemden birini kullanabilirsiniz:  
  
-   Statik yöntemlerini çağırarak <xref:System.Text.RegularExpressions.Regex> sınıfı. Yöntem parametreleri giriş dizesi ve normal ifade deseni içerir. Normal ifade altyapısı aynı normal ifade kullanın statik normal ifade yöntemleri yinelenen çağrıları görece iyi bir performans sağlar, böylece statik yöntem çağrılarında kullanılan normal ifadeler önbelleğe alır.  
  
-   Örnek oluşturma tarafından bir <xref:System.Text.RegularExpressions.Regex> normal bir ifade sınıfı oluşturucusuna geçirerek nesnesi. Bu durumda, <xref:System.Text.RegularExpressions.Regex> nesnesidir değişmez (salt okunur) ve tek bir normal ifade ile sıkı şekilde bağlı bir normal ifade altyapısını temsil eder. Normal ifadeler tarafından kullanıldığından <xref:System.Text.RegularExpressions.Regex> örneklerini önbelleğe alınmaz, değil örneği bir <xref:System.Text.RegularExpressions.Regex> nesnesiyle birden çok kez aynı normal ifade.  
  
 Yöntemleri çağırma <xref:System.Text.RegularExpressions.Regex> sınıfı aşağıdaki işlemleri gerçekleştirin:  
  
-   Bir dizeyi bir normal ifade deseni eşleşip eşleşmediğini belirler.  
  
-   Tek bir eşleşme veya ilk eşleşme ayıklayın.  
  
-   Tüm eşleşmeleri ayıklayın.  
  
-   Eşleşen alt dizeyi değiştirin.  
  
-   Tek bir dize bir dizeler dizisi bölün.  
  
 Bu işlemler aşağıdaki bölümlerde açıklanmıştır.  
  
### <a name="matching-a-regular-expression-pattern"></a>Normal ifade desen eşleştirme  
 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> Yöntemi döndürür `true` dize desen eşleşirse veya `false` mevcut değilse. <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> Yöntemi genellikle dize girişi doğrulamak için kullanılır. Örneğin, aşağıdaki kod bir dizesi geçerli bir sosyal güvenlik numarası Amerika Birleşik Devletleri'nde eşleşmesini sağlar.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/validate1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/validate1.vb#1)]  
  
 Normal ifade deseni `^\d{3}-\d{2}-\d{4}$` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Giriş dizesi başlangıcını eşleşir.|  
|`\d{3}`|Üç ondalık basamakla eşleş.|  
|`-`|Bir tire ile aynı.|  
|`\d{2}`|İki ondalık basamak eşleşir.|  
|`-`|Bir tire ile aynı.|  
|`\d{4}`|Dört ondalık basamak eşleşir.|  
|`$`|Giriş dizesinin sonuyla eşleş.|  
  
### <a name="extracting-a-single-match-or-the-first-match"></a>Tek bir eşleşme veya ilk eşleşme ayıklanıyor  
 <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> Yöntemi döndürür bir <xref:System.Text.RegularExpressions.Match> bir normal ifade ile eşleşen ilk alt dizeyi hakkında bilgi içeren nesne. Varsa `Match.Success` özelliği döndürür `true`, belirten bir eşleşme bulunamadı, çağırarak sonraki eşleşme hakkında bilgi alabilir <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> yöntemi. Bu yöntem çağrılarını kadar devam edebilirsiniz `Match.Success` özelliği döndürür `false`. Örneğin, aşağıdaki kullandığı kod <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> dizesi içinde yinelenen bir sözcük ilk örneğini bulmak için yöntem. Daha sonra çağırır <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> herhangi bir ek oluşumu bulmak için yöntem. Örnek inceler `Match.Success` özelliği geçerli eşleşme başarılı olup olmadığını ve yapılan bir çağrı olup olmadığını belirlemek için her yöntem çağrısı sonra <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> yöntemi izlemelidir.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match1.vb#2)]  
  
 Normal ifade deseni `\b(\w+)\W+(\1)\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Word sınır eşleşmeye başlayın.|  
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|  
|`\W+`|Bir veya daha fazla word olmayan karakter eşleşmesi.|  
|`(\1)`|İlk yakalanan dize eşleşmesi. Bu ikinci yakalama grubudur.|  
|`\b`|Son bir word sınırında eşleşmiyor.|  
  
### <a name="extracting-all-matches"></a>Tüm eşleşmeleri ayıklanıyor  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> Yöntemi döndürür bir <xref:System.Text.RegularExpressions.MatchCollection> normal ifade altyapısı giriş dizesi içinde bulunan tüm eşleşmeleri hakkında bilgi içeren nesne. Örneğin, önceki örnekte çağırmak için yazılması <xref:System.Text.RegularExpressions.Regex.Matches%2A> yöntemi yerine <xref:System.Text.RegularExpressions.Regex.Match%2A> ve <xref:System.Text.RegularExpressions.Match.NextMatch%2A> yöntemleri.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matches1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matches1.vb#3)]  
  
### <a name="replacing-a-matched-substring"></a>Eşleşen alt dize değiştirme  
 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> Yöntemi, normal ifade deseni belirtilen dizenin veya normal ifade deseni ile eşleşen ve değişiklik tüm giriş dizesini döndürür her substring değiştirir. Örneğin, aşağıdaki kod bir ondalık sayı önce ABD para birimi simgesini bir dize ekler.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/replace1.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/replace1.vb#4)]  
  
 Normal ifade deseni `\b\d+\.\d{2}\b` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`\.`|Bir süre aynı.|  
|`\d{2}`|İki ondalık basamak eşleşir.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Değiştirme deseni `$$$&` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Değiştirme dizesi|  
|-------------|------------------------|  
|`$$`|Dolar işareti ($) karakterini.|  
|`$&`|Eşleşen alt dizenin tamamı.|  
  
### <a name="splitting-a-single-string-into-an-array-of-strings"></a>Tek bir dize bir dizeler dizisi halinde bölme  
 <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> Yöntemi giriş dizesi bir normal ifade eşleştirmesi tarafından tanımlanan konumlarda böler. Örneğin, aşağıdaki kod, öğeleri numaralı bir listede bir dize dizisi yerleştirir.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/split1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/split1.vb#5)]  
  
 Normal ifade deseni `\b\d{1,2}\.\s` aşağıdaki tabloda gösterildiği gibi yorumlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\d{1,2}`|Bir veya iki ondalık basamak eşleşir.|  
|`\.`|Bir süre aynı.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
  
<a name="Match_and_MCollection"></a>   
## <a name="the-matchcollection-and-match-objects"></a>MatchCollection ve eşleşen nesneleri  
 Regex yöntemleri normal ifade nesnesi modeli parçası olan iki nesne döndürür: <xref:System.Text.RegularExpressions.MatchCollection> nesnesi ve <xref:System.Text.RegularExpressions.Match> nesne.  
  
<a name="the_match_collection"></a>   
### <a name="the-match-collection"></a>Eşleşme koleksiyonu  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> Yöntemi döndürür bir <xref:System.Text.RegularExpressions.MatchCollection> içeren nesne <xref:System.Text.RegularExpressions.Match> giriş dizesini oluşma sırasına normal ifade altyapısı bulunan tüm eşleşmeleri temsil eden nesne. Herhangi bir eşleşme varsa vardır, yöntem döndürür bir <xref:System.Text.RegularExpressions.MatchCollection> nesnesi ile üye yok. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> Özelliği sağlar, tek tek üyelerine erişme toplama dizini tarafından gelen sıfır bir değerinden daha az <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> özelliği. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A> koleksiyonun oluşturucuda (C#) ve varsayılan özelliği (Visual Basic) olur.  
  
 Varsayılan olarak, çağrısı <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> yöntemi doldurmak için geç değerlendirme kullanan <xref:System.Text.RegularExpressions.MatchCollection> nesnesi. Tam olarak doldurulan bir koleksiyon gibi gereken özelliklerine erişimi <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> özellikleri, performans cezası gerektirebilir. Sonuç olarak, koleksiyon kullanarak erişim öneririz <xref:System.Collections.IEnumerator> tarafından döndürülen nesne <xref:System.Text.RegularExpressions.MatchCollection.GetEnumerator%2A?displayProperty=nameWithType> yöntemi. Tek tek diller sağlayan yapıları gibi `For``Each` Visual Basic'te ve `foreach` C# ' ta, sarmalama koleksiyonunun <xref:System.Collections.IEnumerator> arabirimi.  
  
 Aşağıdaki örnek kullanır <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%29?displayProperty=nameWithType> doldurmak için yöntemi bir <xref:System.Text.RegularExpressions.MatchCollection> bir giriş dizesi içinde bulunan tüm eşleşmeleri olan nesne. Örnek koleksiyonu numaralandırır, eşleşen bir dize dizisi kopyalar ve bir tamsayı dizideki karakter konumlarını kaydeder.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matchcollection1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matchcollection1.vb#6)]  
  
<a name="the_match"></a>   
### <a name="the-match"></a>Eşleşme  
 <xref:System.Text.RegularExpressions.Match> Sınıfı, bir tek normal ifade eşleştirmesi sonucunu temsil eder. Erişebileceğiniz <xref:System.Text.RegularExpressions.Match> iki yolla nesneler:  
  
-   Bunlardan alarak <xref:System.Text.RegularExpressions.MatchCollection> tarafından döndürülen nesne <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> yöntemi. Tek tek almak için <xref:System.Text.RegularExpressions.Match> nesneleri, yineleme koleksiyonu kullanarak bir `foreach` (C# ' ta) veya `For Each`... `Next` (Visual Basic'te) oluşturmak veya kullanmak <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> belirli bir almak için özelliğini <xref:System.Text.RegularExpressions.Match> nesne dizini veya adı. Ayrıca tek tek alabilir <xref:System.Text.RegularExpressions.Match> nesneleri koleksiyonu gelen dizini tarafından yineleme tarafından koleksiyonundan sıfır için daha az, koleksiyondaki nesne sayısı. Eriştiği çünkü Bununla birlikte, bu yöntem, geç değerlendirme avantajından değil <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> özelliği.  
  
     Aşağıdaki örnek tek tek alır <xref:System.Text.RegularExpressions.Match> nesnelerin bir <xref:System.Text.RegularExpressions.MatchCollection> koleksiyonunu kullanarak yineleme nesne `foreach` veya `For Each`... `Next` oluşturun. Normal ifade yalnızca giriş dizesi "abc" dizesini eşleştirir.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match2.vb#7)]  
  
-   Çağırarak <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> döndürür yöntemi bir <xref:System.Text.RegularExpressions.Match> bir dize veya dize bir kısmı, ilk eşleşmeyi temsil eden nesne. Değerini alarak eşleşme bulunamadı olup olmadığını belirlemek `Match.Success` özelliği. Almak için <xref:System.Text.RegularExpressions.Match> sonraki eşleşmeleri temsil eden nesneler çağrısı <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> yöntemi kadar sürekli, `Success` özelliği döndürülen <xref:System.Text.RegularExpressions.Match> nesne `false`.  
  
     Aşağıdaki örnek kullanır <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> giriş dizesi "abc" dizesini eşleştirmek için yöntemleri.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match3.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match3.vb#8)]  
  
 İki özelliklerini <xref:System.Text.RegularExpressions.Match> sınıfının return koleksiyon nesnesi:  
  
-   <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> Özelliği döndürür bir <xref:System.Text.RegularExpressions.GroupCollection> yakalama eşleşen alt dizeler hakkında bilgi içeren nesne grupları normal ifade deseni.  
  
-   `Match.Captures` Özelliği döndürür bir <xref:System.Text.RegularExpressions.CaptureCollection> , nesne sınırlı kullanımı. Koleksiyon için doldurulmaz bir <xref:System.Text.RegularExpressions.Match> nesnesindeki `Success` özelliği `false`. Aksi durumda, tek bir içeren <xref:System.Text.RegularExpressions.Capture> , aynı bilgilerine sahip bir nesne <xref:System.Text.RegularExpressions.Match> nesne.  
  
 Bu nesneler hakkında daha fazla bilgi için bkz: [Grup Collection](#GroupCollection) ve [yakalama Collection](#CaptureCollection) bu konunun ilerleyen bölümlerinde bölümlere.  
  
 İki ek özelliklerini <xref:System.Text.RegularExpressions.Match> sınıfı eşleşme hakkında bilgi sağlar. `Match.Value` Özelliği, normal ifade deseni ile eşleşen giriş dizesi içinde alt dizeyi döndürür. `Match.Index` Özelliği giriş dizesini eşleşen dize sıfır tabanlı başlangıç konumunu döndürür.  
  
 <xref:System.Text.RegularExpressions.Match> Sınıfı da Desen eşleştirme iki yöntem vardır:  
  
-   <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> Yöntemi geçerli tarafından temsil edilen eşleşme sonra eşleşme bulur <xref:System.Text.RegularExpressions.Match> nesne ve döndürür bir <xref:System.Text.RegularExpressions.Match> eşleşen temsil eden nesne.  
  
-   <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> Yöntemi eşleşen dizesinde belirtilen değiştirme işlemi gerçekleştirir ve sonucu döndürür.  
  
 Aşağıdaki örnek kullanır <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> $ simge ve iki kesir basamakları içeren tüm sayıları önce boşluk önüne eklediğinizden yöntemi.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/result1.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/result1.vb#9)]  
  
 Normal ifade deseni `\b\d+(,\d{3})*\.\d{2}\b` aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
|`(,\d{3})*`|Üç ondalık basamak ile izlenen virgül sıfır veya daha çok tekrarı eşleşir.|  
|`\.`|Ondalık karakter eşleşmesi.|  
|`\d{2}`|İki ondalık basamak eşleşir.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Değiştirme deseni `$$ $&` eşleşen alt dizeyi dolar işareti ($) simgeyle yerini aldığını gösterir ( `$$` desen), bir boşluk ve eşleşme değerini ( `$&` desen).  
  
 [Başa dön](#introduction)  
  
<a name="GroupCollection"></a>   
## <a name="the-group-collection"></a>Grup koleksiyonu  
 <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> Özelliği döndürür bir <xref:System.Text.RegularExpressions.GroupCollection> içeren nesne <xref:System.Text.RegularExpressions.Group> tek bir eşleşme yakalanan gruplarında temsil eden nesne. İlk <xref:System.Text.RegularExpressions.Group> (0 dizinindeki) koleksiyon nesnesinde tüm eşleşme temsil eder. Aşağıdaki her nesnenin tek bir yakalama grubunu sonuçlarını temsil eder.  
  
 Tek tek alabilir <xref:System.Text.RegularExpressions.Group> kullanarak koleksiyonundaki nesneleri <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> özelliği. Adlandırılmamış grupları koleksiyonu sıralı konumlarını tarafından almak ve ada göre veya sıralı konuma göre adlandırılmış gruplar alın. Adlandırılmamış yakalamaları koleksiyonda ilk görünür ve soldan sağa dizinlenir normal ifade deseni göründükleri sırada. Adlandırılmış yakalamaları dizine soldan sağa adlandırılmamış yakalamaları sonra normal ifade deseni göründükleri sırada. Numaralı grupları yöntemi eşleşen bir özel normal ifade için döndürülen koleksiyonundaki kullanılabilir olduğunu belirlemek için örnek çağırabilirsiniz <xref:System.Text.RegularExpressions.Regex.GetGroupNumbers%2A?displayProperty=nameWithType> yöntemi. Adlandırılmış grupları koleksiyonda kullanılabilir olduğunu belirlemek için örnek çağırabilirsiniz <xref:System.Text.RegularExpressions.Regex.GetGroupNames%2A?displayProperty=nameWithType> yöntemi. Her iki yöntem tarafından herhangi bir normal ifade bulunan eşleşmeler çözümlemek üzere genel amaçlı yordamlar özellikle yararlıdır.  
  
 <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> Koleksiyon C# ve Visual Basic koleksiyon nesnesinin varsayılan özellik Oluşturucusu bir özelliktir. Bu kişi yani <xref:System.Text.RegularExpressions.Group> nesneleri erişilebilir dizini (veya adlandırılmış gruplar durumunda adına göre) gibi:  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupsyntax1.cs#13)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupsyntax1.vb#13)]  
  
 Aşağıdaki örnek, ay, gün ve tarihin yıl değerini yakalamak için gruplandırma yapıları kullanan normal bir ifade tanımlar.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupcollection1.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupcollection1.vb#10)]  
  
 Normal ifade deseni `\b(\w+)\s(\d{1,2}),\s(\d{4})\b` aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`(\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu ilk yakalama grubudur.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`(\d{1,2})`|Bir veya iki ondalık basamak eşleşir. Bu ikinci yakalama grubudur.|  
|`,`|Bir virgülü eşleştirin.|  
|`\s`|Bir boşluk karakteri ile eşleştirin.|  
|`(\d{4})`|Dört ondalık basamak eşleşir. Bu, üçüncü yakalama grubudur.|  
|`\b`|Son bir word sınırında eşleşmiyor.|  
  
 [Başa dön](#introduction)  
  
<a name="the_captured_group"></a>   
## <a name="the-captured-group"></a>Yakalanan grubu  
 <xref:System.Text.RegularExpressions.Group> Sınıfı tek bir yakalama grubundan sonucunu temsil eder. Normal ifadede tanımlanan yakalama gruplarını temsil eden grup nesneleri tarafından döndürülen <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> özelliği <xref:System.Text.RegularExpressions.GroupCollection> tarafından döndürülen nesne <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliği. <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> Özelliktir oluşturucuda (C#) ve (Visual Basic'te) varsayılan özelliği <xref:System.Text.RegularExpressions.Group> sınıfı. Koleksiyonu kullanarak yineleme, tek tek üyeleri de alabilirsiniz `foreach` veya `For``Each` oluşturun. Örneğin, önceki bölümüne bakın.  
  
 Aşağıdaki örnek, alt dizeler gruplar halinde yakalamak için iç içe gruplandırma yapıları kullanır. Normal ifade deseni `(a(b))c` "abc" dizesini eşleştirir. Bu alt dizeyi "ab" ilk yakalama grubunu ve alt dizeyi "b" ikinci yakalama grubuna atar.  
  
 [!code-csharp[RegularExpressions.Classes#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#6)]
 [!code-vb[RegularExpressions.Classes#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#6)]  
  
 Aşağıdaki örnek, iki nokta (:) normal ifade böler "DATANAME:VALUE" biçiminde veri içeren bir dize öğesinden alt dizeler yakalamak için adlandırılmış gruplandırma yapıları kullanır.  
  
 [!code-csharp[RegularExpressions.Classes#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#8)]
 [!code-vb[RegularExpressions.Classes#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#8)]  
  
 Normal ifade deseni `^(?<name>\w+):(?<value>\w+)` aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Giriş dizesinin başında eşleşmeye başla.|  
|`(?<name>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu yakalama grubunun adı `name`.|  
|`:`|İki nokta ile aynı.|  
|`(?<value>\w+)`|Bir veya daha fazla sözcük karakteri eşleştir. Bu yakalama grubunun adı `value`.|  
  
 Özelliklerini <xref:System.Text.RegularExpressions.Group> sınıfı yakalanan grubu hakkında bilgi sağlar: `Group.Value` özelliği yakalanan alt dizeyi içeren `Group.Index` özelliği, yakalanan grubu Girişmetindekibaşlangıçkonumugösterir`Group.Length` özelliği, yakalanan metnin uzunluğunu içerir ve `Group.Success` özelliği, bir alt dizesi yakalama grubu tarafından tanımlanan desenle eşleşen olup olmadığını belirtir.  
  
 Bir gruba nicelik uygulama (daha fazla bilgi için bkz: [nicelik](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)) iki yolla Grup yakalama başına bir yakalama ilişki değiştirir:  
  
-   Varsa `*` veya `*?` (hangi sıfır veya daha fazla eşleşme belirtir) nicelik, bir gruba uygulanır, bir yakalama grubunu giriş dizesini bir eşleşme olmayabilir. Yakalanan metin, özelliklerini olduğunda <xref:System.Text.RegularExpressions.Group> nesnesi aşağıdaki tabloda gösterildiği gibi ayarlanır.  
  
    |Grup özelliği|Değer|  
    |--------------------|-----------|  
    |`Success`|`false`|  
    |`Value`|<xref:System.String.Empty?displayProperty=nameWithType>|  
    |`Length`|0|  
  
     Aşağıdaki örnek, bir gösterim sağlar. Normal ifade deseni içinde `aaa(bbb)*ccc`, ilk yakalama grubu (substring "bbb"), sıfır veya daha fazla kez eşleşen. Giriş dizesi "aaaccc" deseni eşleştiğinden yakalama grubunu bir eşleşme yok.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/nocapture1.cs#11)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/nocapture1.vb#11)]  
  
-   Nicelik, bir yakalama grubu tarafından tanımlanan bir desen birden çok tekrarı eşleştirebilirsiniz. Bu durumda, `Value` ve `Length` özelliklerini bir <xref:System.Text.RegularExpressions.Group> nesne yalnızca son yakalanan alt dizeyi ilgili bilgiler içerir. Örneğin, bir süre içinde sona erer tek bir cümle şu normal ifadeyle eşleşir. İki gruplandırma yapıları kullanır: ilk sözcükleri tek tek bir boşluk karakteri; birlikte yakalar İkinci ayrı sözcükleri yakalar. Normal ifade tüm cümle yakalama başarılı ancak örnek çıkışı gösterildiği gibi ikinci yakalama grubunu yalnızca son sözcük yakalar.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/lastcapture1.cs#12)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/lastcapture1.vb#12)]  
  
 [Başa dön](#introduction)  
  
<a name="CaptureCollection"></a>   
## <a name="the-capture-collection"></a>Yakalama toplama  
 <xref:System.Text.RegularExpressions.Group> Nesne yalnızca son yakalama hakkında bilgiler içerir. Ancak, bir yakalama grubu tarafından yapılan yakalamaları kümesinin tamamını hala kullanılabilir <xref:System.Text.RegularExpressions.CaptureCollection> tarafından döndürülen nesne <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> özelliği. Her bir koleksiyonun üyesi olan bir <xref:System.Text.RegularExpressions.Capture> bunlar yakalanan sırada Bu yakalama grubu tarafından yapılan bir yakalama temsil eden nesnesi (ve bu nedenle, yakalanan dizeleri eşleşmesi soldan sağa doğru sırayla giriş dizisinde). Tek tek alabilir <xref:System.Text.RegularExpressions.Capture> nesnelerini iki yoldan biriyle koleksiyondan:  
  
-   Bir yapı kullanarak koleksiyonu yineleme yapma tarafından `foreach` (C# ' ta) veya `For``Each` (Visual Basic'te).  
  
-   Kullanarak <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A?displayProperty=nameWithType> özellik dizini tarafından belirli bir nesnesi alınamadı. <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A> Özelliği <xref:System.Text.RegularExpressions.CaptureCollection> nesnesinin varsayılan özelliği (Visual Basic) veya dizin oluşturucu (C# ' ta).  
  
 Bir niceleyici bir yakalama grubuna uygulanmamış durumunda <xref:System.Text.RegularExpressions.CaptureCollection> nesnesini içeren tek bir <xref:System.Text.RegularExpressions.Capture> aynı eşleşme olarak hakkında bilgi sağladığından az ilgi nesne kendi <xref:System.Text.RegularExpressions.Group> nesnesi. Bir niceleyici bir yakalama grubuna uygulanırsa <xref:System.Text.RegularExpressions.CaptureCollection> nesnesi yakalama grubu tarafından yapılan tüm yakalamaları içerir ve koleksiyonun son üyesi olarak aynı yakalama temsil eden <xref:System.Text.RegularExpressions.Group> nesne.  
  
 Örneğin, normal ifade deseni kullanıyorsanız `((a(b))c)+` (burada + nicelik, bir veya daha fazla eşleşme belirtir) yakalamak için "abcabcabc" dizesi ile eşleşen <xref:System.Text.RegularExpressions.CaptureCollection> her nesne <xref:System.Text.RegularExpressions.Group> nesnesini içeren üç üye.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capturecollection1.cs#14)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capturecollection1.vb#14)]  
  
 Aşağıdaki örnek, normal ifade kullanır `(Abc)+` dizesinin bir veya daha fazla ardışık çalışır "Abc" dize "XYZAbcAbcAbcXYZAbcAb" bulmak için. Örnek kullanımını göstermektedir <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> birden çok grupları döndürmek için özellik yakalanan alt dizeler.  
  
 [!code-csharp[RegularExpressions.Classes#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#5)]
 [!code-vb[RegularExpressions.Classes#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#5)]  
  
 [Başa dön](#introduction)  
  
<a name="the_individual_capture"></a>   
## <a name="the-individual-capture"></a>Tek tek yakalama  
 <xref:System.Text.RegularExpressions.Capture> Sınıfı, bir tek alt yakalama sonuçlarından içerir. <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType> Özelliği eşleşen metni içerir ve <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType> özelliği, hangi eşleşen alt dizeyi başlar giriş dizesi içindeki sıfır tabanlı konumu belirtir.  
  
 Aşağıdaki örnek, seçili Şehir sıcaklık için giriş dizesi ayrıştırır. Virgül (",") bir şehir ve onun sıcaklık ve noktalı ayırmak için kullanılan (";") her şehre ait veri ayırmak için kullanılır. Tüm giriş dizesini tek bir eşleşme temsil eder. Normal ifade deseni içinde `((\w+(\s\w+)*),(\d+);)+`dizesini ayrıştırmak için kullanılan, şehir adı ikinci yakalama grubuna atanır ve sıcaklık dördüncü yakalama grubuna atanır.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capture1.cs#16)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capture1.vb#16)]  
  
 Normal ifade aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`(\s\w+)*`|Sıfır veya daha fazla karakterin yineleme sayısını bir veya daha fazla sözcük karakterlerini tarafından izlenen bir boşluk eşleşir. Bu deseni çok word Şehir adları eşleştirir. Bu, üçüncü yakalama grubudur.|  
|`(\w+(\s\w+)*)`|Sıfır veya daha fazla karakterin yineleme sayısını bir boşluk ve bir veya daha fazla sözcük karakterlerini tarafından izlenen bir veya daha fazla sözcük karakterlerini eşleşmesi. Bu ikinci yakalama grubudur.|  
|`,`|Bir virgülü eşleştirin.|  
|`(\d+)`|Bir veya daha fazla basamak eşleşir. Bu dördüncü yakalama grubudur.|  
|`;`|Noktalı virgül ile aynı.|  
|`((\w+(\s\w+)*),(\d+);)+`|Bir veya birden çok kez virgül, bir veya daha fazla basamak ve noktalı virgül tarafından izlenen tüm sözcükleri tarafından izlenen bir word'ün desen ile. Bu ilk yakalama grubudur.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Text.RegularExpressions>  
 [.NET normal ifadeler](../../../docs/standard/base-types/regular-expressions.md)  
 [Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
