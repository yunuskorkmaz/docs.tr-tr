---
title: "İsteğe Bağlı (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3aa01c2c1ae731c8fe00fdee24521760db69e624
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="optional-visual-basic"></a>İsteğe Bağlı (Visual Basic)
Yordam çağrıldığında bir yordam bağımsız değişkenini atlanabilir belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 İsteğe bağlı her parametre için bir sabit ifadesine bu parametrenin varsayılan değeri olarak belirtmeniz gerekir. İfade değerlendirilirse [hiçbir şey](../../../visual-basic/language-reference/nothing.md), değer veri türünün varsayılan değeri parametresinin varsayılan değeri kullanılır.  
  
 Parametre listesi isteğe bağlı bir parametre içeriyorsa, kendisini izleyen her parametre ayrıca isteğe bağlı olmalıdır.  
  
 `Optional` Değiştiricisi bu bağlamlarında kullanılabilir:  
  
-   [Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  İle veya isteğe bağlı parametreler olmadan bir yordamı çağrılırken, konuma göre veya ada göre bağımsız değişkenler geçirebilirsiniz. Daha fazla bilgi için bkz: [geçirme bağımsız değişkenleri konuma ve ada göre](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).  
  
> [!NOTE]
>  İsteğe bağlı parametreleri olan bir yordamı aşırı yükleme kullanarak da tanımlayabilirsiniz. İsteğe bağlı bir parametre varsa, iki aşırı yüklenmiş yordamı, bir parametre kabul eden ve sürümleri olmayan bir tanımlayabilirsiniz. Daha fazla bilgi için bkz: [yordam aşırı yüklemesi](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, isteğe bağlı bir parametre olan bir yordam tanımlar.  
  
```  
Public Function FindMatches(ByRef values As List(Of String),  
                            ByVal searchString As String,  
                            Optional ByVal matchCase As Boolean = False) As List(Of String)  
  
    Dim results As IEnumerable(Of String)  
  
    If matchCase Then  
        results = From v In values  
                  Where v.Contains(searchString)  
    Else  
        results = From v In values  
                  Where UCase(v).Contains(UCase(searchString))  
    End If  
  
    Return results.ToList()  
End Function  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, konuma göre geçirilen bağımsız değişkenlerle ve ada göre geçirilen bağımsız değişkenlerle bir yordam çağırma gösterilmiştir. Yordamın iki isteğe bağlı parametreye sahiptir.  
  
 [!code-vb[VbVbalrKeywords#21](../../../visual-basic/language-reference/codesnippet/VisualBasic/optional_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [İsteğe bağlı parametreler](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [Anahtar sözcükler](../../../visual-basic/language-reference/keywords/index.md)
