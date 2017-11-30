---
title: "void (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords: void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a71cac30132417abce60cdde54322b5f2067d39d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="void-c-reference"></a>void (C# Başvurusu)
Bir yöntemi, dönüş türü olarak kullanıldığında `void` yöntemi bir değer döndürmüyor belirtir.

`void`bir yöntemin parametre listesinde izin verilmiyor. Hiçbir parametre alan ve herhangi bir değer döndüren bir yöntem aşağıdaki gibi bildirilmiş:

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

`void`Ayrıca güvensiz bir bağlamda bilinmeyen bir tür için bir işaretçi bildirmek için kullanılır. Daha fazla bilgi için bkz: [işaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).

`void`.NET Framework için bir diğer ad olduğu <xref:System.Void?displayProperty=nameWithType> türü.

## <a name="c-language-specification"></a>C# Dil Belirtimi
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Başvuru türleri](../../../csharp/language-reference/keywords/reference-types.md)  
 [Değer türleri](../../../csharp/language-reference/keywords/value-types.md)  
 [Yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Güvenli olmayan kod ve işaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
