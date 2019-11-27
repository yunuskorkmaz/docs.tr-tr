---
title: For Each...Next Deyimi
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
ms.openlocfilehash: 572f1efc0148bd8df4f13fa5651e74249caa45a7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351202"
---
# <a name="for-eachnext-statement-visual-basic"></a>For Each...Next Deyimi (Visual Basic)

Bir koleksiyondaki her öğe için bir deyim grubunu yineler.

## <a name="syntax"></a>Sözdizimi

```vb
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
|`element`|`For Each` bildiriminde gereklidir. `Next` bildiriminde isteğe bağlı. Değişken. Koleksiyonun öğeleri arasında yineleme yapmak için kullanılır.|
|`datatype`|[`Option Infer`](option-infer-statement.md) açık (varsayılan) veya `element` zaten bildirilirse, isteğe bağlıdır; `Option Infer` kapalıysa ve `element` önceden bildirilmemiş olması gerekir. `element`veri türü.|
|`group`|Gerekli. Bir koleksiyon türü veya nesne olan türü olan bir değişken. `statements` tekrarlanması gereken koleksiyona başvurur.|
|`statements`|İsteğe bağlı. `group`içindeki her öğe üzerinde çalışan `For Each` ve `Next` arasında bir veya daha fazla deyim.|
|`Continue For`|İsteğe bağlı. Denetimi `For Each` döngüsünün başlangıcına aktarır.|
|`Exit For`|İsteğe bağlı. `For Each` döngüsünün dışına denetimini aktarır.|
|`Next`|Gerekli. `For Each` döngüsünün tanımını sonlandırır.|

## <a name="simple-example"></a>Basit örnek

Bir koleksiyon veya dizinin her öğesi için bir deyim kümesini yinelemek istediğinizde bir `For Each`...`Next` döngüsü kullanın.

> [!TIP]
> [İçin A... Sonraki Ifade](../../../visual-basic/language-reference/statements/for-next-statement.md) , bir döngünün her yinelemesini bir denetim değişkeniyle ilişkilendirebileceğiniz ve değişkenin ilk ve son değerlerini belirleyebileceğiniz zaman iyi şekilde kullanılır. Bununla birlikte, bir koleksiyonla ilgilendiğinizde, ilk ve son değer kavramı anlamlı değildir ve koleksiyonun kaç öğe olduğunu bilmeniz gerekmez. Bu tür bir durumda, bir `For Each`...`Next` döngüsü genellikle daha iyi bir seçimdir.

Aşağıdaki örnekte `For Each`...`Next` ifade, bir liste koleksiyonunun tüm öğeleri boyunca yinelenir.

[!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]

Daha fazla örnek için bkz. [koleksiyonlar](../../../standard/collections/index.md) ve [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).

## <a name="nested-loops"></a>İç içe döngüler

Bir döngüyü diğerinin içine yerleştirerek `For Each` döngüleri iç içe geçirebilirsiniz.

Aşağıdaki örnek iç içe `For Each`gösterir...`Next` Yapıları.

[!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]

Döngüleri iç içe aktardığınızda her döngünün benzersiz bir `element` değişkeni olmalıdır.

Ayrıca, farklı türlerde denetim yapılarını birbirleriyle iç içe geçirebilirsiniz. Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>İçin çık ve devam et

[Exit for](../../../visual-basic/language-reference/statements/exit-statement.md) deyimleri yürütmenin `For`çıkmasına neden olur...`Next` `Next` deyimlerini izleyen deyime döngü ve denetim aktarır.

`Continue For` bildiri, denetimi döngünün bir sonraki yinelemesine hemen aktarır. Daha fazla bilgi için bkz. [Continue bildirisi](../../../visual-basic/language-reference/statements/continue-statement.md).

Aşağıdaki örnek, `Continue For` ve `Exit For` deyimlerinin nasıl kullanılacağını gösterir.

[!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]

Bir `For Each` döngüsünde istediğiniz sayıda `Exit For` deyimi koyabilirsiniz. İç içe geçmiş `For Each` döngüleri içinde kullanıldığında, `Exit For` yürütmenin en içteki döngüden çıkmasına ve denetimi bir sonraki daha yüksek iç içe geçme düzeyine aktarmasına neden olur.

`Exit For`, örneğin bir `If`...`Then`...`Else` yapısı gibi bazı koşulların değerlendirilmesinden sonra kullanılır. Aşağıdaki koşullarda `Exit For` kullanmak isteyebilirsiniz:

- Tekrarlamaya devam etmek gereksiz veya imkansız. Bunun nedeni hatalı bir değer veya sonlandırma isteği olabilir.

- `Try`...`Catch`...`Finally`bir özel durum yakalandı. `Finally` bloğunun sonunda `Exit For` kullanabilirsiniz.

- Sonsuz bir döngü vardır. Bu bir döngü, büyük veya hatta sonsuz bir sayı çalıştırabilir. Böyle bir koşulu tespit ediyorsanız, döngüden çıkmak için `Exit For` kullanabilirsiniz. Daha fazla bilgi için bkz [. do... Loop deyimleri](../../../visual-basic/language-reference/statements/do-loop-statement.md).

## <a name="iterators"></a>Yineleyiciler

Bir koleksiyon üzerinde özel bir yineleme gerçekleştirmek için bir *Yineleyici* kullanırsınız. Yineleyici bir işlev veya `Get` erişimcisi olabilir. Tek seferde koleksiyonun her bir öğesini döndürmek için bir `Yield` ifadesini kullanır.

Bir `For Each...Next` ifadesini kullanarak bir yineleyici çağırın. `For Each` döngüsünün her yinelemesi yineleyiciyi çağırır. Yineleyiciye bir `Yield` deyimine ulaşıldığında, `Yield` deyimindeki ifade döndürülür ve koddaki geçerli konum korunur. Bu konumdan, yineleyici bir sonraki sefer çağrıldığında yürütme yeniden başlatılır.

Aşağıdaki örnek bir yineleyici işlevi kullanır. Yineleyici işlevi bir for... içindeki bir `Yield` bildirimine sahiptir [... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü. `ListEvenNumbers` yönteminde, `For Each` deyimin gövdesinin her yinelemesi, bir sonraki `Yield` ifadesine devam eden Yineleyici işlevine bir çağrı oluşturur.

[!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]

Daha fazla bilgi için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md), [yield ekstresi](../../../visual-basic/language-reference/statements/yield-statement.md)ve [Yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md).

## <a name="technical-implementation"></a>Teknik Uygulama

Bir `For Each`...`Next` deyimin çalışması Visual Basic, döngü başlamadan önce koleksiyonu yalnızca bir kez değerlendirir. Deyiminiz `element` veya `group`değişiklikleri engelleriyorsa, bu değişiklikler döngünün yinelemesini etkilemez.

Koleksiyondaki tüm öğeler `element`için tamamen atandığında, `For Each` döngüsü duraklar ve `Next` deyimlerinden sonraki deyime geçer.

[Seçenek çıkarımı](option-infer-statement.md) açık ise (varsayılan ayarı) Visual Basic derleyici `element`veri türünü çıkarabilir. Kapalı ve `element` döngü dışında bildirilmediyse, bunu `For Each` bildiriminde bildirmeniz gerekir. `element` veri türünü açıkça bildirmek için bir `As` yan tümcesi kullanın. Öğe veri türü `For Each`...`Next` yapısı dışında tanımlanmamışsa, kapsamı döngünün gövdesidir. Hem döngünün dışında hem de içinde `element` bildiremezsiniz.

İsteğe bağlı olarak `Next` bildiriminde `element` belirtebilirsiniz. Bu, özellikle iç içe geçmiş `For Each` döngülerine sahipseniz programınızın okunabilirliğini geliştirir. Karşılık gelen `For Each` ifadesinde görünen değişkenle aynı değişkeni belirtmeniz gerekir.

Bir döngü içindeki `element` değerini değiştirmeyi önlemek isteyebilirsiniz. Bunu yapmak, kodunuzun okunmasını ve hata ayıklamasını daha zor hale getirir. `group` değerini değiştirmek, döngü ilk kez girildiğinde belirlenen koleksiyonu veya öğelerini etkilemez.

Döngüleri iç içe aktardığınızda, iç düzey `Next` önce bir dış iç içe düzeyi `Next` bildirimine karşılaşılırsa, derleyici bir hata bildirir. Ancak, derleyici yalnızca her `Next` bildiriminde `element` belirtirseniz bu çakışan hatayı algılayabilir.

Kodunuz belirli bir sırada bir koleksiyonun geçiş yöntemine bağımlıysa, koleksiyonun sunduğu Numaralandırıcı nesnesinin özelliklerini bilmiyorsanız, bir `For Each`...`Next` döngüsü en iyi seçenektir. Çapraz geçiş sırası Visual Basic tarafından belirlenir, ancak Numaralandırıcı nesnesinin <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi. Bu nedenle, koleksiyonun hangi öğesi `element`döndürüldüğünden veya belirli bir öğeden sonra döndürülecek bir sonraki bir öğe olduğunu tahmin edemeyebilirsiniz. `For`...`Next` veya `Do`...`Loop`gibi farklı bir döngü yapısı kullanarak daha güvenilir sonuçlar elde edebilirsiniz.

Çalışma zamanının `group` öğeleri `element`dönüştürebilmelidir. [`Option Strict`] ifadesinde, hem genişletme hem de daraltma dönüştürmelerine izin verilip verilmeyeceğini (`Option Strict` kapalı, varsayılan değeri) veya yalnızca genişletme dönüştürmelerine izin verilip verilmeyeceğini (`Option Strict` açık olduğunu) denetler. Daha fazla bilgi için bkz. [daraltma dönüştürmeleri](#narrowing-conversions).

`group` veri türü, bir koleksiyona veya Numaralandırılabilir bir diziye başvuran bir başvuru türü olmalıdır. En yaygın olarak bu `group`, `System.Collections` ad alanının <xref:System.Collections.IEnumerable> arabirimini veya `System.Collections.Generic` ad alanının <xref:System.Collections.Generic.IEnumerable%601> arabirimini uygulayan bir nesne anlamına gelir. `System.Collections.IEnumerable`, koleksiyon için bir Numaralandırıcı nesnesi döndüren <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemini tanımlar. Numaralandırıcı nesnesi `System.Collections` ad alanının `System.Collections.IEnumerator` arabirimini uygular ve <xref:System.Collections.IEnumerator.Current%2A> özelliğini ve <xref:System.Collections.IEnumerator.Reset%2A> ve <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemlerini gösterir. Visual Basic, koleksiyonu çapraz geçirmek için bunları kullanır.

### <a name="narrowing-conversions"></a>Daraltma dönüştürmeleri

`Option Strict` `On`olarak ayarlandığında, daraltma dönüştürmeleri normalde derleyici hatalarına neden olur. Ancak, bir `For Each` ifadesinde, `group` öğeden `element` 'e dönüştürme işlemleri değerlendirilir ve çalışma zamanında gerçekleştirilir ve daraltma dönüştürmelerinden kaynaklanan derleyici hataları bastırılır.

Aşağıdaki örnekte, bir `Integer` `Long` dönüştürmesi bir daraltma dönüştürmesi olduğundan, `n` başlangıç değeri olarak `m` atama `Option Strict` açık olduğunda derlenmez. Ancak `For Each` ifadesinde, `number` atama `Long` aynı dönüştürmeyi `Integer`için aynı olsa bile derleyici hatası bildirilmemiştir. Büyük bir sayı içeren `For Each` bildiriminde, <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> büyük sayıya uygulandığında bir çalışma zamanı hatası oluşur.

[!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]

### <a name="ienumerator-calls"></a>IEnumerator çağrıları

`For Each`...`Next` döngüsünün yürütülmesi başladığında Visual Basic `group` geçerli bir koleksiyon nesnesine başvurduğunu doğrular. Aksi takdirde, bir özel durum oluşturur. Aksi takdirde, ilk öğeyi döndürmek için <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemini ve Numaralandırıcı nesnesinin <xref:System.Collections.IEnumerator.Current%2A> özelliğini çağırır. `MoveNext`, Next öğesi olmadığını gösteriyorsa, yani koleksiyon boşsa, `For Each` döngüsü duraklar ve denetim, `Next` deyimlerinden sonraki deyime geçer. Aksi takdirde, Visual Basic `element` ilk öğeye ayarlar ve ekstre bloğunu çalıştırır.

Her Visual Basic `Next` bildirimiyle karşılaştığında `For Each` bildirimine geri döner. Daha sonra, bir sonraki öğeyi döndürmek için `MoveNext` ve `Current` çağırır ve sonra bloğu çalıştırır ya da sonuca bağlı olarak döngüyü sonlandırır. Bu işlem, `MoveNext` sonraki öğe olmadığını veya bir `Exit For` ifadesiyle karşılaşılana kadar devam eder.

**Koleksiyonu değiştirme.** <xref:System.Collections.IEnumerable.GetEnumerator%2A> tarafından döndürülen Numaralandırıcı nesnesi, herhangi bir öğeyi ekleyerek, silerek, değiştirerek veya yeniden sıralayarak koleksiyonu değiştirmenize izin vermez. `For Each`...`Next` döngüsünü başlattıktan sonra koleksiyonu değiştirirseniz, Numaralandırıcı nesnesi geçersiz hale gelir ve bir sonraki erişim girişimi bir <xref:System.InvalidOperationException> özel durumuna neden olur.

Ancak, bu değişikliğin engellenmesi Visual Basic tarafından belirlenir, ancak <xref:System.Collections.IEnumerable> arabiriminin uygulanması bunun yerine. `IEnumerable`, yineleme sırasında değişikliklere izin verecek şekilde uygulamak mümkündür. Bu tür dinamik değişikliği yapmayı düşünüyorsanız, kullanmakta olduğunuz koleksiyondaki `IEnumerable` uygulamasının özelliklerini anladığınızdan emin olun.

**Koleksiyon öğelerini değiştirme.** Numaralandırıcı nesnesinin <xref:System.Collections.IEnumerator.Current%2A> özelliği [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md)ve her koleksiyon öğesinin yerel bir kopyasını döndürür. Bu, öğeleri bir `For Each`...`Next` döngüsünde değiştiremeyeceğiniz anlamına gelir. Yaptığınız tüm değişiklikler yalnızca `Current` Yerel kopyayı etkiler ve temel alınan koleksiyona yansıtılmaz. Ancak, bir öğe bir başvuru türü ise, gösterdiği örnek üyelerini değiştirebilirsiniz. Aşağıdaki örnek her `thisControl` öğesinin `BackColor` üyesini değiştirir. Ancak, `thisControl` değiştiremezsiniz.

```vb
Sub LightBlueBackground(thisForm As System.Windows.Forms.Form)
    For Each thisControl In thisForm.Controls
        thisControl.BackColor = System.Drawing.Color.LightBlue
    Next thisControl
