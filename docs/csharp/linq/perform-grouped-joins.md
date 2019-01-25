---
title: (C# üzerinde LINQ) gruplandırılmış birleştirmeler gerçekleştirme
description: C# içinde LINQ kullanarak gruplandırılmış birleştirmeler gerçekleştirme konusunda bilgi edinin.
ms.date: 12/01/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: dfb75b55336d8ca486d5f10b187e955d20cd06fd
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857560"
---
# <a name="perform-grouped-joins"></a><span data-ttu-id="1b98a-103">Gruplandırılmış birleştirmeler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="1b98a-103">Perform grouped joins</span></span>

<span data-ttu-id="1b98a-104">Grup birleştirme hiyerarşik veri yapıları üretmek için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="1b98a-104">The group join is useful for producing hierarchical data structures.</span></span> <span data-ttu-id="1b98a-105">Bu, her öğeden ilk koleksiyonun ikinci koleksiyondan ilişkili öğeleri kümesi ile eşleşmesini.</span><span class="sxs-lookup"><span data-stu-id="1b98a-105">It pairs each element from the first collection with a set of correlated elements from the second collection.</span></span>

<span data-ttu-id="1b98a-106">Örneğin, bir sınıf veya adlı bir ilişkisel veritabanı tablo `Student` iki alanları içerebilir: `Id` ve `Name`.</span><span class="sxs-lookup"><span data-stu-id="1b98a-106">For example, a class or a relational database table named `Student` might contain two fields: `Id` and `Name`.</span></span> <span data-ttu-id="1b98a-107">Adlı ikinci bir sınıf veya ilişkisel veritabanı tablo `Course` iki alanları içerebilir: `StudentId` ve `CourseTitle`.</span><span class="sxs-lookup"><span data-stu-id="1b98a-107">A second class or relational database table named `Course` might contain two fields: `StudentId` and `CourseTitle`.</span></span> <span data-ttu-id="1b98a-108">Bu iki veri kaynağı grubu birleşimi tabanlı eşleşen `Student.Id` ve `Course.StudentId`, her grup `Student` koleksiyonuyla `Course` (boş olabilir) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1b98a-108">A group join of these two data sources, based on matching `Student.Id` and `Course.StudentId`, would group each `Student` with a collection of `Course` objects (which might be empty).</span></span>

> [!NOTE]
> <span data-ttu-id="1b98a-109">Sonuç kümesinde ilişkili öğeleri ikinci koleksiyonda bulunup bakılmaksızın, bir grup birleşimin ilk koleksiyonun her öğesine görünür.</span><span class="sxs-lookup"><span data-stu-id="1b98a-109">Each element of the first collection appears in the result set of a group join regardless of whether correlated elements are found in the second collection.</span></span> <span data-ttu-id="1b98a-110">Bağlantılı öğe bulunduğu durumlarda, o öğe için bağlantılı öğe dizisi boştur.</span><span class="sxs-lookup"><span data-stu-id="1b98a-110">In the case where no correlated elements are found, the sequence of correlated elements for that element is empty.</span></span> <span data-ttu-id="1b98a-111">Sonuç Seçici, bu nedenle ilk koleksiyonun her öğesine erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="1b98a-111">The result selector therefore has access to every element of the first collection.</span></span> <span data-ttu-id="1b98a-112">Bu ikinci koleksiyonda eşleşme olan ilk koleksiyondan öğeler erişilemiyor bir grup olmayan birleştirme sonucu seçicide farklıdır.</span><span class="sxs-lookup"><span data-stu-id="1b98a-112">This differs from the result selector in a non-group join, which cannot access elements from the first collection that have no match in the second collection.</span></span>

<span data-ttu-id="1b98a-113">Bu makalede ilk örnekte grubuna katılma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1b98a-113">The first example in this article shows you how to perform a group join.</span></span> <span data-ttu-id="1b98a-114">İkinci örnek XML öğeleri oluşturmak için bir grup birleştirme kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b98a-114">The second example shows you how to use a group join to create XML elements.</span></span>

## <a name="example---group-join"></a><span data-ttu-id="1b98a-115">Örnek - Group JOIN</span><span class="sxs-lookup"><span data-stu-id="1b98a-115">Example - Group join</span></span>

<span data-ttu-id="1b98a-116">Aşağıdaki örnek, bir grup birleşim türünde nesne gerçekleştirir `Person` ve `Pet` göre `Person` eşleşen `Pet.Owner` özelliği.</span><span class="sxs-lookup"><span data-stu-id="1b98a-116">The following example performs a group join of objects of type `Person` and `Pet` based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="1b98a-117">Her bir eşleştirmeyi çiftlerini oluşturur, bir grup olmayan birleşimin aksine group JOIN olan bu örnekte ilk koleksiyonun her öğe için yalnızca bir sonuç nesnesi oluşturur. bir `Person` nesne.</span><span class="sxs-lookup"><span data-stu-id="1b98a-117">Unlike a non-group join, which would produce a pair of elements for each match, the group join produces only one resulting object for each element of the first collection, which in this example is a `Person` object.</span></span> <span data-ttu-id="1b98a-118">Olan bu örnekte ikinci koleksiyon karşılık gelen öğeleri `Pet` nesneleri, bir koleksiyona gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="1b98a-118">The corresponding elements from the second collection, which in this example are `Pet` objects, are grouped into a collection.</span></span> <span data-ttu-id="1b98a-119">Son olarak, sonuç Seçici işlevi içeren her bir eşleşme için anonim bir tür oluşturur `Person.FirstName` ve koleksiyonu `Pet` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1b98a-119">Finally, the result selector function creates an anonymous type for each match that consists of `Person.FirstName` and a collection of `Pet` objects.</span></span>

[!code-csharp[CsLINQProgJoining#5](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]

## <a name="example---group-join-to-create-xml"></a><span data-ttu-id="1b98a-120">Örnek - Group JOIN XML dosyası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1b98a-120">Example - Group join to create XML</span></span>

<span data-ttu-id="1b98a-121">Grup birleştirmeleri, LINQ to XML kullanarak XML oluşturmak için idealdir.</span><span class="sxs-lookup"><span data-stu-id="1b98a-121">Group joins are ideal for creating XML by using LINQ to XML.</span></span> <span data-ttu-id="1b98a-122">Aşağıdaki örnek, anonim türler oluşturmak yerine, sonuç Seçici işlevi katılan nesnelerini temsil eden bir XML öğeleri oluşturur dışında önceki örneğe benzerdir.</span><span class="sxs-lookup"><span data-stu-id="1b98a-122">The following example is similar to the previous example except that instead of creating anonymous types, the result selector function creates XML elements that represent the joined objects.</span></span>

[!code-csharp[CsLINQProgJoining#6](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]

## <a name="see-also"></a><span data-ttu-id="1b98a-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b98a-123">See also</span></span>

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [<span data-ttu-id="1b98a-124">İç birleşimler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="1b98a-124">Perform inner joins</span></span>](perform-inner-joins.md)
- [<span data-ttu-id="1b98a-125">Sol dış birleştirmeler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="1b98a-125">Perform left outer joins</span></span>](perform-left-outer-joins.md)
- [<span data-ttu-id="1b98a-126">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="1b98a-126">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)
