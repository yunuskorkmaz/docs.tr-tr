---
title: 'Nasıl yapılır: İçinde sorgu - öğe özelliklerinin alt kümelerini döndürme C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: da4ecb11c51f42c2297b6d40ed9a963590b3f441
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599980"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="d75bd-102">Nasıl yapılır: Bir sorguda öğe özelliklerinin alt kümelerini döndürür (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d75bd-102">How to: Return Subsets of Element Properties in a Query (C# Programming Guide)</span></span>
<span data-ttu-id="d75bd-103">Bu koşulların her ikisinin de geçerli olduğunda anonim bir tür bir sorgu ifadesinde kullanın:</span><span class="sxs-lookup"><span data-stu-id="d75bd-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="d75bd-104">Yalnızca bazı özelliklerin her kaynak öğesinin dönmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="d75bd-104">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="d75bd-105">Sorgunun yürütüldüğü yöntemi kapsamı dışında sorgu sonucunu depolamak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d75bd-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="d75bd-106">Yalnızca bir özellik veya alan her bir kaynak öğeden iade etmek istediğiniz sonra yalnızca nokta işlecinde kullanabilirsiniz `select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d75bd-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="d75bd-107">Örneğin, yalnızca döndürülecek `ID` her `student`, yazma `select` yan tümcesi aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="d75bd-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="d75bd-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="d75bd-108">Example</span></span>  
 <span data-ttu-id="d75bd-109">Aşağıdaki örnek, yalnızca belirtilen koşulu karşılayan her kaynak öğesi özelliklerinin bir alt döndürmek için anonim bir tür kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d75bd-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="d75bd-110">Hiç adları belirtildiyse anonim tür özellikleri için kaynak öğenin adlarını kullandığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="d75bd-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="d75bd-111">Anonim tür özellikleri için yeni adlar vermek için yazma `select` deyimi aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="d75bd-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="d75bd-112">Önceki örnekte, bunu denerseniz sonra `Console.WriteLine` deyimi de değiştirmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="d75bd-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d75bd-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d75bd-113">Compiling the Code</span></span>  
  
- <span data-ttu-id="d75bd-114">Bu kodu çalıştırmak için kopyalayın ve Visual Studio'da oluşturulan bir Visual C# konsol uygulaması projesi sınıfı yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="d75bd-114">To run this code, copy and paste the class into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="d75bd-115">Varsayılan olarak, bu proje 3.5 sürümünü hedefleyen [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], ve bir System.Core.dll başvurusu gerekir ve bir `using` System.Linq yönergesi.</span><span class="sxs-lookup"><span data-stu-id="d75bd-115">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it will have a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="d75bd-116">Projeden bir veya daha fazla bu gereksinimleri eksikse, bunları el ile ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d75bd-116">If one or more of these requirements are missing from the project, you can add them manually.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="d75bd-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d75bd-117">See also</span></span>

- [<span data-ttu-id="d75bd-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d75bd-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d75bd-119">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="d75bd-119">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="d75bd-120">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="d75bd-120">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
