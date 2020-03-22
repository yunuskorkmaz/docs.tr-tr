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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400892"
---
# <a name="statements-in-visual-basic"></a>Visual Basic'deki Deyimler

Visual Basic'teki bir deyim tam bir yönergedir. Anahtar kelimeler, işleçler, değişkenler, sabitler ve ifadeler içerebilir. Her deyim aşağıdaki kategorilerden birine aittir:

- Bir değişken, sabit veya yordam adı veren ve bir veri türünü de belirtebilen **Bildirim İfadeleri.**

- Eylemleri başlatan **Yürütülebilir İfadeler.** Bu ifadeler bir yöntem veya işlev çağırabilir ve kod blokları aracılığıyla döngü veya dalolabilir. Yürütülebilir ifadeler, bir değişkene veya sabite değer veya ifade atayan **Atama Deyimleri'ni**içerir.

Bu konu her kategoriyi açıklar. Ayrıca, bu konu, tek bir satırda birden çok deyimin nasıl birleştirilen nasıl yapılacağını ve birden çok satır üzerinden bir deyimin nasıl devam edeceği açıklanır.

## <a name="declaration-statements"></a>Bildirim deyimleri

Yordamları, değişkenleri, özellikleri, dizileri ve sabitleri adlandırmak ve tanımlamak için bildirim deyimlerini kullanırsınız. Bir programlama öğesini beyan ettiğinizde, veri türünü, erişim düzeyini ve kapsamını da tanımlayabilirsiniz. Daha fazla bilgi için, [Bildirilen Öğe Özellikleri'ne](./declared-elements/declared-element-characteristics.md)bakın.

Aşağıdaki örnekte üç bildirim içerir.

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

İlk bildirim `Sub` deyimdir. Eşleşen `End Sub` deyimi ile birlikte, adlı `applyFormat`bir yordam bildirir. `Public`Ayrıca, `applyFormat` ona başvurabilen herhangi bir kodun onu çağırabileceği anlamına gelir.

İkinci bildirim, `Const` `limit` `Integer` veri türünü ve 33 değerini belirten sabiti bildiren ifadedir.

Üçüncü bildirim, `Dim` değişkeni `thisWidget`bildiren ifadedir. Veri türü belirli bir nesne, yani `Widget` sınıftan oluşturulan bir nesnedir. Bir değişkeni, kullandığınız uygulamada maruz kalan herhangi bir temel veri türünden veya herhangi bir nesne türünden olarak bildirebilirsiniz.

### <a name="initial-values"></a>Başlangıç Değerleri

Bildirim bildirimi ni içeren kod çalıştığında, Visual Basic bildirilen öğe için gereken belleği ayırır. Öğe bir değer taşıyorsa, Visual Basic onu veri türü için varsayılan değere başharfe aktarıyor. Daha fazla bilgi için Dim Bildirimi'ndeki "Davranış" [bilgisine](../../language-reference/statements/dim-statement.md)bakın.

Aşağıdaki örnekte gösterildiği gibi, bir değişkene bildiriminin bir parçası olarak bir başlangıç değeri atayabilirsiniz.

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

Bir değişken bir nesne değişkeniyse, aşağıdaki örnekte gösterildiği [gibi, Yeni Operatör](../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcükünü kullanarak onu beyan ettiğinizde sınıfının bir örneğini açıkça oluşturabilirsiniz.

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

Bir bildirim bildiriminde belirttiğiniz ilk değerin, yürütme deekbesine ulaşana kadar bir değişkene atanmadığını unutmayın. O zamana kadar, değişken veri türü için varsayılan değeri içerir.

## <a name="executable-statements"></a>Çalıştırılabilir ifadeler

Yürütülebilir bir deyim bir eylem gerçekleştirir. Bir yordamı, şubeyi koddaki başka bir yere çağırabilir, çeşitli ifadeler arasında döngü yapabilir veya bir ifadeyi değerlendirebilir. Atama deyimi, yürütülebilir bir deyimin özel bir örneğidir.

Aşağıdaki örnek, `If...Then...Else` bir değişkenin değerini temel alan farklı kod bloklarını çalıştırmak için bir denetim yapısı kullanır. Her kod bloğu içinde, bir `For...Next` döngü belirli sayıda çalışır.

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

Önceki `If` örnekteki deyim, parametrenin `clockwise`değerini denetler. Değeri ise `True`, bu `spinClockwise` yöntemi `aWidget`çağırır . Değeri ise `False`, bu `spinCounterClockwise` yöntemi `aWidget`çağırır . Denetim `If...Then...Else` yapısı `End If`ile biter.

Her `For...Next` blok taki döngü, uygun yöntemi `revolutions` parametrenin değerine eşit bir kaç kez çağırır.

## <a name="assignment-statements"></a>Atama deyimleri

Atama deyimleri, aşağıdaki örnekte olduğu gibi, atama işlecinin`=`() sağ tarafındaki değeri alıp soldaki öğede depolamaktan oluşan atama işlemlerini yürütür.

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

Önceki örnekte, atama deyimi 42 değerini değişkende `v`depolar.

### <a name="eligible-programming-elements"></a>Uygun programlama öğeleri

Atama işlecinin sol tarafındaki programlama öğesi bir değeri kabul edip depolayabilmeli. Bu, [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olmayan bir değişken veya özellik olması veya bir dizi öğesi olması gerektiği anlamına gelir. Atama deyimi bağlamında, bu tür bir öğe bazen "sol değer" için *bir lvalue*olarak adlandırılır.

Atama işlecinin sağ tarafındaki değer, gerçek, sabitler, değişkenler, özellikler, dizi öğeleri, diğer ifadeler veya işlev çağrılarının herhangi bir birleşiminden oluşabilen bir ifade tarafından oluşturulur. Aşağıdaki örnek bunu göstermektedir.

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

Önceki örnek, değişkende `y` tutulan değeri değişkende `z`tutulan değere ekler ve ardından çağrının `findResult`işlevine verdiği değeri ekler. Bu ifadenin toplam değeri daha sonra `x`değişkende depolanır.

### <a name="data-types-in-assignment-statements"></a>Atama ifadelerindeki veri türleri

Sayısal değerlere ek olarak, atama işleci `String` aşağıdaki örnekte gösterildiği gibi değerleri de atayabilir.

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

Aşağıdaki örnekte `Boolean` gösterildiği gibi, `Boolean` gerçek veya `Boolean` ifadeyi kullanarak değerleri de atayabilirsiniz.

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

Benzer şekilde, `Char`, veya `Date` `Object` veri türü programlama öğelerine uygun değerler atayabilirsiniz. Ayrıca, bir nesne örneğini, bu örneğin oluşturulduğu sınıfın olarak bildirilen bir öğesine atayabilirsiniz.

### <a name="compound-assignment-statements"></a>Bileşik atama deyimleri

*Bileşik atama deyimleri,* bir programlama öğesine atamadan önce bir ifade üzerinde önce bir işlem gerçekleştirir. Aşağıdaki örnek, `+=`işleç teki değişkenin değerini sağdaki ifadenin değeriyle artan bu işleçlerden birini göstermektedir.

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

Önceki örnek `n`, değerine 1 ekler ve sonra bu `n`yeni değeri . Bu, aşağıdaki ifadenin kısaltma eşdeğeridir:

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

Bu tür işleçler kullanılarak çeşitli bileşik atama işlemleri gerçekleştirilebilir. Bu işleçlerin listesi ve bunlar hakkında daha fazla bilgi için [Bkz. Atama Operatörleri.](../../../visual-basic/language-reference/operators/assignment-operators.md)

Birleştirme atama işleci`&=`( ) aşağıdaki örnekte gösterildiği gibi, zaten varolan dizeleri sonuna bir dize eklemek için yararlıdır.

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a>Atama Ekstrelerinde Dönüşümler Yazın

Bir değişkene, özellikveya dizi öğesine atadığınız değer, bu hedef öğe öğesine uygun bir veri türüne sahip olmalıdır. Genel olarak, hedef öğeyle aynı veri türünde bir değer oluşturmayı denemelisiniz. Ancak, bazı türler atama sırasında diğer türlere dönüştürülebilir.

Veri türleri arasında dönüştürme hakkında bilgi için [Visual Basic'te Tür Dönüşümleri'ne](./data-types/type-conversions.md)bakın. Kısaca, Visual Basic otomatik olarak belirli bir türün değerini genişletildiği başka bir türe dönüştürür. *Genişleyen dönüştürme,* her zaman çalışma zamanında başarılı olan ve veri kaybetmeyen bir dönüşümdür. Örneğin, Visual Basic bir `Integer` değeri `Double` uygun olduğunda `Integer` dönüştürür, `Double`çünkü genişler. Daha fazla bilgi için [Dönüşümleri Genişletme ve Daraltma'ya](./data-types/widening-and-narrowing-conversions.md)bakın.

*Dönüşümleri daraltmak* (genişletmeyenler) çalışma zamanında arıza lanma veya veri kaybı riski taşır. Bir tür dönüştürme işlevini kullanarak açıkça daraltma dönüştürme gerçekleştirebilirsiniz veya derleyiciyi tüm dönüşümleri `Option Strict Off`dolaylı olarak ayarlayarak gerçekleştirmesi için yönlendirebilirsiniz. Daha fazla bilgi için [örtük ve Açık Dönüşümler'e](./data-types/implicit-and-explicit-conversions.md)bakın.

## <a name="putting-multiple-statements-on-one-line"></a>Birden çok ifadeyi tek satıra koyma

İki nokta üst üste (`:`) karakteriyle ayrılmış tek bir satırda birden çok deyim olabilir. Aşağıdaki örnek bunu göstermektedir.

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

Bazen kullanışlı olsa da, sözdiziminin bu biçimi kodunuzu okumayı ve bakımını zorlaştırır. Bu nedenle, bir satırı bir ifade tutmak önerilir.

## <a name="continuing-a-statement-over-multiple-lines"></a>Birden çok satır üzerinden bir bildirimi devam etme

Bir deyim genellikle bir satıra sığar, ancak çok uzun olduğunda, bir satır devam ı sırasını kullanarak bir sonraki satıra`_`devam edebilirsiniz, bir boşluk ve ardından bir alt çizgi karakteri () ve ardından bir satır iadesi oluşur. Aşağıdaki örnekte, `MsgBox` çalıştırılabilir deyim iki satır üzerinden devam edilir.

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a>Örtük çizgi devamı

Çoğu durumda, alt çizgi karakterini kullanmadan bir sonraki ardışık`_`satırda bir deyim devam edebilirsiniz ( ). Aşağıdaki sözdizimi öğeleri dolaylı olarak bir sonraki kod satırında deyimdevam ediyor.

- Virgülden sonra`,`( ). Örnek:

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- Açık bir parantez sonra`(`( ) veya kapanış parantezinden önce (`)`). Örnek:

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- Açık bir kıvırcık`{`ayraç sonra ( )`}`veya kapanış kıvırcık ayraç önce ( ). Örnek:

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    Daha fazla bilgi için [bkz: Nesne Başlangıç: Adlandırılmış ve Anonim Türleri](./objects-and-classes/object-initializers-named-and-anonymous-types.md) veya [Koleksiyon Initializers](./collection-initializers/index.md).

- Bir XML harfi`<%=`içinde gömülü bir ifadenin`%>`() kapatılmasından önce ( ) veya açık gömülü bir ifadeden sonra. Örnek:

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   Daha fazla bilgi için [XML'deki Gömülü İfadeler'e](./xml/embedded-expressions-in-xml.md)bakın.

- Concatenation işlecinden`&`sonra ( ). Örnek:

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   Daha fazla bilgi için bkz. [İşlevsellik Tarafından Listelenen Operatörler.](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)

- Atama operatörlerinden`=` `&=`sonra `:=` `+=`( `-=` `*=`, `/=` `\=`, `^=` `<<=`, `>>=`, , , , , , , , . Örnek:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Daha fazla bilgi için bkz. [İşlevsellik Tarafından Listelenen Operatörler.](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)

- İkili operatörler`+` `-`sonra `/` `*`( `Mod` `<>`, `<` `>`, `<=` `>=`, `^` `>>` `<<` `And` `OrElse` `Like`, , , , `Xor`, , , , , , , , , , , , , , , , , , , ) içinde bir ifade içinde. `AndAlso` `Or` Örnek:

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   Daha fazla bilgi için bkz. [İşlevsellik Tarafından Listelenen Operatörler.](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)

- Sonra `Is` ve `IsNot` operatörler. Örnek:

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   Daha fazla bilgi için bkz. [İşlevsellik Tarafından Listelenen Operatörler.](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)

- Bir üye niteleyici`.`karaktersonra ( ) ve üye adı önce. Örnek:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Ancak, `With` deyimi kullanırken veya bir`_`tür için başlatma listesinde değerler sağlarken bir üye niteleyici karakterini izleyen bir satır devam karakteri ( ) eklemeniz gerekir. İfadeleri veya nesne başlatma listelerini `=`kullanırken `With` atama işlecinden (örneğin,) sonra satırı bölmeyi düşünün. Örnek:

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   Daha fazla bilgi için [bkz. İfade](../../../visual-basic/language-reference/statements/with-end-with-statement.md) veya [Nesne BaşlangıçLarıyla](./objects-and-classes/object-initializers-named-and-anonymous-types.md)Son: Adlandırılmış ve Anonim Türleri .

- Bir XML eksen özellik`.` `.@` niteleyiciden sonra (veya). `...` Ancak, `With` anahtar kelimeyi kullanırken`_`bir üye niteleyici belirtirken bir satır devam karakteri ( ) eklemeniz gerekir. Örnek:

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   Daha fazla bilgi için [Bkz. XML Eksen Özellikleri.](../../../visual-basic/language-reference/xml-axis/index.md)

- Daha az bir işaretten (<) sonra veya`>`bir öznitelik belirttiğiniz zaman büyük bir işaretten önce ( ) önce. Ayrıca bir öznitelik belirttiğiniz zaman büyük bir işareti sonra (`>`) Ancak, derleme düzeyi veya modül`_`düzeyinde öznitelikleri belirtirken bir satır devam karakteri ( ) eklemeniz gerekir. Örnek:

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   Daha fazla bilgi için, [Bkz. Özniteliklere genel bakış.](../../../visual-basic/programming-guide/concepts/attributes/index.md)

- Önce ve sonra`Aggregate`sorgu `Distinct` `From`operatörleri `Group By` `Group Join`( `Join` `Let`, `Order By` `Select`, `Skip` `Skip While` `Take` `Take While` `Where` `In` `Into` `Ascending`, , , , , `Descending`, , , , , , , , , , ve . `On` Birden çok anahtar kelimeden oluşan sorgu işleçlerinin anahtar`Order By`kelimeleri `Group Join` `Take While`arasındaki `Skip While`çizgiyi kıramazsınız ( , , , ve ). Örnek:

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   Daha fazla bilgi için [Sorgular'a](../../../visual-basic/language-reference/queries/index.md)bakın.

- Bir `For Each` `In` deyimdeki anahtar kelimeden sonra. Örnek:

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   Daha fazla bilgi için [bkz. Sonraki İfade](../../../visual-basic/language-reference/statements/for-each-next-statement.md).

- Bir `From` koleksiyon baş harfindeki anahtar kelimeden sonra. Örnek:

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   Daha fazla bilgi için [Bkz. Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

## <a name="adding-comments"></a>Yorum ekleme

Kaynak kodu her zaman kendini açıklayıcı değildir, hatta bunu yazan programcı için bile. Bu nedenle, kodlarını belgelemelerine yardımcı olmak için, çoğu programcı katışılmış yorumları liberal olarak kullanır. Koddaki yorumlar, bir yordamı veya belirli bir talimatı daha sonra okuyan veya onunla çalışan herkese açıklayabilir. Visual Basic derleme sırasında yapılan açıklamaları yok sayar ve derlenen kodu etkilemez.

Açıklama satırları bir kesit işaretiyle `REM` başlar veya`'`ardından bir boşluk la başlar. Bunlar, bir dize dışında, kod içinde herhangi bir yere eklenebilir. Bir yorumu bir bildirime eklemek için, bir `REM` keseli işareti ekleyin veya deyimden sonra, ardından yorum. Yorumlar da kendi ayrı hat üzerinde gidebilirsiniz. Aşağıdaki örnek, bu olasılıkları göstermektedir.

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a>Derleme hatalarını denetleme

Bir kod satırı yazdıktan sonra satır dalgalı mavi bir altı çizili ile görüntülenirse (bir hata iletisi de görünebilir), ekstrede bir sözdizimi hatası vardır. Deyimin nesi olduğunu bulmanız gerekir (görev listesine bakarak veya fare işaretçisi ile hatanın üzerine gidip hata iletisini okuyarak) ve düzeltin. Kodunuzdaki tüm sözdizimi hatalarını düzeltene kadar, programınız doğru derlemeyapmaz.

## <a name="related-sections"></a>İlgili bölümler

|Sözleşme Dönemi|Tanım|
|---|---|
|[Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)|Atama işleçlerini kapsayan dil başvuru sayfalarına bağlantılar sağlar. `&=` `=` `*=`|
|[İşleçler ve İfadeler](./operators-and-expressions/index.md)|Yeni değerler sağlamak için öğeleri işleçlerle nasıl birleştiringerektiğini gösterir.|
|[Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|Tek bir ifadenin birden çok satıra nasıl kırılabildiğini ve aynı satıra birden fazla deyimin nasıl yerleştirilebildiğini gösterir.|
|[Nasıl yapılır: Etiket Deyimleri](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|Kod satırının nasıl etiketlendiğini gösterir.|
