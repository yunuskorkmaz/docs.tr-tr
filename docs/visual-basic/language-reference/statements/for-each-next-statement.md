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
ms.openlocfilehash: 0feb938121a97b06509b472652e6a753841ab2b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404660"
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
|`element`|`For Each`İfadesinde gereklidir. `Next`Deyimde isteğe bağlı. Değişken. Koleksiyonun öğeleri arasında yineleme yapmak için kullanılır.|
|`datatype`|Açık ise [`Option Infer`](option-infer-statement.md) (varsayılan) veya zaten bildirilirse, isteğe bağlıdır `element` ; `Option Infer` kapalıysa ve önceden bildirilmemiş olması gerekir `element` . Veri türü `element` .|
|`group`|Gereklidir. Bir koleksiyon türü veya nesne olan türü olan bir değişken. Tekrarlanması gereken koleksiyona başvurur `statements` .|
|`statements`|İsteğe bağlı. `For Each` `Next` İçindeki ve içindeki her öğe için çalışan arasında bir veya daha fazla deyim `group` .|
|`Continue For`|İsteğe bağlı. Denetimi döngünün başlangıcına aktarır `For Each` .|
|`Exit For`|İsteğe bağlı. Denetimi döngünün dışına aktarır `For Each` .|
|`Next`|Gereklidir. Döngünün tanımını sonlandırır `For Each` .|

## <a name="simple-example"></a>Basit örnek

Bir `For Each` `Next` koleksiyonun veya dizinin her öğesi için bir deyim kümesini yinelemek istediğinizde bir... döngüsü kullanın.

> [!TIP]
> [İçin A... Sonraki Ifade](for-next-statement.md) , bir döngünün her yinelemesini bir denetim değişkeniyle ilişkilendirebileceğiniz ve değişkenin ilk ve son değerlerini belirleyebileceğiniz zaman iyi şekilde kullanılır. Bununla birlikte, bir koleksiyonla ilgilendiğinizde, ilk ve son değer kavramı anlamlı değildir ve koleksiyonun kaç öğe olduğunu bilmeniz gerekmez. Bu tür bir durumda,... `For Each` `Next` döngüsü genellikle daha iyi bir seçimdir.

Aşağıdaki örnekte, `For Each` ...`Next` ifade, bir liste koleksiyonunun tüm öğeleri boyunca yinelenir.

[!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]

Daha fazla örnek için bkz. [koleksiyonlar](../../../standard/collections/index.md) ve [diziler](../../programming-guide/language-features/arrays/index.md).

## <a name="nested-loops"></a>İç içe döngüler

Bir `For Each` döngüyü diğerinin içine yerleştirerek döngüleri iç içe geçirebilirsiniz.

Aşağıdaki örnek iç içe geçmiş `For Each` ...`Next` yapıları.

[!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]

Döngüleri iç içe aktardığınızda her döngünün benzersiz bir `element` değişkeni olmalıdır.

