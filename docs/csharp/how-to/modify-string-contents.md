---
title: 'Nasıl yapılır: dize içeriklerini - C# Kılavuzu değiştirme'
ms.date: 02/26/2018
helpviewer_keywords:
- strings [C#], modifying
ms.openlocfilehash: 99102fe90f5f675235e2993b7dd99f59214862d2
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39243755"
---
# <a name="how-to-modify-string-contents-in-c"></a>Nasıl yapılır: C# dize içeriklerini değiştirme #

Bu makalede üretmek için çeşitli teknikler gösterir bir `string` değiştirerek varolan `string`. Tüm teknikler gösterilen sonucu olarak yeni bir değişiklik iade `string` nesne. Bunu açıkça göstermek için tüm örnekler sonuç yeni bir değişkende depolayın. Ardından hem özgün inceleyebilirsiniz `string` ve `string` her örneği çalıştırdığınızda değişikliklere karşı kaynaklanan.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Bu makalede gösterilen çeşitli teknikler vardır. Mevcut metni değiştirebilirsiniz. Desen aramak ve diğer metinle eşleşen metin. Bir karakter dizisi bir dize davranabilirsiniz. Boşluk kaldıran yöntemler de kullanabilirsiniz. Kendi senaryonuza en yakından eşleşen teknikleri seçmeniz gerekir.

## <a name="replace-text"></a>Metni Değiştir

Aşağıdaki kod, mevcut metni bir alternatif ile değiştirerek yeni bir dize oluşturur.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#1)]

Yukarıdaki kod bunu göstermektedir *değişmez* dize özelliği. Önceki örnekte gördüğünüz, orijinal dizeyi `source`, değiştirilmez. <xref:System.String.Replace%2A?displayProperty=nameWithType> Yöntemi yeni bir oluşturur `string` değişiklikleri içeren.

<xref:System.String.Replace%2A> Dizeler ya da tek karakterleri yöntemi değiştirebilirsiniz. Her iki durumda da, her geçtiği yeri Aranan metin değiştirilir.  Aşağıdaki örnekte tüm değiştirir ' 'karakterleri ile'\_':

[!code-csharp-interactive[replace characters](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#2)]

Kaynak dizesi değiştirilmez ve değiştirme ile yeni bir dize döndürülür.

## <a name="trim-white-space"></a>Boşluğu Kırp

Kullanabileceğiniz <xref:System.String.Trim%2A?displayProperty=nameWithType>, <xref:System.String.TrimStart%2A?displayProperty=nameWithType>, ve <xref:System.String.TrimEnd%2A?displayProperty=nameWithType> herhangi başında veya sonunda boşluk kaldırmak için yöntemleri.  Aşağıdaki kod, her bir örneğini gösterir. Kaynak dizesi değiştirmez. Bu yöntemler, değiştirilmiş içeriği ile yeni bir dize döndürür.

[!code-csharp-interactive[trim white space](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#3)]

## <a name="remove-text"></a>Metni silin

Kullanarak bir dizeyi metin kaldırabilirsiniz <xref:System.String.Remove%2A?displayProperty=nameWithType> yöntemi. Bu yöntem, belirli bir dizinden başlayarak karakteri kaldırır. Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.String.IndexOf%2A?displayProperty=nameWithType> ardından <xref:System.String.Remove%2A> metni bir dizeden kaldırmak için:

[!code-csharp-interactive[remove text](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#4)]

## <a name="replace-matching-patterns"></a>Eşleme desenleri değiştirin

Kullanabileceğiniz [normal ifadeler](../../standard/base-types/regular-expressions.md) yeni metin, büyük olasılıkla bir desen tarafından tanımlanan desenlerle eşleşen metni değiştirmek için. Aşağıdaki örnekte <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> sınıfı bir kaynak dizeyi bir desenle bulmak ve doğru harfle değiştirin. <xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.Text.RegularExpressions.MatchEvaluator,System.Text.RegularExpressions.RegexOptions)?displayProperty=nameWithType> Yöntemi yerine bağımsız değişkenlerinden biri olarak mantığı sağlayan bir işlevi alır. Bu örnekte, bu işlev `LocalReplaceMatchCase` olduğu bir **yerel işlev** örnek yöntemi içinde bildirilmiş. `LocalReplaceMatchCase` kullanan <xref:System.Text.StringBuilder?displayProperty=nameWithType> uygun bir büyük harf ile değiştirme dizesi oluşturmak için sınıfı.

Arama ve bilinen metin yerine bir yapıdadır metin değiştirme için normal ifadeler ekseriyetle faydalıdır. Bkz: [nasıl yapılır: dizeleri arama](search-strings.md) daha fazla ayrıntı için. Arama deseni "the\s" "" bir boşluk karakteriyle sözcüğünün arar. Desen, bir parçası kaynak dizesinde "var" eşleşmeyen sağlar. Normal ifade dil öğeleri hakkında daha fazla bilgi için bkz. [normal ifade dili - hızlı başvuru](../../standard/base-types/regular-expression-language-quick-reference.md).

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#5)]

<xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> Yöntemi içerikle değişmez bir dize döndürür <xref:System.Text.StringBuilder> nesne.

## <a name="modifying-individual-characters"></a>Karakterlerin tek tek değiştirme

Bir karakter dizisinden bir dize üretir, dizinin içeriğini değiştirin ve ardından dizinin değiştirilmiş içeriğinden yeni bir dize oluşturmak.

Aşağıdaki örnek bir dizedeki karakter kümesini nasıl değiştirileceğini gösterir. İlk olarak, bunu kullanan <xref:System.String.ToCharArray?displayProperty=nameWithName> karakter dizisi oluşturmak için yöntemi. Kullandığı <xref:System.String.IndexOf%2A> "fox." sözcüğü başlangıç dizini bulunacak yöntemi Sonraki üç karakter ile farklı bir sözcük değiştirilir. Son olarak, yeni bir dize, güncelleştirilmiş bir karakter dizisinden oluşturulur.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#6)]

## <a name="unsafe-modifications-to-string"></a>Güvenli olmayan dize değişiklikler

Kullanarak **güvenli** kod, sonra bir dize "yerinde" değiştirebilirsiniz oluşturulduktan. Güvenli olmayan kod .NET belirli türdeki bir kod hataları en aza indirmek için tasarlanmış özelliklerin çoğunu atlar. Güvenli olmayan kod string sınıfı olarak tasarlandığından, yerinde bir dize değiştirmek için kullanmanız gereken bir **değişmez** türü. Oluşturulduktan sonra değerini değiştirmez. Güvenli olmayan kod erişerek ve tarafından kullanılan bellek değiştirerek bu özelliği bozar bir `string` normal kullanmadan `string` yöntemleri.
Aşağıdaki örnek, bir dize güvenli olmayan kod kullanarak yerinde değiştirmek için istediğiniz bu nadir durumlar için sağlanır. Bu örnek nasıl kullanılacağını gösterir `fixed` anahtar sözcüğü. `fixed` Anahtar sözcüğü atık toplayıcı (GC) kod güvenli olmayan işaretçiyi kullanarak bellek erişen sırasında dize nesnesine bellekte taşınmasını engeller. Ayrıca, bir olası yan, C# derleyicisi (Stajyer) dizeleri dahili olarak depolayan biçimi nedeniyle oluşur etkisi dizeleri güvenli olmayan işlemleri gösterir. Genel olarak, kesinlikle gerekli olmadığı sürece bu tekniği kullanması gerekir. Makalelerinde daha fazla bilgi edinebilirsiniz [güvenli olmayan](../language-reference/keywords/unsafe.md) ve [sabit](../language-reference/keywords/fixed-statement.md). API başvurusunu <xref:System.String.Intern%2A> dize kopyası kullanımı hakkında bilgi içerir.

[!code-csharp-interactive[unsafe ways to create a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#7)]

Bu örnekler kodda bakarak deneyebilirsiniz bizim [GitHub deposu](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Örnekleri indirebilirsiniz [zip dosyası olarak](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Ayrıca bkz.

[.NET framework normal ifadeleri](../../standard/base-types/regular-expressions.md)  
 [Normal İfade Dili - Hızlı Başvuru](../../standard/base-types/regular-expression-language-quick-reference.md)  
