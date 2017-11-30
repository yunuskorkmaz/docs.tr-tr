---
title: "-= İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 443f0d717288a491838d23eaa63218150bd346d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="--operator-c-reference"></a>-= İşleci (C# Başvurusu)
Çıkarma atama işleci.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ifade kullanılarak `-=` atama işleci gibi  
  
```  
x -= y  
```  
  
 eşdeğerdir  
  
```  
x = x - y  
```  
  
 dışında `x` yalnızca bir kez değerlendirilir. Anlamını [-işleci](../../../csharp/language-reference/operators/subtraction-operator.md) türleri üzerinde bağımlı `x` ve `y` (sayısal işlenenler için çıkarma kaldırma temsilci işlenenler için temsilci seçme ve benzeri).  
  
 `-=` İşleci olamaz aşırı yüklenebilir doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [-işleci](../../../csharp/language-reference/operators/subtraction-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).  
  
 -= İşleci ayrıca C# dilinde bir olaydan aboneliğinizi iptal etmek için kullanılır. Daha fazla bilgi için bkz: [nasıl yapılır: abone olma ve aboneliği olaylarından](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# işleçleri](../../../csharp/language-reference/operators/index.md)
