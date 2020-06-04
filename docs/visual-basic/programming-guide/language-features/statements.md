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
ms.openlocfilehash: 09fe53f4bc2b6d025b762c6595c5337263456bae
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401985"
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

İlk bildirim, `Sub` deyimidir. Eşleşen `End Sub` ifadesiyle birlikte, adlı bir yordamı bildirir `applyFormat` . Ayrıca bunu belirtir `applyFormat` ; yani `Public` , başvurabilen tüm kodlar bunu çağırabilir.

İkinci bildirim, `Const` `limit` `Integer` veri türünü ve 33 değerini belirterek sabiti bildiren ifadedir.

Üçüncü bildirim, `Dim` değişkeni bildiren deyimidir `thisWidget` . Veri türü, sınıfından oluşturulan bir nesne olarak belirtilen belirli bir nesnedir `Widget` . Bir değişkeni, herhangi bir temel veri türü veya kullandığınız uygulamada kullanıma sunulan herhangi bir nesne türünde olacak şekilde bildirebilirsiniz.

### <a name="initial-values"></a>İlk değerler

Bir bildirim ifadesini içeren kod çalıştırıldığında, Visual Basic bildirimi yapılan öğe için gereken belleği ayırır. Öğe bir değer içeriyorsa, Visual Basic onu veri türü için varsayılan değer olarak başlatır. Daha fazla bilgi için, bkz. [Dim deyimindeki](../../language-reference/statements/dim-statement.md)"davranış".

Aşağıdaki örnekte gösterildiği gibi, bir değişkene, bildiriminin bir parçası olarak bir başlangıç değeri atayabilirsiniz.

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

Bir değişken bir nesne değişkense, aşağıdaki örnekte gösterildiği gibi [New Operator](../../language-reference/operators/new-operator.md) anahtar sözcüğünü kullanarak sınıfını bildirdiğinizde sınıfının bir örneğini açıkça oluşturabilirsiniz.

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

Bir bildirim ifadesinde belirttiğiniz ilk değerin, yürütme bildirim bildirimine ulaşıncaya kadar bir değişkene atanmadığını unutmayın. Bu saate kadar, değişken veri türü için varsayılan değeri içerir.

## <a name="executable-statements"></a>Yürütülebilir deyimler

Yürütülebilir bir ifade bir eylem gerçekleştirir. Bir yordam çağırabilir, koddaki başka bir yere dallandırır, çeşitli deyimlerde döngü gerçekleştirebilir veya bir ifadeyi değerlendirebilir. Atama ekstresi, yürütülebilir bir deyimin özel bir durumdur.

Aşağıdaki örnek, `If...Then...Else` bir değişkenin değerine göre farklı kod blokları çalıştırmak için bir denetim yapısı kullanır. Her kod bloğu içinde, bir `For...Next` döngü belirtilen sayıda çalıştırılır.

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

`If`Önceki örnekteki ifade, parametresinin değerini denetler `clockwise` . Değer ise, `True` `spinClockwise` yöntemini çağırır `aWidget` . Değer ise, `False` `spinCounterClockwise` yöntemini çağırır `aWidget` . `If...Then...Else`Denetim yapısı ile biter `End If` .

`For...Next`Her bloğun içindeki döngü, parametrenin değerine eşit sayıda kez uygun yöntemi çağırır `revolutions` .

## <a name="assignment-statements"></a>Atama deyimleri

Atama deyimleri, atama işlecinin () sağ tarafında değeri alan `=` ve bunu, aşağıdaki örnekte olduğu gibi soldaki öğede depolayan atama işlemlerini gerçekleştirebilir.

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

Yukarıdaki örnekte, atama bildiriminde 42 sabit değeri, değişkende saklanır `v` .

### <a name="eligible-programming-elements"></a>Uygun programlama öğeleri

Atama işlecinin sol tarafındaki programlama öğesi bir değeri kabul edip depolayabilmelidir. Bu, [salt okunur](../../language-reference/modifiers/readonly.md)olmayan bir değişken veya özellik olması veya bir dizi öğesi olması gerektiği anlamına gelir. Atama ifadesinin bağlamında, bu tür bir öğe bazen "sol değer" için *lvalue*olarak adlandırılır.

