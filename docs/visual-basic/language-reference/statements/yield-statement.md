---
title: Yield Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0bc2f5c2dca1fbd6039f10ddd6204673f60a679d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="yield-statement-visual-basic"></a>Yield Deyimi (Visual Basic)
Bir koleksiyona sonraki öğeye gönderir bir `For Each...Next` deyimi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Yield expression  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Terim|Tanım|  
|---|---|  
|`expression`|Gerekli. Yineleyici işlevi türüne örtük olarak dönüştürülebilir bir deyim veya `Get` içeren erişimcisi `Yield` deyimi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Yield` Deyimi bir seferde bir koleksiyonun bir öğesi döndürür. `Yield` Deyimi bir yineleyici işlevinde dahil veya `Get` içinde bir koleksiyon özel yineleme gerçekleştirmek erişimcisi.  
  
 İle bir yineleyici işlevi kullanmasını bir [For Each... Sonraki deyim](../../../visual-basic/language-reference/statements/for-each-next-statement.md) veya bir LINQ Sorgu. Her yinelemesinden `For Each` döngü yineleyici işlevi çağırır. Zaman bir `Yield` deyimi yineleyici işlevinde ulaşıldığında `expression` döndürülür ve kod geçerli konumda korunur. Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.  
  
 Örtük bir dönüştürme türünden bulunmalıdır `expression` içinde `Yield` yineleyici dönüş türü bildirimi.  
  
 Kullanabileceğiniz bir `Exit Function` veya `Return` yinelemeyi sonlandırmak için deyimi.  
  
 "Verim" ayrılmış bir sözcük değildir ve yalnızca içinde kullanıldığında, özel bir anlamı olan bir `Iterator` işlevi veya `Get` erişimcisi.  
  
 Yineleyici işlevleri hakkında daha fazla bilgi için ve `Get` erişimciler, bkz: [yineleyiciler](../../programming-guide/concepts/iterators.md).  
  
## <a name="iterator-functions-and-get-accessors"></a>Yineleyici işlevleri ve Get erişimcisi  
 Yineleyici işlevin bildirimi veya `Get` erişimci aşağıdaki gereksinimleri karşılaması gerekir:  
  
-   İçermesi gerekir bir [yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md) değiştiricisi.  
  
-   Dönüş türü olmalıdır <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.  
  
-   Bunu içeremez `ByRef` parametreleri.  
  
 Yineleyici işlevi, bir olay, örnek oluşturucusu, statik Oluşturucusu veya statik yıkıcı gerçekleşemez.  
  
 Yineleyici işlevi adsız bir işlev olabilir. Daha fazla bilgi için bkz: [yineleyiciler](../../programming-guide/concepts/iterators.md).  
  
## <a name="exception-handling"></a>Özel Durum İşleme  
 A `Yield` deyimi içinde bulunabilir bir `Try` , engelleme bir [deneyin... Catch... Finally ifadesi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). A `Try` sahip blok bir `Yield` deyimi olabilir `Catch` engeller ve olabilir bir `Finally` bloğu.  
  
 A `Yield` deyimi içinde olamaz bir `Catch` blok veya `Finally` bloğu.  
  
 Varsa `For Each` gövdesi (dışında yineleyici işlevi) bir özel durum oluşturur bir `Catch` yineleyici işlevi bloğunda yürütülmez, ancak bir `Finally` yineleyici işlevi bloğunda gerçekleştirilir. A `Catch` yineleyici işlevi bloğunda yineleyici işlevinin içinde oluşan özel durumlarını yakalar.  
  
## <a name="technical-implementation"></a>Teknik Uygulama  
 Aşağıdaki kod döndürür bir `IEnumerable (Of String)` yineleyici işlevden ve öğelerinde yineleme `IEnumerable (Of String)`.  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 Çağrı `MyIteratorFunction` işlevinin gövdesini yürütmez. Bunun yerine çağrı döndürür bir `IEnumerable(Of String)` içine `elements` değişkeni.  
  
 Bir yineleme `For Each` döngü, <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi için çağrılır `elements`. Bu çağrı gövdesini yürütür `MyIteratorFunction` sonraki kadar `Yield` deyimi ulaşıldığında. `Yield` Deyimi yalnızca değerini belirleyen bir ifade döndürür `element` döngü gövdesine tüketimi için değişken aynı zamanda <xref:System.Collections.Generic.IEnumerator%601.Current%2A> olan özelliği öğelerinin bir `IEnumerable (Of String)`.  
  
 Sonraki her yinelemesinden üzerinde `For Each` nereden yürütülmeye yineleyici gövdesinin döngü ulaştığında yeniden durdurma kapalı, solda bir `Yield` deyimi. `For Each` Döngüsü tamamlandıktan yineleyici işlevi sonuna veya `Return` veya `Exit Function` deyimi ulaşıldığında.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek sahip bir `Yield` içinde deyimi bir [için... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü. Her yinelemesinden [her](../../../visual-basic/language-reference/statements/for-each-next-statement.md) deyiminin gövdesinde `Main` yapılan bir çağrı oluşturur `Power` yineleyici işlevi. Yineleyici işlevi her çağrısı devam eder, sonraki yürütülmesi `Yield` sonraki yinelemesini sırasında oluşur deyimi `For…Next` döngü.  
  
 Yineleyici yöntemin dönüş türü <xref:System.Collections.Generic.IEnumerable%601>, bir yineleyici arabirimi türü. Yineleyici yöntem çağrıldığında, bir sayının kuvvetlerini içeren sayılabilir bir nesne döndürür.  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterilmiştir bir `Get` yineleyici olduğu erişimcisi. Özellik bildirimi içeren bir `Iterator` değiştiricisi.  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_2.vb)]  
  
 Ek örnekler için bkz: [yineleyiciler](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Deyimler](../../../visual-basic/language-reference/statements/index.md)
