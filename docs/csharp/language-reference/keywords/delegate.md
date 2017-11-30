---
title: "delegate (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 179e89cea0e683b72e57536d4e4d86b019493aed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="delegate-c-reference"></a>delegate (C# Başvurusu)
Bir temsilci türü bildirimi yöntemi imza benzer. Dönüş değeri ve parametreleri herhangi bir türde herhangi bir sayıda sahiptir:  
  
```  
public delegate void TestDelegate(string message);  
public delegate int TestDelegate(MyType m, long num);  
```  
  
 A `delegate` adlandırılmış kapsüllemek için kullanılan bir başvuru türü veya anonim bir yöntem. C++'ta işlev işaretçileri temsilciler benzer; Ancak, temsilciler tür kullanımı uyumlu ve güvenli değildir. Temsilciler uygulamalar için bkz [Temsilciler](../../../csharp/programming-guide/delegates/index.md) ve [genel temsilciler](../../../csharp/programming-guide/generics/generic-delegates.md).  
  
## <a name="remarks"></a>Açıklamalar  
 Temsilciler olan temelini [olayları](../../../csharp/programming-guide/events/index.md).  
  
 Bir temsilci, herhangi bir adlandırılmış ve anonim yöntemi ile ilişkilendirerek oluşturulabilir. Daha fazla bilgi için bkz: [adlı yöntemleri](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) ve [anonim yöntemler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).  
  
 Temsilci uyumlu bir dönüş türü ve giriş parametreleri olan bir yöntem veya lambda ifadesi ile örneğinin oluşturulması gerekir. Yöntem imzası izin farkı derecesini hakkında daha fazla bilgi için bkz: [Temsilcilerde varyans](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Anonim yöntemler ile kullanım için temsilci ve kod ile ilişkilendirilmesi birlikte bildirilir. Her iki yönde temsilcilerin örnek oluşturma, bu bölümde ele alınmıştır.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csrefKeywordsTypes#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/delegate_1.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Başvuru türleri](../../../csharp/language-reference/keywords/reference-types.md)  
 [Temsilciler](../../../csharp/programming-guide/delegates/index.md)  
 [Olayları](../../../csharp/programming-guide/events/index.md)  
 [Temsilciler adlandırılmış vs ile. Anonim yöntemler](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
 [Anonim yöntemler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
