---
title: .NET’te Genel Koleksiyonlar
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
ms.openlocfilehash: b0de14fd5d576774ed1605784f5f0c6b0fae2c8c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948922"
---
# <a name="generic-collections-in-net"></a><span data-ttu-id="f8d65-102">.NET’te Genel Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="f8d65-102">Generic Collections in .NET</span></span>

 <span data-ttu-id="f8d65-103">.NET sınıf kitaplığı, <xref:System.Collections.Generic> ve <xref:System.Collections.ObjectModel> ad alanlarında çok sayıda genel koleksiyon sınıfı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8d65-103">The .NET class library provides a number of generic collection classes in the <xref:System.Collections.Generic> and <xref:System.Collections.ObjectModel> namespaces.</span></span> <span data-ttu-id="f8d65-104">Bu sınıflar hakkında daha ayrıntılı bilgi için bkz. [yaygın olarak kullanılan koleksiyon türleri](../../../docs/standard/collections/commonly-used-collection-types.md).</span><span class="sxs-lookup"><span data-stu-id="f8d65-104">For more detailed information about these classes, see [Commonly Used Collection Types](../../../docs/standard/collections/commonly-used-collection-types.md).</span></span>  
  
### <a name="systemcollectionsgeneric"></a><span data-ttu-id="f8d65-105">System. Collections. Generic</span><span class="sxs-lookup"><span data-stu-id="f8d65-105">System.Collections.Generic</span></span>  
 <span data-ttu-id="f8d65-106">Genel koleksiyon türlerinin birçoğu genel olmayan türlerin doğrudan analoglarından.</span><span class="sxs-lookup"><span data-stu-id="f8d65-106">Many of the generic collection types are direct analogs of nongeneric types.</span></span> <span data-ttu-id="f8d65-107"><xref:System.Collections.Generic.Dictionary%602>, genel bir sürümüdür <xref:System.Collections.Hashtable>; yerine <xref:System.Collections.DictionaryEntry>numaralandırma için genel yapıyı <xref:System.Collections.Generic.KeyValuePair%602> kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8d65-107"><xref:System.Collections.Generic.Dictionary%602> is a generic version of <xref:System.Collections.Hashtable>; it uses the generic structure <xref:System.Collections.Generic.KeyValuePair%602> for enumeration instead of <xref:System.Collections.DictionaryEntry>.</span></span>  
  
 <span data-ttu-id="f8d65-108"><xref:System.Collections.Generic.List%601>, öğesinin <xref:System.Collections.ArrayList>genel bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="f8d65-108"><xref:System.Collections.Generic.List%601> is a generic version of <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="f8d65-109"><xref:System.Collections.Generic.Queue%601> Genel ve <xref:System.Collections.Generic.Stack%601> olmayan sürümlere karşılık gelen sınıflar vardır.</span><span class="sxs-lookup"><span data-stu-id="f8d65-109">There are generic <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601> classes that correspond to the nongeneric versions.</span></span>  
  
 <span data-ttu-id="f8d65-110">Genel ve genel olmayan sürümleri <xref:System.Collections.Generic.SortedList%602>vardır.</span><span class="sxs-lookup"><span data-stu-id="f8d65-110">There are generic and nongeneric versions of <xref:System.Collections.Generic.SortedList%602>.</span></span> <span data-ttu-id="f8d65-111">Her iki sürüm de bir sözlüğün ve listenin hybrilar.</span><span class="sxs-lookup"><span data-stu-id="f8d65-111">Both versions are hybrids of a dictionary and a list.</span></span> <span data-ttu-id="f8d65-112"><xref:System.Collections.Generic.SortedDictionary%602> Genel sınıf saf bir sözlüktür ve genel olmayan bir karşılığı yoktur.</span><span class="sxs-lookup"><span data-stu-id="f8d65-112">The <xref:System.Collections.Generic.SortedDictionary%602> generic class is a pure dictionary and has no nongeneric counterpart.</span></span>  
  
 <span data-ttu-id="f8d65-113"><xref:System.Collections.Generic.LinkedList%601> Genel sınıf, doğru bağlantılı bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="f8d65-113">The <xref:System.Collections.Generic.LinkedList%601> generic class is a true linked list.</span></span> <span data-ttu-id="f8d65-114">Genel olmayan bir karşılığı yoktur.</span><span class="sxs-lookup"><span data-stu-id="f8d65-114">It has no nongeneric counterpart.</span></span>  
  
