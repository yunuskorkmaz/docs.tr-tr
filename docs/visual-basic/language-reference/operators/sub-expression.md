---
title: Alt İfade (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: d27ca262aa2349d34d78844e0aea0f96a1ced65c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496315"
---
# <a name="sub-expression-visual-basic"></a>Alt İfade (Visual Basic)
Parametreleri ve kodu tanımlayan bir alt yordam lambda ifadesi bildirir.  
  
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
|`parameterlist`|İsteğe bağlı. Yordam parametreleri temsil eden yerel değişken adlarının listesi. Liste boş olduğunda bile parantezler bulunmalıdır. Daha fazla bilgi için [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`statement`|Gerekli. Tek bir deyim.|  
|`statements`|Gerekli. Deyimleri listesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 A *lambda ifadesi* bir ada sahip bir alt yordam olduğunu ve, bir veya daha fazla deyimi yürütür. Bir lambda ifadesi her yerde kullanabilirsiniz, bir temsilci türü dışında bir bağımsız değişken olarak kullanabileceğiniz `RemoveHandler`. Temsilciler ve lambda ifadeleri temsilciler ile kullanımı hakkında daha fazla bilgi için bkz. [temsilci bildirimi](../../../visual-basic/language-reference/statements/delegate-statement.md) ve [gevşek temsilci dönüşümü](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Lambda İfadesi Sözdizimi  
 Bir lambda ifadesi söz dizimi, standart bir alt yordam benzer. Farklar aşağıdaki gibidir:  
  
-   Bir lambda ifadesi, bir adı yok.  
  
-   Bir lambda ifadesi bir değiştirici gibi olamaz `Overloads` veya `Overrides`.  
  
-   Tek satırlı lambda ifadesinin gövdesi bir deyim, bir ifade olmalıdır. Gövde, bir alt yordam çağrısı, ancak bir işlev yordam çağrısı değil, oluşabilir.  
  
-   Bir lambda ifadesinde veri türleri veya tüm parametreleri anlaşılmalıdır tüm parametre ya da belirtmelisiniz.  
  
-   İsteğe bağlı ve `ParamArray` parametreleri lambda ifadelerine izin verilmez.  
  
-   Genel Parametreler lambda ifadelerine izin verilmez.  
  
## <a name="example"></a>Örnek  
 Bir değer konsola yazar bir lambda ifadesi örneği verilmiştir. Bu örnek, hem tek satır ve çok satırlı lambda ifadesi sözdizimi bir alt yordam gösterir. Daha fazla örnek için bkz. [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/sub-expression_1.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Lambda İfadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [İşleçler ve İfadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
- [Gevşek Temsilci Dönüştürme](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
