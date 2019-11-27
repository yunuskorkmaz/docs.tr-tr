---
title: Deyimler
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- colons (:) [Visual Basic]
- constants [Visual Basic], defining
- underlines
- constants [Visual Basic], statements
- blue underline [Visual Basic]
- procedures [Visual Basic], statements
- variables [Visual Basic], assigning
- line breaks [Visual Basic], in code
- executable statements [Visual Basic]
- variables [Visual Basic], defining
- statements [Visual Basic], about statements
ms.assetid: fcfdee1a-82b7-4846-98f7-9ca3f5160089
ms.openlocfilehash: f63f0f0212913f95baab2a8a43c4b7f25a859cd9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352497"
---
# <a name="statements-in-visual-basic"></a>Visual Basic'deki Deyimler

Visual Basic bir ifade, bir bütün yönergedir. Anahtar sözcükler, işleçler, değişkenler, sabitler ve ifadeler içerebilir. Her bir ekstre aşağıdaki kategorilerden birine aittir:

- Bir değişken, sabit veya yordamı belirleyen ve ayrıca bir veri türü de içerebilen **bildirim deyimleri**.

- Eylem başlatan **çalıştırılabilir deyimler**. Bu deyimler bir yöntemi veya işlevi çağırabilir ve kod blokları aracılığıyla döngü ya da dallarda bulunabilir. Executable deyimleri, bir değişkene veya sabitine bir değer veya ifade atayan **atama deyimlerini**içerir.

Bu konuda her kategori açıklanmaktadır. Ayrıca, bu konu, birden çok deyimin tek bir satırda nasıl birleştirileceğini ve birden çok satır üzerinde bir ifadeye nasıl devam edileceğini açıklar.

## <a name="declaration-statements"></a>Bildirim deyimleri

Yordamlar, değişkenler, özellikler, diziler ve sabitleri adlandırmak ve tanımlamak için bildirim deyimlerini kullanırsınız. Bir programlama öğesi bildirdiğinizde, veri türünü, erişim düzeyini ve kapsamını da tanımlayabilirsiniz. Daha fazla bilgi için bkz. [bildirilmemiş öğe özellikleri](./declared-elements/declared-element-characteristics.md).

Aşağıdaki örnek üç bildirim içerir.

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

İlk bildirim `Sub` deyimidir. Eşleşen `End Sub` ifadesiyle birlikte, `applyFormat`adlı bir yordamı bildirir. Ayrıca, `applyFormat` `Public`olduğunu belirtir; Bu, kendisine başvurabilen tüm kodlar bunu çağırabileceği anlamına gelir.

İkinci bildirim, `Integer` veri türünü ve 33 değerini belirterek sabit `limit`bildiren `Const` deyimidir.

Üçüncü bildirim, `thisWidget`değişkenini bildiren `Dim` deyimidir. Veri türü, `Widget` sınıfından oluşturulan bir nesne olan belirli bir nesnedir. Bir değişkeni, herhangi bir temel veri türü veya kullandığınız uygulamada kullanıma sunulan herhangi bir nesne türünde olacak şekilde bildirebilirsiniz.

### <a name="initial-values"></a>İlk değerler

Bir bildirim ifadesini içeren kod çalıştırıldığında, Visual Basic bildirimi yapılan öğe için gereken belleği ayırır. Öğe bir değer içeriyorsa, Visual Basic onu veri türü için varsayılan değer olarak başlatır. Daha fazla bilgi için, bkz. [Dim deyimindeki](../../language-reference/statements/dim-statement.md)"davranış".

Aşağıdaki örnekte gösterildiği gibi, bir değişkene, bildiriminin bir parçası olarak bir başlangıç değeri atayabilirsiniz.

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

