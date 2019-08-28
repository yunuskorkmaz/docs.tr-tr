---
title: For Each...Next Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ForEach
- vb.ForEachNext
- vb.Each
- ForEachNext
helpviewer_keywords:
- infinite loops
- Next statement [Visual Basic], For Each...Next
- endless loops
- loop structures [Visual Basic], For Each...Next
- loops, endless
- Each keyword [Visual Basic]
- instructions, repeating
- For Each statement [Visual Basic]
- collections, instruction repetition
- loops, infinite
- For Each...Next statements
- For keyword [Visual Basic], For Each...Next statements
- Exit statement [Visual Basic], For Each...Next statements
- iteration
ms.assetid: ebce3120-95c3-42b1-b70b-fa7da40c75e2
ms.openlocfilehash: ebfd05a39c290e379bea2b925e7ea30c40d303fe
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046311"
---
# <a name="for-eachnext-statement-visual-basic"></a>For Each...Next Deyimi (Visual Basic)

Bir koleksiyondaki her öğe için bir deyim grubunu yineler.

## <a name="syntax"></a>Sözdizimi

```
For Each element [ As datatype ] In group
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ element ]
```

## <a name="parts"></a>Bölümler

|Terim|Tanım|
|---|---|
|`element`|`For Each` İfadesinde gereklidir. `Next` Deyimde isteğe bağlı. Değişken. Koleksiyonun öğeleri arasında yineleme yapmak için kullanılır.|
|`datatype`|Açık ise (varsayılan) veya `element` `Option Infer` zaten bildirilirse, isteğe bağlıdır; kapalıysa ve `element` önceden bildirilmemiş olması gerekir. [`Option Infer`](option-infer-statement.md) Veri türü `element`.|
|`group`|Gerekli. Bir koleksiyon türü veya nesne olan türü olan bir değişken. Tekrarlanması gereken koleksiyona `statements` başvurur.|
|`statements`|İsteğe bağlı. İçindeki ve `For Each` `Next` içindeki heröğeiçinçalışanarasındabirveyadahafazladeyim.`group`|
|`Continue For`|İsteğe bağlı. Denetimi `For Each` döngünün başlangıcına aktarır.|
|`Exit For`|İsteğe bağlı. Denetimi `For Each` döngünün dışına aktarır.|
|`Next`|Gerekli. `For Each` Döngünün tanımını sonlandırır.|

## <a name="simple-example"></a>Basit örnek

Şunu kullan `For Each`... `Next` bir koleksiyonun ya da dizinin her öğesi için bir deyim kümesini yinelemek istediğinizde Loop.

> [!TIP]
> [İçin A... Sonraki Ifade](../../../visual-basic/language-reference/statements/for-next-statement.md) , bir döngünün her yinelemesini bir denetim değişkeniyle ilişkilendirebileceğiniz ve değişkenin ilk ve son değerlerini belirleyebileceğiniz zaman iyi şekilde kullanılır. Bununla birlikte, bir koleksiyonla ilgilendiğinizde, ilk ve son değer kavramı anlamlı değildir ve koleksiyonun kaç öğe olduğunu bilmeniz gerekmez. Bu tür bir durumda, a `For Each`... `Next` döngü genellikle daha iyi bir seçenektir.

Aşağıdaki örnekte, `For Each`...`Next` ifade, bir liste koleksiyonunun tüm öğeleri boyunca yinelenir.

[!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]

Daha fazla örnek için bkz. [koleksiyonlar](../../../standard/collections/index.md) ve [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).

## <a name="nested-loops"></a>İç içe döngüler

Bir döngüyü diğerinin `For Each` içine yerleştirerek döngüleri iç içe geçirebilirsiniz.

Aşağıdaki örnek iç içe geçmiş `For Each`...`Next` yapıları.

[!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]

Döngüleri iç içe aktardığınızda her döngünün benzersiz `element` bir değişkeni olmalıdır.

Ayrıca, farklı türlerde denetim yapılarını birbirleriyle iç içe geçirebilirsiniz. Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>İçin çık ve devam et

[Exit for](../../../visual-basic/language-reference/statements/exit-statement.md) deyimleri yürütmenin uygulamadan çıkmasına `For`neden olur...`Next` öğesini Loop ve `Next` deyimden sonraki deyime aktarır.

`Continue For` İfade, denetimi döngünün bir sonraki yinelemesine hemen aktarır. Daha fazla bilgi için bkz. [Continue bildirisi](../../../visual-basic/language-reference/statements/continue-statement.md).

Aşağıdaki örnek, `Continue For` ve `Exit For` deyimlerinin nasıl kullanılacağını göstermektedir.

