---
title: Değer türü parametrelerini geçirme- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], value types
- parameters [C#], value
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
ms.openlocfilehash: 670af18d4b2b356aa33a0a03a29c05f5ba9bf78f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744487"
---
# <a name="passing-value-type-parameters-c-programming-guide"></a>Değer Türü Parametrelerini Geçirme (C# Programlama Kılavuzu)
Bir [değer türü](../../language-reference/builtin-types/value-types.md) değişkeni, veri başvurusunu içeren bir [başvuru türü](../../language-reference/keywords/reference-types.md) değişkeni aksine doğrudan verilerini içerir. Değer türü bir değişkeni değere göre yönteme geçirmek, değişkenin bir kopyasının yöntemine geçirilmesi anlamına gelir. Yöntemin içinde yer alan parametrede yapılan tüm değişiklikler bağımsız değişken değişkeninde depolanan özgün veriler üzerinde hiçbir etkisi yoktur. Çağrılan yöntemin bağımsız değişkenin değerini değiştirmesini istiyorsanız [ref](../../language-reference/keywords/ref.md) veya [Out](../../language-reference/keywords/out-parameter-modifier.md) anahtar sözcüğünü kullanarak başvuruya göre geçirmeniz gerekir. Ayrıca, değerin değişmediğinden emin olmak için bir değer parametresini başvuruya göre geçirmek için [ın](../../language-reference/keywords/in-parameter-modifier.md) anahtar sözcüğünü kullanabilirsiniz. Basitlik için aşağıdaki örneklerde `ref`kullanılır.  
  
## <a name="passing-value-types-by-value"></a>Değere göre değer türlerini geçirme  
 Aşağıdaki örnek değer türü parametrelerini değere göre geçirmeyi gösterir. `n` değişkeni değere göre `SquareIt`yöntemine geçirilir. Yöntemin içinde gerçekleşen tüm değişiklikler, değişkenin özgün değeri üzerinde hiçbir etkisi olmaz.  
  
 [!code-csharp[csProgGuideParameters#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#3)]  
  
 `n` değişkeni bir değer türüdür. Onun verilerini, `5`değerini içerir. `SquareIt` çağrıldığında, `n` içerikleri, yöntemin içindeki kare içinde olan `x`parametresine kopyalanır. Ancak `Main`' de, `n` değeri, daha önce olduğu gibi `SquareIt` yöntemi çağrıldıktan sonra aynı olur. Yöntemin içinde gerçekleşen değişiklik yalnızca `x`yerel değişkenini etkiler.  
  
## <a name="passing-value-types-by-reference"></a>Değer türlerini başvuruya göre geçirme  
 Aşağıdaki örnek, bağımsız değişkenin bir `ref` parametresi olarak geçirilmesi dışında, önceki örnekle aynıdır. `n`, temeldeki bağımsız değişkenin değeri, `x` değiştiğinde değişir.  
  
 [!code-csharp[csProgGuideParameters#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#4)]  
  
 Bu örnekte, geçirilen `n` değeri değildir; Bunun yerine, `n` bir başvuru geçirilir. `x` parametresi bir [int](../../language-reference/builtin-types/integral-numeric-types.md)değil; Bu örnekte, `n`bir başvuru olan bir `int`başvurusudur. Bu nedenle, yöntemin içinde `x` kare içinde olduğunda, `x` ne zaman kare olarak ifade edilir `n`.  
  
## <a name="swapping-value-types"></a>Değer türlerini değiştirme  
 Bağımsız değişkenlerin değerlerini değiştirmenin yaygın bir örneği, yöntemine iki değişken geçirdiğiniz ve yöntemi içeriğini değiştiren bir takas yöntemidir. Bağımsız değişkenleri başvuruya göre takas yöntemine geçirmeniz gerekir. Aksi takdirde, yöntemin içindeki yerel kopyaları değiştirirsiniz ve çağırma yönteminde hiçbir değişiklik gerçekleşmez. Aşağıdaki örnek, tamsayı değerlerini değiştirir.  
  
 [!code-csharp[csProgGuideParameters#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#5)]  
  
 `SwapByRef` yöntemini çağırdığınızda, aşağıdaki örnekte gösterildiği gibi, çağrısındaki `ref` anahtar sözcüğünü kullanın.  
  
 [!code-csharp[csProgGuideParameters#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Parametreleri Geçirme](./passing-parameters.md)
- [Başvuru Türü Parametreleri Geçirme](./passing-reference-type-parameters.md)
