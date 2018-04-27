---
title: 'Nasıl yapılır: Bir Sorguda Öğe Özelliklerinin Alt Kümelerini Döndürme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d77c04210c7e6e6084b6f6887378c930abcf1608
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Nasıl yapılır: Bir Sorguda Öğe Özelliklerinin Alt Kümelerini Döndürme (C# Programlama Kılavuzu)
Bu koşulların her ikisi de uyguladığınızda sorgu ifadesinde anonim bir tür kullanın:  
  
-   Her kaynak öğesinin özelliklerini yalnızca bazılarını dönmek istiyor.  
  
-   Sorgunun yürütüldüğü yöntemi kapsamı dışında sorgunun sonuçlarını depolama gerekmez.  
  
 Yalnızca bir özellik veya alan her kaynak öğeden döndürmek istediğiniz sonra dot işleci yalnızca kullanabilirsiniz `select` yan tümcesi. Örneğin, yalnızca döndürülecek `ID` her `student`, yazma `select` şekilde yan tümcesi:  
  
```  
select student.ID;  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, yalnızca belirtilen koşulu ile eşleşen her kaynak öğe özelliklerinin alt döndürmek için anonim bir tür kullanmayı gösterir.  
  
 [!code-csharp[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-subsets-of-element-properties-in-a-query_1.cs)]  
  
 Hiçbir adı belirtilmezse, anonim tür özellikleri için kaynak öğenin adları kullandığına dikkat edin. Anonim tür özelliklerinde yeni adları vermek için yazma `select` deyimi aşağıdaki gibi:  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 Önceki örnekte, bu çalışırsanız sonra `Console.WriteLine` deyimi aynı zamanda değiştirmeniz:  
  
```  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bu kodu çalıştırmak için kopyalayın ve Visual Studio'da oluşturulan bir Visual C# konsol uygulaması projesi sınıfı yapıştırın. Varsayılan olarak, bu proje 3.5 sürümünü hedefler [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], ve System.Core.dll başvuru gerekir ve bir `using` System.Linq yönergesi. Bir veya daha fazla bu gereksinimleri projeden eksikse, bunları el ile ekleyebilirsiniz.   
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Anonim Tipler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)
