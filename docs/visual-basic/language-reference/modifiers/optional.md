---
title: İsteğe Bağlı (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: 67ceedffecdfba8ec0c2829a3af31d194f18bd88
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820795"
---
# <a name="optional-visual-basic"></a>İsteğe Bağlı (Visual Basic)
Yordam çağrıldığında bir yordam bağımsız değişkeninin atlanabileceğini belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 İsteğe bağlı her parametre için bir sabit ifade bu parametrenin varsayılan değeri olarak belirtmeniz gerekir. İfade değerlendirme sonucu [hiçbir şey](../../../visual-basic/language-reference/nothing.md), değer veri türünün varsayılan değeri, parametrenin varsayılan değeri kullanılır.  
  
 Parametre listesi isteğe bağlı bir parametre içeriyorsa, onu takip eden her parametre de isteğe bağlı olmalıdır.  
  
 `Optional` Bu bağlamda değiştirici kullanılabilir:  
  
-   [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  İsteğe bağlı parametrelerle veya parametresiz bir yordamı çağrılırken, konuma veya ada göre bağımsız değişkenler geçirebilirsiniz. Daha fazla bilgi için [geçirmeden bağımsız değişkenleri konuma ve ada göre](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).  
  
> [!NOTE]
>  İsteğe bağlı parametreler içeren bir yordamı aşırı yükleme kullanarak da tanımlayabilirsiniz. İsteğe bağlı bir parametre varsa, iki aşırı yüklenmiş yordamı, bir parametreyi kabul eden ve sürümleri olmayan bir tanımlayabilirsiniz. Daha fazla bilgi için [yordam aşırı yüklemesi](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir isteğe bağlı parametresi olan bir yordam tanımlar.  
  
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
 Aşağıdaki örnek, ada göre geçirilen bağımsız değişkenler ve konuma göre geçirilen bağımsız değişkenler ile bir yordam çağırma gösterilmektedir. Yordamı, iki isteğe bağlı parametreye sahiptir.  
  
 [!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Parametre Listesi](../../../visual-basic/language-reference/statements/parameter-list.md)
- [İsteğe Bağlı Parametreler](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
