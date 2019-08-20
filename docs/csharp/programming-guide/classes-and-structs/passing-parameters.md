---
title: Parametreleri geçirme- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 1c42ce7b258ca35d4e91e1ef28c71b60fe1f01de
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596258"
---
# <a name="passing-parameters-c-programming-guide"></a>Parametreleri Geçirme (C# Programlama Kılavuzu)
' C#De, bağımsız değişkenler değere veya başvuruya göre parametrelere geçirilebilir. Başvuruya göre geçirme işlevi üyeleri, Yöntemler, özellikler, Dizin oluşturucular, işleçler ve oluşturucuların parametrelerin değerini değiştirmesini ve bu değişikliğin çağrı ortamında kalıcı olmasını sağlar. Değeri değiştirme amacına sahip bir parametreyi başvuruya göre geçirmek için, veya `ref` `out` anahtar sözcüğünü kullanın. Kopyalama ve değeri değiştirmemesini sağlama amacını kullanarak başvuruya göre geçiş yapmak için `in` değiştiricisini kullanın. Basitlik için, bu `ref` konudaki örneklerde yalnızca anahtar sözcüğü kullanılır. `in`, Ve`ref` [](../../language-reference/keywords/in-parameter-modifier.md) [](../../language-reference/keywords/ref.md) [](../../language-reference/keywords/out-parameter-modifier.md)arasındaki fark hakkında daha fazla bilgi için bkz. ın, ref ve out. `out`  
  
 Aşağıdaki örnek, değer ve başvuru parametreleri arasındaki farkı gösterir.  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 Daha fazla bilgi için aşağıdaki konulara bakın:  
  
- [Değer Türü Parametrelerini Geçirme](./passing-value-type-parameters.md)  
  
- [Başvuru Türü Parametreleri Geçirme](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için bkz. [ C# dil belirtiminde](../../language-reference/language-specification/index.md) [bağımsız değişken listeleri](~/_csharplang/spec/expressions.md#argument-lists) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Yöntemler](./methods.md)
