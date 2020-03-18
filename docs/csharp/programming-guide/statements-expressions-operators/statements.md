---
title: İfadeler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- statements [C#], about statements
- C# language, statements
ms.assetid: 901bcde7-87de-4e15-833c-f9cfd40c8ce3
ms.openlocfilehash: d50b50bb291d0d087015ea5bd075ae90ced66ff5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711941"
---
# <a name="statements-c-programming-guide"></a>Deyimler (C# Programlama Kılavuzu)

Bir programın gerçekleştirdiği eylemler ifadelerde ifade edilir. Yaygın eylemler değişkenleri bildirmeyi, değerleri atamayı, arama yöntemlerini aramayı, koleksiyonlar arasında döngüyü ve belirli bir koşula bağlı olarak bir veya başka bir kod bloğuna dallanmayı içerir. İfadelerin bir programda yürütülme sırası denetim akışı veya yürütme akışı olarak adlandırılır. Denetim akışı, programın çalışma zamanında aldığı girişe nasıl tepki verdiğine bağlı olarak, bir program çalıştırıldığı her zaman değişebilir.

Deyim, yarı iki nokta yla biten tek bir kod satırından veya bloktaki tek satırlı ifadelerden oluşabilir. İfade bloğu parantez içinde {} çevrilidir ve iç içe blokları içerebilir. Aşağıdaki kod, tek satırlık ifadelere iki örnek ve çok satırlı deyim bloğu gösterir:

[!code-csharp[csProgGuideStatements#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#1)]

## <a name="types-of-statements"></a>İfade türleri

Aşağıdaki tabloda, C# ve bunların ilişkili anahtar kelimelerindeki çeşitli ifade türleri ve daha fazla bilgi içeren konulara bağlantılar listelenir:

|Kategori|C# anahtar kelimeleri / notları|
|--------------|---------------------------|
|[Bildirim deyimleri](#declaration-statements)|Bildirim deyimi yeni bir değişken veya sabit sunar. Değişken bildirimi isteğe bağlı olarak değişkene bir değer atayabilir. Sabit bir bildirimde, atama gereklidir.|
|[İfade deyimleri](expressions.md)|Bir değeri hesaplayan ifade deyimleri, değeri bir değişkende depolamalıdır. Daha fazla bilgi için [İfade İfadeleri'ne](#expression-statements)bakın.|
|Seçim deyimleri|Seçim deyimleri, belirtilen koşullara bağlı olarak kodun farklı bölümlerine dallanmanızı sağlar. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın: <ul><li>[eğer](../../language-reference/keywords/if-else.md)</li><li>[Başka](../../language-reference/keywords/if-else.md)</li><li>[Anahtarı](../../language-reference/keywords/switch.md)</li><li>[Durumda](../../language-reference/keywords/switch.md)</li></ul>|
|Yineleme deyimleri|Yineleme deyimleri, diziler gibi koleksiyonlar arasında döngü kurmanızı veya belirli bir koşul karşılanana kadar aynı ifade kümesini tekrar tekrar gerçekleştirmenizi sağlar. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın: <ul><li>[yapmak](../../language-reference/keywords/do.md)</li><li>[Için](../../language-reference/keywords/for.md)</li><li>[Foreach](../../language-reference/keywords/foreach-in.md)</li><li>[Inç](../../language-reference/keywords/foreach-in.md)</li><li>[Süre](../../language-reference/keywords/while.md)</li></ul>|
|Atlama deyimleri|Atlama deyimleri denetimi kodun başka bir bölümüne aktarın. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın: <ul><li>[Mola](../../language-reference/keywords/break.md)</li><li>[continue](../../language-reference/keywords/continue.md)</li><li>[Varsayılan](../../language-reference/keywords/switch.md)</li><li>[Goto](../../language-reference/keywords/goto.md)</li><li>[return](../../language-reference/keywords/return.md)</li><li>[yield](../../language-reference/keywords/yield.md)</li></ul>|
|Özel durum işleme deyimleri|Özel durum işleme deyimleri, çalışma zamanında oluşan olağanüstü koşullardan zarif bir şekilde kurtarmanızı sağlar. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın: <ul><li>[throw](../../language-reference/keywords/throw.md)</li><li>[try-catch](../../language-reference/keywords/try-catch.md)</li><li>[try-finally](../../language-reference/keywords/try-finally.md)</li><li>[try-catch-finally](../../language-reference/keywords/try-catch-finally.md)</li></ul>|
|[Denetlenmiş ve işaretlenmemiş](../../language-reference/keywords/checked-and-unchecked.md)|Denetlenen ve işaretlenmemiş ifadeler, sonuç elde edilen değeri tutamayacak kadar küçük bir değişkende depolandığında sayısal işlemlerin taşmaya neden olup olmadığını belirtmenize olanak tanır. Daha fazla bilgi için [bkz: denetlenmiş](../../language-reference/keywords/checked.md) ve [işaretlenmemiş.](../../language-reference/keywords/unchecked.md)|
|İfade `await`|Bir yöntemi [async](../../language-reference/keywords/async.md) değiştirici ile işaretlerseniz, yöntemde [bekleme](../../language-reference/operators/await.md) işlecini kullanabilirsiniz. Denetim async `await` yönteminde bir ifadeye ulaştığında, denetim arayana döndürür ve yöntemdeki ilerleme beklenen görev tamamlanana kadar askıya alınır. Görev tamamlandığında, yürütme yöntemde devam edebilir.<br /><br /> Basit bir örnek için, [Yöntemler'in](../classes-and-structs/methods.md)"Async Yöntemleri" bölümüne bakın. Daha fazla bilgi için, [async ile Asynchronous Programming](../concepts/async/index.md)bakın ve bekliyor.|
|İfade `yield return`|Yineleyici, liste veya dizi gibi bir koleksiyon üzerinde özel bir yineleme gerçekleştirir. Bir yineleyici, her öğeyi birer birer döndürmek için [verim iade](../../language-reference/keywords/yield.md) deyimini kullanır. Bir `yield return` bildirime ulaşıldığında, koddaki geçerli konum hatırlanır. Yineleyici bir sonraki seferde çağrıldığında yürütme bu konumdan yeniden başlatılır.<br /><br /> Daha fazla bilgi için [bkz.](../concepts/iterators.md)|
|İfade `fixed`|Sabit ifade, çöp toplayıcısının taşınır değişkeninyerini değiştirmesini engeller. Daha fazla bilgi için [sabit](../../language-reference/keywords/fixed-statement.md)bakın.|
|İfade `lock`|Kilit deyimi, kod bloklarına erişimi aynı anda yalnızca bir iş parçacığıyla sınırlamanızı sağlar. Daha fazla bilgi için [bkz.](../../language-reference/keywords/lock-statement.md)|
|Etiketli deyimler|Bir bildirime bir etiket verebilir ve ardından etiketli ifadeye atlamak için [goto](../../language-reference/keywords/goto.md) anahtar sözcük'ünden yararlanabilirsiniz. (Aşağıdaki satırdaki örneğe bakın.)|
|[Boş ifade](#the-empty-statement)|Boş ifade tek bir yarı kolon oluşur. Hiçbir şey yapmaz ve bir bildirim gerekli ancak hiçbir eylem yapılması gereken yerlerde kullanılabilir.|

## <a name="declaration-statements"></a>Bildirim deyimleri

Aşağıdaki kod, ilk atamalı ve atamasız değişken bildirimleri ve gerekli başlatma ile sabit bir bildirim örneklerini gösterir.

[!code-csharp[csProgGuideStatements#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#23)]

## <a name="expression-statements"></a>İfade deyimleri

Aşağıdaki kod, atama, atama ile nesne oluşturma ve yöntem çağırma dahil olmak üzere ifade ifadeleri örneklerini gösterir.

[!code-csharp[csProgGuideStatements#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#24)]

## <a name="the-empty-statement"></a>Boş ifade

Aşağıdaki örnekler, boş bir ifadeiçin iki kullanım gösterir:

[!code-csharp[csProgGuideStatements#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#25)]

## <a name="embedded-statements"></a>Gömülü ifadeler

Bazı ifadeler, [yapmak](../../language-reference/keywords/do.md)dahil , [süre](../../language-reference/keywords/while.md), [için](../../language-reference/keywords/for.md), ve [foreach](../../language-reference/keywords/foreach-in.md), her zaman onları izleyen gömülü bir ifade var. Bu katıştı lı deyim, tek bir {} deyim veya bir deyim bloğundaki parantezler tarafından kapatılan birden çok deyim olabilir. Tek satırlık katıştılmış ifadeler {} bile aşağıdaki örnekte gösterildiği gibi parantez içine alınabilir:

[!code-csharp[csProgGuideStatements#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#26)]

Parantez içinde {} eklenmiş olmayan katıştırılmış bir deyim, bir bildirim deyimi veya etiketli bir deyim olamaz. Bu, aşağıdaki örnekte gösterilmiştir:

[!code-csharp[csProgGuideStatements#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#27)]

Hatayı düzeltmek için katıştılı deyimi bir bloya koyun:

[!code-csharp[csProgGuideStatements#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#28)]

## <a name="nested-statement-blocks"></a>İç içe deyim blokları

Deyim blokları, aşağıdaki kodda gösterildiği gibi iç içe olabilir:

[!code-csharp[csProgGuideStatements#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#29)]

## <a name="unreachable-statements"></a>Erişilemez ifadeler

Derleyici, denetim akışının hiçbir koşulda belirli bir bildirime asla ulaşamayacağını belirlerse, aşağıdaki örnekte gösterildiği gibi Uyarı CS0162'yi üretecektir:

[!code-csharp[csProgGuideStatements#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#22)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Deyimler](~/_csharplang/spec/statements.md) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Ekstre anahtar kelimeleri](../../language-reference/keywords/statement-keywords.md)  
- [İfadeler](expressions.md)  
