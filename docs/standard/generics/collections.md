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
ms.openlocfilehash: dce0e38b0198396ec0dbc3ced7f2f59c2b112b56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708416"
---
# <a name="generic-collections-in-net"></a><span data-ttu-id="b27e3-102">.NET'teki genel koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="b27e3-102">Generic collections in .NET</span></span>

 <span data-ttu-id="b27e3-103">.NET sınıf kitaplığı, ad alanlarında bir <xref:System.Collections.Generic> <xref:System.Collections.ObjectModel> dizi genel koleksiyon sınıfı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b27e3-103">The .NET class library provides a number of generic collection classes in the <xref:System.Collections.Generic> and <xref:System.Collections.ObjectModel> namespaces.</span></span> <span data-ttu-id="b27e3-104">Bu sınıflar hakkında daha ayrıntılı bilgi için, [Yaygın Kullanılan Koleksiyon Türleri'ne](../../../docs/standard/collections/commonly-used-collection-types.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="b27e3-104">For more detailed information about these classes, see [Commonly Used Collection Types](../../../docs/standard/collections/commonly-used-collection-types.md).</span></span>  
  
## <a name="systemcollectionsgeneric"></a><span data-ttu-id="b27e3-105">System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="b27e3-105">System.Collections.Generic</span></span>

 <span data-ttu-id="b27e3-106">Genel koleksiyon türlerinin çoğu, genel olmayan türlerin doğrudan analoglarıdır.</span><span class="sxs-lookup"><span data-stu-id="b27e3-106">Many of the generic collection types are direct analogs of nongeneric types.</span></span> <span data-ttu-id="b27e3-107"><xref:System.Collections.Generic.Dictionary%602>genel bir <xref:System.Collections.Hashtable>versiyonudur; yerine numaralandırma <xref:System.Collections.Generic.KeyValuePair%602> için genel yapıyı <xref:System.Collections.DictionaryEntry>kullanır.</span><span class="sxs-lookup"><span data-stu-id="b27e3-107"><xref:System.Collections.Generic.Dictionary%602> is a generic version of <xref:System.Collections.Hashtable>; it uses the generic structure <xref:System.Collections.Generic.KeyValuePair%602> for enumeration instead of <xref:System.Collections.DictionaryEntry>.</span></span>  
  
 <span data-ttu-id="b27e3-108"><xref:System.Collections.Generic.List%601>'nin <xref:System.Collections.ArrayList>genel bir versiyonudur.</span><span class="sxs-lookup"><span data-stu-id="b27e3-108"><xref:System.Collections.Generic.List%601> is a generic version of <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="b27e3-109">Genel olmayan <xref:System.Collections.Generic.Queue%601> <xref:System.Collections.Generic.Stack%601> sürümlere karşılık gelen genel ve sınıflar vardır.</span><span class="sxs-lookup"><span data-stu-id="b27e3-109">There are generic <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601> classes that correspond to the nongeneric versions.</span></span>  
  
 <span data-ttu-id="b27e3-110">Genel ve genel olmayan <xref:System.Collections.Generic.SortedList%602>sürümleri vardır.</span><span class="sxs-lookup"><span data-stu-id="b27e3-110">There are generic and nongeneric versions of <xref:System.Collections.Generic.SortedList%602>.</span></span> <span data-ttu-id="b27e3-111">Her iki sürüm de sözlük ve bir listenin melezleridir.</span><span class="sxs-lookup"><span data-stu-id="b27e3-111">Both versions are hybrids of a dictionary and a list.</span></span> <span data-ttu-id="b27e3-112">Genel <xref:System.Collections.Generic.SortedDictionary%602> sınıf saf bir sözlüktür ve genel olmayan bir benzerliği yoktur.</span><span class="sxs-lookup"><span data-stu-id="b27e3-112">The <xref:System.Collections.Generic.SortedDictionary%602> generic class is a pure dictionary and has no nongeneric counterpart.</span></span>  
  
 <span data-ttu-id="b27e3-113">Genel <xref:System.Collections.Generic.LinkedList%601> sınıf gerçek bir bağlı listedir.</span><span class="sxs-lookup"><span data-stu-id="b27e3-113">The <xref:System.Collections.Generic.LinkedList%601> generic class is a true linked list.</span></span> <span data-ttu-id="b27e3-114">Genel olmayan bir benzerliği yoktur.</span><span class="sxs-lookup"><span data-stu-id="b27e3-114">It has no nongeneric counterpart.</span></span>  
  
