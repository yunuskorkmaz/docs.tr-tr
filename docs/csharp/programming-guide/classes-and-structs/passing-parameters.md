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
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404132"
---
# <a name="passing-parameters-c-programming-guide"></a>Parametreleri Geçirme (C# Programlama Kılavuzu)
C# ' ta bağımsız değişkenler parametrelerini değere veya başvuruya göre geçirilebilir. Çağıran ortama oluşturucular parametreleri değiştirin ve değişikliği kalıcı hale getirmek ve başvuruya göre geçirme işlev üyeleri, yöntemleri, özellikleri, Dizinleyicileri, işleçleri sağlar. Değer değiştirme hedefi ile başvuruya göre bir parametre geçirmek için kullanmak `ref`, veya `out` anahtar sözcüğü. Başvuru değiştirme değeri değil ancak kopyalama önleme amacıyla geçirmek için kullanmak `in` değiştiricisi. Kolaylık olması için yalnızca `ref` anahtar sözcüğü, bu konudaki örneklerde kullanılır. Arasındaki fark hakkında daha fazla bilgi için `in`, `ref`, ve `out`, bkz: [içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), [kullanıma](../../../csharp/language-reference/keywords/out-parameter-modifier.md), ve [ Dizileri kullanma ref ve out geçirme](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Aşağıdaki örnek, değer ve başvuru parametreleri arasındaki farkı gösterir.  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Değer Türü Parametrelerini Geçirme](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [Başvuru Türü Parametreleri Geçirme](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)
