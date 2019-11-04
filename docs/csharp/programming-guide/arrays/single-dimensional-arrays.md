---
title: Tek boyutlu diziler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: 5559acd162b26a94b009ec21691d1501c90db290
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419523"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>Tek Boyutlu Diziler (C# Programlama Kılavuzu)

Aşağıdaki örnekte gösterildiği gibi, beş tamsayının tek boyutlu bir dizisini bildirebilirsiniz:  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 Bu dizi `array[4]``array[0]` öğeleri içerir. [New](../../language-reference/operators/new-operator.md) işleci diziyi oluşturmak için kullanılır ve dizi öğelerini varsayılan değerlerine başlatır. Bu örnekte, tüm dizi öğeleri sıfır olarak başlatılır.  
  
 Dize öğelerini depolayan bir dizi aynı şekilde bildirilebilecek. Örneğin:  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a>Dizi başlatma

 Bildirim üzerine bir diziyi başlatmak mümkündür, bu durumda, başlatma listesindeki öğe sayısı tarafından zaten sağlandığı için uzunluk belirleyicisi gerekli değildir. Örneğin:  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 Dize dizisi aynı şekilde başlatılabilir. Aşağıda her dizi öğesinin bir günün adı ile başlatıldığı bir dize dizisinin bildirimi verilmiştir:  
 
 ```csharp
 string[] weekDays = new string[] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
 ```
  
 Bildirim üzerine bir diziyi başlattığınızda, aşağıdaki kısayolları kullanabilirsiniz:  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 Başlatma olmadan bir dizi değişkeni bildirmek mümkündür, ancak bu değişkene bir dizi atadığınızda `new` işlecini kullanmanız gerekir. Örneğin:  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 C#3,0 örtük olarak yazılmış dizileri tanıtır. Daha fazla bilgi için bkz. [örtülü olarak yazılan diziler](./implicitly-typed-arrays.md).  
  
## <a name="value-type-and-reference-type-arrays"></a>Değer türü ve başvuru türü dizileri

 Aşağıdaki dizi bildirimini göz önünde bulundurun:  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 Bu deyimin sonucu, `SomeType` bir değer türü veya bir başvuru türü olmasına bağlıdır. Değer bir tür ise, ifade, her birinin türü `SomeType`olan 10 öğeden oluşan bir dizi oluşturur. `SomeType` bir başvuru türü ise, ifade her biri null başvuruya başlatılan 10 öğeden oluşan bir dizi oluşturur.  
  
 Değer türleri ve başvuru türleri hakkında daha fazla bilgi için bkz. [türler](/dotnet/csharp/language-reference/keywords).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array>
- [C# Programlama Kılavuzu](../index.md)
- [Diziler](./index.md)
- [Çok Boyutlu Diziler](./multidimensional-arrays.md)
- [Düzensiz Diziler](./jagged-arrays.md)
