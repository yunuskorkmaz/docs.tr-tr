---
title: Yield Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: 72a8dafdc5aa834a644e1e70a309cfc0827b5fdf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352720"
---
# <a name="yield-statement-visual-basic"></a>Yield Deyimi (Visual Basic)
Bir koleksiyonun Next öğesini bir `For Each...Next` ifadesine gönderir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Yield expression  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Terim|Tanım|  
|---|---|  
|`expression`|Gerekli. Yineleyici işlevinin türüne örtülü olarak dönüştürülebilir bir ifade veya `Yield` deyimini içeren `Get` erişimcisi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Yield` deyimin her seferinde bir koleksiyonun bir öğesi döndürür. `Yield` deyimin bir yineleyici işlevi veya bir koleksiyon üzerinde özel yinelemeler gerçekleştiren `Get` erişimcisi vardır.  
  
 For each ile bir yineleyici işlevi kullanıyorsunuz [... Sonraki Ifade](../../../visual-basic/language-reference/statements/for-each-next-statement.md) veya BIR LINQ sorgusu. `For Each` döngüsünün her yinelemesi yineleyici işlevini çağırır. Yineleyici işlevinde bir `Yield` ifadesine ulaşıldığında, `expression` döndürülür ve koddaki geçerli konum korunur. Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.  
  
 Örtük bir dönüştürme, `Yield` deyimindeki `expression` türünün, yineleyicinin dönüş türüne sahip olması gerekir.  
  
 Yinelemeyi sonlandırmak için bir `Exit Function` veya `Return` ifadesini kullanabilirsiniz.  
  
 "Yield" ayrılmış bir sözcük değildir ve yalnızca bir `Iterator` işlevinde veya `Get` erişimcisinde kullanıldığında özel anlamı vardır.  
  
 Yineleyici işlevleri ve `Get` erişimcileri hakkında daha fazla bilgi için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).  
  
## <a name="iterator-functions-and-get-accessors"></a>Yineleyici Işlevleri ve get erişimcileri  
 Yineleyici işlev veya `Get` erişimcisinin bildirimi aşağıdaki gereksinimleri karşılamalıdır:  
  
- [Yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md) değiştiricisi içermelidir.  
  
- Dönüş türü <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>veya <xref:System.Collections.Generic.IEnumerator%601>olmalıdır.  
  
- `ByRef` parametreye sahip olamaz.  
  
 Bir olay, örnek Oluşturucu, statik oluşturucu veya statik yok edicisi içinde Yineleyici işlevi oluşamaz.  
  
 Yineleyici işlevi anonim bir işlev olabilir. Daha fazla bilgi için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).  
  
## <a name="exception-handling"></a>Özel Durum İşleme  
 `Yield` bir ifade, TRY `Try` bloğunun içinde olabilir [... Yakala... Finally ekstresi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). `Yield` bildirimine sahip bir `Try` bloğunda `Catch` blokları olabilir ve bir `Finally` bloğuna sahip olabilir.  
  
 `Yield` bir ifade `Catch` bloğunun veya `Finally` bloğunun içinde olamaz.  
  
 `For Each` gövdesi (Yineleyici işlevi dışında) bir özel durum oluşturursa, yineleyici işlevindeki bir `Catch` bloğu yürütülmez, ancak Yineleyici işlevindeki bir `Finally` bloğu yürütülür. Yineleyici işlevi içindeki bir `Catch` bloğu yalnızca Yineleyici işlevinin içinde oluşan özel durumları yakalar.  
  
## <a name="technical-implementation"></a>Teknik Uygulama  
 Aşağıdaki kod bir yineleyici işlevinden `IEnumerable (Of String)` döndürür ve sonra `IEnumerable (Of String)`öğeleri boyunca yinelenir.  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 `MyIteratorFunction` çağrısı işlevin gövdesini yürütmez. Bunun yerine, çağrı `elements` değişkenine bir `IEnumerable(Of String)` döndürür.  
  
 `For Each` döngüsünün bir yinelemesi üzerinde `elements`için <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi çağırılır. Bu çağrı, sonraki `Yield` ifadesine ulaşılana kadar `MyIteratorFunction` gövdesini yürütür. `Yield` deyimi, yalnızca döngü gövdesine göre tüketim için `element` değişkeninin değerini değil, aynı zamanda bir `IEnumerable (Of String)`olan öğelerin <xref:System.Collections.Generic.IEnumerator%601.Current%2A> özelliğini de belirleyen bir ifade döndürür.  
  
 `For Each` döngüsünün sonraki tekrarında, yineleyici gövdesinin yürütülmesi kaldığınız yerden devam eder, bir `Yield` bildirimine ulaştığında yeniden durdurulur. Yineleyici işlevinin sonuna veya bir `Return` ya da `Exit Function` ifadeye ulaşıldığında `For Each` döngüsü tamamlanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Için içinde olan bir `Yield` ifadeye sahiptir [... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü. `Main` [for each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) deyimlerinin her yinelemesi, `Power` Yineleyici işlevine bir çağrı oluşturur. Yineleyici işlevine yapılan her çağrı, `For…Next` döngüsünün bir sonraki yinelemesi sırasında ortaya çıkan `Yield` deyimin bir sonraki yürütmeye ilerler.  
  
 Yineleyici yönteminin dönüş türü, bir Yineleyici arabirimi türü <xref:System.Collections.Generic.IEnumerable%601>. Yineleyici yöntem çağrıldığında, bir sayının kuvvetlerini içeren sayılabilir bir nesne döndürür.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yineleyici olan bir `Get` erişimcisini gösterir. Özellik bildirimi `Iterator` değiştirici içerir.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Ek örnekler için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Deyimler](../../../visual-basic/language-reference/statements/index.md)
