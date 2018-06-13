---
title: () İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 2ded01ef3192e0f34d586cd63d93b894b5347e7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275031"
---
# <a name="-operator-c-reference"></a>() İşleci (C# Başvurusu)
Bir ifadeyi işlemlerin sırasını belirlemek için kullanılan ek olarak, parantez aşağıdaki görevleri gerçekleştirmek için kullanılır:  
  
1.  Atamaları belirtin veya türü dönüşümleri.  
  
     [!code-csharp[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  Yöntemler veya temsilciler çağırır.  
  
     [!code-csharp[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a>Açıklamalar  
 Bir cast açıkça başka bir türden diğerine dönüştürme işleci çağırır; Bu tür bir dönüşüm işleci tanımlanan dönüştürme başarısız olur. Bir dönüşüm işleci tanımlama için bkz: [açık](../../../csharp/language-reference/keywords/explicit.md) ve [örtük](../../../csharp/language-reference/keywords/implicit.md).  
  
 `()` İşleci olamaz aşırı yüklenebilir.  
  
 Daha fazla bilgi için bkz: [atama ve tür dönüşümleri](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
 Cast ifadesi belirsiz sözdizimine yol açabilir. Örneğin, ifade `(x)–y` ya da bir cast ifadesi (– tür x y cast) veya bir ADDITIVE olarak yorumlanabilecek x – değeri hesaplar ve parantez içine alınmış ifade ile birlikte ifade y.  
  
 Yöntem çağırma hakkında daha fazla bilgi için bkz: [yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
