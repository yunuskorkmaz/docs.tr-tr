---
title: Gruplanmış birleştirmeleri gerçekleştirin (LinQ C#'da)
description: C#'da LINQ kullanarak gruplu birleştirmeleri nasıl gerçekleştireceklerini öğrenin.
ms.date: 12/01/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: dfb75b55336d8ca486d5f10b187e955d20cd06fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61689144"
---
# <a name="perform-grouped-joins"></a><span data-ttu-id="bc932-103">Gruplanmış birleşimler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="bc932-103">Perform grouped joins</span></span>

<span data-ttu-id="bc932-104">Grup birleştirme hiyerarşik veri yapıları üretmek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="bc932-104">The group join is useful for producing hierarchical data structures.</span></span> <span data-ttu-id="bc932-105">İlk koleksiyondaki her öğeyi ikinci koleksiyondaki ilişkili öğeler kümesiyle eşler.</span><span class="sxs-lookup"><span data-stu-id="bc932-105">It pairs each element from the first collection with a set of correlated elements from the second collection.</span></span>

<span data-ttu-id="bc932-106">Örneğin, bir sınıf veya ilişkisel `Student` veritabanı tablosu adlı `Id` `Name`iki alan içerebilir: ve .</span><span class="sxs-lookup"><span data-stu-id="bc932-106">For example, a class or a relational database table named `Student` might contain two fields: `Id` and `Name`.</span></span> <span data-ttu-id="bc932-107">İkinci sınıf veya ilişkisel `Course` veritabanı tablosu adlı `StudentId` `CourseTitle`iki alan içerebilir: ve .</span><span class="sxs-lookup"><span data-stu-id="bc932-107">A second class or relational database table named `Course` might contain two fields: `StudentId` and `CourseTitle`.</span></span> <span data-ttu-id="bc932-108">Bu iki veri kaynağının grup birleşimi, `Student.Id` eşleştirmeye dayalıdır `Course.StudentId`ve her birini `Student` bir `Course` nesne koleksiyonuyla gruplar (boş olabilir).</span><span class="sxs-lookup"><span data-stu-id="bc932-108">A group join of these two data sources, based on matching `Student.Id` and `Course.StudentId`, would group each `Student` with a collection of `Course` objects (which might be empty).</span></span>

> [!NOTE]
> <span data-ttu-id="bc932-109">İlk koleksiyonun her öğesi, ikinci koleksiyonda ilişkili öğelerin bulunup bulunmadığına bakılmaksızın bir grup birleştirme sonucu kümesinde görünür.</span><span class="sxs-lookup"><span data-stu-id="bc932-109">Each element of the first collection appears in the result set of a group join regardless of whether correlated elements are found in the second collection.</span></span> <span data-ttu-id="bc932-110">İlişkili öğelerin bulunmadığı durumlarda, bu öğe için ilişkili öğelerin sırası boştur.</span><span class="sxs-lookup"><span data-stu-id="bc932-110">In the case where no correlated elements are found, the sequence of correlated elements for that element is empty.</span></span> <span data-ttu-id="bc932-111">Sonuç seçici bu nedenle ilk koleksiyonun her öğesine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="bc932-111">The result selector therefore has access to every element of the first collection.</span></span> <span data-ttu-id="bc932-112">Bu, ikinci koleksiyonda eşleşmesi olmayan ilk koleksiyondaki öğelere erişemeyen grup dışı bir birleştirmedeki sonuç seçiciden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="bc932-112">This differs from the result selector in a non-group join, which cannot access elements from the first collection that have no match in the second collection.</span></span>

<span data-ttu-id="bc932-113">Bu makaledeki ilk örnek, bir grup birleştirme gerçekleştirmek için nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="bc932-113">The first example in this article shows you how to perform a group join.</span></span> <span data-ttu-id="bc932-114">İkinci örnek, XML öğeleri oluşturmak için bir grup birliğini nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="bc932-114">The second example shows you how to use a group join to create XML elements.</span></span>

## <a name="example---group-join"></a><span data-ttu-id="bc932-115">Örnek - Grup birleştirme</span><span class="sxs-lookup"><span data-stu-id="bc932-115">Example - Group join</span></span>

<span data-ttu-id="bc932-116">Aşağıdaki örnek, `Person` tür nesnelerin birgrup birleştirme `Pet` gerçekleştirir `Person` ve `Pet.Owner` özelliği eşleşen dayalı.</span><span class="sxs-lookup"><span data-stu-id="bc932-116">The following example performs a group join of objects of type `Person` and `Pet` based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="bc932-117">Her eşleşme için bir çift öğe üretecek olan grup dışı birbirleştirmenin aksine, grup birleştirme, bu örnekte bir nesne `Person` olan ilk koleksiyonun her öğesi için yalnızca bir sonuç nesnesi üretir.</span><span class="sxs-lookup"><span data-stu-id="bc932-117">Unlike a non-group join, which would produce a pair of elements for each match, the group join produces only one resulting object for each element of the first collection, which in this example is a `Person` object.</span></span> <span data-ttu-id="bc932-118">Bu örnekte `Pet` nesneler olan ikinci koleksiyondaki karşılık gelen öğeler bir koleksiyonda gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="bc932-118">The corresponding elements from the second collection, which in this example are `Pet` objects, are grouped into a collection.</span></span> <span data-ttu-id="bc932-119">Son olarak, sonuç seçici işlevi, nesnelerin oluşan `Person.FirstName` ve oluşan her `Pet` maç için anonim bir tür oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bc932-119">Finally, the result selector function creates an anonymous type for each match that consists of `Person.FirstName` and a collection of `Pet` objects.</span></span>

[!code-csharp[CsLINQProgJoining#5](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]

## <a name="example---group-join-to-create-xml"></a><span data-ttu-id="bc932-120">Örnek - XML oluşturmak için grup birleştirme</span><span class="sxs-lookup"><span data-stu-id="bc932-120">Example - Group join to create XML</span></span>

<span data-ttu-id="bc932-121">Grup birleştirmeleri, LINQ'dan XML'e kadar kullanarak XML oluşturmak için idealdir.</span><span class="sxs-lookup"><span data-stu-id="bc932-121">Group joins are ideal for creating XML by using LINQ to XML.</span></span> <span data-ttu-id="bc932-122">Aşağıdaki örnek, anonim türler oluşturmak yerine, sonuç seçici işlevinin birleştirilmiş nesneleri temsil eden XML öğeleri oluşturması dışında önceki örneğe benzer.</span><span class="sxs-lookup"><span data-stu-id="bc932-122">The following example is similar to the previous example except that instead of creating anonymous types, the result selector function creates XML elements that represent the joined objects.</span></span>

[!code-csharp[CsLINQProgJoining#6](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]

## <a name="see-also"></a><span data-ttu-id="bc932-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc932-123">See also</span></span>

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [<span data-ttu-id="bc932-124">İç birleşimler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="bc932-124">Perform inner joins</span></span>](perform-inner-joins.md)
- [<span data-ttu-id="bc932-125">Sol dış birleşimler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="bc932-125">Perform left outer joins</span></span>](perform-left-outer-joins.md)
- [<span data-ttu-id="bc932-126">Anonim türleri</span><span class="sxs-lookup"><span data-stu-id="bc932-126">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)
