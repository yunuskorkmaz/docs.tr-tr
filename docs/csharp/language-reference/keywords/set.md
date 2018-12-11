---
title: anahtar sözcüğü - Ayarla C# başvurusu
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: 3020badc8b7873d7feb0b8133d3a181e1c051cbd
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243744"
---
# <a name="set-c-reference"></a>set (C# Başvurusu)

`set` Tanımlayan anahtar sözcüğü bir *erişimci* yönteminde bir özellik veya dizin özelliği veya dizin oluşturucu öğenin bir değer atar. Daha fazla bilgi ve örnekler için bkz. [özellikleri](../../programming-guide/classes-and-structs/properties.md), [Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), ve [dizin oluşturucular](../../programming-guide/indexers/index.md).

Aşağıdaki örnek, her ikisi de tanımlar bir `get` ve `set` adlı bir özellik erişimcisi `Seconds`. Adlı bir özel alan kullanan `_seconds` özellik değeri yedeklenir.

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

Genellikle, `set` erişimci, önceki örnekte olduğu gibi bir değer döndüren tek bir sistem oluşur. C# 7.0 ile başlayarak, uygulayabileceğiniz `set` bir ifade gövdeli üyesi erişimcisi. Aşağıdaki örnek her ikisini birden uygular `get` ve `set` ifade gövdeli üyeler olarak erişimcileri.

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
Basit durumlarda için bir özelliğin `get` ve `set` erişimcileri ayarlama veya özel destek alanı bir değer alınırken daha başka bir işlem gerçekleştirme, otomatik uygulanan özellikler için C# Derleyici desteği yararlanabilir. Aşağıdaki örnek uygulayan `Hours` otomatik uygulanan bir özellik olarak. 

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Özellikler](../../programming-guide/classes-and-structs/properties.md)