---
title: Sorguda öğe özelliklerialt kümeleri nasıl döndürülür - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 27a2626fc46307a7195040adf746d8d8757d2f82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714865"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="63b28-102">Sorguda öğe özelliklerialt kümeleri döndürülür (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="63b28-102">How to return subsets of element properties in a query (C# Programming Guide)</span></span>
<span data-ttu-id="63b28-103">Bu koşulların her ikisi de geçerli olduğunda sorgu ifadesinde anonim bir tür kullanın:</span><span class="sxs-lookup"><span data-stu-id="63b28-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="63b28-104">Her kaynak öğenin özelliklerinden yalnızca bazılarını döndürmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="63b28-104">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="63b28-105">Sorgu sonuçlarını, sorgunun yürütüldedildiği yöntemin kapsamı dışında depolamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="63b28-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="63b28-106">Her kaynak öğeden yalnızca bir özellik veya alan döndürmek istiyorsanız, yan tümcedeki nokta işlecini `select` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63b28-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="63b28-107">Örneğin, her `ID` biri `student`yalnızca dönmek için, aşağıdaki gibi yan tümcesini `select` yazın:</span><span class="sxs-lookup"><span data-stu-id="63b28-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="63b28-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="63b28-108">Example</span></span>  
 <span data-ttu-id="63b28-109">Aşağıdaki örnek, belirtilen koşulla eşleşen her kaynak öğenin özelliklerinin yalnızca bir alt kümesini döndürmek için anonim bir türün nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="63b28-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="63b28-110">Ad belirtilmemişse, adsız yazının özellikleri için kaynak öğe öğesinin adlarını kullandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="63b28-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="63b28-111">Anonim türdeki özelliklere yeni adlar vermek `select` için deyimi aşağıdaki gibi yazın:</span><span class="sxs-lookup"><span data-stu-id="63b28-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="63b28-112">Önceki örnekte bunu denerseniz, `Console.WriteLine` deyimin de değişmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="63b28-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="63b28-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="63b28-113">Compiling the Code</span></span>  
  
<span data-ttu-id="63b28-114">Bu kodu çalıştırmak için sınıfı System.Linq `using` yönergesi ile c# konsolu uygulamasına kopyalayıp yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="63b28-114">To run this code, copy and paste the class into a C# console application  with a `using` directive for System.Linq.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="63b28-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63b28-115">See also</span></span>

- [<span data-ttu-id="63b28-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="63b28-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="63b28-117">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="63b28-117">Anonymous Types</span></span>](./anonymous-types.md)
- [<span data-ttu-id="63b28-118">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="63b28-118">LINQ in C#</span></span>](../../linq/index.md)
