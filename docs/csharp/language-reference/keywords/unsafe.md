---
title: unsafe (C# Başvurusu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1fffbe36e39d279b2364b178188381a403c8ff86
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="unsafe-c-reference"></a>unsafe (C# Başvurusu)
`unsafe` Anahtar sözcüğü işaretçileri içeren herhangi bir işlem için gereken bir güvenli bağlamı gösterir. Daha fazla bilgi için bkz: [güvenli olmayan kod ve işaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md).  
  
 Kullanabileceğiniz `unsafe` bir tür ya da bir üye bildiriminde değiştiricisi. Bu nedenle tür veya üye tüm metinsel kapsamını güvenli olmayan içerik olarak kabul edilir. Örneğin, aşağıdaki ile bildirilen bir yöntemdir `unsafe` değiştiricisi:  
  
```  
      unsafe static void FastCopy(byte[] src, byte[] dst, int count)  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 İşaretçileri parametre listesinde de kullanılabilmesi için güvenli olmayan içerik kapsamını parametre listeden yönteminin sonuna genişletir:  
  
```  
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}  
```  
  
 Güvenli olmayan bir blok, bir güvenli olmayan kod bu bloktaki kullanımını etkinleştirmek için de kullanabilirsiniz. Örneğin:  
  
```  
      unsafe  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 Güvenli olmayan kod derlemek için belirtmeniz gerekir [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği. Güvenli olmayan kod ortak dil çalışma zamanı tarafından doğrulanabilen değil.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csrefKeywordsModifiers#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/unsafe_1.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [fixed deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [Güvenli olmayan kod ve işaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Sabit boyutlu arabellekler](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
