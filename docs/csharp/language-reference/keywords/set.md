---
title: anahtar kelime yi ayarlama - C# Reference
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: 0b293709abe64a0a82d8575f6793a07ca6c9533b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173503"
---
# <a name="set-c-reference"></a>set (C# Başvurusu)

Anahtar `set` kelime, bir özellik veya dizinleyici de bir özellik veya dizinleyici öğesi bir değer atayan bir *erişimci* yöntemi tanımlar. Daha fazla bilgi ve örnekler için Bkz. [Özellikler,](../../programming-guide/classes-and-structs/properties.md) [Otomatik Uygulanan Özellikler](../../programming-guide/classes-and-structs/auto-implemented-properties.md)ve [Dizin leyiciler.](../../programming-guide/indexers/index.md)

Aşağıdaki örnek, adlandırılmış `get` `Seconds`bir `set` özellik için hem a hem de bir erişimci tanımlar. Özellik değerini yedeklemek `_seconds` için özel bir alan kullanır.

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

Genellikle, `set` erişimci önceki örnekte olduğu gibi bir değer atayan tek bir deyimden oluşur. C# 7.0 ile başlayarak, `set` erişime gireni ifade gövdeli bir üye olarak uygulayabilirsiniz. Aşağıdaki örnek, hem `get` `set` erişime girenleri hem de erişime girenleri ifade gövdeli üyeler olarak uygular.

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
Bir özelliğin `get` ve `set` erişime sahip olanların özel bir destek alanında bir değer ayarlamaktan veya almaktan başka bir işlem gerçekleştirmediği basit durumlarda, Otomatik olarak uygulanan özellikler için C# derleyicisinin desteğinden yararlanabilirsiniz. Aşağıdaki örnek, `Hours` otomatik olarak uygulanan bir özellik olarak uygular.

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [Özellikler](../../programming-guide/classes-and-structs/properties.md)
