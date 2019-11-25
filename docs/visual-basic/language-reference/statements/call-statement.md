---
title: Call Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: 7de194ea23827e08c49f4519c1000708a4bd91b4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350156"
---
# <a name="call-statement-visual-basic"></a>Call Deyimi (Visual Basic)

Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>Bölümler  

|||
|---|---|
|`procedureName`|Gerekli. Name of the procedure to call.|
|`argumentList`|İsteğe bağlı. List of variables or expressions representing arguments that are passed to the procedure when it is called. Multiple arguments are separated by commas. If you include `argumentList`, you must enclose it in parentheses.|
|||
  
## <a name="remarks"></a>Açıklamalar

 You can use the `Call` keyword when you call a procedure. For most procedure calls, you aren’t required to use this  keyword.

 You typically use the `Call` keyword when the called expression doesn’t start with an identifier. Use of the `Call` keyword for other uses isn't recommended.

 If the procedure returns a value, the `Call` statement discards it.

## <a name="example"></a>Örnek

 The following code shows two examples where the `Call` keyword is necessary to call a procedure. In both examples, the called expression doesn't start with an identifier.

 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Function Deyimi](function-statement.md)
- [Sub Deyimi](sub-statement.md)
- [Declare Deyimi](declare-statement.md)
- [Lambda İfadeleri](../../programming-guide/language-features/procedures/lambda-expressions.md)