Bir değişken bir nesne değişkense, aşağıdaki örnekte gösterildiği gibi [New Operator](../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcüğünü kullanarak sınıfını bildirdiğinizde sınıfının bir örneğini açıkça oluşturabilirsiniz.

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

Bir bildirim ifadesinde belirttiğiniz ilk değerin, yürütme bildirim bildirimine ulaşıncaya kadar bir değişkene atanmadığını unutmayın. Bu saate kadar, değişken veri türü için varsayılan değeri içerir.

## <a name="executable-statements"></a>Yürütülebilir deyimler

Yürütülebilir bir ifade bir eylem gerçekleştirir. Bir yordam çağırabilir, koddaki başka bir yere dallandırır, çeşitli deyimlerde döngü gerçekleştirebilir veya bir ifadeyi değerlendirebilir. Atama ekstresi, yürütülebilir bir deyimin özel bir durumdur.

Aşağıdaki örnek, bir değişkenin değerine göre farklı kod blokları çalıştırmak için bir `If...Then...Else` denetim yapısı kullanır. Her kod bloğu içinde, bir `For...Next` döngüsü belirtilen sayıda çalıştırılır.

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

Yukarıdaki örnekteki `If` deyimin `clockwise`parametresinin değeri kontrol eder. Değer `True`, `aWidget``spinClockwise` yöntemini çağırır. Değer `False`, `aWidget``spinCounterClockwise` yöntemini çağırır. `If...Then...Else` denetim yapısı `End If`biter.

Her bloğun içindeki `For...Next` döngüsü, uygun yöntemi, `revolutions` parametresinin değerine eşit sayıda kez çağırır.

## <a name="assignment-statements"></a>Atama deyimleri

Atama deyimleri, atama işlecinin sağ tarafında (`=`) değeri alan ve bu dosyayı aşağıdaki örnekte olduğu gibi soldaki öğede depolayan atama işlemlerini gerçekleştirebilir.

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

Yukarıdaki örnekte, atama ifadesinde 42 değişmez değeri `v`değişkenine depolanır.

### <a name="eligible-programming-elements"></a>Uygun programlama öğeleri

Atama işlecinin sol tarafındaki programlama öğesi bir değeri kabul edip depolayabilmelidir. Bu, [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md)olmayan bir değişken veya özellik olması veya bir dizi öğesi olması gerektiği anlamına gelir. Atama ifadesinin bağlamında, bu tür bir öğe bazen "sol değer" için *lvalue*olarak adlandırılır.

Atama işlecinin sağ tarafındaki değer, değişmez değer, sabitler, değişkenler, özellikler, dizi öğeleri, diğer ifadeler veya işlev çağrılarının birleşiminden oluşabilen bir ifade tarafından oluşturulur. Aşağıdaki örnek bunu göstermektedir.

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

Yukarıdaki örnek, `y` değişken içinde tutulan değeri, değişken `z`bulunan değere ekler ve ardından çağrı tarafından döndürülen değeri işlev `findResult`ekler. Bu ifadenin toplam değeri daha sonra `x`değişkende depolanır.

### <a name="data-types-in-assignment-statements"></a>Atama İfadelerdeki veri türleri

Sayısal değerlere ek olarak, aşağıdaki örnekte gösterildiği gibi atama işleci de `String` değerler atayabilir.

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

Aşağıdaki örnekte gösterildiği gibi, `Boolean` değişmez değeri veya `Boolean` ifadesi kullanarak `Boolean` değerleri de atayabilirsiniz.

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

Benzer şekilde, `Char`, `Date`veya `Object` veri türünün programlama öğelerine uygun değerler atayabilirsiniz. Ayrıca bir nesne örneğini, bu örneğin oluşturulduğu sınıf olarak belirtilen bir öğeye atayabilirsiniz.

### <a name="compound-assignment-statements"></a>Bileşik atama deyimleri

*Bileşik atama deyimleri* , bir programlama öğesine atamadan önce bir ifadede bir işlem gerçekleştirir. Aşağıdaki örnek, işlecin sol tarafındaki değişkenin değerini sağdaki değer ile artıran `+=`, bu işleçlerden birini gösterir.

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

Yukarıdaki örnek, `n`değerine 1 ekler ve sonra bu yeni değeri `n`depolar. Bu, aşağıdaki deyimin bir toplu eşdeğeridir.

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

Bu türdeki işleçler kullanılarak çeşitli bileşik atama işlemleri gerçekleştirilebilir. Bu işleçlerin bir listesi ve bunlarla ilgili daha fazla bilgi için bkz. [atama işleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md).

Birleştirme atama işleci (`&=`), aşağıdaki örnekte gösterildiği gibi, zaten var olan dizelerin sonuna bir dize eklemek için yararlıdır.

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a>Atama deyimlerinde tür dönüştürmeleri

Bir değişkene, özelliğe veya dizi öğesine atadığınız değer bu hedef öğeye uygun bir veri türünde olmalıdır. Genel olarak, hedef öğesiyle aynı veri türünde bir değer oluşturmayı denemelisiniz. Ancak, bazı türler atama sırasında diğer türlere dönüştürülebilir.

Veri türleri arasında dönüştürme hakkında daha fazla bilgi için bkz. [tür dönüştürmeleri Visual Basic](./data-types/type-conversions.md). Kısaca Visual Basic, belirli bir türdeki bir değeri otomatik olarak widens diğer bir türe dönüştürür. *Genişleyen dönüştürme* , her zaman çalışma zamanında başarılı olur ve herhangi bir veri kaybetmez. Örneğin, Visual Basic, `Integer` bir değeri uygun olduğunda `Double` dönüştürür, çünkü `Integer` widens `Double`. Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](./data-types/widening-and-narrowing-conversions.md).