Ayrıca, farklı türlerde denetim yapılarını birbirleriyle iç içe geçirebilirsiniz. Daha fazla bilgi için bkz. [Iç Içe denetim yapıları](../../programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>İçin çık ve devam et

[Exit for](exit-statement.md) deyimleri yürütmenin uygulamadan çıkmasına neden olur `For` ...`Next` öğesini Loop ve deyimden sonraki deyime aktarır `Next` .

`Continue For`İfade, denetimi döngünün bir sonraki yinelemesine hemen aktarır. Daha fazla bilgi için bkz. [Continue bildirisi](continue-statement.md).

Aşağıdaki örnek, ve deyimlerinin nasıl kullanılacağını göstermektedir `Continue For` `Exit For` .

[!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]

`Exit For`Bir döngüye herhangi bir sayıda deyim yerleştirebilirsiniz `For Each` . İç içe döngüler içinde kullanıldığında `For Each` `Exit For` yürütmenin en içteki döngüden çıkmasına ve denetimi bir sonraki daha yüksek iç içe geçme düzeyine aktarmasına neden olur.

`Exit For`genellikle bir koşul değerlendirmesinden sonra, örneğin bir `If` .. `Then` . ...`Else` yapısı. `Exit For`Aşağıdaki koşullar için kullanmak isteyebilirsiniz:

- Tekrarlamaya devam etmek gereksiz veya imkansız. Bunun nedeni hatalı bir değer veya sonlandırma isteği olabilir.

- Bir özel durum içinde yakalandı `Try` .. `Catch` . ...`Finally`. `Exit For`Bloğunun sonunda kullanabilirsiniz `Finally` .

- Sonsuz bir döngü vardır. Bu bir döngü, büyük veya hatta sonsuz bir sayı çalıştırabilir. Böyle bir koşulu tespit ediyorsanız, `Exit For` döngüyü atlamak için kullanabilirsiniz. Daha fazla bilgi için bkz [. do... Loop deyimleri](do-loop-statement.md).

## <a name="iterators"></a>Yineleyiciler

Bir koleksiyon üzerinde özel bir yineleme gerçekleştirmek için bir *Yineleyici* kullanırsınız. Yineleyici bir işlev veya `Get` erişimci olabilir. `Yield`Tek seferde koleksiyonun her bir öğesini döndürmek için bir ifade kullanır.

Bir ifadeyi kullanarak bir yineleyici çağırın `For Each...Next` . Döngünün her yinelemesi `For Each` yineleyiciyi çağırır. `Yield`Yineleyiciden bir ifadeye ulaşıldığında, `Yield` deyimdeki ifade döndürülür ve koddaki geçerli konum korunur. Bu konumdan, yineleyici bir sonraki sefer çağrıldığında yürütme yeniden başlatılır.

Aşağıdaki örnek bir yineleyici işlevi kullanır. Yineleyici işlevinin, `Yield` için içindeki bir ifade vardır [... Sonraki](for-next-statement.md) döngü. `ListEvenNumbers`Yönteminde, `For Each` ifade gövdesinin her yinelemesi bir sonraki ifadeye devam eden Yineleyici işlevine bir çağrı oluşturur `Yield` .

[!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]

Daha fazla bilgi için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md), [yield ekstresi](yield-statement.md)ve [Yineleyici](../modifiers/iterator.md).

## <a name="technical-implementation"></a>Teknik Uygulama

Bir... `For Each``Next` deyimin çalışması Visual Basic, döngü başlamadan önce koleksiyonu yalnızca bir kez değerlendirir. Deyiminiz değişiklikleri veya değişiklik engelleriyorsa `element` `group` , bu değişiklikler döngünün yinelemesini etkilemez.

Koleksiyondaki tüm öğeler üzerinde kapsamlı olarak atandığında `element` , `For Each` döngü duraklar ve deyimden sonraki deyime geçer `Next` .

[Seçenek çıkarımı](option-infer-statement.md) açık ise (varsayılan ayarı) Visual Basic derleyici, veri türünü çıkarsalabilir `element` . Kapalıysa ve `element` döngü dışında bildirilmediyse, bunu bildiriminde bildirmeniz gerekir `For Each` . Açıkça veri türünü bildirmek için `element` bir `As` yan tümce kullanın. Öğe veri türü `For Each` ... yapı dışında tanımlanmamışsa `Next` , kapsamı döngünün gövdesidir. `element`Döngüsünün dışında ve içinde bildiremezsiniz.

İsteğe bağlı olarak `element` `Next` deyimde belirtebilirsiniz. Bu, özellikle iç içe döngüler varsa programınızın okunabilirliğini geliştirir `For Each` . Karşılık gelen ifadede görünen değişkenle aynı değişkeni belirtmeniz gerekir `For Each` .

Bir döngünün içindeki değerini değiştirmeyi önlemek isteyebilirsiniz `element` . Bunu yapmak, kodunuzun okunmasını ve hata ayıklamasını daha zor hale getirir. Değerini değiştirmek `group` , döngü ilk kez girildiğinde belirlenen koleksiyonu veya öğelerini etkilemez.

Döngüleri iç içe aktardığınızda, `Next` iç düzeyden önce bir dış iç içe düzeyi ifadesine karşılaşılırsa `Next` , derleyici bir hata bildirir. Ancak, derleyici bu çakışan hatayı yalnızca her ifadede belirtirseniz tespit edebilir `element` `Next` .

Kodunuz belirli bir sırada bir koleksiyonun geçiş yöntemine bağımlıysa, `For Each` `Next` koleksiyonun sunduğu Numaralandırıcı nesnesinin özelliklerini bilmiyorsanız,... Loop en iyi seçim değildir. Çapraz geçiş sırası Visual Basic, ancak <xref:System.Collections.IEnumerator.MoveNext%2A> Numaralandırıcı nesnesinin yöntemine göre belirlenir. Bu nedenle, koleksiyonda hangi öğenin döndürüleceğini `element` veya belirli bir öğeden sonra döndürülecek bir sonraki olduğunu tahmin edemeyebilirsiniz. `For`... `Next` Veya `Do` .. `Loop` . gibi farklı bir döngü yapısı kullanarak daha güvenilir sonuçlar elde edebilirsiniz.

