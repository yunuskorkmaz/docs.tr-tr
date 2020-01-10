---
title: anahtar sözcük C# başvurusunu ayarla
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: 97b0dbf8716edc4cd465eb5ac693efa0ecaa498b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713085"
---
# <a name="set-c-reference"></a>set (C# Başvurusu)

`set` anahtar sözcüğü, özelliğe veya dizinleyici öğesine bir değer atayan bir özellik veya dizin oluşturucuda bir *erişimci* yöntemi tanımlar. Daha fazla bilgi ve örnek için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md), [Otomatik uygulanan özellikler](../../programming-guide/classes-and-structs/auto-implemented-properties.md)ve [Dizin oluşturucular](../../programming-guide/indexers/index.md).

Aşağıdaki örnek, `Seconds`adlı bir özellik için hem `get` hem de `set` erişimcisi tanımlar. Özellik değerini geri yüklemek için `_seconds` adlı bir özel alan kullanır.

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

Genellikle `set` erişimcisi, önceki örnekte olduğu gibi bir değer atayan tek bir deyimden oluşur. 7,0 ' C# den başlayarak, `set` erişimcisini ifade-Bodied üyesi olarak uygulayabilirsiniz. Aşağıdaki örnek hem `get` hem de `set` erişimcileri ifadesini ifade eden Üyeler olarak uygular.

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
Bir özelliğin `get` ve `set` erişimcilerinin özel bir destek alanındaki bir değeri ayarlamaktan veya almadan başka bir işlem gerçekleştirmesinin gerçekleştirdiği basit durumlar için C# derleyicinin otomatik uygulanan özellikler desteğiyle yararlanabilirsiniz. Aşağıdaki örnek, `Hours` otomatik olarak uygulanan bir özellik olarak uygular. 

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Veri Erişimi](../../programming-guide/classes-and-structs/properties.md)