*Daraltma dönüştürmeleri* (genişletme olmayan), çalışma zamanında veya veri kaybından hata riski taşır. Bir tür dönüştürme işlevini kullanarak açıkça bir daraltma dönüştürmesi gerçekleştirebilir veya `Option Strict Off`ayarlayarak derleyiciyi örtük olarak tüm dönüştürmeleri gerçekleştirmeye yönlendirebilirsiniz. Daha fazla bilgi için bkz. [örtük ve açık dönüştürmeler](./data-types/implicit-and-explicit-conversions.md).

## <a name="putting-multiple-statements-on-one-line"></a>Birden çok deyimi tek satıra yerleştirme

İki nokta üst üste (`:`) karakteriyle ayrılmış tek bir satırda birden çok deyimden sahip olabilirsiniz. Aşağıdaki örnek bunu göstermektedir.

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

Bazen kullanışlı olsa da, bu tür bir sözdizimi kodunuzun okunmasını ve bakımını daha zor hale getirir. Bu nedenle, bir ifadeyi bir satıra tutmanız önerilir.

## <a name="continuing-a-statement-over-multiple-lines"></a>Birden çok satır üzerinde bir ifadeye devam etme

Bir ifade genellikle tek bir satıra sığar, ancak çok uzun olduğunda bir satır devamlılığı dizisi kullanarak sonraki satıra devam edebilir. Bu, alt çizgi karakteri (`_`) ve ardından bir satır başı gelir. Aşağıdaki örnekte, `MsgBox` executable deyimleri iki satır üzerinde devam eder.

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a>Örtük satır devamlılığı

Birçok durumda, alt çizgi karakterini (`_`) kullanmadan sonraki ardışık satırda bir ifadeye devam edebilirsiniz. Aşağıdaki sözdizimi öğeleri, bir sonraki kod satırında ifadesiyle dolaylı olarak devam eder.

- Bir virgülden sonra (`,`). Örneğin:

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- Bir açık parantez (`(`) veya kapatma parantezinden (`)`) sonra. Örneğin:

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- Bir açık küme ayracı (`{`) veya bir kapanış büyük ayraçından (`}`) önce. Örneğin:

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    Daha fazla bilgi için bkz. [nesne başlatıcıları: adlandırılmış ve anonim türler](./objects-and-classes/object-initializers-named-and-anonymous-types.md) veya [koleksiyon başlatıcıları](./collection-initializers/index.md).

