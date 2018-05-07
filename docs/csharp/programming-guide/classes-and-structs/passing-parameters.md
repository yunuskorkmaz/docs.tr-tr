---
title: Parametreleri Geçirme (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: a1ccfff8081d101eee46360009653b0591dfb3ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="passing-parameters-c-programming-guide"></a>Parametreleri Geçirme (C# Programlama Kılavuzu)
C# ' ta bağımsız değişken parametreleri değere veya başvuruya göre geçirilebilir. Başvuruya göre geçirme etkinleştirir işlevi üyeleri, yöntemler, özellikler, dizin oluşturucular, işleçler ve parametre değerini değiştirin ve bu değişikliği oluşturucular arama ortamda kalır. Bir parametre değeri değiştirmenin amacıyla başvuruya geçirmek için kullanmak `ref`, veya `out` anahtar sözcüğü. Kopyalama ancak değerini değiştirmeyi değil önleme amacıyla başvuruya geçirmek için kullanmak `in` değiştiricisi. Basitlik, yalnızca için `ref` anahtar sözcüğü, bu konudaki örnekler kullanılıyor. Arasındaki farklar hakkında daha fazla bilgi için `in`, `ref`, ve `out`, bkz: [içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), [çıkışı](../../../csharp/language-reference/keywords/out-parameter-modifier.md), ve [ Dizileri kullanma ref ve out geçirme](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Aşağıdaki örnek, değer ve başvuru parametreleri arasındaki fark gösterilmektedir.  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Değer Türü Parametrelerini Geçirme](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [Başvuru Türü Parametreleri Geçirme](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)
