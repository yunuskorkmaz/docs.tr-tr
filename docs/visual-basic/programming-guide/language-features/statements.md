---
title: Visual Basic'deki Deyimler
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
ms.openlocfilehash: e66acae5e98d561883f4ad59853dfd862c8ebfee
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43462402"
---
# <a name="statements-in-visual-basic"></a>Visual Basic'deki Deyimler

Visual Basic'te bir deyim eksiksiz bir yönergedir. Anahtar sözcükleri, işleçler, değişkenleri, sabitleri ve ifadeleri içerebilir. Her deyim aşağıdaki kategorilerden birine ait:

- **Bildirim deyimleri**, bir değişken, sabit değer ya da yordamın adını ve bir veri türü de belirtebilirsiniz.

- **Executable deyimleri**, Eylemler başlatın. Bu deyimler bir yöntem veya işlev çağırabilir ve döngü veya kod blokları boyunca dal. Executable deyimleri dahil **atama deyimleri**, hangi atama bir değer veya ifade bir değişken veya sabit değer.

Bu konu, her kategori açıklar. Ayrıca, bu konuda, tek bir satırda birden çok deyim bir araya getirilebileceğini öğrenin ve çoklu satırlar üzerinde bir deyim devam etme açıklanmaktadır.

## <a name="declaration-statements"></a>Bildirim deyimleri

Bildirim deyimleri, ad ve yordamları, değişkenleri, özellikleri, diziler ve sabitleri tanımlamak için kullanın. Bir programlama öğesi bildirdiğinizde, kendi veri türü, erişim düzeyi ve kapsam tanımlayabilirsiniz. Daha fazla bilgi için [bildirilen öğe özellikleri](./declared-elements/declared-element-characteristics.md).

Aşağıdaki örnek, üç bildirimleri içerir.

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

İlk bildirimi `Sub` deyimi. Kendi eşleşen birlikte `End Sub` deyimi, adında bir yordamı bildirir `applyFormat`. Ayrıca, belirtir `applyFormat` olduğu `Public`, yani bu başvurduğu herhangi bir kodu çağırabilir.

İkinci bildirimi `Const` sabiti bildirir deyimi `limit`, belirten `Integer` veri türü ve değeri 33.

Üçüncü bildirimi `Dim` değişkeni bildirir deyimi `thisWidget`. Veri türü belirli bir nesnesi, nesne oluşturulduğu yani `Widget` sınıfı. Bir değişken, herhangi bir başlangıç veri türü veya kullanmakta olduğunuz uygulamada kullanıma sunulan herhangi bir nesne türü olmasını bildirebilirsiniz.

### <a name="initial-values"></a>Başlangıç değerleri

Bildirim bir deyim içeren kod çalıştığında, Visual Basic bildirilen öğe için gerekli bellek ayırır. Öğe bir değeri tutar, Visual Basic, kendi veri türü için varsayılan değer başlatır. Daha fazla bilgi için "Davranışı" bölümüne bakın. [Dim deyimi](../../language-reference/statements/dim-statement.md).

Aşağıdaki örnekte gösterildiği gibi bir başlangıç değeri bir değişken, bildiriminin bir parçası olarak atayabilirsiniz.

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

