---
title: Parametreleri geçirme-C# Programlama Kılavuzu
description: Bir bağımsız değişkeni C# ' de değere veya başvuruya göre bir parametreye geçirebilirsiniz. Başvuru kalıcı olarak geçirilen bir bağımsız değişkende yapılan değişiklikler. Başvuruya göre geçmek için ref veya out kullanın.
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 61ec6d31145df5a2aebe805fccdf7614a0ae74f6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186100"
---
# <a name="passing-parameters-c-programming-guide"></a>Parametreleri Geçirme (C# Programlama Kılavuzu)

C# ' de, bağımsız değişkenler değere veya başvuruya göre parametrelere geçirilebilir. Başvuruya göre geçirme işlevi üyeleri, Yöntemler, özellikler, Dizin oluşturucular, işleçler ve oluşturucuların parametrelerin değerini değiştirmesini ve bu değişikliğin çağrı ortamında kalıcı olmasını sağlar. Değeri değiştirme amacına sahip bir parametreyi başvuruya göre geçirmek için, `ref` veya `out` anahtar sözcüğünü kullanın. Kopyalama ve değeri değiştirmemesini sağlama amacını kullanarak başvuruya göre geçiş yapmak için `in` değiştiricisini kullanın. Basitlik için, `ref` Bu konudaki örneklerde yalnızca anahtar sözcüğü kullanılır. , Ve arasındaki fark hakkında daha fazla bilgi için `in` `ref` `out` bkz. [ın](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)ve [Out](../../language-reference/keywords/out-parameter-modifier.md).  
  
 Aşağıdaki örnek, değer ve başvuru parametreleri arasındaki farkı gösterir.  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:  
  
- [Değer Türü Parametrelerini Geçirme](./passing-value-type-parameters.md)  
  
- [Başvuru Türü Parametreleri Geçirme](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [bağımsız değişken listeleri](~/_csharplang/spec/expressions.md#argument-lists) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Yöntemler](./methods.md)
