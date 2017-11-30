---
title: .NET Framework'teki Genel Koleksiyonlar
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET Framework], collections
- generic collections [.NET Framework]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 94da20072f793e137b0b7545c1a658ed20537a7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-collections-in-the-net-framework"></a><span data-ttu-id="c440a-102">.NET Framework'teki Genel Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="c440a-102">Generic Collections in the .NET Framework</span></span>
<span data-ttu-id="c440a-103">Bu konu genel koleksiyon sınıfları ve diğer genel türleri .NET Framework'teki genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="c440a-103">This topic provides an overview of the generic collection classes and other generic types in the .NET Framework.</span></span>  
  
## <a name="generic-collections-in-the-net-framework"></a><span data-ttu-id="c440a-104">.NET Framework'teki Genel Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="c440a-104">Generic Collections in the .NET Framework</span></span>  
 <span data-ttu-id="c440a-105">.NET Framework sınıf kitaplığı bir genel koleksiyon sınıfları sağlar <xref:System.Collections.Generic> ve <xref:System.Collections.ObjectModel> ad alanları.</span><span class="sxs-lookup"><span data-stu-id="c440a-105">The .NET Framework class library provides a number of generic collection classes in the <xref:System.Collections.Generic> and <xref:System.Collections.ObjectModel> namespaces.</span></span> <span data-ttu-id="c440a-106">Bu sınıfları hakkında daha fazla bilgi için bkz: [yaygın olarak kullanılan koleksiyon türleri](../../../docs/standard/collections/commonly-used-collection-types.md).</span><span class="sxs-lookup"><span data-stu-id="c440a-106">For more information about these classes, see [Commonly Used Collection Types](../../../docs/standard/collections/commonly-used-collection-types.md).</span></span>  
  
### <a name="systemcollectionsgeneric"></a><span data-ttu-id="c440a-107">System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="c440a-107">System.Collections.Generic</span></span>  
 <span data-ttu-id="c440a-108">Çoğu genel koleksiyon türleri benzerlikler türlere bulunur.</span><span class="sxs-lookup"><span data-stu-id="c440a-108">Many of the generic collection types are direct analogs of nongeneric types.</span></span> <span data-ttu-id="c440a-109"><xref:System.Collections.Generic.Dictionary%602>Genel bir sürümü <xref:System.Collections.Hashtable>; genel yapısı kullanır <xref:System.Collections.Generic.KeyValuePair%602> yerine numaralandırması için <xref:System.Collections.DictionaryEntry>.</span><span class="sxs-lookup"><span data-stu-id="c440a-109"><xref:System.Collections.Generic.Dictionary%602> is a generic version of <xref:System.Collections.Hashtable>; it uses the generic structure <xref:System.Collections.Generic.KeyValuePair%602> for enumeration instead of <xref:System.Collections.DictionaryEntry>.</span></span>  
  
 <span data-ttu-id="c440a-110"><xref:System.Collections.Generic.List%601>Genel bir sürümü <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="c440a-110"><xref:System.Collections.Generic.List%601> is a generic version of <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="c440a-111">Vardır genel <xref:System.Collections.Generic.Queue%601> ve <xref:System.Collections.Generic.Stack%601> nongeneric sürümüne karşılık gelen sınıfları.</span><span class="sxs-lookup"><span data-stu-id="c440a-111">There are generic <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601> classes that correspond to the nongeneric versions.</span></span>  
  
 <span data-ttu-id="c440a-112">Genel ve nongeneric sürümü vardır <xref:System.Collections.Generic.SortedList%602>.</span><span class="sxs-lookup"><span data-stu-id="c440a-112">There are generic and nongeneric versions of <xref:System.Collections.Generic.SortedList%602>.</span></span> <span data-ttu-id="c440a-113">Her iki sürümleridir sınıflarınızın bir karmasını bir sözlük ve bir listesi.</span><span class="sxs-lookup"><span data-stu-id="c440a-113">Both versions are hybrids of a dictionary and a list.</span></span> <span data-ttu-id="c440a-114"><xref:System.Collections.Generic.SortedDictionary%602> Genel sınıfı saf bir sözlük ve hiçbir nongeneric karşılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="c440a-114">The <xref:System.Collections.Generic.SortedDictionary%602> generic class is a pure dictionary and has no nongeneric counterpart.</span></span>  
  
 <span data-ttu-id="c440a-115"><xref:System.Collections.Generic.LinkedList%601> Genel sınıftır true bağlantılı liste.</span><span class="sxs-lookup"><span data-stu-id="c440a-115">The <xref:System.Collections.Generic.LinkedList%601> generic class is a true linked list.</span></span> <span data-ttu-id="c440a-116">Hiçbir nongeneric karşılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="c440a-116">It has no nongeneric counterpart.</span></span>  
  
