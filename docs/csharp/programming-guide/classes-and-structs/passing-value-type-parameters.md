---
title: Değer türü parametrelerini geçirme-C# Programlama Kılavuzu
description: C# ' deki değere göre bir yönteme değer türü değişkeni geçirdiğinizde, tüm değişikliklerin özgün veriler üzerinde hiçbir etkisi olmaz. Değeri değiştirmek için başvuruya göre geçirin.
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], value types
- parameters [C#], value
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
ms.openlocfilehash: ccc97e2f6e8c6b2b8fd15206a8bcd5cd8a5a8431
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186074"
---
# <a name="passing-value-type-parameters-c-programming-guide"></a>Değer Türü Parametrelerini Geçirme (C# Programlama Kılavuzu)

Bir [değer türü](../../language-reference/builtin-types/value-types.md) değişkeni, veri başvurusunu içeren bir [başvuru türü](../../language-reference/keywords/reference-types.md) değişkeni aksine doğrudan verilerini içerir. Değer türü bir değişkeni değere göre yönteme geçirmek, değişkenin bir kopyasının yöntemine geçirilmesi anlamına gelir. Yöntemin içinde gerçekleşen parametresindeki tüm değişiklikler, bağımsız değişken değişkeninde depolanan özgün veriler üzerinde hiçbir etkiye sahip değildir. Çağrılan yöntemin bağımsız değişkenin değerini değiştirmesini istiyorsanız [ref](../../language-reference/keywords/ref.md) veya [Out](../../language-reference/keywords/out-parameter-modifier.md) anahtar sözcüğünü kullanarak başvuruya göre geçirmeniz gerekir. Ayrıca, değerin değişmediğinden emin olmak için bir değer parametresini başvuruya göre geçirmek için [ın](../../language-reference/keywords/in-parameter-modifier.md) anahtar sözcüğünü kullanabilirsiniz. Basitlik için aşağıdaki örneklerde kullanılması gerekir `ref` .  
  
## <a name="passing-value-types-by-value"></a>Değere göre değer türlerini geçirme  

 Aşağıdaki örnek değer türü parametrelerini değere göre geçirmeyi gösterir. Değişken `n` değerine göre yöntemine geçirilir `SquareIt` . Yöntemin içinde gerçekleşen tüm değişikliklerin, değişkenin özgün değeri üzerinde hiçbir etkisi yoktur.  
  
 [!code-csharp[csProgGuideParameters#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#3)]  
  
 Değişken `n` bir değer türüdür. Verileri, değerini içerir `5` . `SquareIt`Çağrıldığında, öğesinin içeriği `n` `x` , yönteminin içindeki kare içinde olan parametresine kopyalanır. `Main`Ancak içindeki değeri, `n` `SquareIt` yöntemi öncesindeki gibi çağrıldıktan sonra aynı olur. Metodun içinde yer alan değişiklik yalnızca yerel değişkeni etkiler `x` .  
  
## <a name="passing-value-types-by-reference"></a>Değer türlerini başvuruya göre geçirme  

 Aşağıdaki örnek, bağımsız değişkenin parametre olarak geçirilmesi dışında, önceki örnekle aynıdır `ref` . Temel bağımsız değişkenin değeri, yönteminde değiştiğinde `n` değiştirilir `x` .  
  
 [!code-csharp[csProgGuideParameters#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#4)]  
  
 Bu örnekte, geçirilen değeri değildir `n` ; bunun yerine, öğesine bir başvuru `n` geçirilir. Parametre `x` bir [int](../../language-reference/builtin-types/integral-numeric-types.md)değil; `int` Bu durumda öğesine bir başvuru `n` . Bu nedenle, `x` yöntemin içinde kare içinde olduğunda, ne zaman kare olarak ifade edilir `x` `n` .  
  
## <a name="swapping-value-types"></a>Değer türlerini değiştirme  

 Bağımsız değişkenlerin değerlerini değiştirmenin yaygın bir örneği, yöntemine iki değişken geçirdiğiniz ve yöntemi içeriğini değiştiren bir takas yöntemidir. Bağımsız değişkenleri başvuruya göre takas yöntemine geçirmeniz gerekir. Aksi takdirde, yöntemin içindeki yerel kopyaları değiştirirsiniz ve çağırma yönteminde hiçbir değişiklik gerçekleşmez. Aşağıdaki örnek, tamsayı değerlerini değiştirir.  
  
 [!code-csharp[csProgGuideParameters#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#5)]  
  
 `SwapByRef`Yöntemini çağırdığınızda, `ref` Aşağıdaki örnekte gösterildiği gibi, çağrısındaki anahtar sözcüğünü kullanın.  
  
 [!code-csharp[csProgGuideParameters#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Parametreleri geçirme](./passing-parameters.md)
- [Başvuru Türü Parametreleri Geçirme](./passing-reference-type-parameters.md)