[!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]

Bir döngüye herhangi bir `Exit For` `For Each` sayıda deyim yerleştirebilirsiniz. İç içe `For Each` `Exit For` döngüler içinde kullanıldığında yürütmenin en içteki döngüden çıkmasına ve denetimi bir sonraki daha yüksek iç içe geçme düzeyine aktarmasına neden olur.

`Exit For`genellikle bir koşul değerlendirmesinden sonra, örneğin bir `If`... `Then`... `Else` yapısı. Aşağıdaki koşullar için kullanmak `Exit For` isteyebilirsiniz:

- Tekrarlamaya devam etmek gereksiz veya imkansız. Bunun nedeni hatalı bir değer veya sonlandırma isteği olabilir.

- Bir `Try`özel durum içinde yakalandı... `Catch`... `Finally`. Bloğunun`Finally` sonunda kullanabilirsiniz `Exit For` .

- Sonsuz bir döngü vardır. Bu bir döngü, büyük veya hatta sonsuz bir sayı çalıştırabilir. Böyle bir koşulu tespit ediyorsanız, döngüyü atlamak için kullanabilirsiniz `Exit For` . Daha fazla bilgi için bkz [. do... Loop deyimleri](../../../visual-basic/language-reference/statements/do-loop-statement.md).

## <a name="iterators"></a>Yineleyiciler

Bir koleksiyon üzerinde özel bir yineleme gerçekleştirmek için bir *Yineleyici* kullanırsınız. Yineleyici bir işlev veya `Get` erişimci olabilir. Tek seferde koleksiyonun `Yield` her bir öğesini döndürmek için bir ifade kullanır.

Bir `For Each...Next` ifadeyi kullanarak bir yineleyici çağırın. `For Each` Döngünün her yinelemesi yineleyiciyi çağırır. Yineleyiciden bir `Yield` ifadeye ulaşıldığında, `Yield` deyimdeki ifade döndürülür ve koddaki geçerli konum korunur. Bu konumdan, yineleyici bir sonraki sefer çağrıldığında yürütme yeniden başlatılır.

Aşağıdaki örnek bir yineleyici işlevi kullanır. Yineleyici işlevinin, için içindeki `Yield` bir ifade vardır [... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü. Yönteminde, `For Each` ifade gövdesinin her yinelemesi bir sonraki `Yield` ifadeye devam eden Yineleyici işlevine bir çağrı oluşturur. `ListEvenNumbers`

[!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]

Daha fazla bilgi için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md), [yield ekstresi](../../../visual-basic/language-reference/statements/yield-statement.md)ve [Yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md).

## <a name="technical-implementation"></a>Teknik Uygulama

Bir `For Each`...`Next` deyimin çalışması Visual Basic, döngü başlamadan önce koleksiyonu yalnızca bir kez değerlendirir. Deyiminiz değişiklikleri veya `group`değişiklik `element` engelleriyorsa, bu değişiklikler döngünün yinelemesini etkilemez.

Koleksiyondaki tüm öğeler üzerinde kapsamlı olarak `element`atandığında `For Each` , döngü duraklar ve `Next` deyimden sonraki deyime geçer.

[Seçenek çıkarımı](option-infer-statement.md) açık ise (varsayılan ayarı) Visual Basic derleyici, veri türünü `element`çıkarsalabilir. Kapalıysa ve `element` döngü dışında bildirilmediyse, bunu `For Each` bildiriminde bildirmeniz gerekir. `element` Açıkça veri türünü bildirmek için bir `As` yan tümce kullanın. Öğe veri türü `For Each`... dışında tanımlanmamışsa `Next` yapı, kapsamı döngünün gövdesidir. Döngüsünün dışında ve içinde bildiremezsiniz `element` .

İsteğe bağlı olarak `element` `Next` deyimde belirtebilirsiniz. Bu, özellikle iç içe `For Each` döngüler varsa programınızın okunabilirliğini geliştirir. Karşılık gelen `For Each` ifadede görünen değişkenle aynı değişkeni belirtmeniz gerekir.

Bir döngünün `element` içindeki değerini değiştirmeyi önlemek isteyebilirsiniz. Bunu yapmak, kodunuzun okunmasını ve hata ayıklamasını daha zor hale getirir. Değerini `group` değiştirmek, döngü ilk kez girildiğinde belirlenen koleksiyonu veya öğelerini etkilemez.

Döngüleri iç içe aktardığınızda, iç düzeyden `Next` `Next` önce bir dış iç içe düzeyi ifadesine karşılaşılırsa, derleyici bir hata bildirir. Ancak, derleyici bu çakışan hatayı yalnızca her `element` `Next` ifadede belirtirseniz tespit edebilir.

