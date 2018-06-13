---
title: Gruplandırılmış birleştirmeler gerçekleştirme
description: Gruplandırılmış birleştirmeler gerçekleştirme.
ms.date: 12/1/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: fbdb1a69fa2f3b171935fa3a58cf9a045be0a494
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288183"
---
# <a name="perform-grouped-joins"></a><span data-ttu-id="6ff78-103">Gruplandırılmış birleştirmeler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="6ff78-103">Perform grouped joins</span></span>

<span data-ttu-id="6ff78-104">Group JOIN hiyerarşik veri yapılarını üretmek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="6ff78-104">The group join is useful for producing hierarchical data structures.</span></span> <span data-ttu-id="6ff78-105">İlk koleksiyonun ikinci koleksiyondan ilişkili öğeleri kümesi ile her öğeden çiftleri.</span><span class="sxs-lookup"><span data-stu-id="6ff78-105">It pairs each element from the first collection with a set of correlated elements from the second collection.</span></span>  
  
 <span data-ttu-id="6ff78-106">Örneğin, bir sınıf veya adlı bir ilişkisel veritabanı tablo `Student` iki alanları içerebilir: `Id` ve `Name`.</span><span class="sxs-lookup"><span data-stu-id="6ff78-106">For example, a class or a relational database table named `Student` might contain two fields: `Id` and `Name`.</span></span> <span data-ttu-id="6ff78-107">Adlı ikinci sınıf veya ilişkisel veritabanı tablosu `Course` iki alanları içerebilir: `StudentId` ve `CourseTitle`.</span><span class="sxs-lookup"><span data-stu-id="6ff78-107">A second class or relational database table named `Course` might contain two fields: `StudentId` and `CourseTitle`.</span></span> <span data-ttu-id="6ff78-108">Bir grup birleşimi, bu iki veri kaynaklarının dayalı eşleşen `Student.Id` ve `Course.StudentId`, her grup `Student` koleksiyonuyla `Course` (boş olabilir) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="6ff78-108">A group join of these two data sources, based on matching `Student.Id` and `Course.StudentId`, would group each `Student` with a collection of `Course` objects (which might be empty).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ff78-109">İlk koleksiyonun her öğesine bağlantılı öğeler ikinci koleksiyonda bulunup bağımsız olarak bir grup birleştirme sonuç kümesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6ff78-109">Each element of the first collection appears in the result set of a group join regardless of whether correlated elements are found in the second collection.</span></span> <span data-ttu-id="6ff78-110">Bu öğe için ilişkili öğeleri dizisi ilişkili öğe bulunduğu durumda boştur.</span><span class="sxs-lookup"><span data-stu-id="6ff78-110">In the case where no correlated elements are found, the sequence of correlated elements for that element is empty.</span></span> <span data-ttu-id="6ff78-111">Sonuç Seçici bu nedenle ilk koleksiyonun her öğesine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="6ff78-111">The result selector therefore has access to every element of the first collection.</span></span> <span data-ttu-id="6ff78-112">Bu ikinci koleksiyonda eşleşme olan ilk koleksiyon öğeleri erişemez bir grup olmayan birleştirme sonucu seçicide farklıdır.</span><span class="sxs-lookup"><span data-stu-id="6ff78-112">This differs from the result selector in a non-group join, which cannot access elements from the first collection that have no match in the second collection.</span></span>  
  
 <span data-ttu-id="6ff78-113">Bu konudaki ilk örnek bir grup birleştirme gerçekleştirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ff78-113">The first example in this topic shows you how to perform a group join.</span></span> <span data-ttu-id="6ff78-114">İkinci örnek bir grup birleştirme XML öğeleri oluşturmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ff78-114">The second example shows you how to use a group join to create XML elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ff78-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="6ff78-115">Example</span></span>  
  
### <a name="group-join-example"></a><span data-ttu-id="6ff78-116">Grubu birleşim örneği</span><span class="sxs-lookup"><span data-stu-id="6ff78-116">Group join example</span></span>  
 <span data-ttu-id="6ff78-117">Aşağıdaki örnek nesne türü bir grup birleştirme gerçekleştirir `Person` ve `Pet` göre `Person` eşleşen `Pet.Owner` özelliği.</span><span class="sxs-lookup"><span data-stu-id="6ff78-117">The following example performs a group join of objects of type `Person` and `Pet` based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="6ff78-118">Her eşleşen öğeleri çifti oluşturur, bir grup olmayan birleşimin aksine group JOIN olan bu örnekte ilk koleksiyonun her öğe için yalnızca bir sonuç nesnesi oluşturur. bir `Person` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="6ff78-118">Unlike a non-group join, which would produce a pair of elements for each match, the group join produces only one resulting object for each element of the first collection, which in this example is a `Person` object.</span></span> <span data-ttu-id="6ff78-119">İkinci koleksiyon olan bu örnekte karşılık gelen öğeleri `Pet` nesneleri, bir koleksiyona gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="6ff78-119">The corresponding elements from the second collection, which in this example are `Pet` objects, are grouped into a collection.</span></span> <span data-ttu-id="6ff78-120">Son olarak, sonuç Seçici işlevi oluşan her eşleşmesi için anonim bir tür oluşturur `Person.FirstName` ve koleksiyonu `Pet` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="6ff78-120">Finally, the result selector function creates an anonymous type for each match that consists of `Person.FirstName` and a collection of `Pet` objects.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#5](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="6ff78-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="6ff78-121">Example</span></span>  
  
### <a name="group-join-to-create-xml-example"></a><span data-ttu-id="6ff78-122">XML örneği oluşturmak için Grup birleştirme</span><span class="sxs-lookup"><span data-stu-id="6ff78-122">Group join to create XML example</span></span>  
 <span data-ttu-id="6ff78-123">Grup birleştirmeleri LINQ-XML kullanılarak XML oluşturmak için idealdir.</span><span class="sxs-lookup"><span data-stu-id="6ff78-123">Group joins are ideal for creating XML by using LINQ to XML.</span></span> <span data-ttu-id="6ff78-124">Anonim türler oluşturmak yerine, sonuç Seçici işlevi birleştirilmiş nesneleri temsil XML öğeleri oluşturur aşağıdaki örnek önceki örneğe benzerdir.</span><span class="sxs-lookup"><span data-stu-id="6ff78-124">The following example is similar to the previous example except that instead of creating anonymous types, the result selector function creates XML elements that represent the joined objects.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#6](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="6ff78-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ff78-125">See also</span></span>  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [<span data-ttu-id="6ff78-126">İç birleşimler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="6ff78-126">Perform inner joins</span></span>](perform-inner-joins.md)  
 [<span data-ttu-id="6ff78-127">Sol dış birleştirmeler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="6ff78-127">Perform left outer joins</span></span>](perform-left-outer-joins.md)  
 [<span data-ttu-id="6ff78-128">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="6ff78-128">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 
