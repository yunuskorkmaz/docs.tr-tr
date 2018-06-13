---
title: Alt İfade (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 602212e664fa3362742fb1ba0dc033610272d3af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603541"
---
# <a name="sub-expression-visual-basic"></a>Alt İfade (Visual Basic)
Parametreler ve alt yordama lambda ifadesi tanımlamak kod bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`parameterlist`|İsteğe bağlı. Yordam parametreleri temsil eden yerel değişken adları listesi. Parantez listesi boş olsa bile mevcut olması gerekir. Daha fazla bilgi için bkz: [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`statement`|Gerekli. Tek bir deyimde.|  
|`statements`|Gerekli. Deyimleri listesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 A *lambda ifadesi* bir ada sahip olmayan bir alt yordama olduğunu ve bir veya daha fazla deyimleri yürütür. Lambda ifadesi yerde kullanabilir, bir temsilci türü dışında bağımsız değişken olarak kullanabileceğiniz `RemoveHandler`. Temsilciler ve temsilciler ile lambda ifadeleri kullanma hakkında daha fazla bilgi için bkz: [temsilci deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md) ve [gevşek temsilci dönüşümü](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Lambda İfadesi Sözdizimi  
 Lambda ifadesi sözdizimi, standart bir alt yordama benzer. Farkları aşağıdaki gibidir:  
  
-   Lambda ifadesi bir adı yok.  
  
-   Lambda ifadesi bir değiştiricisi gibi olamaz `Overloads` veya `Overrides`.  
  
-   Tek satırlı lambda ifadesi gövdesi bir deyim, bir ifade olmalıdır. Gövde alt yordam çağrısı, ancak olmayan bir işlev yordamı çağrısı oluşabilir.  
  
-   Lambda ifadesinde, veri türleri veya tüm parametreleri olayla gerekir ya da tüm parametreleri belirtilmelidir.  
  
-   İsteğe bağlı ve `ParamArray` parametreleri lambda ifadelerde izin verilmez.  
  
-   Genel Parametreler lambda ifadelerde izin verilmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki değer konsola yazar bir lambda ifadesi bir örnektir. Aşağıdaki örnekte, hem tek satırlı ve çok satırlı lambda ifadesi sözdizimi alt yordam için gösterilir. Daha fazla örnek için bkz: [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/sub-expression_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Lambda İfadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [İşleçler ve İfadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Gevşek Temsilci Dönüştürme](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
