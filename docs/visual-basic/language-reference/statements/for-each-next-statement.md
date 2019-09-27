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
ms.openlocfilehash: f56e5defa2328011d222bfca05334b610e805055
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332782"
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
|`element`|@No__t-0 ifadesinde gereklidir. @No__t-0 ifadesinde isteğe bağlı. Değişken. Koleksiyonun öğeleri arasında yineleme yapmak için kullanılır.|
|`datatype`|[@No__t-1](option-infer-statement.md) varsa (varsayılan) veya `element` zaten bildirilirse, isteğe bağlıdır; `Option Infer` kapalıysa ve `element` zaten bildirilmemiş olması gerekir. @No__t-0 ' ın veri türü.|
|`group`|Gerekli. Bir koleksiyon türü veya nesne olan türü olan bir değişken. @No__t-0 ' ın tekrarlandığı koleksiyona başvurur.|
|`statements`|İsteğe bağlı. @No__t-0 ve `Next` arasında, `group` ' deki her öğede çalışan bir veya daha fazla deyim.|
|`Continue For`|İsteğe bağlı. Denetimi `For Each` döngüsünün başlangıcına aktarır.|
|`Exit For`|İsteğe bağlı. Denetimi `For Each` döngüsü dışına aktarır.|
|`Next`|Gerekli. @No__t-0 döngüsünün tanımını sonlandırır.|

## <a name="simple-example"></a>Basit örnek

Bir koleksiyon veya dizinin her öğesi için bir deyim kümesini yinelemek istediğinizde bir `For Each`... `Next` döngüsü kullanın.

> [!TIP]
> [İçin A... Sonraki Ifade](../../../visual-basic/language-reference/statements/for-next-statement.md) , bir döngünün her yinelemesini bir denetim değişkeniyle ilişkilendirebileceğiniz ve değişkenin ilk ve son değerlerini belirleyebileceğiniz zaman iyi şekilde kullanılır. Bununla birlikte, bir koleksiyonla ilgilendiğinizde, ilk ve son değer kavramı anlamlı değildir ve koleksiyonun kaç öğe olduğunu bilmeniz gerekmez. Bu tür bir durumda, `For Each`... `Next` döngüsü genellikle daha iyi bir seçimdir.

Aşağıdaki örnekte, `For Each`... `Next` ifade, bir liste koleksiyonunun tüm öğeleri boyunca yinelenir.

[!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]

Daha fazla örnek için bkz. [koleksiyonlar](../../../standard/collections/index.md) ve [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).

## <a name="nested-loops"></a>İç içe döngüler

Bir döngüyü diğerinin içine yerleştirerek `For Each` döngüleri iç içe geçirebilirsiniz.

Aşağıdaki örnek iç içe @no__t gösterir-0... `Next` yapıları.

[!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]

Döngüleri iç içe aktardığınızda her döngünün benzersiz bir `element` değişkeni olması gerekir.

Ayrıca, farklı türlerde denetim yapılarını birbirleriyle iç içe geçirebilirsiniz. Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>İçin çık ve devam et

[Exit for](../../../visual-basic/language-reference/statements/exit-statement.md) ifadesinin `For`... `Next` ' den çıkmasına neden olur `Next` ifadesini izleyen deyime döngü yapın ve denetimi aktarır.

@No__t-0 deyimleri, denetimi döngünün bir sonraki yinelemesine hemen aktarır. Daha fazla bilgi için bkz. [Continue bildirisi](../../../visual-basic/language-reference/statements/continue-statement.md).

Aşağıdaki örnek, `Continue For` ve `Exit For` deyimlerinin nasıl kullanılacağını gösterir.

[!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]

Bir `For Each` döngüsünde herhangi bir sayıda `Exit For` deyimi yerleştirebilirsiniz. İç içe `For Each` döngüleri içinde kullanıldığında, `Exit For` yürütmenin en içteki döngüden çıkmasına ve denetimi bir sonraki daha yüksek iç içe geçme düzeyine aktarmasına neden olur.

`Exit For` genellikle bazı koşulların değerlendirilmesinden sonra (örneğin, bir `If`... `Then`... `Else` yapısında) kullanılır. Aşağıdaki koşullarda `Exit For` kullanmak isteyebilirsiniz:

- Tekrarlamaya devam etmek gereksiz veya imkansız. Bunun nedeni hatalı bir değer veya sonlandırma isteği olabilir.

