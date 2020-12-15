---
title: Bir sorguda öğe özelliklerinin alt kümelerini döndürme-C# Programlama Kılavuzu
description: Her bir kaynak öğesinin özelliklerinden bazılarını döndürmek Için C# içindeki bir sorgu ifadesinde anonim bir tür kullanmayı öğrenin.
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 5784d6a288af374d357346e32535ebe9c1877bcc
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512801"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="0dbb8-103">Sorguda öğe özelliklerinin alt kümelerini döndürme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0dbb8-103">How to return subsets of element properties in a query (C# Programming Guide)</span></span>

<span data-ttu-id="0dbb8-104">Bu koşulların her ikisi de geçerli olduğunda bir sorgu ifadesinde anonim bir tür kullanın:</span><span class="sxs-lookup"><span data-stu-id="0dbb8-104">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="0dbb8-105">Her bir kaynak öğenin özelliklerinden yalnızca bazılarını döndürmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="0dbb8-105">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="0dbb8-106">Sorgu sonuçlarını sorgunun yürütüldüğü yöntemin kapsamı dışında saklamak zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="0dbb8-106">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="0dbb8-107">Her kaynak öğesinden yalnızca bir özellik veya alan döndürmek istiyorsanız, yan tümcesindeki nokta işlecini kullanabilirsiniz `select` .</span><span class="sxs-lookup"><span data-stu-id="0dbb8-107">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="0dbb8-108">Örneğin, yalnızca her birini döndürmek için `ID` `student` `select` yan tümcesini aşağıdaki gibi yazın:</span><span class="sxs-lookup"><span data-stu-id="0dbb8-108">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="0dbb8-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="0dbb8-109">Example</span></span>  

 <span data-ttu-id="0dbb8-110">Aşağıdaki örnek, belirtilen koşulla eşleşen her bir kaynak öğenin özelliklerinin yalnızca bir alt kümesini döndürmek için anonim bir türün nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0dbb8-110">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="0dbb8-111">Anonim türün, hiçbir ad belirtilmemişse, özellikleri için kaynak öğenin adlarını kullandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0dbb8-111">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="0dbb8-112">Anonim türdeki özelliklere yeni adlar vermek için, `select` aşağıdaki gibi bir ifade yazın:</span><span class="sxs-lookup"><span data-stu-id="0dbb8-112">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="0dbb8-113">Önceki örnekte bunu denerseniz `Console.WriteLine` deyimin de değiştirilmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="0dbb8-113">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0dbb8-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0dbb8-114">Compiling the Code</span></span>  
  
<span data-ttu-id="0dbb8-115">Bu kodu çalıştırmak için, sınıfı bir C# konsol uygulamasına kopyalayın ve bir `using` System. LINQ yönergesi ile yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="0dbb8-115">To run this code, copy and paste the class into a C# console application  with a `using` directive for System.Linq.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0dbb8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dbb8-116">See also</span></span>

- [<span data-ttu-id="0dbb8-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0dbb8-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0dbb8-118">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="0dbb8-118">Anonymous Types</span></span>](./anonymous-types.md)
- [<span data-ttu-id="0dbb8-119">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="0dbb8-119">LINQ in C#</span></span>](../../linq/index.md)
