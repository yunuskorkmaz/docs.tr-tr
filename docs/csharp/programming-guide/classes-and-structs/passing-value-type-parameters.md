---
title: Değer türü parametrelerini geçirme- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], value types
- parameters [C#], value
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
ms.openlocfilehash: dfd2c39eff44b431ec10d85f855fb015a2391f29
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596246"
---
# <a name="passing-value-type-parameters-c-programming-guide"></a>Değer Türü Parametrelerini Geçirme (C# Programlama Kılavuzu)
Bir [değer türü](../../language-reference/keywords/value-types.md) değişkeni, veri başvurusunu içeren bir [başvuru türü](../../language-reference/keywords/reference-types.md) değişkeni aksine doğrudan verilerini içerir. Değer türü bir değişkeni değere göre yönteme geçirmek, değişkenin bir kopyasının yöntemine geçirilmesi anlamına gelir. Yöntemin içinde yer alan parametrede yapılan tüm değişiklikler bağımsız değişken değişkeninde depolanan özgün veriler üzerinde hiçbir etkisi yoktur. Çağrılan yöntemin bağımsız değişkenin değerini değiştirmesini istiyorsanız [ref](../../language-reference/keywords/ref.md) veya [Out](../../language-reference/keywords/out-parameter-modifier.md) anahtar sözcüğünü kullanarak başvuruya göre geçirmeniz gerekir. Ayrıca, değerin değişmediğinden emin olmak için bir değer parametresini başvuruya göre geçirmek için [ın](../../language-reference/keywords/in-parameter-modifier.md) anahtar sözcüğünü kullanabilirsiniz. Basitlik için aşağıdaki örneklerde kullanılması `ref`gerekir.  
  
## <a name="passing-value-types-by-value"></a>Değere göre değer türlerini geçirme  
 Aşağıdaki örnek değer türü parametrelerini değere göre geçirmeyi gösterir. Değişken `n` değerine göre yöntemine `SquareIt`geçirilir. Yöntemin içinde gerçekleşen tüm değişiklikler, değişkenin özgün değeri üzerinde hiçbir etkisi olmaz.  
  
 [!code-csharp[csProgGuideParameters#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#3)]  
  
 Değişken `n` bir değer türüdür. Verileri, değerini `5`içerir. Çağrıldığında, öğesinin `n` içeriği, yönteminin içindeki kare içinde olan parametresine `x`kopyalanır. `SquareIt` Ancak `Main`içindeki değeri,`SquareIt` yöntemi öncesindeki gibi çağrıldıktan sonra aynı olur.`n` Metodun içinde yer alan değişiklik yalnızca yerel değişkeni `x`etkiler.  
  
## <a name="passing-value-types-by-reference"></a>Değer türlerini başvuruya göre geçirme  
 Aşağıdaki örnek, bağımsız değişkenin `ref` parametre olarak geçirilmesi dışında, önceki örnekle aynıdır. Temel bağımsız değişkenin değeri, `n`yönteminde değiştiğinde `x` değiştirilir.  
  
 [!code-csharp[csProgGuideParameters#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#4)]  
  
 Bu örnekte, geçirilen değeri `n` değildir; Bunun yerine, öğesine `n` bir başvuru geçirilir. Parametre `x` bir [int](../../language-reference/builtin-types/integral-numeric-types.md)değil; `int`bu durumda öğesine `n`bir başvuru. Bu nedenle, `x` yöntemin içinde kare içinde olduğunda, ne zaman kare `x` olarak ifade `n`edilir.  
  
## <a name="swapping-value-types"></a>Değer türlerini değiştirme  
 Bağımsız değişkenlerin değerlerini değiştirmenin yaygın bir örneği, yöntemine iki değişken geçirdiğiniz ve yöntemi içeriğini değiştiren bir takas yöntemidir. Bağımsız değişkenleri başvuruya göre takas yöntemine geçirmeniz gerekir. Aksi takdirde, yöntemin içindeki yerel kopyaları değiştirirsiniz ve çağırma yönteminde hiçbir değişiklik gerçekleşmez. Aşağıdaki örnek, tamsayı değerlerini değiştirir.  
  
 [!code-csharp[csProgGuideParameters#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#5)]  
  
 `SwapByRef` Yöntemini çağırdığınızda, aşağıdaki örnekte gösterildiği gibi, `ref` çağrısındaki anahtar sözcüğünü kullanın.  
  
 [!code-csharp[csProgGuideParameters#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Parametreleri Geçirme](./passing-parameters.md)
- [Başvuru Türü Parametreleri Geçirme](./passing-reference-type-parameters.md)
