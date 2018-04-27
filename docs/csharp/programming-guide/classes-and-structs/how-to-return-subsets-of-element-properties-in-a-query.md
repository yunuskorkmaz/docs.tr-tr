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
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="59931-102">Nasıl yapılır: Bir Sorguda Öğe Özelliklerinin Alt Kümelerini Döndürme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="59931-102">How to: Return Subsets of Element Properties in a Query (C# Programming Guide)</span></span>
<span data-ttu-id="59931-103">Bu koşulların her ikisi de uyguladığınızda sorgu ifadesinde anonim bir tür kullanın:</span><span class="sxs-lookup"><span data-stu-id="59931-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
-   <span data-ttu-id="59931-104">Her kaynak öğesinin özelliklerini yalnızca bazılarını dönmek istiyor.</span><span class="sxs-lookup"><span data-stu-id="59931-104">You want to return only some of the properties of each source element.</span></span>  
  
-   <span data-ttu-id="59931-105">Sorgunun yürütüldüğü yöntemi kapsamı dışında sorgunun sonuçlarını depolama gerekmez.</span><span class="sxs-lookup"><span data-stu-id="59931-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="59931-106">Yalnızca bir özellik veya alan her kaynak öğeden döndürmek istediğiniz sonra dot işleci yalnızca kullanabilirsiniz `select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="59931-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="59931-107">Örneğin, yalnızca döndürülecek `ID` her `student`, yazma `select` şekilde yan tümcesi:</span><span class="sxs-lookup"><span data-stu-id="59931-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="59931-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="59931-108">Example</span></span>  
 <span data-ttu-id="59931-109">Aşağıdaki örnekte, yalnızca belirtilen koşulu ile eşleşen her kaynak öğe özelliklerinin alt döndürmek için anonim bir tür kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="59931-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-subsets-of-element-properties-in-a-query_1.cs)]  
  
 <span data-ttu-id="59931-110">Hiçbir adı belirtilmezse, anonim tür özellikleri için kaynak öğenin adları kullandığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="59931-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="59931-111">Anonim tür özelliklerinde yeni adları vermek için yazma `select` deyimi aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="59931-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="59931-112">Önceki örnekte, bu çalışırsanız sonra `Console.WriteLine` deyimi aynı zamanda değiştirmeniz:</span><span class="sxs-lookup"><span data-stu-id="59931-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="59931-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="59931-113">Compiling the Code</span></span>  
  
-   <span data-ttu-id="59931-114">Bu kodu çalıştırmak için kopyalayın ve Visual Studio'da oluşturulan bir Visual C# konsol uygulaması projesi sınıfı yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="59931-114">To run this code, copy and paste the class into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="59931-115">Varsayılan olarak, bu proje 3.5 sürümünü hedefler [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], ve System.Core.dll başvuru gerekir ve bir `using` System.Linq yönergesi.</span><span class="sxs-lookup"><span data-stu-id="59931-115">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it will have a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="59931-116">Bir veya daha fazla bu gereksinimleri projeden eksikse, bunları el ile ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59931-116">If one or more of these requirements are missing from the project, you can add them manually.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="59931-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="59931-117">See Also</span></span>  
 [<span data-ttu-id="59931-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="59931-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="59931-119">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="59931-119">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="59931-120">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="59931-120">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
