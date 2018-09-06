---
title: += İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: bd0997ec5b7d79a41e01f9c2b17533293e412c1e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43857513"
---
# <a name="-operator-c-reference"></a>+= İşleci (C# Başvurusu)
Toplama atama işleci.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ifade kullanarak `+=` atama işleci gibi  
  
```csharp  
x += y  
```  
  
 eşdeğerdir  
  
```csharp  
x = x + y  
```  
  
 dışında `x` yalnızca bir kez değerlendirilir. Anlamını [+ işleci](../../../csharp/language-reference/operators/addition-operator.md) türlerine bağlıdır `x` ve `y` (sayısal işlenenler, dize işlenenler ve benzeri için birleştirme için ek olarak).  
  
 `+=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [+ işleci](../../../csharp/language-reference/operators/addition-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).  
  
 `+=` İşleci ayrıca bir olaya yanıt olarak çağrılacak bir yöntem belirtmek için kullanılır; bu tür yöntemler olay işleyicileri olarak adlandırılır. Kullanımını `+=` bu bağlam içinde işleç olarak adlandırılır *bir olaya abone olma*. Daha fazla bilgi için [nasıl yapılır: abone olma ve aboneliği, olaylarından](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md) ve [Temsilciler](../../../csharp/programming-guide/delegates/index.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
