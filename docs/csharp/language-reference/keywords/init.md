---
description: init anahtar sözcüğü-C# başvurusu
title: init anahtar sözcüğü-C# başvurusu
ms.date: 03/03/2021
f1_keywords:
- init
- init_CSharpKeyword
helpviewer_keywords:
- init keyword [C#]
ms.openlocfilehash: 2271b5332c8bfd3223d0c034a44eca4e2ca0ca54
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190471"
---
# <a name="init-c-reference"></a>init (C# Başvurusu)

C# 9 ve sonraki sürümlerde `init` anahtar sözcüğü bir özellik veya dizin oluşturucuda bir *erişimci* yöntemi tanımlar. Yalnızca bir başlatma ayarlayıcısı, özellik veya Dizin Oluşturucu öğesi yalnızca nesne oluşturma sırasında bir değer atar. Daha fazla bilgi ve örnek için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md), [Otomatik uygulanan özellikler](../../programming-guide/classes-and-structs/auto-implemented-properties.md)ve [Dizin oluşturucular](../../programming-guide/indexers/index.md).

Aşağıdaki örnek `get` `init` adlı bir özellik için hem hem de erişimcisini tanımlar `Seconds` . `_seconds`Özellik değerini geri yüklemek için adlı bir özel alan kullanır.

[!code-csharp[init#1](snippets/InitExample1.cs)]

Genellikle, `init` erişimci, önceki örnekte olduğu gibi bir değer atayan tek bir deyimden oluşur. `init`Erişimciyi bir ifade olarak uygulayabilirsiniz. Aşağıdaki örnek, hem hem de `get` `init` erişimcilerinin ifade-Bodied Üyeler olarak uyguladığı.

[!code-csharp[init#3](snippets/InitExample3.cs)]
  
Bir özelliğin `get` ve `init` erişimcilerinin özel bir destek alanındaki bir değeri ayarlamaktan veya almadan başka bir işlem gerçekleştirdiği basit durumlarda, C# derleyicisinin otomatik uygulanan özellikler için destek özelliğinden yararlanabilirsiniz. Aşağıdaki örnek `Hours` Otomatik uygulanan bir özellik olarak uygulanır.

[!code-csharp[init#2](snippets/InitExample2.cs)]
  
## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [Özellikler](../../programming-guide/classes-and-structs/properties.md)
