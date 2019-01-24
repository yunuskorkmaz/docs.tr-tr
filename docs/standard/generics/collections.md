---
title: . NET'te genel koleksiyonlar
ms.date: 02/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET], collections
- generic collections [.NET]
- generic types [.NET]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec3f8fb16245318cab8706a2ed136e51f3dc31db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705803"
---
# <a name="generic-collections-in-net"></a><span data-ttu-id="3910a-102">. NET'te genel koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="3910a-102">Generic Collections in .NET</span></span>

 <span data-ttu-id="3910a-103">.NET sınıf kitaplığı genel koleksiyon sınıflarını sunar <xref:System.Collections.Generic> ve <xref:System.Collections.ObjectModel> ad alanları.</span><span class="sxs-lookup"><span data-stu-id="3910a-103">The .NET class library provides a number of generic collection classes in the <xref:System.Collections.Generic> and <xref:System.Collections.ObjectModel> namespaces.</span></span> <span data-ttu-id="3910a-104">Bu sınıflar hakkında daha ayrıntılı bilgi için bkz: [yaygın olarak kullanılan koleksiyon türleri](../../../docs/standard/collections/commonly-used-collection-types.md).</span><span class="sxs-lookup"><span data-stu-id="3910a-104">For more detailed information about these classes, see [Commonly Used Collection Types](../../../docs/standard/collections/commonly-used-collection-types.md).</span></span>  
  
### <a name="systemcollectionsgeneric"></a><span data-ttu-id="3910a-105">System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="3910a-105">System.Collections.Generic</span></span>  
 <span data-ttu-id="3910a-106">Birçok genel koleksiyon tür benzerlikler türlere var.</span><span class="sxs-lookup"><span data-stu-id="3910a-106">Many of the generic collection types are direct analogs of nongeneric types.</span></span> <span data-ttu-id="3910a-107"><xref:System.Collections.Generic.Dictionary%602> Genel bir sürümü <xref:System.Collections.Hashtable>; genel yapısı kullanır <xref:System.Collections.Generic.KeyValuePair%602> yerine sabit listesi için <xref:System.Collections.DictionaryEntry>.</span><span class="sxs-lookup"><span data-stu-id="3910a-107"><xref:System.Collections.Generic.Dictionary%602> is a generic version of <xref:System.Collections.Hashtable>; it uses the generic structure <xref:System.Collections.Generic.KeyValuePair%602> for enumeration instead of <xref:System.Collections.DictionaryEntry>.</span></span>  
  
 <span data-ttu-id="3910a-108"><xref:System.Collections.Generic.List%601> Genel bir sürümü <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="3910a-108"><xref:System.Collections.Generic.List%601> is a generic version of <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="3910a-109">Vardır genel <xref:System.Collections.Generic.Queue%601> ve <xref:System.Collections.Generic.Stack%601> jenerik olmayan sürümlerle karşılık gelen sınıflar.</span><span class="sxs-lookup"><span data-stu-id="3910a-109">There are generic <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601> classes that correspond to the nongeneric versions.</span></span>  
  
 <span data-ttu-id="3910a-110">Jenerik ve jenerik olmayan sürümleri vardır <xref:System.Collections.Generic.SortedList%602>.</span><span class="sxs-lookup"><span data-stu-id="3910a-110">There are generic and nongeneric versions of <xref:System.Collections.Generic.SortedList%602>.</span></span> <span data-ttu-id="3910a-111">Her iki sınıflarınızın bir sözlük ve bir listesinin bir karmasını sürümleridir.</span><span class="sxs-lookup"><span data-stu-id="3910a-111">Both versions are hybrids of a dictionary and a list.</span></span> <span data-ttu-id="3910a-112"><xref:System.Collections.Generic.SortedDictionary%602> Genel sınıf saf bir sözlük ve jenerik olmayan hiçbir karşılığı yoktur.</span><span class="sxs-lookup"><span data-stu-id="3910a-112">The <xref:System.Collections.Generic.SortedDictionary%602> generic class is a pure dictionary and has no nongeneric counterpart.</span></span>  
  
 <span data-ttu-id="3910a-113"><xref:System.Collections.Generic.LinkedList%601> Genel sınıftır true olarak bağlı bir liste.</span><span class="sxs-lookup"><span data-stu-id="3910a-113">The <xref:System.Collections.Generic.LinkedList%601> generic class is a true linked list.</span></span> <span data-ttu-id="3910a-114">Bu, hiçbir jenerik olmayan karşılığı yoktur.</span><span class="sxs-lookup"><span data-stu-id="3910a-114">It has no nongeneric counterpart.</span></span>  
  