### <a name="systemcollectionsobjectmodel"></a><span data-ttu-id="c440a-117">System.Collections.ObjectModel</span><span class="sxs-lookup"><span data-stu-id="c440a-117">System.Collections.ObjectModel</span></span>  
 <span data-ttu-id="c440a-118"><xref:System.Collections.ObjectModel.Collection%601> Genel bir sınıf kendi genel koleksiyon türleri türetme için temel sınıf sağlar.</span><span class="sxs-lookup"><span data-stu-id="c440a-118">The <xref:System.Collections.ObjectModel.Collection%601> generic class provides a base class for deriving your own generic collection types.</span></span> <span data-ttu-id="c440a-119"><xref:System.Collections.ObjectModel.ReadOnlyCollection%601> Sınıfı uygulayan herhangi bir türü salt okunur bir koleksiyondan üretmek için kolay bir yol sağlar <xref:System.Collections.Generic.IList%601> genel arabirim.</span><span class="sxs-lookup"><span data-stu-id="c440a-119">The <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class provides an easy way to produce a read-only collection from any type that implements the <xref:System.Collections.Generic.IList%601> generic interface.</span></span> <span data-ttu-id="c440a-120"><xref:System.Collections.ObjectModel.KeyedCollection%602> Genel bir sınıf kendi anahtarlarını içeren nesneleri depolamak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="c440a-120">The <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class provides a way to store objects that contain their own keys.</span></span>  
  
## <a name="other-generic-types"></a><span data-ttu-id="c440a-121">Diğer genel türler</span><span class="sxs-lookup"><span data-stu-id="c440a-121">Other Generic Types</span></span>  
 <span data-ttu-id="c440a-122"><xref:System.Nullable%601> Genel yapısı sanki bunlar atanabilir değer türlerinin kullanmanıza olanak verir `null`.</span><span class="sxs-lookup"><span data-stu-id="c440a-122">The <xref:System.Nullable%601> generic structure allows you to use value types as if they could be assigned `null`.</span></span> <span data-ttu-id="c440a-123">Burada, değer türleri içeren alanlar eksik olabilir veritabanı sorguları ile çalışırken, bu yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c440a-123">This can be useful when working with database queries, where fields that contain value types can be missing.</span></span> <span data-ttu-id="c440a-124">Genel tür parametresi herhangi bir değer türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="c440a-124">The generic type parameter can be any value type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c440a-125">C# ile kullanmak ise gerekli değildir <xref:System.Nullable%601> açıkça dili sözdizimi boş değer atanabilir türler için sahip olduğu.</span><span class="sxs-lookup"><span data-stu-id="c440a-125">In C# it is not necessary to use <xref:System.Nullable%601> explicitly because the language has syntax for nullable types.</span></span>  
  
 <span data-ttu-id="c440a-126"><xref:System.ArraySegment%601> Genel yapısı içinde herhangi bir türde tek boyutlu, sıfır tabanlı bir dizi öğelerin bir dizi sınırlandırmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="c440a-126">The <xref:System.ArraySegment%601> generic structure provides a way to delimit a range of elements within a one-dimensional, zero-based array of any type.</span></span> <span data-ttu-id="c440a-127">Genel tür parametresi dizi öğeleri türüdür.</span><span class="sxs-lookup"><span data-stu-id="c440a-127">The generic type parameter is the type of the array's elements.</span></span>  
  
 <span data-ttu-id="c440a-128"><xref:System.EventHandler%601> Genel temsilcisi ortadan kaldırır, olay tarafından kullanılan olay işleme düzeni izliyorsa olayları işlemek için bir temsilci bildirmek için gereken [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c440a-128">The <xref:System.EventHandler%601> generic delegate eliminates the need to declare a delegate type to handle events, if your event follows the event-handling pattern used by the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="c440a-129">Örneğin, oluşturduğunuz varsayalım bir `MyEventArgs` türetilmiş sınıf <xref:System.EventArgs>, olay verilerini tutacak.</span><span class="sxs-lookup"><span data-stu-id="c440a-129">For example, suppose you have created a `MyEventArgs` class, derived from <xref:System.EventArgs>, to hold the data for your event.</span></span> <span data-ttu-id="c440a-130">Ardından, olay gibi bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c440a-130">You can then declare the event as follows:</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="c440a-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c440a-131">See Also</span></span>  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [<span data-ttu-id="c440a-132">Genel türler</span><span class="sxs-lookup"><span data-stu-id="c440a-132">Generics</span></span>](../../../docs/standard/generics/index.md)  
 [<span data-ttu-id="c440a-133">Dizi ve listeleri düzenlemek için genel temsilciler</span><span class="sxs-lookup"><span data-stu-id="c440a-133">Generic Delegates for Manipulating Arrays and Lists</span></span>](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
 [<span data-ttu-id="c440a-134">Genel arabirimler</span><span class="sxs-lookup"><span data-stu-id="c440a-134">Generic Interfaces</span></span>](../../../docs/standard/generics/interfaces.md)
