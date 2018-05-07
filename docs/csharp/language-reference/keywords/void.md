---
title: void (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: e66efc287fc3ed0fcc15963a827fccb788c38753
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="void-c-reference"></a>void (C# Başvurusu)
Bir yöntemi, dönüş türü olarak kullanıldığında `void` yöntemi bir değer döndürmüyor belirtir.

`void` bir yöntemin parametre listesinde izin verilmiyor. Hiçbir parametre alan ve herhangi bir değer döndüren bir yöntem aşağıdaki gibi bildirilmiş:

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

`void` Ayrıca güvensiz bir bağlamda bilinmeyen bir tür için bir işaretçi bildirmek için kullanılır. Daha fazla bilgi için bkz: [işaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).

`void` .NET Framework için bir diğer ad olduğu <xref:System.Void?displayProperty=nameWithType> türü.

## <a name="c-language-specification"></a>C# Dil Belirtimi
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Başvuru Türleri](../../../csharp/language-reference/keywords/reference-types.md)  
 [Değer Türleri](../../../csharp/language-reference/keywords/value-types.md)  
 [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Güvenli Olmayan Kod ve İşaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