### <a name="systemcollectionsobjectmodel"></a><span data-ttu-id="3910a-115">System.Collections.ObjectModel</span><span class="sxs-lookup"><span data-stu-id="3910a-115">System.Collections.ObjectModel</span></span>  
 <span data-ttu-id="3910a-116"><xref:System.Collections.ObjectModel.Collection%601> Kendi genel koleksiyon türlerini türetmek için genel sınıf bir temel sınıf sağlar.</span><span class="sxs-lookup"><span data-stu-id="3910a-116">The <xref:System.Collections.ObjectModel.Collection%601> generic class provides a base class for deriving your own generic collection types.</span></span> <span data-ttu-id="3910a-117"><xref:System.Collections.ObjectModel.ReadOnlyCollection%601> Sınıf uygulayan her tür salt okunur bir koleksiyon oluşturmak için kolay bir yol sağlar <xref:System.Collections.Generic.IList%601> genel arabirim.</span><span class="sxs-lookup"><span data-stu-id="3910a-117">The <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class provides an easy way to produce a read-only collection from any type that implements the <xref:System.Collections.Generic.IList%601> generic interface.</span></span> <span data-ttu-id="3910a-118"><xref:System.Collections.ObjectModel.KeyedCollection%602> Genel sınıf içeren, kendi anahtarlarına nesneleri depolamak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="3910a-118">The <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class provides a way to store objects that contain their own keys.</span></span>  
  
## <a name="other-generic-types"></a><span data-ttu-id="3910a-119">Diğer genel türler</span><span class="sxs-lookup"><span data-stu-id="3910a-119">Other Generic Types</span></span>  
 <span data-ttu-id="3910a-120"><xref:System.Nullable%601> Genel yapısı alacağı bunlar atanabilir değer türlerinin kullanmanıza olanak verir `null`.</span><span class="sxs-lookup"><span data-stu-id="3910a-120">The <xref:System.Nullable%601> generic structure allows you to use value types as if they could be assigned `null`.</span></span> <span data-ttu-id="3910a-121">Bu veritabanı sorgusu, burada, değer türleri içeren alanlar eksik olabilir çalışırken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3910a-121">This can be useful when working with database queries, where fields that contain value types can be missing.</span></span> <span data-ttu-id="3910a-122">Genel tür parametresi, herhangi bir değer türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="3910a-122">The generic type parameter can be any value type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3910a-123">C# ve Visual Basic kullanmak gerekli değildir <xref:System.Nullable%601> açıkça dili sözdizimi için boş değer atanabilir türleri olduğundan.</span><span class="sxs-lookup"><span data-stu-id="3910a-123">In C# and Visual Basic, it is not necessary to use <xref:System.Nullable%601> explicitly because the language has syntax for nullable types.</span></span> <span data-ttu-id="3910a-124">Bkz: [boş değer atanabilir türler (C# programlama Kılavuzu)](../../csharp/programming-guide/nullable-types/index.md) ve [boş değer atanabilen değer türleri (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="3910a-124">See [Nullable types (C# Programming Guide)](../../csharp/programming-guide/nullable-types/index.md) and [Nullable value types (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span></span> 
  
 <span data-ttu-id="3910a-125"><xref:System.ArraySegment%601> Genel yapısı, herhangi bir türde tek boyutlu, sıfır tabanlı bir dizi içinde öğe aralığını sınırlandırmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="3910a-125">The <xref:System.ArraySegment%601> generic structure provides a way to delimit a range of elements within a one-dimensional, zero-based array of any type.</span></span> <span data-ttu-id="3910a-126">Genel tür parametresi, dizi öğelerinin türüdür.</span><span class="sxs-lookup"><span data-stu-id="3910a-126">The generic type parameter is the type of the array's elements.</span></span>  
  
 <span data-ttu-id="3910a-127"><xref:System.EventHandler%601> Genel temsilci ortadan kaldırır, olay tarafından kullanılan olay işleme desen izliyorsa, olayları işlemek için bir temsilci türü bildirmek için gereken [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3910a-127">The <xref:System.EventHandler%601> generic delegate eliminates the need to declare a delegate type to handle events, if your event follows the event-handling pattern used by the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="3910a-128">Örneğin, oluşturduğunuz düşünün bir `MyEventArgs` sınıfından türetilen <xref:System.EventArgs>, olay verilerini tutacak.</span><span class="sxs-lookup"><span data-stu-id="3910a-128">For example, suppose you have created a `MyEventArgs` class, derived from <xref:System.EventArgs>, to hold the data for your event.</span></span> <span data-ttu-id="3910a-129">Ardından, olay şu şekilde bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3910a-129">You can then declare the event as follows:</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="3910a-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3910a-130">See also</span></span>

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [<span data-ttu-id="3910a-131">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="3910a-131">Generics</span></span>](../../../docs/standard/generics/index.md)
- [<span data-ttu-id="3910a-132">Dizi ve Listeleri Düzenlemek için Genel Temsilciler</span><span class="sxs-lookup"><span data-stu-id="3910a-132">Generic Delegates for Manipulating Arrays and Lists</span></span>](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [<span data-ttu-id="3910a-133">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="3910a-133">Generic Interfaces</span></span>](../../../docs/standard/generics/interfaces.md)