Kodunuz belirli bir sırada bir koleksiyonun geçiş yöntemine bağımlıysa, a `For Each`... `Next` toplama, koleksiyonun sunduğu Numaralandırıcı nesnesinin özelliklerini bilmiyorsanız en iyi seçim değildir. Çapraz geçiş sırası Visual Basic, ancak Numaralandırıcı nesnesinin <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemine göre belirlenir. Bu nedenle, koleksiyonda hangi öğenin döndürüleceğini `element`veya belirli bir öğeden sonra döndürülecek bir sonraki olduğunu tahmin edemeyebilirsiniz. Farklı bir döngü yapısı (örneğin, `For`) kullanarak daha güvenilir sonuçlar elde edebilirsiniz... ya da`Do`... `Next` `Loop`.

Çalışma zamanının içindeki öğeleri ' `group` `element`a dönüştürebilmelidir. [`Option Strict`] İfadesinde, hem genişletme hem de daraltma dönüştürmelerine izin verilip verilmeyeceğini`Option Strict` (kapalı, varsayılan değeri) veya yalnızca genişletme dönüştürmelerine izin verilip verilmeyeceğini (`Option Strict` açık olduğunu) denetler. Daha fazla bilgi için bkz. [daraltma dönüştürmeleri](#narrowing-conversions).

Veri türü `group` , bir koleksiyona veya Numaralandırılabilir bir diziye başvuran bir başvuru türü olmalıdır. `group` En yaygın olarak bu, `System.Collections` ad alanının <xref:System.Collections.IEnumerable> arabirimini veya <xref:System.Collections.Generic.IEnumerable%601> `System.Collections.Generic` ad alanının arabirimini uygulayan bir nesneye başvurur. `System.Collections.IEnumerable`koleksiyon için bir Numaralandırıcı nesnesi döndüren yönteminitanımlar.<xref:System.Collections.IEnumerable.GetEnumerator%2A> Numaralandırıcı nesnesi `System.Collections.IEnumerator` `System.Collections` ad alanı arabirimini uygular ve <xref:System.Collections.IEnumerator.Current%2A> özelliğini ve <xref:System.Collections.IEnumerator.Reset%2A> ve <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemlerini gösterir. Visual Basic, koleksiyonu çapraz geçirmek için bunları kullanır.

### <a name="narrowing-conversions"></a>Daraltma dönüştürmeleri

Ne `Option Strict` zaman`On`ayarlandığında, daraltma dönüştürmeleri normalde derleyici hatalarına neden olur. Ancak, `group` '`element` deki öğelerinden dönüşümler, çalışma zamanında değerlendirilir ve gerçekleştirilir ve daraltma dönüştürmelerinden kaynaklanan derleyici hataları bastırılır. `For Each`

Aşağıdaki örnekte, ' a `m` `Option Strict` `n` `Long`'a dönüştürmebirdaraltmadönüştürmesiolduğundan,içinbaşlangıçdeğeriolarakatama,tarihindederlemeyapmaz.`Integer` Ancak,, öğesine `number` atama, ' den `Long` `Integer`' e aynı dönüştürmeyi gerektirse de, hiçbir derleyici hatası raporlanır. `For Each` Büyük bir sayı içeren <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> ifadede,büyüksayıyauygulandığındabirçalışmazamanıhatasıoluşur.`For Each`

[!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]

### <a name="ienumerator-calls"></a>IEnumerator çağrıları

Bir `For Each`... döngü başlar, geçerli bir koleksiyon `group` nesnesine başvuran Visual Basic doğrular. `Next` Aksi takdirde, bir özel durum oluşturur. Aksi takdirde, ilk öğeyi <xref:System.Collections.IEnumerator.MoveNext%2A> döndürmek için yöntemini <xref:System.Collections.IEnumerator.Current%2A> ve Numaralandırıcı nesnesinin özelliğini çağırır. Eğer `MoveNext` bir sonraki öğe olmadığını gösteriyorsa, diğer bir deyişle, koleksiyon boşsa `For Each` , döngü duraklar ve denetimi `Next` deyimden sonraki ifadeye geçirir. Aksi takdirde, Visual Basic `element` ilk öğesine ayarlar ve ekstre bloğunu çalıştırır.

Her Visual Basic `Next` deyimle karşılaştığında, `For Each` ifadeye geri döner. Yeniden çağırır `MoveNext` ve `Current` bir sonraki öğesini döndürür ve sonra da bloğu çalıştırır veya sonuca bağlı olarak döngüyü sonlandırır. Bu işlem, bir `MoveNext` sonraki öğe veya bir `Exit For` deyimin karşılaştığı anlamına gelene kadar devam eder.

