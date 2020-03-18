---
title: Geçen Parametreler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 60ac7a8d982e7788f07debce114896859385c8e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705476"
---
# <a name="passing-parameters-c-programming-guide"></a>Parametreleri Geçirme (C# Programlama Kılavuzu)
C#'da bağımsız değişkenler parametrelere değer veya başvuru ile geçirilebilir. Başvuruyla geçmek, işlev üyelerinin, yöntemlerinin, özelliklerinin, dizin leyicilerin ve oluşturucuların parametrelerin değerini değiştirmesini ve bu değişikliğin çağrı ortamında devam etmesini sağlar. Değeri değiştirme amacıyla bir parametreyi referans olarak geçirmek `ref`için, `out` "veya anahtar kelimeyi" kullanın. Kopyalamaktan kaçınmak ancak değeri değiştirmemek amacıyla referans la geçmek `in` için değiştiricikullanın. Basitlik için, bu `ref` konudaki örneklerde yalnızca anahtar kelime kullanılır. Arasındaki `in`fark hakkında daha `ref`fazla `out`bilgi için , , ve , [,](../../language-reference/keywords/in-parameter-modifier.md)bakınız , [ref](../../language-reference/keywords/ref.md), ve [dışarı](../../language-reference/keywords/out-parameter-modifier.md).  
  
 Aşağıdaki örnekte değer ve başvuru parametreleri arasındaki fark gösterin.  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:  
  
- [Değer Türü Parametrelerini Geçirme](./passing-value-type-parameters.md)  
  
- [Başvuru Türü Parametreleri Geçirme](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Bağımsız Değişken listelerine](~/_csharplang/spec/expressions.md#argument-lists) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Yöntemler](./methods.md)
