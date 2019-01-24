---
title: 'Nasıl yapılır: İçinde sorgu - öğe özelliklerinin alt kümelerini döndürme C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 36e910328651cc4f91acdfb2d40edea56cde2a9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676490"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Nasıl yapılır: Bir sorguda öğe özelliklerinin alt kümelerini döndürür (C# Programlama Kılavuzu)
Bu koşulların her ikisinin de geçerli olduğunda anonim bir tür bir sorgu ifadesinde kullanın:  
  
-   Yalnızca bazı özelliklerin her kaynak öğesinin dönmek istiyorsunuz.  
  
-   Sorgunun yürütüldüğü yöntemi kapsamı dışında sorgu sonucunu depolamak gerekmez.  
  
 Yalnızca bir özellik veya alan her bir kaynak öğeden iade etmek istediğiniz sonra yalnızca nokta işlecinde kullanabilirsiniz `select` yan tümcesi. Örneğin, yalnızca döndürülecek `ID` her `student`, yazma `select` yan tümcesi aşağıdaki gibi:  
  
```  
select student.ID;  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yalnızca belirtilen koşulu karşılayan her kaynak öğesi özelliklerinin bir alt döndürmek için anonim bir tür kullanmayı gösterir.  
  
 [!code-csharp[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-subsets-of-element-properties-in-a-query_1.cs)]  
  
 Hiç adları belirtildiyse anonim tür özellikleri için kaynak öğenin adlarını kullandığına dikkat edin. Anonim tür özellikleri için yeni adlar vermek için yazma `select` deyimi aşağıdaki gibi:  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 Önceki örnekte, bunu denerseniz sonra `Console.WriteLine` deyimi de değiştirmesi gerekir:  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bu kodu çalıştırmak için kopyalayın ve Visual Studio'da oluşturulan bir Visual C# konsol uygulaması projesi sınıfı yapıştırın. Varsayılan olarak, bu proje 3.5 sürümünü hedefleyen [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], ve bir System.Core.dll başvurusu gerekir ve bir `using` System.Linq yönergesi. Projeden bir veya daha fazla bu gereksinimleri eksikse, bunları el ile ekleyebilirsiniz.   
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Anonim Tipler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)