Atama işlecinin sağ tarafındaki değer, değişmez değer, sabitler, değişkenler, özellikler, dizi öğeleri, diğer ifadeler veya işlev çağrılarının birleşiminden oluşabilen bir ifade tarafından oluşturulur. Aşağıdaki örnek bunu göstermektedir.

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

Yukarıdaki örnek, değişkenine tutulan değeri `y` değişkeninde bulunan değere ekler `z` ve sonra çağrısı tarafından döndürülen değeri işlevine ekler `findResult` . Bu ifadenin toplam değeri daha sonra değişkende depolanır `x` .

### <a name="data-types-in-assignment-statements"></a>Atama İfadelerdeki veri türleri

Sayısal değerlere ek olarak, aşağıdaki örnekte gösterildiği gibi atama işleci de `String` değerler atayabilir.

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

Ayrıca `Boolean` , `Boolean` Aşağıdaki örnekte gösterildiği gibi, değişmez değer veya ifade kullanarak değerler atayabilirsiniz `Boolean` .

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

Benzer şekilde,,, `Char` `Date` veya veri türünün programlama öğelerine uygun değerler atayabilirsiniz `Object` . Ayrıca bir nesne örneğini, bu örneğin oluşturulduğu sınıf olarak belirtilen bir öğeye atayabilirsiniz.

### <a name="compound-assignment-statements"></a>Bileşik atama deyimleri

*Bileşik atama deyimleri* , bir programlama öğesine atamadan önce bir ifadede bir işlem gerçekleştirir. Aşağıdaki örnek, `+=` işlecin sol tarafındaki değişkenin değerini sağdaki ifadenin değeri ile artıran bu işleçlerden birini gösterir.

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

Yukarıdaki örnek, değerine 1 ekler `n` ve ardından bu yeni değeri içinde depolar `n` . Bu, aşağıdaki deyimin bir toplu eşdeğeridir.

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

Bu türdeki işleçler kullanılarak çeşitli bileşik atama işlemleri gerçekleştirilebilir. Bu işleçlerin bir listesi ve bunlarla ilgili daha fazla bilgi için bkz. [atama işleçleri](../../language-reference/operators/assignment-operators.md).

Birleştirme atama işleci ( `&=` ), aşağıdaki örnekte gösterildiği gibi, zaten var olan dizelerin sonuna bir dize eklemek için yararlıdır.

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a>Atama deyimlerinde tür dönüştürmeleri

Bir değişkene, özelliğe veya dizi öğesine atadığınız değer bu hedef öğeye uygun bir veri türünde olmalıdır. Genel olarak, hedef öğesiyle aynı veri türünde bir değer oluşturmayı denemelisiniz. Ancak, bazı türler atama sırasında diğer türlere dönüştürülebilir.

Veri türleri arasında dönüştürme hakkında daha fazla bilgi için bkz. [tür dönüştürmeleri Visual Basic](./data-types/type-conversions.md). Kısaca Visual Basic, belirli bir türdeki bir değeri otomatik olarak widens diğer bir türe dönüştürür. *Genişleyen dönüştürme* , her zaman çalışma zamanında başarılı olur ve herhangi bir veri kaybetmez. Örneğin, Visual Basic bir `Integer` değeri `Double` uygun olduğunda öğesine dönüştürür, çünkü `Integer` widens to `Double` . Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](./data-types/widening-and-narrowing-conversions.md).

*Daraltma dönüştürmeleri* (genişletme olmayan), çalışma zamanında veya veri kaybından hata riski taşır. Bir tür dönüştürme işlevini kullanarak açıkça bir daraltma dönüştürmesi gerçekleştirebilir veya derleyiciyi ayarlayarak tüm dönüştürmeleri gerçekleştirmek üzere derleyiciye yönlendirebilirsiniz `Option Strict Off` . Daha fazla bilgi için bkz. [örtük ve açık dönüştürmeler](./data-types/implicit-and-explicit-conversions.md).

## <a name="putting-multiple-statements-on-one-line"></a>Birden çok deyimi tek satıra yerleştirme

İki nokta () karakteriyle ayrılmış tek bir satırda birden çok deyimden sahip olabilirsiniz `:` . Aşağıdaki örnek bunu göstermektedir.

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

