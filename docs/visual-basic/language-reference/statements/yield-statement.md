---
title: Yield Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: e417e13f1617f3ad8064c9e1b0eec835938b6200
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978927"
---
# <a name="yield-statement-visual-basic"></a>Yield Deyimi (Visual Basic)
Bir koleksiyona sonraki öğeye gönderen bir `For Each...Next` deyimi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Yield expression  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Terim|Tanım|  
|---|---|  
|`expression`|Gerekli. Yineleyici işleve türüne örtük olarak dönüştürülebilir bir ifade veya `Get` içeren erişimci `Yield` deyimi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Yield` Deyimi aynı anda bir koleksiyonun bir öğesi döndürür. `Yield` Deyimi bir yineleyici işlevinde dahil veya `Get` form veya erişimci bir koleksiyon üzerinde özel yineleme gerçekleştirin.  
  
 Kullanarak bir yineleyici işlevi tükettiğiniz bir [her biri için... Sonraki deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md) veya LINQ sorgusu. Her bir yinelemesini `For Each` döngüsü yineleyici işlevi çağırır. Olduğunda bir `Yield` yineleyici işlevinde deyimine ulaşıldığında `expression` döndürülür ve kodun geçerli konumu korunur. Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.  
  
 Örtük bir dönüştürme türünden bulunmalıdır `expression` içinde `Yield` deyimi için dönüş türü yineleyici.  
  
 Kullanabileceğiniz bir `Exit Function` veya `Return` yinelemeyi sonlandırmak için deyimi.  
  
 "Yield" ayrılmış bir sözcük değildir ve yalnızca içinde kullanıldığında özel anlamı bir `Iterator` işlevi veya `Get` erişimcisi.  
  
 Yineleyici işlevleri hakkında daha fazla bilgi ve `Get` erişimcileri bkz [yineleyiciler](../../programming-guide/concepts/iterators.md).  
  
## <a name="iterator-functions-and-get-accessors"></a>Yineleyici işlevleri ve Get erişimcileri  
 Bir yineleyici işlevin bildirimi ya da `Get` erişimci aşağıdaki gereksinimleri karşılaması gerekir:  
  
-   Bunu içermelidir bir [yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md) değiştiricisi.  
  
-   Dönüş türü olmalıdır <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.  
  
-   Bunu içeremez `ByRef` parametreleri.  
  
 Bir yineleyici işlevine bir olay, örnek oluşturucusu, statik oluşturucu veya statik yok Edicisi olamaz.  
  
 Bir yineleyici işlevi anonim bir işlevdir olabilir. Daha fazla bilgi için [yineleyiciler](../../programming-guide/concepts/iterators.md).  
  
## <a name="exception-handling"></a>Özel Durum İşleme  
 A `Yield` deyimi içinde olabilir bir `Try` bloğu bir [deneyin... Catch... Finally deyimini](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). A `Try` sahip blok bir `Yield` deyimi olabilir `Catch` engeller ve olabilir bir `Finally` blok.  
  
 A `Yield` deyimi içinde olamaz bir `Catch` blok veya `Finally` blok.  
  
 Varsa `For Each` gövdesi (yineleyici işleve dışında) bir özel durum oluşturursa bir `Catch` yineleyici işleve bloğunda yürütülmedi, ancak bir `Finally` yineleyici işleve bloğunda yürütülür. A `Catch` blok içinde bir yineleyici işlevi yineleyici işlevde oluşan özel durumları yakalar.  
  
## <a name="technical-implementation"></a>Teknik Uygulama  
 Aşağıdaki kod döndürür bir `IEnumerable (Of String)` yineleyici işlevi ve ardından öğeleri yinelenir `IEnumerable (Of String)`.  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 Çağrı `MyIteratorFunction` işlev gövdesini yürütmez. Bunun yerine çağrı döndürür bir `IEnumerable(Of String)` içine `elements` değişkeni.  
  
 Yinelemesi üzerinde `For Each` döngü <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi için çağrılır `elements`. Bu çağrı gövdesini yürütür `MyIteratorFunction` sonraki kadar `Yield` deyimine ulaşıldığında. `Yield` Deyimi yalnızca değerini belirleyen bir ifade döndürür `element` döngü gövdesinin tüketimi için değişken aynı zamanda <xref:System.Collections.Generic.IEnumerator%601.Current%2A> olan özellik öğelerinin bir `IEnumerable (Of String)`.  
  
 Her yinelemesinde `For Each` kadar yineleyici gövdenin yürütülmesi devam eder, döngü onu ulaştığında yeniden kaldığı bir `Yield` deyimi. `For Each` Tamamlandıktan döngüsü yineleyici işlevin sonuna veya bir `Return` veya `Exit Function` deyimine ulaşıldığında.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek sahip bir `Yield` içindeki bir [için... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü. Her bir yinelemesini [her](../../../visual-basic/language-reference/statements/for-each-next-statement.md) deyiminin gövdesinde `Main` bir çağrı oluşturur `Power` yineleyici işlevi. Her yineleyici işleve çağrı için sonraki yürütme devam eder `Yield` sıradaki yinelemesi süresince gerçekleşen deyimi `For…Next` döngü.  
  
 Yineleyici yöntemin dönüş türü <xref:System.Collections.Generic.IEnumerable%601>, bir yineleyici arabirimi türü. Yineleyici yöntem çağrıldığında, bir sayının kuvvetlerini içeren sayılabilir bir nesne döndürür.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, gösterir bir `Get` bir yineleyici erişimcisi. Özellik bildirimi içeren bir `Iterator` değiştiricisi.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Diğer örnekler için [yineleyiciler](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Deyimler](../../../visual-basic/language-reference/statements/index.md)
