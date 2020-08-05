---
title: Deyimler-C# Programlama Kılavuzu
description: C# programlamasında deyimler hakkında bilgi edinin. İfade türlerinin bir listesini görün ve kod örneklerini ve ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- statements [C#], about statements
- C# language, statements
ms.assetid: 901bcde7-87de-4e15-833c-f9cfd40c8ce3
ms.openlocfilehash: 3f8ac88525c44f9572f4f647145ad251537aba57
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556754"
---
# <a name="statements-c-programming-guide"></a>Deyimler (C# Programlama Kılavuzu)

Bir programın aldığı eylemler deyimler bölümünde ifade edilir. Yaygın eylemler, belirli bir koşula bağlı olarak değişkenleri bildirme, değer atama, yöntemleri çağırma, koleksiyonlar aracılığıyla döngü oluşturma ve bir veya başka bir kod bloğuna dallandırma içerir. Bir programda deyimlerin yürütülme sırası, denetim akışı veya yürütme akışı olarak adlandırılır. Programın çalışma zamanında aldığı girişe nasıl davrandığına bağlı olarak, denetim akışı, programın her çalıştırılışında farklılık gösterebilir.

Bir deyim, noktalı virgül veya bir blokta bir dizi tek satırlık deyimlerle biten tek satırlık koddan oluşabilir. Bir ifade bloğu {} köşeli ayraç içine alınır ve iç içe bloklar içerebilir. Aşağıdaki kod, tek satırlık deyimlerin iki örneğini ve çok satırlı bir deyim bloğunu göstermektedir:

