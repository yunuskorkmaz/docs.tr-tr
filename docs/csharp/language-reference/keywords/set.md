---
description: Set anahtar sözcüğü-C# başvurusu
title: Set anahtar sözcüğü-C# başvurusu
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: ff0c99e5d4d6271351783befd6650d9a77f39886
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136921"
---
# <a name="set-c-reference"></a>set (C# Başvurusu)

Anahtar sözcüğü, özelliği veya dizinleyici `set` öğesine bir değer atayan bir özellik veya dizin oluşturucuda bir *erişimci* yöntemi tanımlar. Daha fazla bilgi ve örnek için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md), [Otomatik uygulanan özellikler](../../programming-guide/classes-and-structs/auto-implemented-properties.md)ve [Dizin oluşturucular](../../programming-guide/indexers/index.md).

Aşağıdaki örnek `get` `set` adlı bir özellik için hem hem de erişimcisini tanımlar `Seconds` . `_seconds`Özellik değerini geri yüklemek için adlı bir özel alan kullanır.

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

Genellikle, `set` erişimci, önceki örnekte olduğu gibi bir değer atayan tek bir deyimden oluşur. C# 7,0 ' den başlayarak, `set` erişimciyi bir ifade olarak uygulayabilirsiniz. Aşağıdaki örnek, hem hem de `get` `set` erişimcilerinin ifade-Bodied Üyeler olarak uyguladığı.

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
Bir özelliğin `get` ve `set` erişimcilerinin özel bir destek alanındaki bir değeri ayarlamaktan veya almadan başka bir işlem gerçekleştirdiği basit durumlarda, C# derleyicisinin otomatik uygulanan özellikler için destek özelliğinden yararlanabilirsiniz. Aşağıdaki örnek `Hours` Otomatik uygulanan bir özellik olarak uygulanır.

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [Özellikler](../../programming-guide/classes-and-structs/properties.md)