Bazen kullanışlı olsa da, bu tür bir sözdizimi kodunuzun okunmasını ve bakımını daha zor hale getirir. Bu nedenle, bir ifadeyi bir satıra tutmanız önerilir.

## <a name="continuing-a-statement-over-multiple-lines"></a>Birden çok satır üzerinde bir ifadeye devam etme

Bir ifade genellikle tek bir satıra sığar, ancak çok uzun olduğunda bir satır devamlılığı dizisi kullanarak sonraki satıra devam edebilir. Bu, alt çizgi karakteri () ve ardından `_` bir satır başı gelir. Aşağıdaki örnekte, `MsgBox` çalıştırılabilir ifade iki satır üzerinde devam ediyor.

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a>Örtük satır devamlılığı

Birçok durumda, alt çizgi karakterini () kullanmadan sonraki ardışık satırda bir ifadeye devam edebilirsiniz `_` . Aşağıdaki sözdizimi öğeleri, bir sonraki kod satırında ifadesiyle dolaylı olarak devam eder.

- Virgülden sonra ( `,` ). Örnek:

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- Bir açık parantezden ( `(` ) sonra veya kapatma parantezinden ( `)` ) önce. Örnek:

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- Açık bir küme ayracı ( `{` ) veya bir kapanış küme ayracı () öncesi `}` . Örnek:

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    Daha fazla bilgi için bkz. [nesne başlatıcıları: adlandırılmış ve anonim türler](./objects-and-classes/object-initializers-named-and-anonymous-types.md) veya [koleksiyon başlatıcıları](./collection-initializers/index.md).

