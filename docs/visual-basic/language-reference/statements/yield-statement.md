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
ms.openlocfilehash: cc89e6f9bc2ccb4fff9a9fe12cd190a6b2d212dc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401374"
---
# <a name="yield-statement-visual-basic"></a>Yield Deyimi (Visual Basic)
Bir koleksiyonun Next öğesini bir `For Each...Next` ifadeye gönderir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```vb  
Yield expression  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Terim|Tanım|  
|---|---|  
|`expression`|Gereklidir. İfadeyi içeren yineleyici işlevin veya erişimcinin türüne örtülü olarak dönüştürülebilir bir ifade `Get` `Yield` .|  
  
## <a name="remarks"></a>Açıklamalar  
 `Yield`İfade, aynı anda bir koleksiyonun bir öğesini döndürür. `Yield`İfade, `Get` bir koleksiyon üzerinde özel yinelemeler gerçekleştiren bir Yineleyici işlevine veya erişimciye dahil edilmiştir.  
  
 For each ile bir yineleyici işlevi kullanıyorsunuz [... Sonraki Ifade](for-each-next-statement.md) veya BIR LINQ sorgusu. Döngünün her yinelemesi `For Each` yineleyici işlevini çağırır. `Yield`Yineleyici işlevinde bir ifadeye ulaşıldığında, `expression` döndürülür ve koddaki geçerli konum korunur. Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.  
  
 Örtük dönüştürme, `expression` `Yield` deyimdeki türünden yineleyicinin dönüş türüne sahip olmalıdır.  
  
 `Exit Function` `Return` Yinelemeyi sonlandırmak için bir veya ifadesini kullanabilirsiniz.  
  
 "Yield" ayrılmış bir sözcük değildir ve yalnızca bir `Iterator` işlevde veya erişimcisinde kullanıldığında özel anlamı vardır `Get` .  
  
 Yineleyici işlevleri ve erişimcileri hakkında daha fazla bilgi için `Get` bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).  
  
## <a name="iterator-functions-and-get-accessors"></a>Yineleyici Işlevleri ve get erişimcileri  
 Yineleyici işlev veya `Get` erişimcinin bildirimi aşağıdaki gereksinimleri karşılamalıdır:  
  
- [Yineleyici](../modifiers/iterator.md) değiştiricisi içermelidir.  
  
- Dönüş türü <xref:System.Collections.IEnumerable> ,, veya olmalıdır <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator> <xref:System.Collections.Generic.IEnumerator%601> .  
  
- Herhangi bir parametreye sahip olamaz `ByRef` .  
  
 Bir olay, örnek Oluşturucu, statik oluşturucu veya statik yok edicisi içinde Yineleyici işlevi oluşamaz.  
  
 Yineleyici işlevi anonim bir işlev olabilir. Daha fazla bilgi için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).  
  
## <a name="exception-handling"></a>Özel Durum İşleme  
 Bir `Yield` ifade bir `Try` try bloğunun içinde olabilir [... Yakala... Finally ekstresi](try-catch-finally-statement.md). `Try`Bir deyime sahip bir blok `Yield` blokları olabilir `Catch` ve bir bloğuna sahip olabilir `Finally` .  
  
 Bir `Yield` ifade bir `Catch` blok veya blok içinde olamaz `Finally` .  
  
 `For Each`Gövde (Yineleyici işlevi dışında) bir özel durum oluşturursa, `Catch` Yineleyici işlevindeki bir blok yürütülmez, ancak `Finally` Yineleyici işlevindeki bir blok yürütülür. `Catch`Yineleyici işlevi içindeki bir blok yalnızca Yineleyici işlevinin içinde oluşan özel durumları yakalar.  
  
## <a name="technical-implementation"></a>Teknik Uygulama  
 Aşağıdaki kod bir `IEnumerable (Of String)` Yineleyici işlevinden bir döndürür ve sonra öğelerinin öğeleri boyunca yinelenir `IEnumerable (Of String)` .  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 Çağrısı, `MyIteratorFunction` işlevinin gövdesini yürütmez. Bunun yerine, çağrı `IEnumerable(Of String)` değişkenine bir döndürür `elements` .  
  
 Döngüsünün bir yinelemesinde `For Each` , <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi için çağrılır `elements` . Bu çağrı, `MyIteratorFunction` sonraki `Yield` ifadeye ulaşılana kadar gövdesini yürütür. `Yield`Deyimi, `element` döngü gövdesi tarafından tüketim için değişkenin değerini değil, aynı zamanda bir olan öğelerin özelliğini de belirleyen bir ifade döndürür <xref:System.Collections.Generic.IEnumerator%601.Current%2A> `IEnumerable (Of String)` .  
  
 Döngünün sonraki tekrarında `For Each` , yineleyici gövdesinin yürütülmesi kaldığınız yerden devam eder, bir ifadeye ulaştığında yeniden durdurulur `Yield` . `For Each`Döngü, Yineleyici işlevinin veya `Return` or ifadesinin sonuna ulaşıldığında tamamlanır `Exit Function` .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Yield` için içinde olan bir ifadeye sahiptir [... Sonraki](for-next-statement.md) döngü. İçindeki [her bir for](for-each-next-statement.md) Ifadesinin gövdesi için her yineleme, `Main` Yineleyici işlevine bir çağrı oluşturur `Power` . Yineleyici işlevine yapılan her çağrı, `Yield` döngüsünün bir sonraki yinelemesi sırasında ortaya çıkan deyimin bir sonraki yürütmeye ilerler `For…Next` .  
  
 Yineleyici yönteminin dönüş türü <xref:System.Collections.Generic.IEnumerable%601> , bir Yineleyici arabirimi türüdür. Yineleyici yöntem çağrıldığında, bir sayının kuvvetlerini içeren sayılabilir bir nesne döndürür.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Get` Yineleyici olan bir erişimciyi gösterir. Özellik bildirimi bir değiştirici içerir `Iterator` .  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Ek örnekler için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Deyimler](index.md)
