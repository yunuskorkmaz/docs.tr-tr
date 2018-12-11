---
title: -= İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: dc3cedafc57e1c6ec9bc34ca4e2c2aa9c604848c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239592"
---
# <a name="--operator-c-reference"></a>-= İşleci (C# Başvurusu)
Çıkarma atama işleci.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ifade kullanarak `-=` atama işleci gibi  
  
```csharp  
x -= y  
```  
  
 eşdeğerdir  
  
```csharp  
x = x - y  
```  
  
 dışında `x` yalnızca bir kez değerlendirilir. Anlamını [-işleci](../../../csharp/language-reference/operators/subtraction-operator.md) türlerine bağlıdır `x` ve `y` (sayısal işlenenler için çıkarma temsilci temsilcinin işlenenleri için temizleme vb.).  
  
 `-=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [-işleci](../../../csharp/language-reference/operators/subtraction-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).  
  
 -= İşleci ayrıca C# dilinde bir olayın aboneliğini kaldırmak için kullanılır. Daha fazla bilgi için [nasıl yapılır: Abone olma ve aboneliği olaylardan](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
