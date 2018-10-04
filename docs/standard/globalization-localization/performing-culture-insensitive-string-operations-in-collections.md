---
title: Koleksiyonlarda Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e458f45fea8e2207ced930daebf10e653901fa7
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582807"
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a><span data-ttu-id="2d657-102">Koleksiyonlarda Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="2d657-102">Performing Culture-Insensitive String Operations in Collections</span></span>
<span data-ttu-id="2d657-103">Sınıfları ve üyeleri <xref:System.Collections> varsayılan olarak kültüre duyarlı davranış sağlayan ad alanı.</span><span class="sxs-lookup"><span data-stu-id="2d657-103">There are classes and members in the <xref:System.Collections> namespace that provide culture-sensitive behavior by default.</span></span> <span data-ttu-id="2d657-104">İçin varsayılan oluşturucular <xref:System.Collections.CaseInsensitiveComparer> ve <xref:System.Collections.CaseInsensitiveHashCodeProvider> sınıfları başlatma kullanarak yeni bir örneğini <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="2d657-104">The default constructors for the <xref:System.Collections.CaseInsensitiveComparer> and <xref:System.Collections.CaseInsensitiveHashCodeProvider> classes initialize a new instance using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="2d657-105">Tüm aşırı yüklemeler, <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> yöntemi yeni bir örneğini oluşturma <xref:System.Collections.Hashtable> kullanarak `Thread.CurrentCulture` özelliği varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="2d657-105">All overloads of the <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> method create a new instance of the <xref:System.Collections.Hashtable> class using the `Thread.CurrentCulture` property by default.</span></span> <span data-ttu-id="2d657-106">Overloads biri <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> yöntemi gerçekleştirmek varsayılan kullanarak kültüre duyarlı sıralamaları `Thread.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="2d657-106">Overloads of the <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> method perform culture-sensitive sorts by default using `Thread.CurrentCulture`.</span></span> <span data-ttu-id="2d657-107">Sıralama ve arama bir <xref:System.Collections.SortedList> etkilenebilir `Thread.CurrentCulture` dizeleri anahtar olarak kullanılan zaman.</span><span class="sxs-lookup"><span data-stu-id="2d657-107">Sorting and lookup in a <xref:System.Collections.SortedList> can be affected by `Thread.CurrentCulture` when strings are used as the keys.</span></span> <span data-ttu-id="2d657-108">Bu sınıfları ve yöntemleri kültüre duyarlı olmayan sonuçlar elde etmek için bu bölümde sağlanan kullanım önerilere uyun `Collections` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="2d657-108">Follow the usage recommendations provided in this section to obtain culture-insensitive results from these classes and methods in the `Collections` namespace.</span></span>  
  
 <span data-ttu-id="2d657-109">**Not** geçirme <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> karşılaştırma yöntemi kültüre duyarsız bir karşılaştırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="2d657-109">**Note** Passing <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="2d657-110">Ancak, bir dilsel karşılaştırma örneğin dosya yolları, kayıt defteri anahtarları ve ortam değişkenleri için neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="2d657-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="2d657-111">Karşılaştırma sonucuna dayalı güvenlik kararları diğerinden destekler.</span><span class="sxs-lookup"><span data-stu-id="2d657-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="2d657-112">Uygulama, bir dilsel karşılaştırma veya sonuç dayalı güvenlik kararları desteği için kabul eden bir karşılaştırma yöntemi kullanmalıdır bir <xref:System.StringComparison> değeri.</span><span class="sxs-lookup"><span data-stu-id="2d657-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="2d657-113">Uygulama ardından geçmelidir <xref:System.StringComparison>.</span><span class="sxs-lookup"><span data-stu-id="2d657-113">The application should then pass <xref:System.StringComparison>.</span></span>  
  
## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a><span data-ttu-id="2d657-114">Caseınsensitivecomparer ve Caseınsensitivehashcodeprovider sınıfları kullanma</span><span class="sxs-lookup"><span data-stu-id="2d657-114">Using the CaseInsensitiveComparer and CaseInsensitiveHashCodeProvider Classes</span></span>  
 <span data-ttu-id="2d657-115">İçin varsayılan oluşturucular `CaseInsensitiveHashCodeProvider` ve `CaseInsensitiveComparer` sınıfı kullanarak yeni bir örneği başlatmak `Thread.CurrentCulture`, sonuçta elde edilen kültüre duyarlı davranış.</span><span class="sxs-lookup"><span data-stu-id="2d657-115">The default constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer` initialize a new instance of the class using the `Thread.CurrentCulture`, resulting in culture-sensitive behavior.</span></span> <span data-ttu-id="2d657-116">Aşağıdaki kod örneği için oluşturucu gösteren bir `Hashtable` , kültüre duyarlı için varsayılan oluşturucular kullandığından `CaseInsensitiveHashCodeProvider` ve `CaseInsensitiveComparer`.</span><span class="sxs-lookup"><span data-stu-id="2d657-116">The following code example demonstrates the constructor for a `Hashtable` that is culture-sensitive because it uses the default constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer`.</span></span>  
  
```vb  
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)  
```  
  
```csharp  
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);  
```  
  
 <span data-ttu-id="2d657-117">Bir kültüre duyarsız oluşturmak istiyorsanız `Hashtable` kullanarak `CaseInsensitiveComparer` ve `CaseInsensitiveHashCodeProvider` sınıfları başlatma kabul oluşturucular kullanarak bu sınıfların yeni örnekleri bir `culture` parametresi.</span><span class="sxs-lookup"><span data-stu-id="2d657-117">If you want to create a culture-insensitive `Hashtable` using the `CaseInsensitiveComparer` and `CaseInsensitiveHashCodeProvider` classes, initialize new instances of these classes using the constructors that accept a `culture` parameter.</span></span> <span data-ttu-id="2d657-118">İçin `culture` parametresi belirtin <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2d657-118">For the `culture` parameter, specify <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2d657-119">Aşağıdaki kod örneği bir kültüre duyarsız Oluşturucusu gösterir `Hashtable`.</span><span class="sxs-lookup"><span data-stu-id="2d657-119">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>  
  
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
  
## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a><span data-ttu-id="2d657-120">Collectionsutil.createcaseınsensitivehashtable metodu kullanma</span><span class="sxs-lookup"><span data-stu-id="2d657-120">Using the CollectionsUtil.CreateCaseInsensitiveHashTable Method</span></span>  
 <span data-ttu-id="2d657-121">`CollectionsUtil.CreateCaseInsensitiveHashTable` Yöntemidir, yeni bir örneğini oluşturmak için yararlı bir kısayol `Hashtable` dizelerinin büyük/küçük harfleri sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2d657-121">The `CollectionsUtil.CreateCaseInsensitiveHashTable` method is a useful shortcut for creating a new instance of the `Hashtable` class that ignores the case of strings.</span></span> <span data-ttu-id="2d657-122">Ancak, tüm aşırı yüklemeler `CollectionsUtil.CreateCaseInsensitiveHashTable` yöntemi kültüre duyarlı kullandıkları için `Thread.CurrentCulture` özelliği.</span><span class="sxs-lookup"><span data-stu-id="2d657-122">However, all overloads of the `CollectionsUtil.CreateCaseInsensitiveHashTable` method are culture-sensitive because they use the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="2d657-123">Bir kültüre duyarsız oluşturulamıyor `Hashtable` bu yöntemi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="2d657-123">You cannot create a culture-insensitive `Hashtable` using this method.</span></span> <span data-ttu-id="2d657-124">Bir kültüre duyarsız oluşturmak için `Hashtable`, kullanın `Hashtable` kabul eden Oluşturucu bir `culture` parametresi.</span><span class="sxs-lookup"><span data-stu-id="2d657-124">To create a culture-insensitive `Hashtable`, use the `Hashtable` constructor that accepts a `culture` parameter.</span></span> <span data-ttu-id="2d657-125">İçin `culture` parametresi belirtin `CultureInfo.InvariantCulture`.</span><span class="sxs-lookup"><span data-stu-id="2d657-125">For the `culture` parameter, specify `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="2d657-126">Aşağıdaki kod örneği bir kültüre duyarsız Oluşturucusu gösterir `Hashtable`.</span><span class="sxs-lookup"><span data-stu-id="2d657-126">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>  
  
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
## <a name="using-the-sortedlist-class"></a><span data-ttu-id="2d657-127">SortedList sınıfı kullanma</span><span class="sxs-lookup"><span data-stu-id="2d657-127">Using the SortedList Class</span></span>  
 <span data-ttu-id="2d657-128">A `SortedList` anahtarlara göre sıralanır ve anahtar ve dizin tarafından erişilebilir olan anahtar-değer çifti koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2d657-128">A `SortedList` represents a collection of key-and-value pairs that are sorted by the keys and are accessible by key and by index.</span></span> <span data-ttu-id="2d657-129">Kullandığınızda, bir `SortedList` dizeleri anahtarların bulunduğu, sıralama ve arama etkilenebilir `Thread.CurrentCulture` özelliği.</span><span class="sxs-lookup"><span data-stu-id="2d657-129">When you use a `SortedList` where strings are the keys, the sorting and lookup can be affected by the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="2d657-130">Kültüre duyarsız davranış elde etmek için bir `SortedList`, oluşturun bir `SortedList` kabul oluşturucular birini kullanarak bir `comparer` parametresi.</span><span class="sxs-lookup"><span data-stu-id="2d657-130">To obtain culture-insensitive behavior from a `SortedList`, create a `SortedList` using one of the constructors that accepts a `comparer` parameter.</span></span> <span data-ttu-id="2d657-131">`comparer` Parametresinin belirttiği <xref:System.Collections.IComparer> anahtarları karşılaştırırken kullanılacak uygulama.</span><span class="sxs-lookup"><span data-stu-id="2d657-131">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing keys.</span></span> <span data-ttu-id="2d657-132">Parametresi, kullanan özel bir karşılaştırıcı sınıf belirtin `CultureInfo.InvariantCulture` anahtarları karşılaştırmak için.</span><span class="sxs-lookup"><span data-stu-id="2d657-132">For the parameter, specify a custom comparer class that uses `CultureInfo.InvariantCulture` to compare keys.</span></span> <span data-ttu-id="2d657-133">Aşağıdaki örnek olarak belirleyebileceğiniz bir özel bir karşılaştırıcı kültüre duyarsız sınıfı göstermektedir `comparer` parametresine bir `SortedList` Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="2d657-133">The following example illustrates a custom culture-insensitive comparer class that you can specify as the `comparer` parameter to a `SortedList` constructor.</span></span>  
  
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
  
 <span data-ttu-id="2d657-134">Genel olarak kullanırsanız, bir `SortedList` özel sabit bir karşılaştırıcı olan bir değişiklik belirtmeden dizelerde `Thread.CurrentCulture` listesi doldurulur sonra listenin geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="2d657-134">In general, if you use a `SortedList` on strings without specifying a custom invariant comparer, a change to `Thread.CurrentCulture` after the list has been populated can invalidate the list.</span></span>  
  