Bir nesne değişkeninin bir değişken ise kullanarak bildirme zaman açıkça kendi sınıfının bir örneğini oluşturabilirsiniz [New işleci](../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcüğü, aşağıdaki örnek gösterir.

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

Yürütme, bildirim deyimindeki ulaşana kadar bir bildirim deyiminde belirttiğiniz başlangıç değeri bir değişkene atanmaz unutmayın. O zamana kadar değişken veri türü için varsayılan değeri içerir.

## <a name="executable-statements"></a>Executable deyimleri

Yürütülebilir bir deyimin bir eylem gerçekleştirir. Bu dalı başka bir yere kodda, birkaç deyimleri, döngü bir yordam çağırma veya bir ifadeyi değerlendirir. Atama ifadesi, yürütülebilir bir deyimin özel bir durumdur.

Aşağıdaki örnekte bir `If...Then...Else` denetim yapısı farklı bir değişken değerine göre kod bloklarını çalıştırmak için. Her kod bloğu içinde bir `For...Next` belirtilen sayıda döngü çalıştırır.

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

`If` Parametresinin değerini yukarıdaki örnekte deyimi denetler `clockwise`. Değer ise `True`, çağrı `spinClockwise` yöntemi `aWidget`. Değer ise `False`, çağrı `spinCounterClockwise` yöntemi `aWidget`. `If...Then...Else` Denetim yapısı ile sona erer `End If`.

`For...Next` Her blok içindeki döngü uygun yöntemini çağırır birkaç kez değerine eşit `revolutions` parametresi.

## <a name="assignment-statements"></a>Atama deyimleri

Değer atama işlecinin sağ tarafında kabul oluşan atama işlemleri atama deyimleri yürütmek (`=`) ve aşağıdaki örnekte olduğu gibi sol taraftaki öğesinde depolama.

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

Önceki örnekte, atama ifadesi değişmez değer 42 değişkeninde depolar. `v`.

### <a name="eligible-programming-elements"></a>Uygun programlama öğeleri

Programlama öğesine atama işlecinin sol tarafındaki kabul edin ve bir değer olmalıdır. Bir değişken veya özellik değil olmalıdır bir deyişle [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md), veya bir dizi öğesi olması gerekir. Atama ifadesi bağlamında, bu tür bir öğe adlandırılır bir *lvalue*, "sol değeri."

Atama işlecinin sağ tarafında değer değişmez değerleri, sabitleri, değişkenleri, özellikleri, dizi öğeleri, diğer ifadeler veya işlev çağrıları, herhangi bir birleşimini içerebilir bir ifade tarafından oluşturulur. Aşağıdaki örnek bunu göstermektedir.

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

Önceki örnekte, değişken tuttuğu değeri ekler `y` değişkeninde tutulan değere `z`ve ardından işlev çağrısı tarafından döndürülen değer ekler `findResult`. Bu ifadenin toplam değeri ardından değişkeninde depolanan `x`.

### <a name="data-types-in-assignment-statements"></a>Veri türlerini atama deyimleri

Sayısal değerlere ek olarak atama işleci de atayabilirsiniz `String` aşağıdaki örnekte gösterildiği gibi değerleri.

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

De atayabilirsiniz `Boolean` değerlerini kullanarak bir `Boolean` değişmez değer veya `Boolean` ifade, aşağıdaki örnek olarak gösterilmiştir.

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

Benzer şekilde, programlama öğeleri için uygun değerleri atayabilirsiniz `Char`, `Date`, veya `Object` veri türü. Bu örneği oluşturulduğu sınıfı olarak bildirilmiş bir öğeye bir nesne örneği de atayabilirsiniz.

### <a name="compound-assignment-statements"></a>Bileşik atama deyimleri

*Bileşik atama deyimleri* ilk önce bir programlama öğesine atama bir ifade üzerinde bir işlem gerçekleştirin. Aşağıdaki örnekte, bu işleçler birini gösterilmektedir `+=`, işlecin sol tarafındaki değişkeninin değeri ifade sağdaki değerini artırır.

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

Yukarıdaki örnekte, 1 değerine ekler `n`ve ardından yeni değeri depolar `n`. Bir toplu özelliktir aşağıdaki ifadenin eşdeğeri:

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

Bu tür işleçleri kullanarak çeşitli bileşik atama işlemleri gerçekleştirilebilir. Bu işleçler ve bunlar hakkında daha fazla bilgi listesi için bkz: [atama işleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md).

Birleştirme atama işleci (`&=`), mevcut sonuna bir dize eklemek için yararlıdır aşağıdaki örnekte gösterildiği gibi dizeleri.

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a>Atama deyimleri, tür dönüştürmeleri

Bir değişken, özelliği veya dizi öğesi atadığınız değeri bu hedef öğeye uygun bir veri türünde olmalıdır. Genel olarak, aynı veri türü, hedef öğenin değerini oluşturmak denemelisiniz. Ancak, bazı türleri, atama sırasında diğer türlere dönüştürülebilir.

Veri türleri arasında dönüştürme hakkında daha fazla bilgi için bkz: [Visual Basic'de tür dönüştürmeleri](./data-types/type-conversions.md). Kısaca, Visual Basic widens, başka bir tür, belirli bir türde bir değer otomatik olarak dönüştürür. A *dönüştürme genişletme* olan biri, her zaman çalışma zamanında başarılı olur ve tüm verileri kaybetmez. Örneğin, Visual Basic dönüştürür bir `Integer` değerini `Double` , çünkü uygun olduğunda `Integer` için widens `Double`. Daha fazla bilgi için [Widening ve daraltma dönüşümleri](./data-types/widening-and-narrowing-conversions.md).

*Daraltma dönüştürmeleri* çalışma zamanında hata veya veri kaybı riski taşıyan (olanlar değil genişletme). Derleyici örtük olarak ayarlayarak tüm dönüştürmeler gerçekleştirmek için yönlendirebilir veya bir tür dönüştürme işlevini kullanarak bir daraltma dönüşümü açıkça gerçekleştirebilirsiniz `Option Strict Off`. Daha fazla bilgi için [örtük ve açık dönüştürmeler](./data-types/implicit-and-explicit-conversions.md).

## <a name="putting-multiple-statements-on-one-line"></a>Birden çok deyim bir satıra koyarak

Virgül ile ayrılmış tek bir satırda birden çok deyime sahip olabilir (`:`) karakter. Aşağıdaki örnek bunu göstermektedir.

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

Bu söz dizimi biçimi bazen kullanışlı olsa kodunuzu okunması ve düzenlenmesi zor hale getirir. Bu nedenle, bir deyimi bir satıra tutmanız önerilir.

## <a name="continuing-a-statement-over-multiple-lines"></a>Bir deyim çoklu satırlar üzerinde devam etme

Bir deyimi, genellikle bir satıra sığacak, ancak çok uzun olduğunda, bir boşluk bir alt çizgi karakteriyle oluşan bir satır devamlılığı sırası kullanılarak sonraki satıra devam edebilirsiniz (`_`) başı tarafından izlenen. Aşağıdaki örnekte, `MsgBox` yürütülebilir deyimi üzerinde iki satır devam edilir.

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a>Örtük satır devamlılığı

Çoğu durumda, bir deyim sonraki ardışık satırda alt çizgi karakterini kullanmaya olmadan devam edebilirsiniz (`_`). Aşağıdaki sözdizimi öğeleri ifadesi örtük olarak kodun sonraki satırında devam edin.

- Sonra bir virgül (`,`). Örneğin:

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- Bir açık parantez sonra (`(`) veya bir kapanış parantezi önce (`)`). Örneğin:

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- Sonra bir açık küme ayracı (`{`) veya bir kapanış küme ayracını önce (`}`). Örneğin:

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    Daha fazla bilgi için [nesne başlatıcıları: adlandırılmış ve anonim türler](./objects-and-classes/object-initializers-named-and-anonymous-types.md) veya [koleksiyon başlatıcıları](./collection-initializers/index.md).

- Sonra açık bir gömülü ifade (`<%=`) veya bir katıştırılmış deyim bitiminden önce (`%>`) içinde bir XML değişmez değeri. Örneğin:

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   Daha fazla bilgi için [XML'de katıştırılmış ifadeler](./xml/embedded-expressions-in-xml.md).

- Birleştirme işleci sonra (`&`). Örneğin:

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   Daha fazla bilgi için [işleçleri listelenir işlevselliğe göre](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Atama İşleçleri sonra (`=`, `&=`, `:=`, `+=`, `-=`, `*=`, `/=`, `\=`, `^=`, `<<=`, `>>=`). Örneğin:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Daha fazla bilgi için [işleçleri listelenir işlevselliğe göre](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- İkili işleçler sonra (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`, `Like`, `Xor`) içinde bir ifade. Örneğin:

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   Daha fazla bilgi için [işleçleri listelenir işlevselliğe göre](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Sonra `Is` ve `IsNot` işleçleri. Örneğin:

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   Daha fazla bilgi için [işleçleri listelenir işlevselliğe göre](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Bir üye niteleyicisi karakterinden sonraki (`.`) ve üye adından önce. Örneğin:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Ancak, bir satır devamlılığı karakteri içermelidir (`_`) kullanıldığında bir üye niteleyicisi karakterinden `With` deyimi veya bir tür için başlatma listesindeki değerlerin sağlama. Atama işlecinden sonra satır sonu göz önünde bulundurun (örneğin, `=`) kullanırken `With` deyimleri ya da nesne başlatma listeler. Örneğin:

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   Daha fazla bilgi için [ile... End With deyimi](../../../visual-basic/language-reference/statements/with-end-with-statement.md) veya [nesne başlatıcıları: adlandırılmış ve anonim türler](./objects-and-classes/object-initializers-named-and-anonymous-types.md).

- Bir XML eksen özellik niteleyicisi sonra (`.` veya `.@` veya `...`). Ancak, bir satır devamlılığı karakteri içermelidir (`_`) belirttiğinizde üye niteleyicisi kullanırken `With` anahtar sözcüğü. Örneğin:

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   Daha fazla bilgi için [XML eksen özellikleri](../../../visual-basic/language-reference/xml-axis/index.md).

- Daha az sonra-işareti (<) veya daha büyük bir önce-işareti (`>`) belirttiğinizde bir öznitelik. Ayrıca sonra bir büyük-işareti (`>`) belirttiğinizde bir öznitelik. Ancak, bir satır devamlılığı karakteri içermelidir (`_`) belirttiğinizde derleme düzeyi veya modül düzeyinde öznitelikler. Örneğin:

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   Daha fazla bilgi için [öznitelikler genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md).

- Sorgu işleçlerden önce ve sonra (`Aggregate`, `Distinct`, `From`, `Group By`, `Group Join`, `Join`, `Let`, `Order By`, `Select`, `Skip`, `Skip While`, `Take`, `Take While`, `Where`, `In`, `Into`, `On`, `Ascending`, ve `Descending`). Birden çok anahtar sözcükleri yapılan sorgu işleçlerinin anahtar sözcükleri arasına bir satır sonu olamaz (`Order By`, `Group Join`, `Take While`, ve `Skip While`). Örneğin:

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   Daha fazla bilgi için [sorguları](../../../visual-basic/language-reference/queries/index.md).

- Sonra `In` anahtar sözcüğü bir `For Each` deyimi. Örneğin:

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   Nesne, salt okunur.[For Each...Next Deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md)

- Sonra `From` bir koleksiyon başlatıcısında anahtar sözcüğü. Örneğin:

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   Daha fazla bilgi için [koleksiyon başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

## <a name="adding-comments"></a>Açıklama ekleme

Kaynak kodu her zaman bile yazdığı Programcı açıklayıcı değil. Kodlarını belge yardımcı olmak için bu nedenle, Yorumlar embedded serbest ayraç kullanımı çoğu programcılar olun. Kod açıklamaları bir yordam ya da belirli bir yönerge herkese okuma veya daha sonra Bununla çalışmaya açıklayabilir. Visual Basic, derleme sırasında açıklamaları yok sayar ve derlenmiş kodu etkilemez.

Açıklama satırı tırnak işaretiyle başlar (`'`) veya `REM` ardından bir boşluk. Bunlar herhangi bir kod içinde dışında bir dizede eklenebilir. Bir deyim için bir açıklama eklemek için kesme işareti ekleyin veya `REM` ve ardından yorumun deyimi sonra. Açıklamalar, ayrıca kendi ayrı bir satıra gidebilirsiniz. Aşağıdaki örnek bu olasılıklar gösterilmektedir.

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a>Derleme hataları denetleniyor

Sonra bir satırlık bir kod yazarsanız, satır (hata iletisi de görünebilir) dalgalı mavi bir çizgi görüntülenir, ifadede sözdizimi hatası var. (Görev listesinde arama veya fare işaretçisi hatasıyla üzerine gelin ve hata iletisini okuyarak) deyimiyle nerede olduğunu bulmak ve düzeltmek için gerekir. Kodunuzda tüm söz dizimi hataları düzelttik kadar programınızı doğru şekilde derlenmesi başarısız olur.

## <a name="related-sections"></a>İlgili bölümler

|Terim|Tanım|
|---|---|
|[Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)|Atama İşleçleri gibi kapsayan dil başvurusu sayfalara bağlantılar sağlar `=`, `*=`, ve `&=`.|
|[İşleçler ve İfadeler](./operators-and-expressions/index.md)|Öğelerinin yeni değerleri yield işleçlerle nasıl birleştirileceğini gösterir.|
|[Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|Tek bir deyimde birden çok çizgiye bölün ve aynı satırda birden çok deyim koyun gösterir.|
|[Nasıl yapılır: Etiket Deyimleri](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|Bir kod satırı etiket gösterilmektedir.|
