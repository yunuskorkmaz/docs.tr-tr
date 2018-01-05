---
title: For Each...Next Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "56"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 11601eb1caad1c6cc6d9898f590436a977a78fa1
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="for-eachnext-statement-visual-basic"></a>For Each...Next Deyimi (Visual Basic)
Bir koleksiyondaki her öğe için bir grup ifadeleri tekrarlar.  
  
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
|`element`|Gerekli `For Each` deyimi. İsteğe bağlı olarak `Next` deyimi. Değişkeni. Koleksiyon öğelerinde yineleme yapmak için kullanılır.|  
|`datatype`|Gerekli olursa `element` zaten tanımlanmış değil. Veri türü `element`.|  
|`group`|Gerekli. Bir koleksiyon türü veya nesne türüne sahip bir değişken. Koleksiyon, içinde başvurduğu `statements` yinelenmesi üzeresiniz.|  
|`statements`|İsteğe bağlı. Bir veya daha fazla deyimleri arasında `For Each` ve `Next` her öğe çalışan `group`.|  
|`Continue For`|İsteğe bağlı. Denetim başlangıcına aktarır `For Each` döngü.|  
|`Exit For`|İsteğe bağlı. Denetimin dışarı aktarır `For Each` döngü.|  
|`Next`|Gerekli. Tanımını sonlandırır `For Each` döngü.|  
  
## <a name="simple-example"></a>Basit bir örnek  
 Kullanım bir `For Each`... `Next` döngü ifadeleri kümesi bir koleksiyon veya dizi her öğe için yineleyin istediğinizde.  
  