- Açık bir katıştırılmış ifadeden sonra (`<%=`) veya bir XML sabit değeri içindeki katıştırılmış bir ifadenin (`%>`) kapatıldıktan önce. Örneğin:

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   Daha fazla bilgi için bkz. [XML 'de katıştırılmış ifadeler](./xml/embedded-expressions-in-xml.md).

- Birleştirme işlecinden sonra (`&`). Örneğin:

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   Daha fazla bilgi için bkz. [işlevlere göre listelenen işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Atama işleçlerinden (`=`, `&=`, `:=`, `+=`, `-=`, `*=`, `/=`, `\=`, `^=`, `<<=`, `>>=`) sonra. Örneğin:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Daha fazla bilgi için bkz. [işlevlere göre listelenen işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- İkili işleçler (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`) bir ifade içinde.`Like``Xor` Örneğin:

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   Daha fazla bilgi için bkz. [işlevlere göre listelenen işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- `Is` ve `IsNot` işleçlerinden sonra. Örneğin:

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   Daha fazla bilgi için bkz. [işlevlere göre listelenen işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Üye niteleyicisi karakterinden (`.`) sonra ve üye adından önce. Örneğin:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Ancak, `With` ifadesini kullanırken veya bir tür için başlatma listesinde değerler sağlarken, bir üye niteleyicisi karakterini takip eden bir satır devamlılık karakteri (`_`) eklemeniz gerekir. `With` deyimlerini veya nesne başlatma listelerini kullanırken, atama işlecinden (örneğin, `=`) sonra çizgiyi koparın. Örneğin:

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   Daha fazla bilgi için bkz [.... WITH Ifadesiyle](../../../visual-basic/language-reference/statements/with-end-with-statement.md) veya [nesne başlatıcılarına son: adlandırılmış ve anonim türler](./objects-and-classes/object-initializers-named-and-anonymous-types.md).

- Bir XML ekseni Özellik niteleyicisi (`.` veya `.@` veya `...`) sonra. Ancak, `With` anahtar sözcüğünü kullanırken bir üye niteleyicisi belirttiğinizde bir satır devamlılık karakteri (`_`) eklemeniz gerekir. Örneğin:

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   Daha fazla bilgi için bkz. [xml eksen özellikleri](../../../visual-basic/language-reference/xml-axis/index.md).

- Bir öznitelik belirttiğinizde küçüktür işaretinden (<) veya büyüktür işaretinden (`>`) sonra. Ayrıca bir özniteliği belirttiğinizde büyüktür işaretinden (`>`) sonra. Ancak, derleme düzeyi veya modül düzeyi öznitelikleri belirttiğinizde bir satır devamlılık karakteri (`_`) eklemeniz gerekir. Örneğin:

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   Daha fazla bilgi için bkz. [özniteliklere genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md).

- Sorgu işleçlerinden önce ve sonra (`Aggregate`, `Distinct`, `From`, `Group By`, `Group Join`, `Join`, `Let`, `Order By`, `Select`, `Skip`, `Skip While`, `Take`, `Take While`, `Where`, `In`, `Into`, `On`, `Ascending`ve `Descending`). Birden çok anahtar kelimesinden (`Order By`, `Group Join`, `Take While`ve `Skip While`) oluşan sorgu işleçlerinin anahtar kelimeleri arasında bir satırı bozamaz. Örneğin:

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   Daha fazla bilgi için bkz. [sorgular](../../../visual-basic/language-reference/queries/index.md).

- `For Each` bildiriminde `In` anahtar sözcüğünden sonra. Örneğin:

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   Daha fazla bilgi için bkz [. her biri için... Sonraki Ifade](../../../visual-basic/language-reference/statements/for-each-next-statement.md).

- Bir koleksiyon başlatıcısındaki `From` anahtar sözcüğünden sonra. Örneğin:

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   Daha fazla bilgi için bkz. [koleksiyon başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

## <a name="adding-comments"></a>Açıklama ekleme

Kaynak kodu her zaman kendi kendine açıklama değil, onu yazan programcıya da. Bu nedenle, çoğu programcı gömülü açıklamaların serbest bir şekilde kullanılmasını sağlar. Koddaki açıklamalar, daha sonra okuma veya bunlarla çalışan herkes için bir yordamı veya belirli bir yönergeyi açıklayabilir. Visual Basic, derleme sırasında açıklamaları yoksayar ve derlenen kodu etkilemez.

Açıklama satırları, bir kesme işareti (`'`) veya `REM` ardından bir boşluk ile başlar. Bunlar, bir dize dışında, kodda herhangi bir yere eklenebilir. Bir ifadeye açıklama eklemek için, deyiminden sonra bir kesme işareti veya `REM` ekleyin ve ardından yorum yapın. Açıklamalar Ayrıca kendi ayrı hattına da gidebilir. Aşağıdaki örnek bu olasılıkları göstermektedir.

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a>Derleme hataları denetleniyor

Bir kod satırı yazdığınızda, çizgi dalgalı mavi alt çizgiyle görüntülenir (bir hata iletisi de görünebilir), bildirimde bir sözdizimi hatası vardır. Deyimle ilgili nelerin yanlış olduğunu bulmanız gerekir (görev listesine bakarak veya fare işaretçisi ile hata üzerinde gezinerek ve hata iletisini okuyarak) ve bunu düzeltebilirsiniz. Kodunuzda tüm sözdizimi hatalarını düzeltene kadar, programınız doğru şekilde derlenmeyecektir.

## <a name="related-sections"></a>İlgili bölümler

|Terim|Tanım|
|---|---|
|[Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)|`=`, `*=`ve `&=`gibi atama işleçlerini kapsayan dil başvurusu sayfalarına bağlantılar sağlar.|
|[İşleçler ve İfadeler](./operators-and-expressions/index.md)|Yeni değerler sağlamak için işleçlerle öğelerin nasıl birleştirileceğini gösterir.|
|[Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|Tek bir deyimin birden çok satıra nasıl kesilmesini ve birden çok deyimin aynı satıra nasıl yerleştirileceğini gösterir.|
|[Nasıl yapılır: Etiket Deyimleri](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|Bir kod satırının nasıl etiketleneceğini gösterir.|
