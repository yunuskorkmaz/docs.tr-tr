---
title: "AddressOf İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 52560a2d9071373fd28f7aad2e485da08324656d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="addressof-operator-visual-basic"></a>AddressOf İşleci (Visual Basic)
Özel yordam başvuruda bulunan bir yordam temsilci örneği oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a>Bölümler  
 `procedurename`  
 Gerekli. Yeni oluşturulan yordamı temsilci tarafından başvurulan yordamı belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 `AddressOf` İşleci tarafından belirtilen işlevin işaret eden bir işlev temsilcisi oluşturur `procedurename`. Örnek ve yöntemi için örnek yöntemi sonra işlev temsilcisi başvuruyor belirtilen yordam olduğunda. Ardından, işlev temsilcisi çağrıldığında belirtilen örneğinin belirtilen yöntem çağrılır.  
  
 `AddressOf` İşleci temsilci Oluşturucu işleneni olarak kullanılabilir veya hangi temsilci türü belirlenebilir derleyici tarafından bağlamda kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `AddressOf` işlemek için temsilci atamak işleci `Click` düğmesinin olay.  
  
 [!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `AddressOf` başlangıç işlevi için bir iş parçacığı atamak işleci.  
  
 [!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Temsilciler](../../../visual-basic/programming-guide/language-features/delegates/index.md)
