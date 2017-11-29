---
title: "+= İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 91286b3c6b9a7239bcd5d5bac0ef08bfd7fa8345
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>+= İşleci (C# Başvurusu)
Toplama atama işleci.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ifade kullanılarak `+=` atama işleci gibi  
  
```  
x += y  
```  
  
 eşdeğerdir  
  
```  
x = x + y  
```  
  
 dışında `x` yalnızca bir kez değerlendirilir. Anlamını [+ işleci](../../../csharp/language-reference/operators/addition-operator.md) türlerine bağlıdır `x` ve `y` (toplama sayısal işlenenler, dize işlenenleri ve benzeri için birleştirme).  
  
 `+=` İşleci olamaz aşırı yüklenebilir doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [+ işleci](../../../csharp/language-reference/operators/addition-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).  
  
 `+=` İşleci bir olaya yanıt olarak çağrılacak bir yöntem belirtmek için de kullanılır; bu tür yöntemleri olay işleyicileri çağırılır. Kullanımını `+=` bu bağlamda işleci olarak adlandırılır *bir olaya abone*. Daha fazla bilgi için bkz: [nasıl yapılır: abone olma ve aboneliği olaylarından](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md). ve [Temsilciler](../../../csharp/programming-guide/delegates/index.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# işleçleri](../../../csharp/language-reference/operators/index.md)
