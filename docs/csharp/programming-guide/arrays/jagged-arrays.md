---
title: Pürüzlü Diziler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 56013f0143d5efcb31a476909cb6e92504ff0dbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705710"
---
# <a name="jagged-arrays-c-programming-guide"></a>Basit Diziler (C# Programlama Kılavuzu)

Basit bir dizi, öğeleri dizi olan bir dizidir. Pürüzlü bir dizinin öğeleri farklı boyut ve boyutlarda olabilir. Pürüzlü bir dizi bazen "diziler dizisi" olarak adlandırılır. Aşağıdaki örnekler, pürüzlü dizileri nasıl bildirecek, başharfe bildirecek ve bunlara erişeceklerini gösterir.  
  
 Aşağıda, her biri tek boyutlu bir tamsayı dizisi olan üç öğeye sahip tek boyutlu bir dizinin bildirimi veremi ve  
  
 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]  
  
 Kullanmadan `jaggedArray`önce, öğeleri nin baş harfe byönelik olması gerekir. Aşağıdaki gibi öğeleri başlangıç yapabilirsiniz:  
  
 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]  
  
 Öğelerin her biri tamsayılar tek boyutlu bir dizidir. İlk öğe 5 tümseci, ikinci 4 tümseci bir dizi ve üçüncü 2 tümsek bir dizi.  
  
 Dizi öğelerini değerlerle doldurmak için baş harflerini kullanmak da mümkündür, bu durumda dizi boyutuna ihtiyacınız yoktur. Örnek:  
  
 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]  
  
 Ayrıca, aşağıdaki gibi bir bildirim üzerine diziyi de başolarak alabilirsiniz:  
  
 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]  
  
 Aşağıdaki steno formunu kullanabilirsiniz. Öğeler için varsayılan bir `new` başlatma olmadığından işleci eleman başlatmadan atlayamayacağınıza dikkat edin:  
  
 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]  
  
 Pürüzlü bir dizi dizi dizidir ve bu nedenle öğeleri başvuru `null`türleridir ve '' için başharfler.  
  
 Aşağıdaki örnekler gibi tek tek dizi öğelerine erişebilirsiniz:  
  
 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]  
  
 Pürüzlü ve çok boyutlu dizileri karıştırmak mümkündür. Aşağıda, farklı boyutlarda üç iki boyutlu dizi öğesi içeren tek boyutlu pürüzlü bir dizinin bildirimi ve başlatılması dır. İki boyutlu diziler hakkında daha fazla bilgi için [çok boyutlu diziler'e](./multidimensional-arrays.md)bakın.  
  
 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]  
  
 İlk dizi (değer) `[1,0]` `5`öğesinin değerini görüntüleyen bu örnekte gösterildiği gibi tek tek öğelere erişebilirsiniz:  
  
 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]  
  
 Yöntem, `Length` pürüzlü dizide bulunan dizi sayısını döndürür. Örneğin, önceki diziyi beyan ettiğinizi varsayarsak, bu satır:  
  
 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]  
  
 3 değerini döndürür.  
  
## <a name="example"></a>Örnek

 Bu örnek, öğeleri kendileri dizileri olan bir dizi oluşturur. Dizi öğelerinin her birinin farklı bir boyutu vardır.  
  
 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array>
- [C# Programlama Kılavuzu](../index.md)
- [Diziler](./index.md)
- [Tek Boyutlu Diziler](./single-dimensional-arrays.md)
- [Çok Boyutlu Diziler](./multidimensional-arrays.md)