- @No__t-0... `Catch`... `Finally` ' de bir özel durum yakalandı. @No__t-1 bloğunun sonunda `Exit For` kullanabilirsiniz.

- Sonsuz bir döngü vardır. Bu bir döngü, büyük veya hatta sonsuz bir sayı çalıştırabilir. Böyle bir koşulu tespit ediyorsanız, döngüden çıkmak için `Exit For` kullanabilirsiniz. Daha fazla bilgi için bkz [. do... Loop deyimleri](../../../visual-basic/language-reference/statements/do-loop-statement.md).

## <a name="iterators"></a>Yineleyiciler

Bir koleksiyon üzerinde özel bir yineleme gerçekleştirmek için bir *Yineleyici* kullanırsınız. Yineleyici bir işlev veya `Get` erişimcisi olabilir. Tek seferde koleksiyonun her bir öğesini döndürmek için `Yield` ifadesini kullanır.

@No__t-0 ifadesini kullanarak bir yineleyici çağırın. @No__t-0 döngüsünün her yinelemesi yineleyiciyi çağırır. Yineleyiciye bir `Yield` deyimine ulaşıldığında, `Yield` deyimindeki ifade döndürülür ve koddaki geçerli konum korunur. Bu konumdan, yineleyici bir sonraki sefer çağrıldığında yürütme yeniden başlatılır.

Aşağıdaki örnek bir yineleyici işlevi kullanır. Yineleyici işlevi bir for... içindeki bir `Yield` bildirimine sahip [. Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü. @No__t-0 yönteminde, `For Each` ifade gövdesinin her yinelemesi, bir sonraki `Yield` ifadesine devam eden Yineleyici işlevine bir çağrı oluşturur.

[!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]

Daha fazla bilgi için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md), [yield ekstresi](../../../visual-basic/language-reference/statements/yield-statement.md)ve [Yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md).

## <a name="technical-implementation"></a>Teknik Uygulama

@No__t-0... `Next` deyimin çalışması Visual Basic, döngü başlamadan önce koleksiyonu yalnızca bir kez değerlendirir. Deyiminiz `element` veya `group` ' i değiştirirse, bu değişiklikler döngünün yinelemesini etkilemez.

Koleksiyondaki tüm öğeler `element` ' a tamamen atandığında, `For Each` döngüsü duraklar ve denetim, `Next` ifadesiyle sonraki deyime geçer.

[Seçenek çıkarımı](option-infer-statement.md) açık ise (varsayılan ayarı) Visual Basic derleyici `element` ' in veri türünü çıkarabilir. Kapalıysa ve `element` döngü dışında bildirilmemişse, bunu `For Each` ifadesinde bildirmeniz gerekir. @No__t-0 ' ın veri türünü açıkça bildirmek için bir `As` yan tümcesi kullanın. Öğe veri türü `For Each`... `Next` yapısı dışında tanımlanmamışsa, kapsamı döngünün gövdesidir. @No__t-0 ' ın hem döngünün dışında hem de içinde bildiremediğini unutmayın.

İsteğe bağlı olarak `Next` ifadesinde `element` belirleyebilirsiniz. Bu, özellikle iç içe geçmiş `For Each` döngülerine sahipseniz programınızın okunabilirliğini geliştirir. Karşılık gelen `For Each` ifadesinde görüntülenen değişkenle aynı değişkeni belirtmeniz gerekir.

@No__t-0 değerini bir döngü içinde değiştirmekten kaçınmak isteyebilirsiniz. Bunu yapmak, kodunuzun okunmasını ve hata ayıklamasını daha zor hale getirir. @No__t-0 değeri değiştirildiğinde, döngü ilk kez girildiğinde belirlenen koleksiyon veya öğeleri etkilenmez.

Döngüleri iç içe aktardığınızda, iç düzeyin `Next` ' den önce dış iç içe düzey `Next` ifadesine karşılaşılırsa, derleyici bir hata bildirir. Ancak, derleyici yalnızca her `Next` ifadesinde `element` ' ı belirtirseniz bu çakışan hatayı algılayabilir.