[!code-csharp[csProgGuideStatements#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#1)]

## <a name="types-of-statements"></a>Deyim türleri

Aşağıdaki tabloda, daha fazla bilgi içeren konuların bağlantılarıyla birlikte C# ve ilişkili anahtar sözcüklerindeki çeşitli deyim türleri listelenmektedir:

|Kategori|C# anahtar sözcükleri/notları|
|--------------|---------------------------|
|[Bildirim deyimleri](#declaration-statements)|Bir bildirim bildirimi yeni bir değişken veya sabit tanıtır. Değişken bildirimi, isteğe bağlı olarak değişkenine bir değer atayabilir. Sabit bildiriminde atama gereklidir.|
|[İfade deyimleri](#expression-statements)|Bir değeri hesaplayan ifade deyimleri değeri bir değişkende depoalmalıdır.|
|Seçim deyimleri|Seçim deyimleri, belirtilen bir veya daha fazla koşula bağlı olarak farklı kod bölümlerine dallandırmayı sağlar. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın: <ul><li>[if](../../language-reference/keywords/if-else.md)</li><li>[else](../../language-reference/keywords/if-else.md)</li><li>[değiştirebilirsiniz](../../language-reference/keywords/switch.md)</li><li>[harflerini](../../language-reference/keywords/switch.md)</li></ul>|
|Yineleme deyimleri|Yineleme deyimleri, diziler gibi koleksiyonlar aracılığıyla döngü gerçekleştirmenizi veya belirli bir koşul karşılanana kadar aynı deyim kümesini sürekli olarak gerçekleştirmenizi sağlar. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın: <ul><li>[do](../../language-reference/keywords/do.md)</li><li>[:](../../language-reference/keywords/for.md)</li><li>[foreach](../../language-reference/keywords/foreach-in.md)</li><li>['ndaki](../../language-reference/keywords/foreach-in.md)</li><li>[while](../../language-reference/keywords/while.md)</li></ul>|
|Atlama deyimleri|Atdeyimlerini, kodun başka bir bölümüne aktarma denetimi. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın: <ul><li>[break](../../language-reference/keywords/break.md)</li><li>[devam](../../language-reference/keywords/continue.md)</li><li>[varsayılanını](../../language-reference/keywords/switch.md)</li><li>[goto](../../language-reference/keywords/goto.md)</li><li>[return](../../language-reference/keywords/return.md)</li><li>[yield](../../language-reference/keywords/yield.md)</li></ul>|
|Özel durum işleme deyimleri|Özel durum işleme deyimleri, çalışma zamanında oluşan olağanüstü koşullardan sorunsuz bir şekilde kurtarmanızı sağlar. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın: <ul><li>[throw](../../language-reference/keywords/throw.md)</li><li>[try-catch](../../language-reference/keywords/try-catch.md)</li><li>[try-finally](../../language-reference/keywords/try-finally.md)</li><li>[try-catch-finally](../../language-reference/keywords/try-catch-finally.md)</li></ul>|
|[Checked ve unchecked](../../language-reference/keywords/checked-and-unchecked.md)|Checked ve unchecked deyimleri, sonuçta elde edilen değeri tutmak için çok küçük bir değişkende depolandığında sayısal işlemlere taşma olmasına izin verilip verilmeyeceğini belirtmenizi sağlar. Daha fazla bilgi için bkz. [Checked](../../language-reference/keywords/checked.md) ve [unchecked](../../language-reference/keywords/unchecked.md).|
|`await`İfade|[Zaman uyumsuz](../../language-reference/keywords/async.md) değiştiriciyle bir yöntemi işaretlerseniz, yönteminde [await](../../language-reference/operators/await.md) işlecini kullanabilirsiniz. Denetim `await` zaman uyumsuz yöntemde bir ifadeye ulaştığında denetim çağırana döner ve beklenen görev tamamlanana kadar yöntem içindeki ilerleme durumu askıya alınır. Görev tamamlandığında, yürütme yöntemi içinde çalışmaya çalışabilir.<br /><br /> Basit bir örnek için, [yöntemlerin](../classes-and-structs/methods.md)"zaman uyumsuz metotlar" bölümüne bakın. Daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama](../concepts/async/index.md).|
|`yield return`İfade|Yineleyici, bir koleksiyon üzerinde liste veya dizi gibi özel bir yineleme gerçekleştirir. Bir yineleyici, her öğeyi birer birer döndürmek için [yield return](../../language-reference/keywords/yield.md) ifadesini kullanır. Bir `yield return` ifadeye ulaşıldığında, koddaki geçerli konum hatırlanır. Yineleyici bir sonraki sefer çağrıldığında, yürütme o konumdan yeniden başlatılır.<br /><br /> Daha fazla bilgi için bkz. [yineleyiciler](../concepts/iterators.md).|
|`fixed`İfade|Fixed deyimleri, çöp toplayıcısının taşınabilir bir değişkenin yerini değiştirmesini engeller. Daha fazla bilgi için bkz. [düzeltildi](../../language-reference/keywords/fixed-statement.md).|
|`lock`İfade|Lock deyimleri tek seferde yalnızca bir iş parçacığına kod bloklarına erişimi sınırlamanıza olanak sağlar. Daha fazla bilgi için bkz. [Lock](../../language-reference/keywords/lock-statement.md).|
|Etiketli deyimler|Bir deyime bir etiket verebilir ve sonra etiketli ifadeye geçmek için [goto](../../language-reference/keywords/goto.md) anahtar sözcüğünü kullanabilirsiniz. (Aşağıdaki satırdaki örneğe bakın.)|
|[Boş ifade](#the-empty-statement)|Boş ifade tek bir noktalı virgülden oluşur. Hiçbir şey yapmaz ve bir deyimin gerekli olduğu, ancak herhangi bir eylemin gerçekleştirilmesi gereken yerlerde kullanılabilir.|

## <a name="declaration-statements"></a>Bildirim deyimleri

Aşağıdaki kod, bir başlangıç ataması ve, gerekli başlatmaya sahip sabit bir bildirime sahip ve olmayan değişken bildirimlerinin örneklerini gösterir.

[!code-csharp[csProgGuideStatements#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#23)]

## <a name="expression-statements"></a>İfade deyimleri

Aşağıdaki kod, atama, atamayla nesne oluşturma ve yöntem çağırma dahil olmak üzere ifade deyimlerinin örneklerini gösterir.

[!code-csharp[csProgGuideStatements#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#24)]

## <a name="the-empty-statement"></a>Boş ifade

Aşağıdaki örneklerde boş bir deyimin iki kullanımı gösterilmektedir:

[!code-csharp[csProgGuideStatements#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#25)]

## <a name="embedded-statements"></a>Gömülü deyimler

[Do](../../language-reference/keywords/do.md), [while](../../language-reference/keywords/while.md), [for](../../language-reference/keywords/for.md)ve [foreach](../../language-reference/keywords/foreach-in.md)dahil bazı deyimler, her zaman bunları izleyen bir katıştırılmış ifadeye sahiptir. Bu katıştırılmış deyim tek bir deyim veya {} deyim bloğunda köşeli ayraç içine alınmış birden çok deyim olabilir. Hatta, tek satırlı katıştırılmış deyimler {} , aşağıdaki örnekte gösterildiği gibi köşeli ayraç içine alınabilir:

[!code-csharp[csProgGuideStatements#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#26)]

Köşeli ayraçlar içine alınmış gömülü bir ifade, {} bir bildirim bildirimi veya etiketli bir ifade olamaz. Bu, aşağıdaki örnekte gösterilmiştir:

[!code-csharp[csProgGuideStatements#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#27)]

Hatayı onarmak için katıştırılmış ifadeyi bir bloğa yerleştirin:

[!code-csharp[csProgGuideStatements#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#28)]

## <a name="nested-statement-blocks"></a>İç içe geçmiş ifade blokları

Aşağıdaki kodda gösterildiği gibi, ekstre blokları iç içe olabilir:

[!code-csharp[csProgGuideStatements#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#29)]

## <a name="unreachable-statements"></a>Erişilemeyen deyimler

Derleyici, denetim akışının herhangi bir koşullarda belirli bir deyime hiçbir şekilde ulaşamayacağını belirlerse, aşağıdaki örnekte gösterildiği gibi, uyarı CS0162 oluşturacaktır:

[!code-csharp[csProgGuideStatements#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#22)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [deyimler](~/_csharplang/spec/statements.md) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [İfade anahtar sözcükleri](../../language-reference/keywords/statement-keywords.md)
- [C# işleçleri ve ifadeleri](../../language-reference/operators/index.md)
