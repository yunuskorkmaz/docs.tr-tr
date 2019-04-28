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
ms.openlocfilehash: 5081f80ad0da738ebb950bcd649af7a593582356
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638083"
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
|`element`|Gerekli `For Each` deyimi. İsteğe bağlı olarak `Next` deyimi. değişken. Koleksiyon öğelerinde yineleme yapmak için kullanılır.|  
|`datatype`|Gerekli if `element` zaten bildirildi değil. Veri türü `element`.|  
|`group`|Gerekli. Bir koleksiyon türü veya nesne bir türe sahip bir değişken. Hangi koleksiyona başvuran `statements` yinelenmesi üzeresiniz.|  
|`statements`|İsteğe bağlı. Bir veya daha fazla deyim arasında `For Each` ve `Next` her öğe üzerinde çalışan `group`.|  
|`Continue For`|İsteğe bağlı. Başlangıcına kadar denetim aktarır `For Each` döngü.|  
|`Exit For`|İsteğe bağlı. Dışı denetim aktarır `For Each` döngü.|  
|`Next`|Gerekli. Tanımını sonlandırır `For Each` döngü.|  
  
## <a name="simple-example"></a>Basit bir örnek  
 Kullanım bir `For Each`... `Next` döngü, her bir koleksiyon veya dizi öğesi için bir dizi ifadeleri yineleyin istediğinizde.  
  
