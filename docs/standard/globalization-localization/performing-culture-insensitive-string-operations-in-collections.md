---
title: "Koleksiyonlarda Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme"
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
helpviewer_keywords:
- CaseInsensitiveComparer class, using
- CollectionsUtil.CreateCaseInsensitiveHashtable method
- culture-insensitive string operations, collections
- collections [.NET Framework], culture-insensitive string operations
- CaseInsensitiveHashCodeProvider class, using
- ArrayList.Sort method
- SortedList class, culture-insensitive string operations
- culture parameter
ms.assetid: 5cdc9396-a64b-4615-a1cd-b605db4c5983
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a1ecba9c055f8e99d26283c7f37c2430dc17bf31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a><span data-ttu-id="5f825-102">Koleksiyonlarda Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="5f825-102">Performing Culture-Insensitive String Operations in Collections</span></span>
<span data-ttu-id="5f825-103">Sınıflar ve üyeleri <xref:System.Collections> varsayılan kültüre duyarlı davranışı sağlamak ad alanı.</span><span class="sxs-lookup"><span data-stu-id="5f825-103">There are classes and members in the <xref:System.Collections> namespace that provide culture-sensitive behavior by default.</span></span> <span data-ttu-id="5f825-104">Varsayılan Oluşturucu için <xref:System.Collections.CaseInsensitiveComparer> ve <xref:System.Collections.CaseInsensitiveHashCodeProvider> sınıfları başlatma kullanarak yeni bir örneğini <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5f825-104">The default constructors for the <xref:System.Collections.CaseInsensitiveComparer> and <xref:System.Collections.CaseInsensitiveHashCodeProvider> classes initialize a new instance using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="5f825-105">Tüm aşırı <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> yöntemi yeni bir örneğini oluşturmak <xref:System.Collections.Hashtable> kullanarak sınıfı `Thread.CurrentCulture` özelliği varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="5f825-105">All overloads of the <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> method create a new instance of the <xref:System.Collections.Hashtable> class using the `Thread.CurrentCulture` property by default.</span></span> <span data-ttu-id="5f825-106">Overloads <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> yöntemi kullanarak varsayılan kültüre duyarlı sıralar gerçekleştirmek `Thread.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="5f825-106">Overloads of the <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> method perform culture-sensitive sorts by default using `Thread.CurrentCulture`.</span></span> <span data-ttu-id="5f825-107">Sıralama ve arama bir <xref:System.Collections.SortedList> tarafından etkilenen `Thread.CurrentCulture` dizeleri anahtar olarak kullanılan zaman.</span><span class="sxs-lookup"><span data-stu-id="5f825-107">Sorting and lookup in a <xref:System.Collections.SortedList> can be affected by `Thread.CurrentCulture` when strings are used as the keys.</span></span> <span data-ttu-id="5f825-108">Bu sınıflar ve yöntemler de kültüre duyarsız sonuçları almak için bu bölümde sağlanan kullanım önerilere uyun `Collections` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="5f825-108">Follow the usage recommendations provided in this section to obtain culture-insensitive results from these classes and methods in the `Collections` namespace.</span></span>  
  
 <span data-ttu-id="5f825-109">**Not** geçirme <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> karşılaştırma yöntemi kültüre duyarsız bir karşılaştırma işlemini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="5f825-109">**Note** Passing <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="5f825-110">Ancak, bu dile ait olmayan bir karşılaştırma, örneğin, dosya yolları, kayıt defteri anahtarları ve ortam değişkenleri için neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="5f825-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="5f825-111">Güvenlik kararları karşılaştırma sonucuna desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="5f825-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="5f825-112">Dil olmayan karşılaştırma veya sonuç tabanlı güvenlik kararları desteği için uygulama kabul eden bir karşılaştırma yöntemi kullanması gereken bir <xref:System.StringComparison> değeri.</span><span class="sxs-lookup"><span data-stu-id="5f825-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="5f825-113">Uygulama sonra geçirmelisiniz <xref:System.StringComparison>.</span><span class="sxs-lookup"><span data-stu-id="5f825-113">The application should then pass <xref:System.StringComparison>.</span></span>  
  
## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a><span data-ttu-id="5f825-114">Caseınsensitivecomparer ve Caseınsensitivehashcodeprovider sınıfları kullanma</span><span class="sxs-lookup"><span data-stu-id="5f825-114">Using the CaseInsensitiveComparer and CaseInsensitiveHashCodeProvider Classes</span></span>  
 <span data-ttu-id="5f825-115">Varsayılan Oluşturucu için `CaseInsensitiveHashCodeProvider` ve `CaseInsensitiveComparer` sınıfı kullanarak yeni bir örneği başlatmak `Thread.CurrentCulture`, sonuçta elde edilen kültüre duyarlı davranış.</span><span class="sxs-lookup"><span data-stu-id="5f825-115">The default constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer` initialize a new instance of the class using the `Thread.CurrentCulture`, resulting in culture-sensitive behavior.</span></span> <span data-ttu-id="5f825-116">Aşağıdaki kod örneğinde Oluşturucusu gösteren bir `Hashtable` olan kültüre duyarlı için varsayılan oluşturucu kullandığından `CaseInsensitiveHashCodeProvider` ve `CaseInsensitiveComparer`.</span><span class="sxs-lookup"><span data-stu-id="5f825-116">The following code example demonstrates the constructor for a `Hashtable` that is culture-sensitive because it uses the default constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer`.</span></span>  
  
```vb  
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)  
```  
  
```csharp  
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);  
```  
  
 <span data-ttu-id="5f825-117">Bir kültüre duyarsız oluşturmak istiyorsanız `Hashtable` kullanarak `CaseInsensitiveComparer` ve `CaseInsensitiveHashCodeProvider` sınıfları başlatma yeni kabul oluşturucuları kullanarak bu sınıfların örnekleri bir `culture` parametresi.</span><span class="sxs-lookup"><span data-stu-id="5f825-117">If you want to create a culture-insensitive `Hashtable` using the `CaseInsensitiveComparer` and `CaseInsensitiveHashCodeProvider` classes, initialize new instances of these classes using the constructors that accept a `culture` parameter.</span></span> <span data-ttu-id="5f825-118">İçin `culture` parametresini belirtin <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5f825-118">For the `culture` parameter, specify <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5f825-119">Aşağıdaki kod örneğinde bir kültüre duyarsız oluşturucusu gösterilmektedir `Hashtable`.</span><span class="sxs-lookup"><span data-stu-id="5f825-119">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>  
  
```vb  
internalHashtable = New Hashtable(New  
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),  
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))  
```  
  
```csharp  
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider  
    (CultureInfo.InvariantCulture),   
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));  
```  
  
## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a><span data-ttu-id="5f825-120">Collectionsutil.createcaseınsensitivehashtable yöntemi kullanılarak</span><span class="sxs-lookup"><span data-stu-id="5f825-120">Using the CollectionsUtil.CreateCaseInsensitiveHashTable Method</span></span>  
 <span data-ttu-id="5f825-121">`CollectionsUtil.CreateCaseInsensitiveHashTable` Yöntemdir yeni bir örneğini oluşturmak için yararlı bir kısayol `Hashtable` dizeleri küçük büyük harf duyarlı sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5f825-121">The `CollectionsUtil.CreateCaseInsensitiveHashTable` method is a useful shortcut for creating a new instance of the `Hashtable` class that ignores the case of strings.</span></span> <span data-ttu-id="5f825-122">Ancak, tüm overloads `CollectionsUtil.CreateCaseInsensitiveHashTable` yöntemi kültüre duyarlı kullandıkları için `Thread.CurrentCulture` özelliği.</span><span class="sxs-lookup"><span data-stu-id="5f825-122">However, all overloads of the `CollectionsUtil.CreateCaseInsensitiveHashTable` method are culture-sensitive because they use the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="5f825-123">Bir kültüre duyarsız oluşturulamıyor `Hashtable` bu yöntemi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="5f825-123">You cannot create a culture-insensitive `Hashtable` using this method.</span></span> <span data-ttu-id="5f825-124">Bir kültüre duyarsız oluşturmak için `Hashtable`, kullanın `Hashtable` kabul Oluşturucusu bir `culture` parametresi.</span><span class="sxs-lookup"><span data-stu-id="5f825-124">To create a culture-insensitive `Hashtable`, use the `Hashtable` constructor that accepts a `culture` parameter.</span></span> <span data-ttu-id="5f825-125">İçin `culture` parametresini belirtin `CultureInfo.InvariantCulture`.</span><span class="sxs-lookup"><span data-stu-id="5f825-125">For the `culture` parameter, specify `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="5f825-126">Aşağıdaki kod örneğinde bir kültüre duyarsız oluşturucusu gösterilmektedir `Hashtable`.</span><span class="sxs-lookup"><span data-stu-id="5f825-126">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>  
  
```vb  
internalHashtable = New Hashtable(New  
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),  
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))  
```  
  
```csharp  
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider  
    (CultureInfo.InvariantCulture),   
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));  
```  
  
<a name="cpconperformingculture-insensitivestringoperationsincollectionsanchor1"></a>   
## <a name="using-the-sortedlist-class"></a><span data-ttu-id="5f825-127">SortedList sınıfı kullanma</span><span class="sxs-lookup"><span data-stu-id="5f825-127">Using the SortedList Class</span></span>  
 <span data-ttu-id="5f825-128">A `SortedList` anahtarlara göre sıralanır ve anahtar ve dizini tarafından erişilebilir olan anahtar ve değer çiftlerinin koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5f825-128">A `SortedList` represents a collection of key-and-value pairs that are sorted by the keys and are accessible by key and by index.</span></span> <span data-ttu-id="5f825-129">Kullandığınızda, bir `SortedList` dizeleri anahtarları bulunduğu, sıralama ve arama tarafından etkilenebilir `Thread.CurrentCulture` özelliği.</span><span class="sxs-lookup"><span data-stu-id="5f825-129">When you use a `SortedList` where strings are the keys, the sorting and lookup can be affected by the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="5f825-130">Kültüre duyarsız bir davranış elde etmek için bir `SortedList`, oluşturma bir `SortedList` kabul oluşturucular birini kullanarak bir `comparer` parametresi.</span><span class="sxs-lookup"><span data-stu-id="5f825-130">To obtain culture-insensitive behavior from a `SortedList`, create a `SortedList` using one of the constructors that accepts a `comparer` parameter.</span></span> <span data-ttu-id="5f825-131">`comparer` Parametresi belirtir <xref:System.Collections.IComparer> anahtarları karşılaştırılırken kullanmak için uygulama.</span><span class="sxs-lookup"><span data-stu-id="5f825-131">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing keys.</span></span> <span data-ttu-id="5f825-132">Kullanan bir özel karşılaştırıcı sınıfı parametresi için belirlediğiniz `CultureInfo.InvariantCulture` anahtarları karşılaştırmak için.</span><span class="sxs-lookup"><span data-stu-id="5f825-132">For the parameter, specify a custom comparer class that uses `CultureInfo.InvariantCulture` to compare keys.</span></span> <span data-ttu-id="5f825-133">Aşağıdaki örnek olarak belirleyebilirsiniz özel kültüre duyarsız karşılaştırıcı sınıfı gösterilmektedir `comparer` parametresi için bir `SortedList` Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="5f825-133">The following example illustrates a custom culture-insensitive comparer class that you can specify as the `comparer` parameter to a `SortedList` constructor.</span></span>  
  