- Açık bir katıştırılmış ifadeden sonra ( `<%=` ) veya BIR `%>` XML sabit değeri içindeki katıştırılmış bir ifadenin () kapatıldıktan önce. Örnek:

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   Daha fazla bilgi için bkz. [XML 'de katıştırılmış ifadeler](./xml/embedded-expressions-in-xml.md).

- Birleştirme işlecinden sonra ( `&` ). Örnek:

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   Daha fazla bilgi için bkz. [işlevlere göre listelenen işleçler](../../language-reference/operators/operators-listed-by-functionality.md).

- Atama işleçleri ( `=` , `&=` ,, `:=` , `+=` , `-=` `*=` , `/=` , `\=` , `^=` , `<<=` , `>>=` ,,,,) sonra. Örnek:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Daha fazla bilgi için bkz. [işlevlere göre listelenen işleçler](../../language-reference/operators/operators-listed-by-functionality.md).

- İkili işleçlerden (,,,,,,,,,,,,,, `+` `-` `/` `*` `Mod` `<>` `<` `>` `<=` `>=` `^` `>>` `<<` `And` `AndAlso` , `Or` `OrElse` `Like` `Xor` ,,,,,,,,,,,,, Örnek:

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   Daha fazla bilgi için bkz. [işlevlere göre listelenen işleçler](../../language-reference/operators/operators-listed-by-functionality.md).

- `Is`Ve `IsNot` işleçlerinden sonra. Örnek:

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   Daha fazla bilgi için bkz. [işlevlere göre listelenen işleçler](../../language-reference/operators/operators-listed-by-functionality.md).

- Bir üye niteleyicisi karakterinden ( `.` ) sonra ve üye adından önce. Örnek:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Ancak, `_` `With` ifadeyi kullanırken veya bir tür için başlatma listesinde değerler sağlayan bir üye niteleyicisi karakterini takip eden bir satır devamlılık karakteri () eklemeniz gerekir. `=` `With` Deyim veya nesne başlatma listeleri kullanırken, atama işlecinden (örneğin,) sonra çizgiyi koparın. Örnek:

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   Daha fazla bilgi için bkz [.... WITH Ifadesiyle](../../language-reference/statements/with-end-with-statement.md) veya [nesne başlatıcılarına son: adlandırılmış ve anonim türler](./objects-and-classes/object-initializers-named-and-anonymous-types.md).

- Bir XML ekseni Özellik niteleyicisi ( `.` veya `.@` veya) sonra `...` . Ancak, `_` anahtar sözcüğünü kullanırken bir üye niteleyicisi belirttiğinizde bir satır devamlılık karakteri () eklemeniz gerekir `With` . Örnek:

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   Daha fazla bilgi için bkz. [xml eksen özellikleri](../../language-reference/xml-axis/index.md).

- Bir öznitelik belirttiğinizde küçüktür işaretinden (<) veya büyüktür işaretinden ( `>` ) önce. Ayrıca bir özniteliği belirttiğinizde büyüktür işaretinden ( `>` ) sonra. Ancak, `_` derleme düzeyi veya modül düzeyi öznitelikleri belirttiğinizde bir satır devamlılık karakteri () eklemeniz gerekir. Örnek:

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   Daha fazla bilgi için bkz. [özniteliklere genel bakış](../concepts/attributes/index.md).

- Sorgu işleçlerinden önce ve sonra ( `Aggregate` , `Distinct` ,, `From` `Group By` , `Group Join` , `Join` , `Let` , `Order By` , `Select` , `Skip` , `Skip While` , `Take` ,,,,, `Take While` , `Where` `In` `Into` `On` `Ascending` `Descending` ,,,,, ve). Birden çok anahtar kelimeyle ( `Order By` ,, `Group Join` `Take While` ve) oluşan sorgu işleçleri anahtar kelimeleri arasında bir satırı bozamaz `Skip While` . Örnek:

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   Daha fazla bilgi için bkz. [sorgular](../../language-reference/queries/index.md).

- `In`Deyimdeki anahtar sözcükten sonra `For Each` . Örnek:

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   Daha fazla bilgi için bkz [. her biri için... Sonraki Ifade](../../language-reference/statements/for-each-next-statement.md).

- `From`Bir koleksiyon başlatıcısındaki anahtar sözcükten sonra. Örnek:

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   Daha fazla bilgi için bkz. [koleksiyon başlatıcıları](collection-initializers/index.md).

## <a name="adding-comments"></a>Açıklama ekleme

Kaynak kodu her zaman kendi kendine açıklama değil, onu yazan programcıya da. Bu nedenle, çoğu programcı gömülü açıklamaların serbest bir şekilde kullanılmasını sağlar. Koddaki açıklamalar, daha sonra okuma veya bunlarla çalışan herkes için bir yordamı veya belirli bir yönergeyi açıklayabilir. Visual Basic, derleme sırasında açıklamaları yoksayar ve derlenen kodu etkilemez.

Açıklama satırları, bir kesme işareti ( `'` ) veya `REM` arkasından bir boşluk ile başlar. Bunlar, bir dize dışında, kodda herhangi bir yere eklenebilir. Bir ifadeye açıklama eklemek için, bir kesme işareti ekleyin ve `REM` sonra açıklama gelir. Açıklamalar Ayrıca kendi ayrı hattına da gidebilir. Aşağıdaki örnek bu olasılıkları göstermektedir.

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a>Derleme hataları denetleniyor

Bir kod satırı yazdığınızda, çizgi dalgalı mavi alt çizgiyle görüntülenir (bir hata iletisi de görünebilir), bildirimde bir sözdizimi hatası vardır. Deyimle ilgili nelerin yanlış olduğunu bulmanız gerekir (görev listesine bakarak veya fare işaretçisi ile hata üzerinde gezinerek ve hata iletisini okuyarak) ve bunu düzeltebilirsiniz. Kodunuzda tüm sözdizimi hatalarını düzeltene kadar, programınız doğru şekilde derlenmeyecektir.

## <a name="related-sections"></a>İlgili bölümler

|Terim|Tanım|
|---|---|
|[Atama Işleçleri](../../language-reference/operators/assignment-operators.md)|, Ve gibi atama işleçlerini kapsayan dil başvuru sayfalarına bağlantılar sağlar `=` `*=` `&=` .|
|[İşleçler ve Ifadeler](./operators-and-expressions/index.md)|Yeni değerler sağlamak için işleçlerle öğelerin nasıl birleştirileceğini gösterir.|
|[Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../program-structure/how-to-break-and-combine-statements-in-code.md)|Tek bir deyimin birden çok satıra nasıl kesilmesini ve birden çok deyimin aynı satıra nasıl yerleştirileceğini gösterir.|
|[Nasıl yapılır: Etiket Deyimleri](../program-structure/how-to-label-statements.md)|Bir kod satırının nasıl etiketleneceğini gösterir.|