> [!TIP]
>  A [için... Sonraki deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md) ne zaman bir döngünün her yinelemesinden bir denetim değişkeni ile ilişkilendirmek ve bu değişkenin ilk ve son değerleri belirlemek de çalışır. Ancak, bir koleksiyon ile ilgilenirken, ilk ve son değerleri kavramını anlamlı değildir ve koleksiyonda kaç öğenin mutlaka bilmiyorum. Bu tür bir durumda, bir `For Each`... `Next` döngü olduğu genellikle daha iyi bir seçenek.  
  
 Aşağıdaki örnekte, `For Each`...`Next` deyimi bir listesi koleksiyonun tüm öğeleri yinelenir.  
  
 [!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]  
  
 Daha fazla örnek için bkz. [koleksiyonları](../../../standard/collections/index.md) ve [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="nested-loops"></a>İç içe döngüleri  
 İç içe yerleştirebilirsiniz `For Each` içindeki başka bir döngü koyarak döngüleri.  
  
 Aşağıdaki örnek, iç içe geçmiş gösterir `For Each`...`Next` yapılar.  
  
 [!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]  
  
 İç içe döngüleri, her döngü benzersiz olması gerekir `element` değişkeni.  
  
 Farklı türlerde denetim yapılarını birbirine içinde iç içe yerleştirebilirsiniz. Daha fazla bilgi için [iç içe geçmiş denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-for-and-continue-for"></a>İçin çıkmak ve için devam edin  
 [Çıkmak için](../../../visual-basic/language-reference/statements/exit-statement.md) deyimi neden çıkmak yürütme `For`...`Next` izleyen deyime döngüsü ve aktarımları denetimine `Next` deyimi.  
  
 `Continue For` Deyime aktarır denetimi hemen döngünün sonraki yinelemesine. Daha fazla bilgi için [Continue deyimi](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `Continue For` ve `Exit For` deyimleri.  
  
 [!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]  
  
 Herhangi bir sayıda koyabilirsiniz `Exit For` deyimlerinde bir `For Each` döngü. Kullanıldığında içinde iç içe geçmiş `For Each` döngüleri `Exit For` iç döngü ve aktarımları denetimi iç içe geçme sonraki daha yüksek düzeye çıkmak yürütülmesine neden olur.  
  
 `Exit For` Bazı koşullar bir değerlendirmesinden sonra genellikle kullanılır, örneğin, bir `If`... `Then`... `Else` yapısı. Kullanmak istediğiniz `Exit For` aşağıdaki koşulları için:  
  
- Yineleme devam gereksiz veya imkansız olabilir. Bunun nedeni hatalı bir değer veya bir sonlandırma isteği.  
  
- Bir özel durum yakalandı bir `Try`... `Catch`... `Finally`. Kullanabileceğinize `Exit For` sonunda `Finally` blok.  
  
- Büyük veya hatta sonsuz birkaç kez çalıştırabileceğiniz bir döngü sonsuz bir döngüye vardır. Bir koşul algılama, kullanabileceğiniz `Exit For` döngüden çıkma. Daha fazla bilgi için [yapın... Döngü deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## <a name="iterators"></a>Yineleyiciler  
 Kullandığınız bir *yineleyici* bir koleksiyon üzerinde özel yineleme yapmak için. Bir yineleyiciyi bir işlevi olabilir veya bir `Get` erişimcisi. Bunu kullanan bir `Yield` deyimini her öğesini birer birer koleksiyonunun bir döndürür.  
  
 Kullanarak bir yineleyici çağırabilirsiniz bir `For Each...Next` deyimi. Her bir yinelemesini `For Each` döngü yineleyiciyi çağırır. Olduğunda bir `Yield` yineleyicide ifade deyimine ulaşıldığında `Yield` deyimi döndürülür ve kodun geçerli konumu korunur. Yürütme, yineleyicinin bir sonraki açışınızda bu konumdan başlatılır.  
  
 Aşağıdaki örnek, bir yineleyici işlevi kullanır. Yineleyici işleve sahip bir `Yield` içindeki bir [için... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü. İçinde `ListEvenNumbers` yöntemi, her bir yinelemesini `For Each` diğerine geçer yineleyici işlevine bir çağrı oluşturur ve deyim gövdesi `Yield` deyimi.  
  
 [!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]  
  
 Daha fazla bilgi için [yineleyiciler](../../programming-guide/concepts/iterators.md), [Yield deyimi](../../../visual-basic/language-reference/statements/yield-statement.md), ve [yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
## <a name="technical-implementation"></a>Teknik Uygulama  
 Olduğunda bir `For Each`...`Next` deyimi çalıştırır, Visual Basic koleksiyon yalnızca bir kez döngü başlamadan önce değerlendirilir. Deyim bloğunu değişirse `element` veya `group`, bu değişiklikleri döngü etkilemez.  
  
 Ne zaman koleksiyondaki tüm öğeler sırayla atandı için `element`, `For Each` döngü durdurur ve denetim deyime geçer `Next` deyimi.  
  
 Varsa `element` henüz bu döngü dışında bildirmelidir bildirilmiş içinde `For Each` deyimi. Türünü bildirebilirsiniz `element` kullanılarak açık şekilde bir `As` deyimi veya atamak üzere tür çıkarımı güvenebilirler. Her iki durumda da kapsamını `element` döngü gövdesi. Ancak, bildiremezsiniz `element` hem dışından hem de döngü içinde.  
  
 İsteğe bağlı olarak belirtebilirsiniz `element` içinde `Next` deyimi. Özellikle, iç içe geçmiş varsa bu programınızı okunabilirliğini artırır `For Each` döngüleri. Görüntülenen ilgili olarak aynı değişkene belirtmelisiniz `For Each` deyimi.  
  
 Değerinin değiştirilmesi önlemek isteyebilirsiniz `element` bir döngü içinde. Bunun yapılması daha zor okuyun ve kod hatalarını ayıklama işlemleri yapabilirsiniz. Değerinin değiştirilmesi `group` koleksiyondan veya döngü girildiğinde, belirlenen öğelerine etkilemez.  
  
 Ne zaman, iç içe döngüleri, bir `Next` ifadesi bir dış iç içe geçme düzeyi önce karşılaşıldığında `Next` iç düzeyine, derleyici bir hata bildirir. Ancak, derleyici bu hata yalnızca belirtirseniz, çakışan algılayabilir `element` içinde her `Next` deyimi.  
  
 Belirli bir sırada bir koleksiyon geçiş üzerinde kodunuzu bağımlı olması durumunda bir `For Each`... `Next` döngü en iyi seçenek değilse, numaralandırıcı nesne özelliklerini bilmiyorsanız koleksiyonu kullanıma sunar. Geçişi sırasını Visual Basic, ancak göre belirlenen değil <xref:System.Collections.IEnumerator.MoveNext%2A> Numaralandırıcı nesnesi yöntemi. Bu nedenle, hangi öğedir, döndürülen ilk koleksiyonun tahmin etmek mümkün olmayabilir `element`, ya da belirli bir öğeden sonra döndürülecek sonraki olduğu. Bunu gibi farklı bir döngü yapısı, kullanılarak daha güvenilir sonuçlar elde `For`... `Next` veya `Do`... `Loop`.  
  
 Veri türü `element` öğelerin veri türü şekilde olmalıdır `group` kendisine dönüştürülebilir.  
  
 Veri türü `group` numaralandırılabilir bir dizi veya koleksiyon başvuran bir başvuru türü olması gerekir. Buna genellikle `group` uygulayan bir nesneye başvuruyor <xref:System.Collections.IEnumerable> arabiriminin `System.Collections` ad alanı veya <xref:System.Collections.Generic.IEnumerable%601> arabiriminin `System.Collections.Generic` ad alanı. `System.Collections.IEnumerable` tanımlar <xref:System.Collections.IEnumerable.GetEnumerator%2A> koleksiyonu için bir numaralandırıcı nesnesi döndüren bir yöntem. Numaralandırıcı nesnesi uygulayan `System.Collections.IEnumerator` arabiriminin `System.Collections` ad alanı ve ortaya çıkaran <xref:System.Collections.IEnumerator.Current%2A> özelliği ve <xref:System.Collections.IEnumerator.Reset%2A> ve <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemleri. Visual Basic koleksiyonu geçirmek için bunları kullanır.  
  
### <a name="narrowing-conversions"></a>Daraltma dönüşümleri  
 Zaman `Option Strict` ayarlanır `On`, daraltma dönüştürmelerini genellikle derleme hatalarına neden olabilir. İçinde bir `For Each` deyimi, ancak öğeleri Dönüştürmelere `group` için `element` değerlendirilir ve çalışma zamanında gerçekleşen ve daraltma dönüşümleri kaynaklanan derleyici hataları gizlenir.  
  
 Aşağıdaki örnekte, atamasını `m` ilk değeri olarak `n` ne zaman derleme değil `Option Strict` üzerinde olduğundan dönüştürülmesi bir `Long` için bir `Integer` ise daralan dönüştürmedir. İçinde `For Each` deyimi, ancak hiçbir derleyici hatası olduğunu bildirdi, rağmen atama için `number` aynı dönüştürme gerektiriyor `Long` için `Integer`. İçinde `For Each` büyük bir sayı içeren deyimi, bir çalışma zamanı hatası oluşur, <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> büyük sayıya uygulanır.  
  
 [!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]  
  
### <a name="ienumerator-calls"></a>IEnumerator çağrıları  
 Zaman yürütülmesini bir `For Each`... `Next` döngü başlatır, Visual Basic doğrular `group` geçerli koleksiyon nesnesine başvuruyor. Aksi durumda, bir özel durum oluşturur. Aksi takdirde, çağrı <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi ve <xref:System.Collections.IEnumerator.Current%2A> ilk öğesi döndürülecek Numaralandırıcı nesnesi bir özelliğidir. Varsa `MoveNext` koleksiyonu boş ise, herhangi bir sonraki öğe başka bir deyişle, gösterir `For Each` döngü durdurur ve denetim deyime geçer `Next` deyimi. Aksi takdirde, Visual Basic ayarlar `element` ilk öğe ve deyim bloğunu çalıştırır.  
  
 Her zaman Visual Basic karşılaştığı `Next` deyimi döndürdüğü için `For Each` deyimi. Yeniden çağırdığı `MoveNext` ve `Current` sonraki öğeyi ve yeniden döndürülecek bloğu çalışır veya sonuca bağlı olarak döngü durur. Bu işlem kadar devam eder `MoveNext` sonraki herhangi bir öğe olduğunu gösterir veya `Exit For` deyimi karşılaştı.  
  
 **Koleksiyon değiştiriliyor.** Numaralandırıcı nesnesi tarafından döndürülen <xref:System.Collections.IEnumerable.GetEnumerator%2A> normalde koleksiyon ekleme, silme, değiştirme veya öğeleri yeniden sıralama değiştirmenize izin vermez. Koleksiyon, başlattıktan sonra değiştirirseniz bir `For Each`... `Next` döngü, numaralandırıcı nesnesi geçersiz olur ve sonraki öğeye erişme denemesi neden bir <xref:System.InvalidOperationException> özel durum.  
  
 Ancak, bu değişikliği engelleme Visual Basic, ancak bunun yerine uygulaması tarafından belirlenen değil <xref:System.Collections.IEnumerable> arabirimi. Uygulanması mümkün `IEnumerable` yineleme sırasında değiştirilmesine izin veren bir yolla. Dinamik tür değişikliği yapmadan düşünüyorsanız özelliklerini anladığınızdan emin olun `IEnumerable` uygulama kullanmakta olduğunuz koleksiyonu.  
  
 **Koleksiyon öğelerini değiştirme.** <xref:System.Collections.IEnumerator.Current%2A> Numaralandırıcı nesnesi özelliği [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md), ve her koleksiyon öğesi yerel bir kopyasını döndürür. Bu öğeleri değiştiremezsiniz anlamına gelir, bir `For Each`... `Next` döngü. Yaptığınız değişiklikler yalnızca yerel kopyadan etkiler `Current` ve temel alınan koleksiyona gösterilmez. Ancak, bir öğenin bir başvuru türü ise, işaret ettiği örnek üyelerini değiştirebilirsiniz. Aşağıdaki örnek `BackColor` her üyesi `thisControl` öğesi. Ancak değişiklik yapamazsınız `thisControl` kendisi.  
  
```vb  
Sub lightBlueBackground(ByVal thisForm As System.Windows.Forms.Form)  
    For Each thisControl As System.Windows.Forms.Control In thisForm.Controls  
        thisControl.BackColor = System.Drawing.Color.LightBlue  
    Next thisControl  
End Sub  
```  
  
 Önceki örnekte değiştirebilirsiniz `BackColor` her üyesi `thisControl` öğesini değiştiremezsiniz ancak `thisControl` kendisi.  
  
 **Diziler geçme.** Çünkü <xref:System.Array> sınıfının Implements <xref:System.Collections.IEnumerable> arabirimi, tüm dizileri ortaya <xref:System.Array.GetEnumerator%2A> yöntemi. Bu, bir dizi aracılığıyla yineleyebilirsiniz anlamına gelir. bir `For Each`... `Next` döngü. Ancak dizi öğelerine salt okunur. Bunları değiştiremezsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kullanarak C:\ dizinindeki tüm klasörleri listeler <xref:System.IO.DirectoryInfo> sınıfı.  
  
 [!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir koleksiyonu sıralamak için bir yordam gösterir. Örnek örneklerini sıralar bir `Car` depolanan sınıfı bir <xref:System.Collections.Generic.List%601>. `Car` Sınıfının Implements <xref:System.IComparable%601> gerektiren arabirimi <xref:System.IComparable%601.CompareTo%2A> yönteminin uygulanmasını.  
  
 Her çağrı <xref:System.IComparable%601.CompareTo%2A> yöntemi sıralama için kullanılan tek bir karşılaştırma yapar. Kullanıcı tarafından yazılan kodu `CompareTo` geçerli nesnenin başka bir nesneyle her karşılaştırılışında bir değer döndürür. Döndürülen değer daha az nesne geçerli nesneye sıfırdan küçük nesnesine, geçerli nesne diğer nesneden büyükse sıfır ve sıfır büyüktür eşit olmaları durumunda. Bu, kodda büyüktür, küçüktür ölçütleri tanımlayın ve eşit sağlar.  
  
 İçinde `ListCars` yöntemi `cars.Sort()` deyimi listeyi sıralar. Bu çağrıyı <xref:System.Collections.Generic.List%601.Sort%2A> yöntemi <xref:System.Collections.Generic.List%601> neden `CompareTo` otomatik olarak çağrılmasına yöntemi `Car` nesneler `List`.  
  
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