```vb  
Imports System  
Imports System.Collections  
Imports System.Globalization  
  
Friend Class InvariantComparer  
    Implements IComparer   
    Private m_compareInfo As CompareInfo  
    Friend Shared [Default] As New InvariantComparer()  
  
    Friend Sub New()  
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo  
    End Sub     
  
    Public Function Compare(a As Object, b As Object) As Integer _  
            Implements IComparer.Compare  
        Dim sa As String = CType(a, String)  
        Dim sb As String = CType(b, String)  
        If Not (sa Is Nothing) And Not (sb Is Nothing) Then  
            Return m_compareInfo.Compare(sa, sb)  
        Else  
            Return Comparer.Default.Compare(a, b)  
        End If  
    End Function  
End Class  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Globalization;  
  
internal class InvariantComparer : IComparer   
{  
    private CompareInfo m_compareInfo;  
    internal static readonly InvariantComparer Default = new  
        InvariantComparer();  
  
    internal InvariantComparer()   
    {  
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo;  
    }  
  
    public int Compare(Object a, Object b)  
    {  
        String sa = a as String;  
        String sb = b as String;  
        if (sa != null && sb != null)  
            return m_compareInfo.Compare(sa, sb);  
        else  
            return Comparer.Default.Compare(a,b);  
    }  
}  
```  
  
 <span data-ttu-id="5f825-134">Genel olarak kullanırsanız, bir `SortedList` özel sabit bir karşılaştırıcı olan bir değişiklik belirtmeden dizelerde `Thread.CurrentCulture` liste doldurulduktan sonra listesi geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="5f825-134">In general, if you use a `SortedList` on strings without specifying a custom invariant comparer, a change to `Thread.CurrentCulture` after the list has been populated can invalidate the list.</span></span>  
  
## <a name="using-the-arraylistsort-method"></a><span data-ttu-id="5f825-135">ArrayList.Sort yöntemi kullanma</span><span class="sxs-lookup"><span data-stu-id="5f825-135">Using the ArrayList.Sort Method</span></span>  
 <span data-ttu-id="5f825-136">Overloads `ArrayList.Sort` yöntemi kullanarak varsayılan kültüre duyarlı sıralar gerçekleştirmek `Thread.CurrentCulture` özelliği.</span><span class="sxs-lookup"><span data-stu-id="5f825-136">Overloads of the `ArrayList.Sort` method perform culture-sensitive sorts by default using the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="5f825-137">Sonuçları farklı sıralamalar nedeniyle kültür göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="5f825-137">Results can vary by culture due to different sort orders.</span></span> <span data-ttu-id="5f825-138">Kültüre duyarlı davranışı ortadan kaldırmak için bu yöntemin kabul aşırı kullanmak bir `IComparer` uygulaması.</span><span class="sxs-lookup"><span data-stu-id="5f825-138">To eliminate culture-sensitive behavior, use the overloads of this method that accept an `IComparer` implementation.</span></span> <span data-ttu-id="5f825-139">İçin `comparer` parametresini kullanan bir özel değişmez karşılaştırıcı sınıfı belirtin `CultureInfo.InvariantCulture`.</span><span class="sxs-lookup"><span data-stu-id="5f825-139">For the `comparer` parameter, specify a custom invariant comparer class that uses `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="5f825-140">Özel sabit karşılaştırıcı sınıfı örneği sağlanan [SortedList sınıfı kullanarak](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) konu.</span><span class="sxs-lookup"><span data-stu-id="5f825-140">An example of a custom invariant comparer class is provided in the [Using the SortedList Class](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f825-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f825-141">See Also</span></span>  
 <xref:System.Collections.CaseInsensitiveComparer>  
 <xref:System.Collections.CaseInsensitiveHashCodeProvider>  
 <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Collections.SortedList>  
 <xref:System.Collections.Hashtable>  
 <xref:System.Collections.IComparer>  
 [<span data-ttu-id="5f825-142">Kültüre duyarsız dize işlemlerini gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="5f825-142">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)  
 <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