End Sub
```

Önceki örnek, `thisControl` değiştiremese de, her bir `thisControl` öğesinin `BackColor` üyesini değiştirebilir.

**Dizileri geçme.** <xref:System.Array> sınıfı <xref:System.Collections.IEnumerable> arabirimini gerçekleştirdiğinden, tüm diziler <xref:System.Array.GetEnumerator%2A> yöntemini kullanıma sunar. Yani, bir dizi boyunca `For Each`...`Next` döngüsü ile yineleyebilirsiniz. Ancak, yalnızca dizi öğelerini okuyabilirsiniz. Bunları değiştiremezsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, C:\ içindeki tüm klasörleri listeler. <xref:System.IO.DirectoryInfo> sınıfını kullanarak dizin.

[!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]

## <a name="example"></a>Örnek

Aşağıdaki örnek bir koleksiyonu sıralamak için bir yordam gösterir. Örnek, bir <xref:System.Collections.Generic.List%601>depolanan `Car` sınıfının örneklerini sıralar. `Car` sınıfı, <xref:System.IComparable%601.CompareTo%2A> yönteminin uygulanması için <xref:System.IComparable%601> arabirimini uygular.

<xref:System.IComparable%601.CompareTo%2A> yöntemine yapılan her çağrı, sıralama için kullanılan tek bir karşılaştırma yapar. `CompareTo` yönteminde Kullanıcı tarafından yazılan kod, geçerli nesnenin her karşılaştırması için başka bir nesneyle ilgili bir değer döndürür. Geçerli nesne diğer nesneden daha küçükse döndürülen değer sıfırdan küçük, geçerli nesne diğer nesneden büyükse sıfırdan büyük ve eşitse sıfır. Bu, büyük, küçüktür ve eşittir ölçütlerine göre kod içinde tanımlamanızı sağlar.

`ListCars` yönteminde, `cars.Sort()` ifade listeyi sıralar. <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.List%601.Sort%2A> yöntemine yapılan bu çağrı, `CompareTo` yönteminin `List``Car` nesneler için otomatik olarak çağrılmasına neden olur.

[!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyonlar](../../../standard/collections/index.md)
- [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Döngü Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While Deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop Deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Öğe Başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md)