## <a name="systemcollectionsobjectmodel"></a><span data-ttu-id="b27e3-115">System.Collections.ObjectModel</span><span class="sxs-lookup"><span data-stu-id="b27e3-115">System.Collections.ObjectModel</span></span>

 <span data-ttu-id="b27e3-116">Genel <xref:System.Collections.ObjectModel.Collection%601> sınıf, kendi genel koleksiyon türlerinizi türemeniz için bir taban sınıf sağlar.</span><span class="sxs-lookup"><span data-stu-id="b27e3-116">The <xref:System.Collections.ObjectModel.Collection%601> generic class provides a base class for deriving your own generic collection types.</span></span> <span data-ttu-id="b27e3-117">Sınıf, <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> <xref:System.Collections.Generic.IList%601> genel arabirimi uygulayan herhangi bir türden salt okunur bir koleksiyon oluşturmak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="b27e3-117">The <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class provides an easy way to produce a read-only collection from any type that implements the <xref:System.Collections.Generic.IList%601> generic interface.</span></span> <span data-ttu-id="b27e3-118">Genel <xref:System.Collections.ObjectModel.KeyedCollection%602> sınıf, kendi anahtarlarını içeren nesneleri depolamak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="b27e3-118">The <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class provides a way to store objects that contain their own keys.</span></span>  
  
## <a name="other-generic-types"></a><span data-ttu-id="b27e3-119">Diğer genel türler</span><span class="sxs-lookup"><span data-stu-id="b27e3-119">Other generic types</span></span>

 <span data-ttu-id="b27e3-120">Genel <xref:System.Nullable%601> yapı, değer türlerini atanmış `null`gibi kullanmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b27e3-120">The <xref:System.Nullable%601> generic structure allows you to use value types as if they could be assigned `null`.</span></span> <span data-ttu-id="b27e3-121">Bu, değer türleri içeren alanların eksik olabileceği veritabanı sorgularıyla çalışırken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b27e3-121">This can be useful when working with database queries, where fields that contain value types can be missing.</span></span> <span data-ttu-id="b27e3-122">Genel tür parametresi herhangi bir değer türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="b27e3-122">The generic type parameter can be any value type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b27e3-123">C# ve Visual Basic'te, dilin nullable türleri için sözdizimi olduğundan açıkça kullanılması <xref:System.Nullable%601> gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b27e3-123">In C# and Visual Basic, it is not necessary to use <xref:System.Nullable%601> explicitly because the language has syntax for nullable types.</span></span> <span data-ttu-id="b27e3-124">Bkz. [Nullable değer türleri (C# başvurusu)](../../csharp/language-reference/builtin-types/nullable-value-types.md) ve [Nullable değer türleri (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="b27e3-124">See [Nullable value types (C# reference)](../../csharp/language-reference/builtin-types/nullable-value-types.md) and [Nullable value types (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span></span>
  
 <span data-ttu-id="b27e3-125">Genel <xref:System.ArraySegment%601> yapı, herhangi bir türdeki tek boyutlu, sıfır tabanlı diziiçindeki bir öğe aralığını sınırlamanın bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="b27e3-125">The <xref:System.ArraySegment%601> generic structure provides a way to delimit a range of elements within a one-dimensional, zero-based array of any type.</span></span> <span data-ttu-id="b27e3-126">Genel tür parametresi, dizinin öğelerinin türüdür.</span><span class="sxs-lookup"><span data-stu-id="b27e3-126">The generic type parameter is the type of the array's elements.</span></span>  
  
 <span data-ttu-id="b27e3-127">Genel <xref:System.EventHandler%601> temsilci, etkinliğiniz .NET Framework tarafından kullanılan olay işleme deseni izliyorsa, olayları işlemek için bir temsilci türü bildirme gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b27e3-127">The <xref:System.EventHandler%601> generic delegate eliminates the need to declare a delegate type to handle events, if your event follows the event-handling pattern used by the .NET Framework.</span></span> <span data-ttu-id="b27e3-128">Örneğin, etkinliğiniz için `MyEventArgs` verileri tutmak <xref:System.EventArgs>için türetilen bir sınıf oluşturduğunuzu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="b27e3-128">For example, suppose you have created a `MyEventArgs` class, derived from <xref:System.EventArgs>, to hold the data for your event.</span></span> <span data-ttu-id="b27e3-129">Daha sonra olayı aşağıdaki gibi bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b27e3-129">You can then declare the event as follows:</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="b27e3-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b27e3-130">See also</span></span>

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [<span data-ttu-id="b27e3-131">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="b27e3-131">Generics</span></span>](../../../docs/standard/generics/index.md)
- [<span data-ttu-id="b27e3-132">Dizi ve Listeleri Düzenlemek için Genel Temsilciler</span><span class="sxs-lookup"><span data-stu-id="b27e3-132">Generic Delegates for Manipulating Arrays and Lists</span></span>](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [<span data-ttu-id="b27e3-133">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="b27e3-133">Generic Interfaces</span></span>](../../../docs/standard/generics/interfaces.md)