### <a name="systemcollectionsobjectmodel"></a><span data-ttu-id="f8d65-115">System. Collections. ObjectModel</span><span class="sxs-lookup"><span data-stu-id="f8d65-115">System.Collections.ObjectModel</span></span>  
 <span data-ttu-id="f8d65-116">Genel <xref:System.Collections.ObjectModel.Collection%601> sınıf, kendi genel koleksiyon türlerinizi türetmede bir temel sınıf sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8d65-116">The <xref:System.Collections.ObjectModel.Collection%601> generic class provides a base class for deriving your own generic collection types.</span></span> <span data-ttu-id="f8d65-117">Sınıfı <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> , <xref:System.Collections.Generic.IList%601> genel arabirimi uygulayan herhangi bir türden salt okunurdur bir koleksiyon oluşturmak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8d65-117">The <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class provides an easy way to produce a read-only collection from any type that implements the <xref:System.Collections.Generic.IList%601> generic interface.</span></span> <span data-ttu-id="f8d65-118">Genel <xref:System.Collections.ObjectModel.KeyedCollection%602> sınıfı, kendi anahtarlarını içeren nesneleri depolamanın bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8d65-118">The <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class provides a way to store objects that contain their own keys.</span></span>  
  
## <a name="other-generic-types"></a><span data-ttu-id="f8d65-119">Diğer genel türler</span><span class="sxs-lookup"><span data-stu-id="f8d65-119">Other Generic Types</span></span>  
 <span data-ttu-id="f8d65-120">Genel yapı değer türlerini atandıklarından `null`farklı şekilde kullanmanıza olanak sağlar. <xref:System.Nullable%601></span><span class="sxs-lookup"><span data-stu-id="f8d65-120">The <xref:System.Nullable%601> generic structure allows you to use value types as if they could be assigned `null`.</span></span> <span data-ttu-id="f8d65-121">Bu, değer türlerini içeren alanların eksik olduğu veritabanı sorgularıyla çalışırken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f8d65-121">This can be useful when working with database queries, where fields that contain value types can be missing.</span></span> <span data-ttu-id="f8d65-122">Genel tür parametresi herhangi bir değer türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="f8d65-122">The generic type parameter can be any value type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8d65-123">C# Ve Visual Basic, dilin Nullable türler için sözdizimi olduğundan açıkça <xref:System.Nullable%601> kullanılması gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="f8d65-123">In C# and Visual Basic, it is not necessary to use <xref:System.Nullable%601> explicitly because the language has syntax for nullable types.</span></span> <span data-ttu-id="f8d65-124">Bkz. [Nullable türlerC# (Programlama Kılavuzu)](../../csharp/programming-guide/nullable-types/index.md) ve [Nullable değer türleri (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="f8d65-124">See [Nullable types (C# Programming Guide)](../../csharp/programming-guide/nullable-types/index.md) and [Nullable value types (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span></span> 
  
 <span data-ttu-id="f8d65-125"><xref:System.ArraySegment%601> Genel yapı, herhangi bir türdeki tek boyutlu, sıfır tabanlı dizi içindeki bir öğe aralığını sınırlandırmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8d65-125">The <xref:System.ArraySegment%601> generic structure provides a way to delimit a range of elements within a one-dimensional, zero-based array of any type.</span></span> <span data-ttu-id="f8d65-126">Genel tür parametresi, dizinin öğelerinin türüdür.</span><span class="sxs-lookup"><span data-stu-id="f8d65-126">The generic type parameter is the type of the array's elements.</span></span>  
  
 <span data-ttu-id="f8d65-127"><xref:System.EventHandler%601> Genel temsilci, olaylarınız .NET Framework tarafından kullanılan olay işleme modelini takip eden olayları işlemek için bir temsilci türü bildirme gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f8d65-127">The <xref:System.EventHandler%601> generic delegate eliminates the need to declare a delegate type to handle events, if your event follows the event-handling pattern used by the .NET Framework.</span></span> <span data-ttu-id="f8d65-128">Örneğin, olayınıza ilişkin verileri tutmak için `MyEventArgs` , öğesinden <xref:System.EventArgs>türetilmiş bir sınıf oluşturduğunuzu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="f8d65-128">For example, suppose you have created a `MyEventArgs` class, derived from <xref:System.EventArgs>, to hold the data for your event.</span></span> <span data-ttu-id="f8d65-129">Olayı daha sonra aşağıdaki gibi bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f8d65-129">You can then declare the event as follows:</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="f8d65-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8d65-130">See also</span></span>

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [<span data-ttu-id="f8d65-131">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="f8d65-131">Generics</span></span>](../../../docs/standard/generics/index.md)
- [<span data-ttu-id="f8d65-132">Dizi ve Listeleri Düzenlemek için Genel Temsilciler</span><span class="sxs-lookup"><span data-stu-id="f8d65-132">Generic Delegates for Manipulating Arrays and Lists</span></span>](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [<span data-ttu-id="f8d65-133">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="f8d65-133">Generic Interfaces</span></span>](../../../docs/standard/generics/interfaces.md)