Çalışma zamanının içindeki öğeleri ' a dönüştürebilmelidir `group` `element` . [ `Option Strict` ] İfadesinde, hem genişletme hem de daraltma dönüştürmelerine izin verilip verilmeyeceğini ( `Option Strict` kapalı, varsayılan değeri) veya yalnızca genişletme dönüştürmelerine izin verilip verilmeyeceğini ( `Option Strict` açık olduğunu) denetler. Daha fazla bilgi için bkz. [daraltma dönüştürmeleri](#narrowing-conversions).

Veri türü, `group` bir koleksiyona veya Numaralandırılabilir bir diziye başvuran bir başvuru türü olmalıdır. En yaygın olarak bu `group` <xref:System.Collections.IEnumerable> , `System.Collections` ad alanının arabirimini veya <xref:System.Collections.Generic.IEnumerable%601> `System.Collections.Generic` ad alanının arabirimini uygulayan bir nesneye başvurur. `System.Collections.IEnumerable`<xref:System.Collections.IEnumerable.GetEnumerator%2A>koleksiyon için bir Numaralandırıcı nesnesi döndüren yöntemini tanımlar. Numaralandırıcı nesnesi `System.Collections.IEnumerator` `System.Collections` ad alanı arabirimini uygular ve <xref:System.Collections.IEnumerator.Current%2A> özelliğini ve <xref:System.Collections.IEnumerator.Reset%2A> ve <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemlerini gösterir. Visual Basic, koleksiyonu çapraz geçirmek için bunları kullanır.

### <a name="narrowing-conversions"></a>Daraltma dönüştürmeleri

Ne zaman `Option Strict` ayarlandığında `On` , daraltma dönüştürmeleri normalde derleyici hatalarına neden olur. Ancak, ' `For Each` deki öğelerinden dönüşümler, `group` çalışma zamanında `element` değerlendirilir ve gerçekleştirilir ve daraltma dönüştürmelerinden kaynaklanan derleyici hataları bastırılır.

Aşağıdaki örnekte, ' `m` `n` `Option Strict` a ' a dönüştürme bir `Long` daraltma dönüştürmesi olduğundan, için başlangıç değeri olarak atama, tarihinde derleme yapmaz `Integer` . Ancak,, öğesine atama, ' den ' e `For Each` `number` aynı dönüştürmeyi gerektirse de, hiçbir derleyici hatası raporlanır `Long` `Integer` . `For Each`Büyük bir sayı içeren ifadede, büyük sayıya uygulandığında bir çalışma zamanı hatası oluşur <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> .

[!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]

### <a name="ienumerator-calls"></a>IEnumerator çağrıları

Bir `For Each` ... `Next` döngüsünün yürütülmesi başladığında, `group` geçerli bir koleksiyon nesnesine başvuran Visual Basic doğrular. Aksi takdirde, bir özel durum oluşturur. Aksi takdirde, <xref:System.Collections.IEnumerator.MoveNext%2A> <xref:System.Collections.IEnumerator.Current%2A> ilk öğeyi döndürmek için yöntemini ve Numaralandırıcı nesnesinin özelliğini çağırır. Eğer `MoveNext` bir sonraki öğe olmadığını gösteriyorsa, diğer bir deyişle, koleksiyon boşsa, `For Each` döngü duraklar ve denetimi deyimden sonraki ifadeye geçirir `Next` . Aksi takdirde, Visual Basic `element` ilk öğesine ayarlar ve ekstre bloğunu çalıştırır.

Her Visual Basic `Next` deyimle karşılaştığında, ifadeye geri döner `For Each` . Yeniden çağırır `MoveNext` ve bir `Current` sonraki öğesini döndürür ve sonra da bloğu çalıştırır veya sonuca bağlı olarak döngüyü sonlandırır. Bu işlem `MoveNext` , bir sonraki öğe veya bir deyimin karşılaştığı anlamına gelene kadar devam eder `Exit For` .

**Koleksiyonu değiştirme.** Normal olarak döndürülen Numaralandırıcı nesnesi <xref:System.Collections.IEnumerable.GetEnumerator%2A> herhangi bir öğeyi ekleyerek, silerek, değiştirerek veya yeniden sıralayarak koleksiyonu değiştirmenize izin vermez. `For Each`... Döngüsünü başlattıktan sonra koleksiyonu değiştirirseniz `Next` , Numaralandırıcı nesnesi geçersiz hale gelir ve bir sonraki erişim denemesi <xref:System.InvalidOperationException> özel duruma neden olur.

