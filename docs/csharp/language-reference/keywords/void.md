---
title: void (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 223db893dd42181c234d9a07c1a1c00af26f0c30
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46325857"
---
# <a name="void-c-reference"></a>void (C# Başvurusu)
Bir yöntem için dönüş türü olarak kullanıldığında `void` yöntemi bir değer döndürmediğini belirtir.

`void` bir yöntemin parametre listesinde izin verilmez. Hiçbir parametre almayan ve hiçbir değer döndürmeyen bir yöntem şu şekilde bildirilir:

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

`void` Ayrıca güvenli olmayan bir bağlamda, bir işaretçi türü bilinmiyor bildirmek için kullanılır. Daha fazla bilgi için [işaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).

`void` .NET Framework için bir diğer addır <xref:System.Void?displayProperty=nameWithType> türü.

## <a name="c-language-specification"></a>C# Dil Belirtimi
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [Başvuru Türleri](../../../csharp/language-reference/keywords/reference-types.md)  
- [Değer Türleri](../../../csharp/language-reference/keywords/value-types.md)  
- [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)  
- [Güvenli Olmayan Kod ve İşaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
