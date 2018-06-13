---
title: += İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: bcd56acad8e2b08585e5ae60f1c3cf8183b5664a
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171885"
---
# <a name="-operator-c-reference"></a>+= İşleci (C# Başvurusu)
Toplama atama işleci.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ifade kullanılarak `+=` atama işleci gibi  
  
```csharp  
x += y  
```  
  
 eşdeğerdir  
  
```csharp  
x = x + y  
```  
  
 dışında `x` yalnızca bir kez değerlendirilir. Anlamını [+ işleci](../../../csharp/language-reference/operators/addition-operator.md) türlerine bağlıdır `x` ve `y` (toplama sayısal işlenenler, dize işlenenleri ve benzeri için birleştirme).  
  
 `+=` İşleci olamaz aşırı yüklenebilir doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [+ işleci](../../../csharp/language-reference/operators/addition-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).  
  
 `+=` İşleci bir olaya yanıt olarak çağrılacak bir yöntem belirtmek için de kullanılır; bu tür yöntemleri olay işleyicileri çağırılır. Kullanımını `+=` bu bağlamda işleci olarak adlandırılır *bir olaya abone*. Daha fazla bilgi için bkz: [nasıl yapılır: abone olma ve aboneliği olaylarından](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md) ve [Temsilciler](../../../csharp/programming-guide/delegates/index.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