## <a name="using-the-arraylistsort-method"></a><span data-ttu-id="2d657-135">ArrayList.Sort yöntemi kullanarak</span><span class="sxs-lookup"><span data-stu-id="2d657-135">Using the ArrayList.Sort Method</span></span>  
 <span data-ttu-id="2d657-136">Overloads biri `ArrayList.Sort` yöntemi gerçekleştirmek varsayılan kullanarak kültüre duyarlı sıralamaları `Thread.CurrentCulture` özelliği.</span><span class="sxs-lookup"><span data-stu-id="2d657-136">Overloads of the `ArrayList.Sort` method perform culture-sensitive sorts by default using the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="2d657-137">Sonuçları nedeniyle farklı sıralamalar kültüre göre değişebilir.</span><span class="sxs-lookup"><span data-stu-id="2d657-137">Results can vary by culture due to different sort orders.</span></span> <span data-ttu-id="2d657-138">Kültüre duyarlı davranışı ortadan kaldırmak için kabul eden aşırı yüklemeleri bu yöntemi kullanın. bir `IComparer` uygulaması.</span><span class="sxs-lookup"><span data-stu-id="2d657-138">To eliminate culture-sensitive behavior, use the overloads of this method that accept an `IComparer` implementation.</span></span> <span data-ttu-id="2d657-139">İçin `comparer` parametresini kullanan bir özel sabit karşılaştırıcısı sınıfı belirtin `CultureInfo.InvariantCulture`.</span><span class="sxs-lookup"><span data-stu-id="2d657-139">For the `comparer` parameter, specify a custom invariant comparer class that uses `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="2d657-140">Sabit özel bir karşılaştırıcı sınıfı örneği sağlanan [SortedList sınıfı kullanarak](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) konu.</span><span class="sxs-lookup"><span data-stu-id="2d657-140">An example of a custom invariant comparer class is provided in the [Using the SortedList Class](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d657-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d657-141">See also</span></span>

- <xref:System.Collections.CaseInsensitiveComparer>  
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>  
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>  
- <xref:System.Collections.SortedList>  
- <xref:System.Collections.Hashtable>  
- <xref:System.Collections.IComparer>  
- [<span data-ttu-id="2d657-142">Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="2d657-142">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)  
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
