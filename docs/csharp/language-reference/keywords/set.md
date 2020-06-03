---
title: Set anahtar sözcüğü-C# başvurusu
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: cdd84c824cc4dc93f4433f07e9978d22cba3f245
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795072"
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
