---
title: Basit diziler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 9fc05c8bdebf9c1c6b613db0b6a121e06765ac00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61652006"
---
# <a name="jagged-arrays-c-programming-guide"></a>Basit Diziler (C# Programlama Kılavuzu)

Basit bir dizi, öğeleri dizi olan bir dizidir. Düzensiz bir dizi öğelerinden farklı boyutları ve boyutları olabilir. Basit bir dizi bazen "oluşan bir dizi." olarak adlandırılır Aşağıdaki örnekler nasıl bildirin, başlatmak ve erişimi, diziler basit.  
  
 Her biri tek boyutlu dizisi olan üç öğeye sahip bir tek boyutlu dizi bildirimi verilmiştir:  
  
 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]  
  
 Kullanmadan önce `jaggedArray`, öğeleri başlatılması gerekir. Bunun gibi öğelerin başlatabilirsiniz:  
  
 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]  
  
 Öğelerin her biri, tamsayı tek boyutlu bir dizidir. İlk öğe 5 tamsayı dizisi, ikinci 4 tamsayı dizisi ve üçüncü 2 tamsayılar dizisidir.  
  
 Dizi öğeleri değerlerle doldurmak için başlatıcılar kullanmak da mümkündür, bu durumda, dizi boyutu ihtiyacınız yoktur. Örneğin:  
  
 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]  
  
 Ayrıca, dizi bildirimi böyle üzerine başlatabilirsiniz:  
  
 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]  
  
 Aşağıdaki toplu formu kullanabilirsiniz. Dikkat edin, atlayamazsınız `new` öğeleri başlatma operatöründen olmadığı için öğeler için varsayılan başlatma:  
  
 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]  
  
 Düzensiz bir dizi, dizilerin bir dizidir ve bu nedenle öğeleri başvuru türleridir ve başlatılır `null`.  
  
 Bu örnekler gibi tek bir dizi öğelerine erişebilirsiniz:  
  
 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]  
  
 Basit ve çok boyutlu diziler karıştırmak mümkündür. Bir bildirimi ve başlatılması farklı boyutlardaki üç iki boyutlu dizi öğeleri içeren tek boyutlu bir düzensiz dizi aşağıda verilmiştir. İki boyutlu dizileri hakkında daha fazla bilgi için bkz: [çok boyutlu diziler](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).  
  
 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]  
  
 Öğenin değeri görüntüler bu örnekte gösterildiği gibi tek tek öğelerine erişebilirsiniz `[1,0]` ilk dizinin (değer `5`):  
  
 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]  
  
 Yöntem `Length` diziler düzensiz dizi içinde yer alan sayısını döndürür. Bu satır önceki dizinin derlendiğinden varsayılarak örneğin:  
  
 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]  
  
 3 değerini döndürür.  
  
## <a name="example"></a>Örnek

 Bu örnek, dizileri kendilerini öğeleri olan bir dizi oluşturur. Dizi öğelerinin her biri farklı bir boyuta sahiptir.  
  
 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array>
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Diziler](../../../csharp/programming-guide/arrays/index.md)
- [Tek Boyutlu Diziler](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [Çok Boyutlu Diziler](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
