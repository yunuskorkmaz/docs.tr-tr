---
title: "Gruplandırılmış birleştirmeler gerçekleştirme"
description: "Gruplandırılmış birleştirmeler gerçekleştirme."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: 5e26473e19a5b6107d7aceea5e9829b48aa522b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="perform-grouped-joins"></a><span data-ttu-id="ec0a3-104">Gruplandırılmış birleştirmeler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="ec0a3-104">Perform grouped joins</span></span>

<span data-ttu-id="ec0a3-105">Group JOIN hiyerarşik veri yapılarını üretmek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="ec0a3-105">The group join is useful for producing hierarchical data structures.</span></span> <span data-ttu-id="ec0a3-106">İlk koleksiyonun ikinci koleksiyondan ilişkili öğeleri kümesi ile her öğeden çiftleri.</span><span class="sxs-lookup"><span data-stu-id="ec0a3-106">It pairs each element from the first collection with a set of correlated elements from the second collection.</span></span>  
  
 <span data-ttu-id="ec0a3-107">Örneğin, bir sınıf veya adlı bir ilişkisel veritabanı tablo `Student` iki alanları içerebilir: `Id` ve `Name`.</span><span class="sxs-lookup"><span data-stu-id="ec0a3-107">For example, a class or a relational database table named `Student` might contain two fields: `Id` and `Name`.</span></span> <span data-ttu-id="ec0a3-108">Adlı ikinci sınıf veya ilişkisel veritabanı tablosu `Course` iki alanları içerebilir: `StudentId` ve `CourseTitle`.</span><span class="sxs-lookup"><span data-stu-id="ec0a3-108">A second class or relational database table named `Course` might contain two fields: `StudentId` and `CourseTitle`.</span></span> <span data-ttu-id="ec0a3-109">Bir grup birleşimi, bu iki veri kaynaklarının dayalı eşleşen `Student.Id` ve `Course.StudentId`, her grup `Student` koleksiyonuyla `Course` (boş olabilir) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="ec0a3-109">A group join of these two data sources, based on matching `Student.Id` and `Course.StudentId`, would group each `Student` with a collection of `Course` objects (which might be empty).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec0a3-110">İlk koleksiyonun her öğesine bağlantılı öğeler ikinci koleksiyonda bulunup bağımsız olarak bir grup birleştirme sonuç kümesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ec0a3-110">Each element of the first collection appears in the result set of a group join regardless of whether correlated elements are found in the second collection.</span></span> <span data-ttu-id="ec0a3-111">Bu öğe için ilişkili öğeleri dizisi ilişkili öğe bulunduğu durumda boştur.</span><span class="sxs-lookup"><span data-stu-id="ec0a3-111">In the case where no correlated elements are found, the sequence of correlated elements for that element is empty.</span></span> <span data-ttu-id="ec0a3-112">Sonuç Seçici bu nedenle ilk koleksiyonun her öğesine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="ec0a3-112">The result selector therefore has access to every element of the first collection.</span></span> <span data-ttu-id="ec0a3-113">Bu ikinci koleksiyonda eşleşme olan ilk koleksiyon öğeleri erişemez bir grup olmayan birleştirme sonucu seçicide farklıdır.</span><span class="sxs-lookup"><span data-stu-id="ec0a3-113">This differs from the result selector in a non-group join, which cannot access elements from the first collection that have no match in the second collection.</span></span>  
  
 <span data-ttu-id="ec0a3-114">Bu konudaki ilk örnek bir grup birleştirme gerçekleştirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec0a3-114">The first example in this topic shows you how to perform a group join.</span></span> <span data-ttu-id="ec0a3-115">İkinci örnek bir grup birleştirme XML öğeleri oluşturmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec0a3-115">The second example shows you how to use a group join to create XML elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec0a3-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec0a3-116">Example</span></span>  
  
### <a name="group-join-example"></a><span data-ttu-id="ec0a3-117">Grubu birleşim örneği</span><span class="sxs-lookup"><span data-stu-id="ec0a3-117">Group join example</span></span>  
 <span data-ttu-id="ec0a3-118">Aşağıdaki örnek nesne türü bir grup birleştirme gerçekleştirir `Person` ve `Pet` göre `Person` eşleşen `Pet.Owner` özelliği.</span><span class="sxs-lookup"><span data-stu-id="ec0a3-118">The following example performs a group join of objects of type `Person` and `Pet` based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="ec0a3-119">Her eşleşen öğeleri çifti oluşturur, bir grup olmayan birleşimin aksine group JOIN olan bu örnekte ilk koleksiyonun her öğe için yalnızca bir sonuç nesnesi oluşturur. bir `Person` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ec0a3-119">Unlike a non-group join, which would produce a pair of elements for each match, the group join produces only one resulting object for each element of the first collection, which in this example is a `Person` object.</span></span> <span data-ttu-id="ec0a3-120">İkinci koleksiyon olan bu örnekte karşılık gelen öğeleri `Pet` nesneleri, bir koleksiyona gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="ec0a3-120">The corresponding elements from the second collection, which in this example are `Pet` objects, are grouped into a collection.</span></span> <span data-ttu-id="ec0a3-121">Son olarak, sonuç Seçici işlevi oluşan her eşleşmesi için anonim bir tür oluşturur `Person.FirstName` ve koleksiyonu `Pet` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="ec0a3-121">Finally, the result selector function creates an anonymous type for each match that consists of `Person.FirstName` and a collection of `Pet` objects.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#5](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="ec0a3-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec0a3-122">Example</span></span>  
  
### <a name="group-join-to-create-xml-example"></a><span data-ttu-id="ec0a3-123">XML örneği oluşturmak için Grup birleştirme</span><span class="sxs-lookup"><span data-stu-id="ec0a3-123">Group join to create XML example</span></span>  
 <span data-ttu-id="ec0a3-124">Grup birleştirmeleri LINQ-XML kullanılarak XML oluşturmak için idealdir.</span><span class="sxs-lookup"><span data-stu-id="ec0a3-124">Group joins are ideal for creating XML by using LINQ to XML.</span></span> <span data-ttu-id="ec0a3-125">Anonim türler oluşturmak yerine, sonuç Seçici işlevi birleştirilmiş nesneleri temsil XML öğeleri oluşturur aşağıdaki örnek önceki örneğe benzerdir.</span><span class="sxs-lookup"><span data-stu-id="ec0a3-125">The following example is similar to the previous example except that instead of creating anonymous types, the result selector function creates XML elements that represent the joined objects.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#6](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="ec0a3-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec0a3-126">See also</span></span>  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [<span data-ttu-id="ec0a3-127">İç birleştirmeler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="ec0a3-127">Perform inner joins</span></span>](perform-inner-joins.md)  
 [<span data-ttu-id="ec0a3-128">Sol dış birleştirmeler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="ec0a3-128">Perform left outer joins</span></span>](perform-left-outer-joins.md)  
 [<span data-ttu-id="ec0a3-129">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="ec0a3-129">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 
