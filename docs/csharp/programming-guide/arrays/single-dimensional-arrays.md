---
title: Tek Boyutlu Diziler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: bd4ab53a9cb53e5cf636601bff5ac64a10a310a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170357"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>Tek Boyutlu Diziler (C# Programlama Kılavuzu)

Aşağıdaki örnekte gösterildiği gibi beş tamsayı tek boyutlu bir dizi bildirebilirsiniz:  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 Bu dizi, `array[0]` `array[4]`'den. [Yeni](../../language-reference/operators/new-operator.md) işleç dizioluşturmak ve dizi öğelerini varsayılan değerlerine çıkarmak için kullanılır. Bu örnekte, tüm dizi öğeleri sıfıra başlanır.  
  
 Dize öğelerini depolayan bir dizi aynı şekilde bildirilebilir. Örnek:  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a>Dizi Başlatma

 Bir diziyi bildirim üzerine başlatmayapmak mümkündür, bu durumda, zaten başlatma listesindeki öğe sayısı tarafından sağlandığı için uzunluk belirtici gerekli değildir. Örnek:  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 Bir dize dizisi aynı şekilde başharfe bilebilir. Aşağıda, her dizi öğesinin bir gün adı ile başharflere verildiği bir dize dizisi bildirimi vereme sayısı veremeği ve  

 ```csharp
 string[] weekDays = new string[] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
 ```
  
 Bir diziyi bildirim üzerine başharfe aldığınızda, aşağıdaki kısayolları kullanabilirsiniz:  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 Bir dizi değişkenini başlatma olmadan bildirmek mümkündür, `new` ancak bu değişkene bir dizi atadığınızda işleci kullanmanız gerekir. Örnek:  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 C# 3.0 örtülü olarak yazılan dizileri tanır. Daha fazla bilgi için [bkz.](./implicitly-typed-arrays.md)  
  
## <a name="value-type-and-reference-type-arrays"></a>Değer Türü ve Referans Türü Dizileri

 Aşağıdaki dizi bildirimini göz önünde bulundurun:  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 Bu bildirimin sonucu bir `SomeType` değer türü veya bir başvuru türü olup olmadığına bağlıdır. Bir değer türüyse, deyim, her biri türü `SomeType`olan 10 öğeden oluşan bir dizi oluşturur. Bir `SomeType` başvuru türüyse, deyim, her biri null başvurusuna başharfle başharfe verilen 10 öğeden oluşan bir dizi oluşturur.  
  
Değer türleri ve başvuru türleri hakkında daha fazla bilgi için [Değer türleri](../../language-reference/builtin-types/value-types.md) ve [Başvuru türlerine](../../language-reference/keywords/reference-types.md)bakın.
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array>
- [C# Programlama Kılavuzu](../index.md)
- [Diziler](./index.md)
- [Çok Boyutlu Diziler](./multidimensional-arrays.md)
- [Basit Diziler](./jagged-arrays.md)