Kodunuz belirli bir sırada bir koleksiyonun geçiş yöntemine bağımlıysa, koleksiyonun sunduğu Numaralandırıcı nesnesinin özelliklerini bilmiyorsanız, bir `For Each`... `Next` döngüsü en iyi seçenektir. Çapraz geçiş sırası Visual Basic tarafından belirlenmemiştir, ancak Numaralandırıcı nesnesinin <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi ile. Bu nedenle, koleksiyonun hangi öğesinin `element` ' ta döndürüldüğünden veya belirli bir öğeden sonra döndürülecek bir sonraki bir öğe olduğunu tahmin edemeyebilirsiniz. @No__t-0... `Next` veya `Do`... `Loop` gibi farklı bir döngü yapısı kullanarak daha güvenilir sonuçlar elde edebilirsiniz.

Çalışma zamanının `group` ' daki öğeleri `element` ' e dönüştürebilmelidir. [@No__t-0] ifadesinde, hem genişletme hem de daraltma dönüştürmelerine izin verilip verilmeyeceğini (`Option Strict` kapalı, varsayılan değeri) veya yalnızca genişletme dönüştürmelerine izin verilip verilmeyeceğini (`Option Strict` ' nin açık olduğunu) denetler. Daha fazla bilgi için bkz. [daraltma dönüştürmeleri](#narrowing-conversions).

@No__t-0 ' ın veri türü, bir koleksiyona veya Numaralandırılabilir bir diziye başvuran bir başvuru türü olmalıdır. En yaygın olarak bu, `group` ' ın `System.Collections` ad alanının <xref:System.Collections.IEnumerable> arabirimini veya `System.Collections.Generic` ad alanının <xref:System.Collections.Generic.IEnumerable%601> arabirimini uygulayan bir nesneye başvurduğu anlamına gelir. `System.Collections.IEnumerable`, koleksiyon için bir Numaralandırıcı nesnesi döndüren <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemini tanımlar. Numaralandırıcı nesnesi `System.Collections` ad alanının `System.Collections.IEnumerator` arabirimini uygular ve <xref:System.Collections.IEnumerator.Current%2A> özelliğini ve <xref:System.Collections.IEnumerator.Reset%2A> ve <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemlerini gösterir. Visual Basic, koleksiyonu çapraz geçirmek için bunları kullanır.

### <a name="narrowing-conversions"></a>Daraltma dönüştürmeleri

@No__t-0 `On` olarak ayarlandığında, daraltma dönüştürmeleri normalde derleyici hatalarına neden olur. Ancak, `For Each` ifadesinde, `group` ' deki öğelerden `element` ' ye dönüştürme, çalışma zamanında değerlendirilir ve gerçekleştirilir ve daraltma dönüştürmelerinden kaynaklanan derleyici hataları bastırılır.

Aşağıdaki örnekte, `n` ' in ilk değeri olarak `m` ' ı bir `Integer` ' e @no__t dönüştürme bir daraltma dönüştürmesi olduğundan `Option Strict` olduğunda derlenmez. Ancak, `For Each` ifadesinde, `number` ' e atama, `Long` ' den `Integer` ' e kadar aynı dönüştürmeyi gerektirdiğinden bile derleyici hatası raporlanmayacaktır. Büyük bir sayı içeren `For Each` ifadesinde, büyük sayıya <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> uygulandığında bir çalışma zamanı hatası oluşur.

[!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]

### <a name="ienumerator-calls"></a>IEnumerator çağrıları

@No__t-0... `Next` döngüsünün yürütülmesi başladığında Visual Basic `group` ' nin geçerli bir koleksiyon nesnesine başvurduğunu doğrular. Aksi takdirde, bir özel durum oluşturur. Aksi halde, ilk öğeyi döndürmek için <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemini ve Numaralandırıcı nesnesinin <xref:System.Collections.IEnumerator.Current%2A> özelliğini çağırır. @No__t-0 bir sonraki öğe olmadığını gösteriyorsa, diğer bir deyişle, koleksiyon boşsa, `For Each` döngüsü durdurulduğunda ve denetim, `Next` ifadesiyle sonra ifadeye geçer. Aksi takdirde, Visual Basic `element` ' ı ilk öğeye ayarlar ve ekstre bloğunu çalıştırır.

Her Visual Basic `Next` ifadesiyle karşılaştığında `For Each` ifadesine geri döner. Sonra, bir sonraki öğeyi döndürmek için `MoveNext` ve `Current` ' i çağırır ve sonra da bloğu çalıştırır veya sonuca bağlı olarak döngüyü sonlandırır. @No__t-0 ' a kadar işlem devam eder veya bir sonraki öğe olmadığını veya bir `Exit For` ifadesiyle karşılaşdığını gösterir.

**Koleksiyonu değiştirme.** @No__t-0 tarafından döndürülen Numaralandırıcı nesnesi normalde herhangi bir öğeyi ekleyerek, silerek, değiştirerek veya yeniden sıralayarak koleksiyonu değiştirmenize izin vermez. @No__t-0... `Next` döngüsünü başlattıktan sonra koleksiyonu değiştirirseniz, Numaralandırıcı nesnesi geçersiz hale gelir ve bir sonraki erişim denemesi <xref:System.InvalidOperationException> özel durumuna neden olur.

Ancak, bu değişikliğin engellenmesi Visual Basic tarafından belirlenir, ancak <xref:System.Collections.IEnumerable> arabiriminin uygulanması bunun yerine. Yineleme sırasında değişikliklere izin verecek şekilde `IEnumerable` uygulamak mümkündür. Bu tür dinamik değişikliği yapmayı düşünüyorsanız, kullanmakta olduğunuz koleksiyonda `IEnumerable` uygulamasının özelliklerini anladığınızdan emin olun.

**Koleksiyon öğelerini değiştirme.** Numaralandırıcı nesnesinin <xref:System.Collections.IEnumerator.Current%2A> özelliği [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md)ve her koleksiyon öğesinin yerel bir kopyasını döndürür. Bu, öğeleri `For Each`... `Next` döngüsünde değiştiremeyeceğiniz anlamına gelir. Yaptığınız tüm değişiklikler yalnızca `Current` ' dan yerel kopyayı etkiler ve temel alınan koleksiyona yansıtılmaz. Ancak, bir öğe bir başvuru türü ise, gösterdiği örnek üyelerini değiştirebilirsiniz. Aşağıdaki örnek her `thisControl` öğesinin `BackColor` üyesini değiştirir. Ancak, `thisControl` ' ı değiştiremezsiniz.

```vb
Sub LightBlueBackground(thisForm As System.Windows.Forms.Form)
    For Each thisControl In thisForm.Controls
        thisControl.BackColor = System.Drawing.Color.LightBlue
    Next thisControl
End Sub
```

Önceki örnek, her bir `thisControl` öğesinin `BackColor` üyesini değiştirebilir, ancak `thisControl` ' i değiştiremezler.

**Dizileri geçme.** @No__t-0 sınıfı <xref:System.Collections.IEnumerable> arabirimini gerçekleştirdiğinden, tüm diziler <xref:System.Array.GetEnumerator%2A> yöntemini kullanıma sunar. Yani, bir dizi boyunca `For Each`... `Next` döngüsü ile yineleyebilirsiniz. Ancak, yalnızca dizi öğelerini okuyabilirsiniz. Bunları değiştiremezsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, C:\ içindeki tüm klasörleri listeler. <xref:System.IO.DirectoryInfo> sınıfını kullanarak dizin.

[!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]

## <a name="example"></a>Örnek

Aşağıdaki örnek bir koleksiyonu sıralamak için bir yordam gösterir. Örnek, bir <xref:System.Collections.Generic.List%601> ' de depolanan `Car` sınıfının örneklerini sıralar. @No__t-0 sınıfı, <xref:System.IComparable%601.CompareTo%2A> yönteminin uygulanması için <xref:System.IComparable%601> arabirimini uygular.

@No__t-0 yöntemine yapılan her çağrı, sıralama için kullanılan tek bir karşılaştırma yapar. @No__t-0 yönteminde Kullanıcı tarafından yazılan kod, geçerli nesnenin her karşılaştırması için başka bir nesneyle ilgili bir değer döndürür. Geçerli nesne diğer nesneden daha küçükse döndürülen değer sıfırdan küçük, geçerli nesne diğer nesneden büyükse sıfırdan büyük ve eşitse sıfır. Bu, büyük, küçüktür ve eşittir ölçütlerine göre kod içinde tanımlamanızı sağlar.

@No__t-0 yönteminde `cars.Sort()` ifadesinde liste sıralanır. @No__t-1 ' in <xref:System.Collections.Generic.List%601.Sort%2A> yöntemine yapılan bu çağrı, `List` ' teki @no__t 3 nesneleri için `CompareTo` yönteminin otomatik olarak çağrılmasına neden olur.

[!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyonlar](../../../standard/collections/index.md)
- [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Döngü Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While Deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop Deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Nesne başlatıcıları: Adlandırılmış ve anonim türler @ no__t-0
- [Öğe Başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md)
