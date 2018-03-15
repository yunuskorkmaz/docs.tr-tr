---
title: "Nasıl yapılır: dize içeriklerini - C# Kılavuzu değiştirme"
ms.date: 02/26/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- strings [C#], modifying
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 830ca207c4cd5bd24dbb667328465cafb2509409
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="how-to-modify-string-contents-in-c"></a>Nasıl yapılır: C# dize içeriklerini değiştirme #

Bu makalede üretmek için çeşitli teknikler gösterilmektedir bir `string` varolan değiştirerek `string`. Tüm teknikler gösterilen dönüş yeni değişikliklerin sonucu `string` nesnesi. Açıkça bunu göstermek için tüm örnekler sonucu yeni bir değişkende saklayın. Her iki özgün sonra inceleyebilirsiniz `string` ve `string` her örnek çalıştırdığınızda değiştirilmeye karşı sonuçlanır.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Bu makalede gösterilen bazı teknikler vardır. Varolan metni değiştirebilirsiniz. Desen aramak ve diğer metinle eşleşen metin. Bir karakter dizisi bir dize davranabilirsiniz. Beyaz alan kaldırmak kullanışlı yöntemler de kullanabilirsiniz. Senaryonuza en yakından eşleşen teknikleri seçmeniz gerekir.

## <a name="replace-text"></a>Metin değiştirme

Aşağıdaki kod ile değiştirin varolan metin değiştirerek yeni bir dize oluşturur.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#1)]

Önceki kod bu gösterir *değişmez* dizeleri özelliği. Yukarıdaki örnekte bkz, özgün dizeye `source`, değiştirilmez. <xref:System.String.Replace%2A?displayProperty=nameWithType> Yöntemi yeni bir oluşturur `string` değişiklikleri içeren.

<xref:System.String.Replace%2A> Dizeyi veya tek karakter yöntemi değiştirebilirsiniz. Her iki durumda da, her oluşumu aranan metnin yerini alır.  Aşağıdaki örnekte tüm değiştirir ' 'ile karakter'\_':

[!code-csharp-interactive[replace characters](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#2)]

Kaynak dizesi değiştirilmemiştir ve yeni bir dize ile değiştirme döndürülür.

## <a name="trim-white-space"></a>Kırpma beyaz alan

Kullanabileceğiniz <xref:System.String.Trim%2A?displayProperty=nameWithType>, <xref:System.String.TrimStart%2A?displayProperty=nameWithType>, ve <xref:System.String.TrimEnd%2A?displayProperty=nameWithType> yöntemleri herhangi baştaki veya sondaki boşlukları kaldırın.  Aşağıdaki kod, her bir örneği gösterir. Kaynak dizesi değiştirmez; Bu yöntemler değiştirilmiş içeriği ile yeni bir dize döndürür.

[!code-csharp-interactive[trim white space](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#3)]

## <a name="remove-text"></a>Metin Kaldır

Kullanarak bir dize metin kaldırabilirsiniz <xref:System.String.Remove%2A?displayProperty=nameWithType> yöntemi. Bu yöntemi, belirli bir dizinden başlayarak karakteri kaldırır. Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.String.IndexOf%2A?displayProperty=nameWithType> arkasından <xref:System.String.Remove%2A> bir dizeden metni kaldırmak için:

[!code-csharp-interactive[remove text](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#4)]

## <a name="replace-matching-patterns"></a>Eşleme desenleri Değiştir

Kullanabileceğiniz [normal ifadeler](../../standard/base-types/regular-expressions.md) desenleri büyük olasılıkla bir desen tarafından tanımlanan yeni metinle eşleşen metni değiştirmek için. Aşağıdaki örnek kullanır <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> sınıfı bir kaynak dizesi bir deseni bulun ve doğru harfle değiştirin. <xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.Text.RegularExpressions.MatchEvaluator,System.Text.RegularExpressions.RegexOptions)?displayProperty=nameWithType> Yöntem bağımsız değişkenlerinden biri olarak değiştirme mantığı sağlayan bir işlev alır. Bu örnekte, bu işlev `LocalReplaceMatchCase` olan bir **yerel işlevi** içinde örnek yöntemini bildirdi. `LocalReplaceMatchCase` kullanan <xref:System.Text.StringBuilder?displayProperty=nameWithType> doğru kaydolurken ile değiştirme dizesi oluşturma sınıfı.

Normal ifadeler, arama ve bilinen metin yerine bir deseni takip eder metin değiştirme için çok kullanışlıdır. Bkz: [nasıl yapılır: dizeleri arama](search-strings.md) daha fazla ayrıntı için. Arama deseni "the\s" "" sonrasında bir boşluk karakteri word arar. Kaynak dizesi "yok" eşleşmeyen düzeni kısmı sağlar. Normal ifade dil öğeleri hakkında daha fazla bilgi için bkz: [normal ifade dili - hızlı başvuru](../../standard/base-types/regular-expression-language-quick-reference.md).

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#5)]

<xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> Yöntemi döndürür bir değişmez dize içerikle <xref:System.Text.StringBuilder> nesnesi.

## <a name="modifying-individual-characters"></a>Tek tek karakterleri değiştirme

Bir dizeden bir karakter dizisi oluşturmak, dizinin içeriğini değiştirin ve ardından yeni bir dize dizisi değiştirilmiş içeriğinden oluşturun.

Aşağıdaki örnek, bir dizedeki karakter kümesini değiştirmek gösterilmiştir. İlk olarak, kullanan <xref:System.String.ToCharArray?displayProperty=nameWithName> karakter dizisi oluşturmak için yöntemi. Kullandığı <xref:System.String.IndexOf%2A> "fox." word'ün başlangıç dizini bulmak için yöntemi Sonraki üç karakterler farklı bir word ile değiştirilir. Son olarak, yeni bir dize güncelleştirilmiş karakter dizisinden oluşturulur.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#6)]

## <a name="unsafe-modifications-to-string"></a>Dize güvensiz değişiklikler

Kullanarak **güvensiz** kodu, sonra bir dize "yerinde" değiştirebilirsiniz oluşturulduktan. Güvenli olmayan kod .NET belirli türde bir kodundaki hatalar en aza indirmek için tasarlanmış özelliklerin çoğunu atlar. String sınıfı olarak tasarlandığından yerinde bir dize değiştirmek için güvenli olmayan kod kullanmanıza gerek bir **değişmez** türü. Oluşturulduktan sonra değeri değiştirmez. Güvenli olmayan kod erişme ve tarafından kullanılan bellek değiştirerek bu özelliği bozar bir `string` normal kullanmadan `string` yöntemleri.
Aşağıdaki örnek, bir dize güvenli olmayan kod kullanarak yerinde değiştirmek istediğiniz bu nadir durumlarda sağlanır. Bu örnek nasıl kullanılacağını gösterir `fixed` anahtar sözcüğü. `fixed` Anahtar sözcüğü kod güvensiz işaretçisi kullanılarak bellek erişen sırada dize nesnesi bellekte taşıma atık toplayıcı (GC) engeller. Ayrıca, bir olası yan C# Derleyici (Stajyer) dizeleri dahili olarak depolar şekilde sonucu etkisi dizelerde güvensiz işlemleri gösterir. Genel olarak, kesinlikle gerekli olmadığı sürece bu teknik kullanmamalısınız. Üzerinde makalelerde daha fazla bilgiyi [güvensiz](../language-reference/keywords/unsafe.md) ve [sabit](../language-reference/keywords/fixed-statement.md). İçin API Başvurusu <xref:System.String.Intern%2A> dize interning hakkında bilgi içerir.

[!code-csharp-interactive[unsafe ways to create a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#7)]

Kodda bakarak bu örnekleri deneyebilirsiniz bizim [GitHub deposunu](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings). Veya örnekleri indirebilirsiniz [zip dosyası olarak](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Ayrıca bkz.

[.NET framework normal ifadeleri](../../standard/base-types/regular-expressions.md)  
 [Normal İfade Dili - Hızlı Başvuru](../../standard/base-types/regular-expression-language-quick-reference.md)  