Ancak, bu değişikliğin engellenmesi Visual Basic tarafından belirlenir, ancak bunun yerine <xref:System.Collections.IEnumerable> arabirimin uygulanması. `IEnumerable`Yineleme sırasında değişikliklere izin veren bir şekilde uygulanması mümkündür. Bu tür dinamik değişikliği yapmayı düşünüyorsanız, kullanmakta olduğunuz koleksiyonda uygulamanın özelliklerini anladığınızdan emin olun `IEnumerable` .

**Koleksiyon öğelerini değiştirme.** <xref:System.Collections.IEnumerator.Current%2A>Numaralandırıcı nesnesinin özelliği [salt okunur](../modifiers/readonly.md)ve her koleksiyon öğesinin yerel bir kopyasını döndürür. Bu, öğeleri bir `For Each` ... döngüsünde değiştiremeyeceğiniz anlamına gelir `Next` . Yaptığınız herhangi bir değişiklik yalnızca yerel kopyayı etkiler `Current` ve temel koleksiyona geri yansıtılmaz. Ancak, bir öğe bir başvuru türü ise, gösterdiği örnek üyelerini değiştirebilirsiniz. Aşağıdaki örnek `BackColor` her bir öğenin üyesini değiştirir `thisControl` . Ancak, `thisControl` kendisini değiştiremezsiniz.

```vb
Sub LightBlueBackground(thisForm As System.Windows.Forms.Form)
    For Each thisControl In thisForm.Controls
        thisControl.BackColor = System.Drawing.Color.LightBlue
    Next thisControl
End Sub
```

Önceki örnek, `BackColor` `thisControl` kendisini değiştiremese de, her öğenin üyesini değiştirebilir `thisControl` .

**Dizileri geçme.** <xref:System.Array>Sınıfı <xref:System.Collections.IEnumerable> arabirimini uyguladığından, tüm diziler yöntemini kullanıma sunar <xref:System.Array.GetEnumerator%2A> . Bu,... döngüsü ile bir dizi içinde yineleyebilir `For Each` `Next` . Ancak, yalnızca dizi öğelerini okuyabilirsiniz. Bunları değiştiremezsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, C:\ içindeki tüm klasörleri listeler. sınıfını kullanarak Dizin <xref:System.IO.DirectoryInfo> .

[!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]

## <a name="example"></a>Örnek

Aşağıdaki örnek bir koleksiyonu sıralamak için bir yordam gösterir. Örnek, `Car` içinde depolanan bir sınıfın örneklerini sıralar <xref:System.Collections.Generic.List%601> . `Car`Sınıfı, <xref:System.IComparable%601> yönteminin uygulanması için arabirimini uygular <xref:System.IComparable%601.CompareTo%2A> .

Yöntemine yapılan her çağrı, <xref:System.IComparable%601.CompareTo%2A> sıralama için kullanılan tek bir karşılaştırma yapar. Yöntemdeki Kullanıcı tarafından yazılan kod, `CompareTo` geçerli nesnenin her bir karşılaştırması için başka bir nesneyle ilgili bir değer döndürür. Geçerli nesne diğer nesneden daha küçükse döndürülen değer sıfırdan küçük, geçerli nesne diğer nesneden büyükse sıfırdan büyük ve eşitse sıfır. Bu, büyük, küçüktür ve eşittir ölçütlerine göre kod içinde tanımlamanızı sağlar.

Yönteminde, `ListCars` `cars.Sort()` ifade listeyi sıralar. Öğesinin yöntemine yapılan bu çağrı, <xref:System.Collections.Generic.List%601.Sort%2A> <xref:System.Collections.Generic.List%601> `CompareTo` yönteminin içindeki nesneler için otomatik olarak çağrılmasına neden olur `Car` `List` .

[!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyonlar](../../../standard/collections/index.md)
- [For...Next Deyimi](for-next-statement.md)
- [Döngü Yapıları](../../programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While Deyimi](while-end-while-statement.md)
- [Do...Loop Deyimi](do-loop-statement.md)
- [Genişletme ve Daraltma Dönüşümleri](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Koleksiyon Başlatıcıları](../../programming-guide/language-features/collection-initializers/index.md)
- [Diziler](../../programming-guide/language-features/arrays/index.md)
