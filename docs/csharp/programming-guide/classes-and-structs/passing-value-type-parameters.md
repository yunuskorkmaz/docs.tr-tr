---
title: Geçen Değer Türü Parametreleri - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], value types
- parameters [C#], value
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
ms.openlocfilehash: 670af18d4b2b356aa33a0a03a29c05f5ba9bf78f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76744487"
---
# <a name="passing-value-type-parameters-c-programming-guide"></a>Değer Türü Parametrelerini Geçirme (C# Programlama Kılavuzu)
[Değer türünde](../../language-reference/builtin-types/value-types.md) bir değişken, verilerine bir başvuru içeren [bir referans türü](../../language-reference/keywords/reference-types.md) değişkenin aksine verilerini doğrudan içerir. Değer türündeki bir değişkenin değer olarak bir yönteme geçirilmesi, değişkenin bir kopyasını yönteme aktarmak anlamına gelir. Yöntem içinde gerçekleşen parametredeki herhangi bir değişikliğin bağımsız değişken değişkeninde depolanan özgün verileri etkilemez. Çağrılan yöntemin bağımsız değişkenin değerini değiştirmesini istiyorsanız, [bunu ref](../../language-reference/keywords/ref.md) veya [anahtar kelimeyi](../../language-reference/keywords/out-parameter-modifier.md) kullanarak başvuruyla geçirmeniz gerekir. Ayrıca, değerin [in](../../language-reference/keywords/in-parameter-modifier.md) değiştirilmeyeceğini garanti ederken kopyadan kaçınmak için referans olarak bir değer parametresi geçirmek için anahtar sözcüğü de kullanabilirsiniz. Basitlik için aşağıdaki örnekler `ref`kullanılır.  
  
## <a name="passing-value-types-by-value"></a>Değere Göre Değer Türleri Geçme  
 Aşağıdaki örnekte değer türü parametreleri değere göre geçen gösterir. Değişken `n` yönteme değer olarak `SquareIt`geçirilir. Yöntem içinde gerçekleşen herhangi bir değişiklik değişkenin özgün değeri üzerinde hiçbir etkisi yoktur.  
  
 [!code-csharp[csProgGuideParameters#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#3)]  
  
 Değişken `n` bir değer türüdür. Verilerini, değerini `5`içerir. Çağrıldığınızda, `SquareIt` içeriği `n` yöntem içinde kare parametre `x`, kopyalanır. `Main`Ancak, yöntemi daha `n` önce olduğu gibi `SquareIt` aradıktan sonra değeri aynıdır. Yöntem içinde gerçekleşen değişiklik yalnızca yerel değişkeni `x`etkiler.  
  
## <a name="passing-value-types-by-reference"></a>Referansa Göre Değer Türlerini Geçme  
 Aşağıdaki örnek, bağımsız değişkenin parametre `ref` olarak geçirilmesi dışında, önceki örnekle aynıdır. Yöntemde değiştirildiğinde, `x` `n`temel bağımsız değişkenin değeri değiştirilir.  
  
 [!code-csharp[csProgGuideParameters#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#4)]  
  
 Bu örnekte, geçirilen değer `n` değildir; bunun yerine, `n` bir referans geçirilir. Parametre `x` bir [int](../../language-reference/builtin-types/integral-numeric-types.md)değildir; bu durumda, bir `int` `n`referanstır. Bu nedenle, yöntem içinde kare olduğunda, `x` aslında ne `x` kare `n`olduğunu ifade eder, .  
  
## <a name="swapping-value-types"></a>Değer Türlerini Değiştirme  
 Bağımsız değişkenlerin değerlerini değiştirmeye yaygın bir örnek, yönteme iki değişken ilerlediğiniz ve yöntemin içeriğini değiştirdiği bir takas yöntemidir. Bağımsız değişkenleri başvuru yla takas yöntemine geçirmeniz gerekir. Aksi takdirde, yöntem içindeki parametrelerin yerel kopyalarını değiştirirsiniz ve arama yönteminde herhangi bir değişiklik olmaz. Aşağıdaki örnek, sonsayı değerlerini değiştirir.  
  
 [!code-csharp[csProgGuideParameters#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#5)]  
  
 `SwapByRef` Yöntemi aradiğinizde, aşağıdaki `ref` örnekte gösterildiği gibi aramadaki anahtar sözcüğü kullanın.  
  
 [!code-csharp[csProgGuideParameters#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Parametreleri Geçirme](./passing-parameters.md)
- [Başvuru Türü Parametreleri Geçirme](./passing-reference-type-parameters.md)