> [!TIP]
>  A [için... Sonraki deyim](../../../visual-basic/language-reference/statements/for-next-statement.md) zaman her bir yineleme döngüsü denetim değişkeni ile ilişkilendirmek ve bu değişkenin ilk ve son değerleri belirlemek iyi çalışır. Ancak, bir koleksiyonu ile ilgilenirken, ilk ve son değerleri kavramı anlamlı değil ve gruplandırmasında kaç öğeleri mutlaka tanımadığınız. Bu tür bir durumda, içinde bir `For Each`... `Next` döngü olan genellikle daha uygun bir seçenektir.  
  
 Aşağıdaki örnekte, `For Each`...`Next` Liste koleksiyonu tüm öğelerinden deyimi yineler.  
  
 [!code-vb[VbVbalrStatements#121](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_1.vb)]  
  
 Daha fazla örnek için bkz: [koleksiyonları](../../../standard/collections/index.md) ve [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="nested-loops"></a>İç içe geçmiş döngüler  
 Geçirebilmenize `For Each` döngüler içinde başka bir döngü koyarak kullanılabilir.  
  
 Aşağıdaki örnek, iç içe geçmiş gösterir `For Each`...`Next` yapıları.  
  
 [!code-vb[VbVbalrStatements#122](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_2.vb)]  
  
 Döngüler iç içe, her döngü benzersiz olmalıdır `element` değişkeni.  
  
 Ayrıca, değişik birbirine içindeki denetim yapıları yerleştirebilirsiniz. Daha fazla bilgi için bkz: [iç içe geçmiş denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-for-and-continue-for"></a>İçin çıkın ve devam etmek için  
 [Çıkmak için](../../../visual-basic/language-reference/statements/exit-statement.md) deyimi neden çıkmak yürütme `For`...`Next` aşağıdaki deyim döngü ve aktarımları denetimine `Next` deyimi.  
  
 `Continue For` Deyimi aktarır denetim hemen sonraki döngü için. Daha fazla bilgi için bkz: [devam deyimi](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir `Continue For` ve `Exit For` deyimleri.  
  
 [!code-vb[VbVbalrStatements#123](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_3.vb)]  
  
 Herhangi bir sayıda koyabilirsiniz `Exit For` deyimlerinde bir `For Each` döngü. Kullanıldığında içinde iç içe geçmiş `For Each` döngüler, `Exit For` iç içe geçme sonraki yüksek düzeyde en içteki döngü ve aktarımları denetimi'ndan çıkmak yürütme neden olur.  
  
 `Exit For`belli bir koşul bir değerlendirmesinden sonra sık kullanılan Örneğin, bir `If`... `Then`... `Else` yapısı. Kullanmak istediğiniz `Exit For` aşağıdaki koşulları için:  
  
-   Yinelemek etmeden gereksiz veya mümkün değil. Bunun nedeni hatalı bir değer veya bir sonlandırma isteği.  
  
-   İçinde bir özel durum yakalandı bir `Try`... `Catch`... `Finally`. Kullanabileceğinize `Exit For` sonunda `Finally` bloğu.  
  
-   Bir büyük veya hatta sonsuz sayıda çalışacak bir döngü sonsuz bir döngüde vardır. Böyle bir durum tespit ederse kullanabileceğiniz `Exit For` döngü kaçınmak için. Daha fazla bilgi için bkz: [yapın... Loop deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## <a name="iterators"></a>Yineleyiciler  
 Kullandığınız bir *yineleyici* özel bir yineleme içinde bir koleksiyon gerçekleştirmek için. Yineleyici bir işlev olabilir veya bir `Get` erişimcisi. Kullandığı bir `Yield` deyimi her birer birer koleksiyonun bir öğesi döndürür.  
  
 Yineleyici kullanarak çağırma bir `For Each...Next` deyimi. Her yinelemesinden `For Each` döngü yineleyici çağırır. Zaman bir `Yield` deyimi ifade yineleyici ulaşıldığında `Yield` deyimi döndürülür ve kod geçerli konumda korunur. Yürütme o konumdan yineleyici adlı bir sonraki başlatılışında yeniden başlatılır.  
  
 Aşağıdaki örnek, bir yineleyici işlevi kullanır. Yineleyici işlevinin bir `Yield` içinde deyimi bir [için... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü. İçinde `ListEvenNumbers` yöntemi, her yinelemesinden `For Each` deyimi gövde oluşturur diğerine geçer yineleyici işlevi çağrısı `Yield` deyimi.  
  
 [!code-vb[VbVbalrStatements#127](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_4.vb)]  
  
 Daha fazla bilgi için bkz: [yineleyiciler](../../programming-guide/concepts/iterators.md), [Yield deyimi](../../../visual-basic/language-reference/statements/yield-statement.md), ve [yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
## <a name="technical-implementation"></a>Teknik Uygulama  
 Zaman bir `For Each`...`Next` deyimi çalıştığında, Visual Basic koleksiyon yalnızca bir kez döngü başlamadan önce değerlendirir. Bir ifade bloğu değişirse `element` veya `group`, bu değişiklikleri döngü etkilemez.  
  
 Ne zaman koleksiyondaki tüm öğeleri sırayla atanan için `element`, `For Each` döngü durdurur ve denetim deyimi aşağıdaki geçer `Next` deyimi.  
  
 Varsa `element` kurmadı Bu döngü dışında bildirmelidir bildirilmiş içinde `For Each` deyimi. Türü bildirebilir `element` kullanarak açıkça bir `As` deyimi veya atamak için tür çıkarımı güvenebilirler. Her iki durumda da kapsamını `element` döngü gövdesi. Ancak, bildiremezsiniz `element` dışında hem döngü içinde.  
  
 İsteğe bağlı olarak belirtebilirsiniz `element` içinde `Next` deyimi. Özellikle, iç içe geçmiş durumunda bu programınızın okunabilirliğini artırır `For Each` döngüler. İlgili görüntülenen olarak aynı değişkeni belirtmeniz gerekir `For Each` deyimi.  
  
 Değerini değiştirmekten kaçınmak isteyebilirsiniz `element` döngü içinde. Bunun yapılması daha okuyun ve kodunuzun hatalarını ayıklamak üzere zorlaştırabilir. Değerinin değiştirilmesi `group` koleksiyonu veya döngü ilk girdiğinizde, belirlenen öğeleri, etkilemez.  
  
 Ne zaman, iç içe geçme döngüler, varsa bir `Next` önce bir dış iç içe geçirme düzeyi deyiminin karşılaştı `Next` bir iç düzeyini derleyici bir hata bildirir. Ancak, derleyici bu hata yalnızca belirtirseniz, çakışan algılayabilir `element` içinde her `Next` deyimi.  
  
 Belirli bir sırada bir koleksiyon geçiş kodunuzu bağımlı olması durumunda bir `For Each`... `Next` döngü en iyi seçenek değilse, numaralandırıcı nesne özelliklerini bilmiyorsanız koleksiyonu kullanıma sunar. Çapraz Geçişi sırasını Visual Basic, ancak göre belirlenen değil <xref:System.Collections.IEnumerator.MoveNext%2A> Numaralandırıcı nesnesinin yöntemi. Bu nedenle, hangi koleksiyonu içinde döndürülecek ilk öğesidir tahmin etmek mümkün olmayabilir `element`, ya da sonra belirli bir öğenin döndürülecek sonraki olduğu. Farklı döngü yapısı gibi kullanarak daha güvenilir sonuçlar elde edemezsiniz `For`... `Next` veya `Do`... `Loop`.  
  
 Veri türü `element` öğelerini veri türü gibi olmalıdır `group` kendisine dönüştürülebilir.  
  
 Veri türü `group` bir koleksiyon veya numaralandırılabilir bir dizi başvuran bir başvuru türü olmalıdır. Buna genellikle `group` uygulayan bir nesneye başvuruyor <xref:System.Collections.IEnumerable> arabiriminin `System.Collections` ad alanı veya <xref:System.Collections.Generic.IEnumerable%601> arabiriminin `System.Collections.Generic` ad alanı. `System.Collections.IEnumerable`tanımlar <xref:System.Collections.IEnumerable.GetEnumerator%2A> koleksiyonu için bir numaralandırıcı nesnesi döndüren yöntemi. Numaralandırıcı nesnesi uygulayan `System.Collections.IEnumerator` arabiriminin `System.Collections` ad alanı ve ortaya çıkaran <xref:System.Collections.IEnumerator.Current%2A> özelliği ve <xref:System.Collections.IEnumerator.Reset%2A> ve <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemleri. Visual Basic Bu koleksiyonu geçiş için kullanır.  
  
### <a name="narrowing-conversions"></a>Daraltma dönüşümleri  
 Zaman `Option Strict` ayarlanır `On`, daraltma dönüşümleri normalde derleyici hatalarına neden olabilir. İçinde bir `For Each` deyimi, ancak dönüşümleri öğelerde bulunan `group` için `element` değerlendirilir ve çalışma zamanında gerçekleştirilen ve daraltma dönüşümleri kaynaklanan derleyici hataları gizlenir.  
  
 Aşağıdaki örnekte, atanması `m` ilk değeri olarak `n` ne zaman derleme değil `Option Strict` üzerinde olduğundan dönüştürülmesi bir `Long` için bir `Integer` daraltma dönüştürme. İçinde `For Each` , ancak hiçbir derleyici hatası açıklamadır bildirilen, rağmen atamayı `number` aynı dönüştürme gerektirir `Long` için `Integer`. İçinde `For Each` büyük bir sayı içeren deyimi, bir çalışma zamanı hatası meydana zaman <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> sayıda uygulanır.  
  
 [!code-vb[VbVbalrStatements#89](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_5.vb)]  
  
### <a name="ienumerator-calls"></a>IEnumerator çağrıları  
 Zaman yürütülmesini bir `For Each`... `Next` döngü başlatır, Visual Basic doğrular `group` geçerli koleksiyon nesnesine başvuruyor. Aksi durumda, bir özel durum oluşturur. Aksi takdirde, çağıran <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi ve <xref:System.Collections.IEnumerator.Current%2A> özelliği Numaralandırıcı nesnenin ilk öğesini döndürür. Varsa `MoveNext` koleksiyonu boş ise, herhangi bir sonraki öğe başka bir deyişle, gösterir `For Each` döngü durdurur ve denetim deyimi aşağıdaki geçer `Next` deyimi. Aksi takdirde, Visual Basic ayarlar `element` ilk öğe ve ifade bloğu çalıştırır.  
  
 Visual Basic karşılaştığı her zaman `Next` deyiminin döndürdüğü için `For Each` deyimi. Yeniden çağırır `MoveNext` ve `Current` sonraki öğeye ve yeniden geri dönmek için blok çalışır veya sonucuna döngü durur. Kadar bu işlem devam `MoveNext` herhangi bir sonraki öğe gösterir ya da bir `Exit For` deyimi karşılaştı.  
  
 **Koleksiyon değiştirme.** Numaralandırıcı nesnesi tarafından döndürülen <xref:System.Collections.IEnumerable.GetEnumerator%2A> normalde koleksiyon ekleme, silme, değiştirme veya herhangi bir öğe yeniden sıralama değiştirmenize izin vermez. Koleksiyon, başlattıktan sonra değiştirirseniz bir `For Each`... `Next` döngü, numaralandırıcı nesnesi geçersiz hale gelir ve sonraki bir öğesine erişme girişimi neden olan bir <xref:System.InvalidOperationException> özel durum.  
  
 Ancak, bu değişikliği engelleme tarafından belirlenen değil [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], ancak bunun yerine uygulaması tarafından <xref:System.Collections.IEnumerable> arabirimi. Uygulamak mümkündür `IEnumerable` yineleme sırasında değişikliğe izin veren şekilde. Dinamik tür değişiklik yapılması düşünüyorsanız, özelliklerini anladığınızdan emin olun `IEnumerable` uygulama kullanmakta olduğunuz koleksiyonu.  
  
 **Koleksiyon öğeleri değiştirme.** <xref:System.Collections.IEnumerator.Current%2A> Numaralandırıcı nesnesi özelliği [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md), ve her koleksiyon öğesi yerel bir kopyasını döndürür. Bu öğeleri kendilerini değiştiremeyeceğiniz anlamına gelir, bir `For Each`... `Next` döngü. Yaptığınız değişiklikler yalnızca yerel kopyadan etkiler `Current` ve arka plandaki koleksiyona yansıtılan değil. Ancak, bir öğenin bir başvuru türü ise işaret ettiği örnek üyeleri değiştirebilir. Aşağıdaki örnek değiştirir `BackColor` her üyesi `thisControl` öğesi. Ancak, değiştiremezsiniz `thisControl` kendisi.  
  
```vb  
Sub lightBlueBackground(ByVal thisForm As System.Windows.Forms.Form)  
    For Each thisControl As System.Windows.Forms.Control In thisForm.Controls  
        thisControl.BackColor = System.Drawing.Color.LightBlue  
    Next thisControl  
End Sub  
```  
  
 Önceki örnekte değiştirebilirsiniz `BackColor` her üyesi `thisControl` öğesi, onu değiştiremezsiniz rağmen `thisControl` kendisi.  
  
 **Diziler çapraz geçiş yapma.** Çünkü <xref:System.Array> uygulayan sınıf <xref:System.Collections.IEnumerable> arabirimi, tüm dizileri ortaya <xref:System.Array.GetEnumerator%2A> yöntemi. Bu, bir dizi aracılığıyla yineleyebilirsiniz anlamına gelir. bir `For Each`... `Next` döngü. Ancak, dizi öğeleri yalnızca okuyabilir. Bunları değiştiremezsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek C:\ dizinindeki tüm klasörleri kullanarak listeler <xref:System.IO.DirectoryInfo> sınıfı.  
  
 [!code-vb[VbVbalrStatements#124](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_6.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir koleksiyon sıralamak için bir yordam gösterilmektedir. Örnek örneklerini sıralar bir `Car` depolanmış sınıfı bir <xref:System.Collections.Generic.List%601>. `Car` Uygulayan sınıf <xref:System.IComparable%601> gerektiren arabirimi <xref:System.IComparable%601.CompareTo%2A> uygulanan yöntemi.  
  
 Her çağrı <xref:System.IComparable%601.CompareTo%2A> yöntemi sıralama için kullanılan tek bir karşılaştırma yapar. Kullanıcı tarafından yazılan kodu `CompareTo` yöntemi başka bir nesnenin geçerli nesnenin her karşılaştırma için bir değer döndürür. Döndürülen değer olan geçerli nesne ise sıfırdan az diğerinden daha az nesne, geçerli nesne bir nesneden daha büyükse, sıfır ve sıfırdan büyük eşit olup olmadıkları. Bu, kodda daha fazla değerinden ölçütleri tanımlayın ve eşit olanak sağlar.  
  
 İçinde `ListCars` yöntemi, `cars.Sort()` deyimi listesini sıralar. Bu çağrıyı <xref:System.Collections.Generic.List%601.Sort%2A> yöntemi <xref:System.Collections.Generic.List%601> neden `CompareTo` yöntemi için otomatik olarak adlandırılan `Car` nesnelerini `List`.  
  
 [!code-vb[VbVbalrStatements#125](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_7.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Koleksiyonlar](../../../standard/collections/index.md)  
 [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Döngü Yapıları](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [While...End While Deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [Do...Loop Deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Öğe Başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [Diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md)
