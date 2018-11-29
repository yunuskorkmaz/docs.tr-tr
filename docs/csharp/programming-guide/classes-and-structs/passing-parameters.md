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
ms.openlocfilehash: 241beb56b0e0f00dae63e12ea775b2b982200efc
ms.sourcegitcommit: 302908367e82742d3e5ef7e5f3ce190a39300d64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2018
ms.locfileid: "44194859"
---
# <a name="passing-parameters-c-programming-guide"></a>Parametreleri Geçirme (C# Programlama Kılavuzu)
C# ' ta bağımsız değişkenler parametrelerini değere veya başvuruya göre geçirilebilir. Çağıran ortama oluşturucular parametreleri değiştirin ve değişikliği kalıcı hale getirmek ve başvuruya göre geçirme işlev üyeleri, yöntemleri, özellikleri, Dizinleyicileri, işleçleri sağlar. Değer değiştirme hedefi ile başvuruya göre bir parametre geçirmek için kullanmak `ref`, veya `out` anahtar sözcüğü. Başvuru değiştirme değeri değil ancak kopyalama önleme amacıyla geçirmek için kullanmak `in` değiştiricisi. Kolaylık olması için yalnızca `ref` anahtar sözcüğü, bu konudaki örneklerde kullanılır. Arasındaki fark hakkında daha fazla bilgi için `in`, `ref`, ve `out`, bkz: [içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), ve [kullanıma](../../../csharp/language-reference/keywords/out-parameter-modifier.md).  
  
 Aşağıdaki örnek, değer ve başvuru parametreleri arasındaki farkı gösterir.  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Değer Türü Parametrelerini Geçirme](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [Başvuru Türü Parametreleri Geçirme](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [bağımsız değişken listeleri](~/_csharplang/spec/expressions.md#argument-lists) içinde [ C# dil belirtimi](../../language-reference/language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)
