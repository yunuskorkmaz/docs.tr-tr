---
title: "Alt İfade (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 43e35bd0386bc56478603ec36437981785cc8ffb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [İşleçler ve ifadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Deyimleri](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Gevşek temsilci dönüşümü](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
