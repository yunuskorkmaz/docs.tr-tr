---
title: "Nasıl yapılır: Bir Sorguda Öğe Özelliklerinin Alt Kümelerini Döndürme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6654b162fbdeb59ed2a135d7d8cf58c8b3406c13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
-   Bu kodu çalıştırmak için kopyalayıp sınıfı içinde oluşturduğunuz bir Visual C# konsol uygulaması projesi yapıştırın [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)]. Varsayılan olarak, bu proje 3.5 sürümünü hedefler [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], ve System.Core.dll başvuru gerekir ve bir `using` System.Linq yönergesi. Bir veya daha fazla bu gereksinimleri projeden eksikse, bunları el ile ekleyebilirsiniz.   
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)