**Koleksiyonu değiştirme.** <xref:System.Collections.IEnumerable.GetEnumerator%2A> Normal olarak döndürülen Numaralandırıcı nesnesi herhangi bir öğeyi ekleyerek, silerek, değiştirerek veya yeniden sıralayarak koleksiyonu değiştirmenize izin vermez. Öğesini başlattıktan sonra `For Each`koleksiyonu değiştirirseniz... döngü, Numaralandırıcı nesnesi geçersiz hale gelir ve bir sonraki erişim denemesi <xref:System.InvalidOperationException> özel duruma neden olur. `Next`

Ancak, bu değişikliğin engellenmesi Visual Basic tarafından belirlenir, ancak bunun yerine <xref:System.Collections.IEnumerable> arabirimin uygulanması. Yineleme sırasında değişikliklere izin veren `IEnumerable` bir şekilde uygulanması mümkündür. Bu tür dinamik değişikliği yapmayı düşünüyorsanız, kullanmakta olduğunuz koleksiyonda `IEnumerable` uygulamanın özelliklerini anladığınızdan emin olun.

**Koleksiyon öğelerini değiştirme.** Numaralandırıcı nesnesinin özelliği salt okunur ve her koleksiyon öğesinin yerel bir kopyasını döndürür. [](../../../visual-basic/language-reference/modifiers/readonly.md) <xref:System.Collections.IEnumerator.Current%2A> Bu, öğeleri bir `For Each`... içinde değiştiremeyeceğiniz anlamına gelir. `Next` Loop. Yaptığınız herhangi bir değişiklik yalnızca yerel kopyayı `Current` etkiler ve temel koleksiyona geri yansıtılmaz. Ancak, bir öğe bir başvuru türü ise, gösterdiği örnek üyelerini değiştirebilirsiniz. Aşağıdaki örnek her `thisControl` bir öğenin `BackColor` üyesini değiştirir. Ancak, kendisini değiştiremezsiniz `thisControl` .

```vb
Sub lightBlueBackground(ByVal thisForm As System.Windows.Forms.Form)
    For Each thisControl As System.Windows.Forms.Control In thisForm.Controls
        thisControl.BackColor = System.Drawing.Color.LightBlue
    Next thisControl
End Sub
```

Önceki örnek, kendisini değiştiremese `BackColor` `thisControl` de, her `thisControl` öğenin üyesini değiştirebilir.

**Dizileri geçme.** Sınıfı arabirimini uyguladığından, tüm diziler yöntemini kullanıma sunar. <xref:System.Array.GetEnumerator%2A> <xref:System.Array> <xref:System.Collections.IEnumerable> Bu, bir dizi içinde bir `For Each`... ile yineleyebilir olabileceği anlamına gelir. `Next` Loop. Ancak, yalnızca dizi öğelerini okuyabilirsiniz. Bunları değiştiremezsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, C:\ içindeki tüm klasörleri listeler. <xref:System.IO.DirectoryInfo> sınıfını kullanarak dizin.

[!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]

## <a name="example"></a>Örnek

Aşağıdaki örnek bir koleksiyonu sıralamak için bir yordam gösterir. Örnek, `Car` <xref:System.Collections.Generic.List%601>içinde depolanan bir sınıfın örneklerini sıralar. Sınıfı, <xref:System.IComparable%601.CompareTo%2A> yönteminin uygulanması <xref:System.IComparable%601> için arabirimini uygular. `Car`

Yöntemine yapılan her çağrı <xref:System.IComparable%601.CompareTo%2A> , sıralama için kullanılan tek bir karşılaştırma yapar. `CompareTo` Yöntemdeki Kullanıcı tarafından yazılan kod, geçerli nesnenin her bir karşılaştırması için başka bir nesneyle ilgili bir değer döndürür. Geçerli nesne diğer nesneden daha küçükse döndürülen değer sıfırdan küçük, geçerli nesne diğer nesneden büyükse sıfırdan büyük ve eşitse sıfır. Bu, büyük, küçüktür ve eşittir ölçütlerine göre kod içinde tanımlamanızı sağlar.

`ListCars` Yönteminde`cars.Sort()` , ifade listeyi sıralar. <xref:System.Collections.Generic.List%601.Sort%2A> `CompareTo` Öğesininyöntemine`Car` yapılan bu çağrı, yönteminin içindeki `List`nesneler için otomatik olarak çağrılmasına neden olur. <xref:System.Collections.Generic.List%601>

[!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyonlar](../../../standard/collections/index.md)
- [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Döngü Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While Deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop Deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Öğe Başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md)
