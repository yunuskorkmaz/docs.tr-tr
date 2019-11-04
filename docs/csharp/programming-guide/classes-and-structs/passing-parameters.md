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
ms.openlocfilehash: 22f58bda5aa5b60248902a4130f3ea9b6caa65cf
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419118"
---
# <a name="passing-parameters-c-programming-guide"></a>Parametreleri Geçirme (C# Programlama Kılavuzu)
' C#De, bağımsız değişkenler değere veya başvuruya göre parametrelere geçirilebilir. Başvuruya göre geçirme işlevi üyeleri, Yöntemler, özellikler, Dizin oluşturucular, işleçler ve oluşturucuların parametrelerin değerini değiştirmesini ve bu değişikliğin çağrı ortamında kalıcı olmasını sağlar. Değeri değiştirme amacına sahip bir parametreyi başvuruya göre geçirmek için `ref`veya `out` anahtar sözcüğünü kullanın. Kopyalamayı önleme amacını vererek ve değeri değiştirmezseniz başvuruya göre geçiş yapmak için `in` değiştiricisini kullanın. Basitlik için, bu konudaki örneklerde yalnızca `ref` anahtar sözcüğü kullanılır. `in`, `ref`ve `out`arasındaki fark hakkında daha fazla bilgi için bkz. [ın](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)ve [Out](../../language-reference/keywords/out-parameter-modifier.md).  
  
 Aşağıdaki örnek, değer ve başvuru parametreleri arasındaki farkı gösterir.  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 Daha fazla bilgi için aşağıdaki konulara bakın:  
  
- [Değer Türü Parametrelerini Geçirme](./passing-value-type-parameters.md)  
  
- [Başvuru Türü Parametreleri Geçirme](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [bağımsız değişken listeleri](~/_csharplang/spec/expressions.md#argument-lists) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Yöntemler](./methods.md)
