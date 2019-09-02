---
title: 'Nasıl yapılır: Sorgu C# programlama kılavuzundaki öğe özelliklerinin alt kümelerini döndürme'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 2c9fea2189819058187020c2e67b8826659fbed4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205439"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="996d4-102">Nasıl yapılır: Sorguda öğe özelliklerinin alt kümelerini döndürme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="996d4-102">How to: Return Subsets of Element Properties in a Query (C# Programming Guide)</span></span>
<span data-ttu-id="996d4-103">Bu koşulların her ikisi de geçerli olduğunda bir sorgu ifadesinde anonim bir tür kullanın:</span><span class="sxs-lookup"><span data-stu-id="996d4-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="996d4-104">Her bir kaynak öğenin özelliklerinden yalnızca bazılarını döndürmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="996d4-104">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="996d4-105">Sorgu sonuçlarını sorgunun yürütüldüğü yöntemin kapsamı dışında saklamak zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="996d4-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="996d4-106">Her kaynak öğesinden yalnızca bir özellik veya alan döndürmek istiyorsanız, `select` yan tümcesindeki nokta işlecini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="996d4-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="996d4-107">Örneğin, yalnızca `ID` her `student`birini döndürmek için `select` yan tümcesini aşağıdaki gibi yazın:</span><span class="sxs-lookup"><span data-stu-id="996d4-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="996d4-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="996d4-108">Example</span></span>  
 <span data-ttu-id="996d4-109">Aşağıdaki örnek, belirtilen koşulla eşleşen her bir kaynak öğenin özelliklerinin yalnızca bir alt kümesini döndürmek için anonim bir türün nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="996d4-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="996d4-110">Anonim türün, hiçbir ad belirtilmemişse, özellikleri için kaynak öğenin adlarını kullandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="996d4-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="996d4-111">Anonim türdeki özelliklere yeni adlar vermek için, aşağıdaki gibi bir `select` ifade yazın:</span><span class="sxs-lookup"><span data-stu-id="996d4-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="996d4-112">Önceki örnekte `Console.WriteLine` bunu denerseniz deyimin de değiştirilmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="996d4-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="996d4-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="996d4-113">Compiling the Code</span></span>  
  
<span data-ttu-id="996d4-114">Bu kodu çalıştırmak için, bir C# `using` System. LINQ yönergesi ile sınıfı kopyalayıp bir konsol uygulamasına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="996d4-114">To run this code, copy and paste the class into a C# console application  with a `using` directive for System.Linq.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="996d4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="996d4-115">See also</span></span>

- [<span data-ttu-id="996d4-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="996d4-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="996d4-117">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="996d4-117">Anonymous Types</span></span>](./anonymous-types.md)
- [<span data-ttu-id="996d4-118">LINQ sorgu Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="996d4-118">LINQ Query Expressions</span></span>](../linq-query-expressions/index.md)
