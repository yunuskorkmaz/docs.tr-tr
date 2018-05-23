---
title: 'Nasıl yapılır: Bir Sorguda Öğe Özelliklerinin Alt Kümelerini Döndürme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 3b43e7e3aafda5ee5b6a49f271f725fb8eeeca59
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="10fa4-102">Nasıl yapılır: Bir Sorguda Öğe Özelliklerinin Alt Kümelerini Döndürme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="10fa4-102">How to: Return Subsets of Element Properties in a Query (C# Programming Guide)</span></span>
<span data-ttu-id="10fa4-103">Bu koşulların her ikisi de uyguladığınızda sorgu ifadesinde anonim bir tür kullanın:</span><span class="sxs-lookup"><span data-stu-id="10fa4-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
-   <span data-ttu-id="10fa4-104">Her kaynak öğesinin özelliklerini yalnızca bazılarını dönmek istiyor.</span><span class="sxs-lookup"><span data-stu-id="10fa4-104">You want to return only some of the properties of each source element.</span></span>  
  
-   <span data-ttu-id="10fa4-105">Sorgunun yürütüldüğü yöntemi kapsamı dışında sorgunun sonuçlarını depolama gerekmez.</span><span class="sxs-lookup"><span data-stu-id="10fa4-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="10fa4-106">Yalnızca bir özellik veya alan her kaynak öğeden döndürmek istediğiniz sonra dot işleci yalnızca kullanabilirsiniz `select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="10fa4-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="10fa4-107">Örneğin, yalnızca döndürülecek `ID` her `student`, yazma `select` şekilde yan tümcesi:</span><span class="sxs-lookup"><span data-stu-id="10fa4-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="10fa4-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="10fa4-108">Example</span></span>  
 <span data-ttu-id="10fa4-109">Aşağıdaki örnekte, yalnızca belirtilen koşulu ile eşleşen her kaynak öğe özelliklerinin alt döndürmek için anonim bir tür kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="10fa4-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-subsets-of-element-properties-in-a-query_1.cs)]  
  
 <span data-ttu-id="10fa4-110">Hiçbir adı belirtilmezse, anonim tür özellikleri için kaynak öğenin adları kullandığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="10fa4-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="10fa4-111">Anonim tür özelliklerinde yeni adları vermek için yazma `select` deyimi aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="10fa4-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="10fa4-112">Önceki örnekte, bu çalışırsanız sonra `Console.WriteLine` deyimi aynı zamanda değiştirmeniz:</span><span class="sxs-lookup"><span data-stu-id="10fa4-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="10fa4-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="10fa4-113">Compiling the Code</span></span>  
  
-   <span data-ttu-id="10fa4-114">Bu kodu çalıştırmak için kopyalayın ve Visual Studio'da oluşturulan bir Visual C# konsol uygulaması projesi sınıfı yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="10fa4-114">To run this code, copy and paste the class into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="10fa4-115">Varsayılan olarak, bu proje 3.5 sürümünü hedefler [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], ve System.Core.dll başvuru gerekir ve bir `using` System.Linq yönergesi.</span><span class="sxs-lookup"><span data-stu-id="10fa4-115">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it will have a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="10fa4-116">Bir veya daha fazla bu gereksinimleri projeden eksikse, bunları el ile ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10fa4-116">If one or more of these requirements are missing from the project, you can add them manually.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="10fa4-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="10fa4-117">See Also</span></span>  
 [<span data-ttu-id="10fa4-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="10fa4-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="10fa4-119">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="10fa4-119">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="10fa4-120">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="10fa4-120">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
