---
title: "Basit Diziler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f74eaf5334e8e2198f7a058717a4eb2ff0c1e775
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="jagged-arrays-c-programming-guide"></a>Basit Diziler (C# Programlama Kılavuzu)
Basit bir dizi, öğeleri dizi olan bir dizidir. Basit bir dizinin öğeleri farklı boyutları ve boyutları olabilir. Basit dizi bazen "oluşan bir dizi." olarak adlandırılır Aşağıdaki örnekler bildirmek üzere, başlatmak ve diziler erişim basit.  
  
 Her biri tek boyutlu dizisi olan üç öğeye sahip bir tek boyutlu dizi bildirimi verilmiştir:  
  
 [!code-csharp[csProgGuideArrays#19](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_1.cs)]  
  
 Kullanmadan önce `jaggedArray`, öğeleri başlatılması gerekir. Bu gibi öğeleri başlatabilirsiniz:  
  
 [!code-csharp[csProgGuideArrays#20](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_2.cs)]  
  
 Her öğe tek boyutlu dizisi içerir. İlk öğe 5 dizisi ikinci 4 dizisi ve üçüncü 2 tamsayılar dizisidir.  
  
 Dizi öğeleri değerlerle doldurmak için başlatıcıları kullanmak da mümkündür, bu durumda, dizi büyüklüğü gerekmez. Örneğin:  
  
 [!code-csharp[csProgGuideArrays#21](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_3.cs)]  
  
 Dizi bildirimi şöyle üzerine de başlatabilirsiniz:  
  
 [!code-csharp[csProgGuideArrays#22](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_4.cs)]  
  
 Aşağıdaki toplu formu kullanabilirsiniz. Atlayamazsınız bildirimi `new` öğeleri başlatma operatöründen öğeleri için hiçbir varsayılan başlatma olduğundan:  
  
 [!code-csharp[csProgGuideArrays#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_5.cs)]  
  
 Basit dizi oluşan bir dizi ve bu nedenle öğeleri başvuru türleri için başlatılan `null`.  
  
 Bu örnekler gibi tek bir dizi öğeleri erişebilirsiniz:  
  
 [!code-csharp[csProgGuideArrays#24](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_6.cs)]  
  
 Basit ve çok boyutlu diziler karıştırmak da mümkündür. Bir bildirim ve başlatma dizisinin farklı boyutlarda üç iki boyutlu dizi öğelerini içeren bir tek boyutlu basit verilmiştir. İki boyutlu diziler hakkında daha fazla bilgi için bkz: [çok boyutlu diziler](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).  
  
 [!code-csharp[csProgGuideArrays#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_7.cs)]  
  
 Öğesinin değerini görüntüler bu örnekte gösterildiği gibi ayrı ayrı öğeler erişebilirsiniz `[1,0]` ilk dizi (değer `5`):  
  
 [!code-csharp[csProgGuideArrays#26](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_8.cs)]  
  
 Yöntem `Length` basit dizinin içindeki diziler sayısını döndürür. Bu satırı önceki dizi bildirilen varsayılarak örneğin:  
  
 [!code-csharp[csProgGuideArrays#27](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_9.cs)]  
  
 3 değerini döndürür.  
  
## <a name="example"></a>Örnek  
 Bu örnek diziler kendilerini öğeleri olan bir dizi oluşturur. Dizi öğelerin her biri farklı bir boyutu vardır.  
  
 [!code-csharp[csProgGuideArrays#18](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_10.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Array>  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Diziler](../../../csharp/programming-guide/arrays/index.md)  
 [Tek boyutlu diziler](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Çok boyutlu diziler](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
