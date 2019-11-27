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
ms.openlocfilehash: 13a9f4896a37be4297f2a1a11435b85ade381c66
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353666"
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a><span data-ttu-id="977d3-102">Koleksiyonlarda Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="977d3-102">Performing Culture-Insensitive String Operations in Collections</span></span>

<span data-ttu-id="977d3-103"><xref:System.Collections> ad alanında, varsayılan olarak kültüre duyarlı davranış sağlayan sınıflar ve Üyeler vardır.</span><span class="sxs-lookup"><span data-stu-id="977d3-103">There are classes and members in the <xref:System.Collections> namespace that provide culture-sensitive behavior by default.</span></span> <span data-ttu-id="977d3-104"><xref:System.Collections.CaseInsensitiveComparer> ve <xref:System.Collections.CaseInsensitiveHashCodeProvider> sınıflarının parametresiz oluşturucuları <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliğini kullanarak yeni bir örnek başlatır.</span><span class="sxs-lookup"><span data-stu-id="977d3-104">The parameterless constructors for the <xref:System.Collections.CaseInsensitiveComparer> and <xref:System.Collections.CaseInsensitiveHashCodeProvider> classes initialize a new instance using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="977d3-105"><xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> yönteminin tüm aşırı yüklemeleri, varsayılan olarak `Thread.CurrentCulture` özelliğini kullanarak <xref:System.Collections.Hashtable> sınıfının yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="977d3-105">All overloads of the <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> method create a new instance of the <xref:System.Collections.Hashtable> class using the `Thread.CurrentCulture` property by default.</span></span> <span data-ttu-id="977d3-106"><xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> yönteminin aşırı yüklemeleri, varsayılan olarak `Thread.CurrentCulture`kullanarak kültüre duyarlı sıralar gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="977d3-106">Overloads of the <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> method perform culture-sensitive sorts by default using `Thread.CurrentCulture`.</span></span> <span data-ttu-id="977d3-107">Bir <xref:System.Collections.SortedList> sıralama ve arama, dizeler anahtarlar olarak kullanıldığında `Thread.CurrentCulture` etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="977d3-107">Sorting and lookup in a <xref:System.Collections.SortedList> can be affected by `Thread.CurrentCulture` when strings are used as the keys.</span></span> <span data-ttu-id="977d3-108">`Collections` ad alanındaki bu sınıflardan ve metotlardan kültürden duyarlı sonuçlar almak için bu bölümde belirtilen kullanım önerilerini izleyin.</span><span class="sxs-lookup"><span data-stu-id="977d3-108">Follow the usage recommendations provided in this section to obtain culture-insensitive results from these classes and methods in the `Collections` namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="977d3-109">Karşılaştırma yöntemine <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> geçirmek, kültüre duyarsız bir karşılaştırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="977d3-109">Passing <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="977d3-110">Ancak, dosya yolları, kayıt defteri anahtarları ve ortam değişkenleri gibi dil olmayan bir karşılaştırmaya neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="977d3-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="977d3-111">, Karşılaştırma sonucuna göre güvenlik kararlarını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="977d3-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="977d3-112">Dil olmayan bir karşılaştırma veya sonuç tabanlı güvenlik kararları için destek için, uygulamanın <xref:System.StringComparison> değeri kabul eden bir karşılaştırma yöntemi kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="977d3-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="977d3-113">Uygulamanın <xref:System.StringComparison>geçmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="977d3-113">The application should then pass <xref:System.StringComparison>.</span></span>

## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a><span data-ttu-id="977d3-114">CaseInsensitiveComparer ve CaseInsensitiveHashCodeProvider sınıflarını kullanma</span><span class="sxs-lookup"><span data-stu-id="977d3-114">Using the CaseInsensitiveComparer and CaseInsensitiveHashCodeProvider Classes</span></span>

<span data-ttu-id="977d3-115">`CaseInsensitiveHashCodeProvider` ve `CaseInsensitiveComparer` için parametresiz oluşturucular, `Thread.CurrentCulture`kullanarak sınıfının yeni bir örneğini başlatır ve kültüre duyarlı davranışa neden olur.</span><span class="sxs-lookup"><span data-stu-id="977d3-115">The parameterless constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer` initialize a new instance of the class using the `Thread.CurrentCulture`, resulting in culture-sensitive behavior.</span></span> <span data-ttu-id="977d3-116">Aşağıdaki kod örneği, `CaseInsensitiveHashCodeProvider` ve `CaseInsensitiveComparer`için parametresiz oluşturucular kullandığından, kültüre duyarlı bir `Hashtable` için olan oluşturucuyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="977d3-116">The following code example demonstrates the constructor for a `Hashtable` that is culture-sensitive because it uses the parameterless constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer`.</span></span>

```vb
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)
```

```csharp
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);
```

<span data-ttu-id="977d3-117">`CaseInsensitiveComparer` ve `CaseInsensitiveHashCodeProvider` sınıfları kullanarak kültüre duyarsız `Hashtable` oluşturmak istiyorsanız, bir `culture` parametresi kabul eden oluşturucuları kullanarak bu sınıfların yeni örneklerini başlatın.</span><span class="sxs-lookup"><span data-stu-id="977d3-117">If you want to create a culture-insensitive `Hashtable` using the `CaseInsensitiveComparer` and `CaseInsensitiveHashCodeProvider` classes, initialize new instances of these classes using the constructors that accept a `culture` parameter.</span></span> <span data-ttu-id="977d3-118">`culture` parametresi için <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>belirtin.</span><span class="sxs-lookup"><span data-stu-id="977d3-118">For the `culture` parameter, specify <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="977d3-119">Aşağıdaki kod örneği, kültüre duyarsız `Hashtable`için oluşturucuyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="977d3-119">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>

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

## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a><span data-ttu-id="977d3-120">CollectionsUtil. CreateCaseInsensitiveHashTable yöntemini kullanma</span><span class="sxs-lookup"><span data-stu-id="977d3-120">Using the CollectionsUtil.CreateCaseInsensitiveHashTable Method</span></span>

<span data-ttu-id="977d3-121">`CollectionsUtil.CreateCaseInsensitiveHashTable` yöntemi, dizelerin durumunu yok sayan `Hashtable` sınıfının yeni bir örneğini oluşturmaya yönelik faydalı bir kısayoldur.</span><span class="sxs-lookup"><span data-stu-id="977d3-121">The `CollectionsUtil.CreateCaseInsensitiveHashTable` method is a useful shortcut for creating a new instance of the `Hashtable` class that ignores the case of strings.</span></span> <span data-ttu-id="977d3-122">Ancak, `CollectionsUtil.CreateCaseInsensitiveHashTable` yönteminin tüm aşırı yüklemeleri, `Thread.CurrentCulture` özelliğini kullandıkları için kültüre duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="977d3-122">However, all overloads of the `CollectionsUtil.CreateCaseInsensitiveHashTable` method are culture-sensitive because they use the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="977d3-123">Bu yöntemi kullanarak kültüre duyarsız `Hashtable` oluşturamazsınız.</span><span class="sxs-lookup"><span data-stu-id="977d3-123">You cannot create a culture-insensitive `Hashtable` using this method.</span></span> <span data-ttu-id="977d3-124">Kültüre duyarsız `Hashtable`oluşturmak için bir `culture` parametresi kabul eden `Hashtable` oluşturucusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="977d3-124">To create a culture-insensitive `Hashtable`, use the `Hashtable` constructor that accepts a `culture` parameter.</span></span> <span data-ttu-id="977d3-125">`culture` parametresi için `CultureInfo.InvariantCulture`belirtin.</span><span class="sxs-lookup"><span data-stu-id="977d3-125">For the `culture` parameter, specify `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="977d3-126">Aşağıdaki kod örneği, kültüre duyarsız `Hashtable`için oluşturucuyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="977d3-126">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>

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

## <a name="using-the-sortedlist-class"></a><span data-ttu-id="977d3-127">SortedList sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="977d3-127">Using the SortedList Class</span></span>

<span data-ttu-id="977d3-128">`SortedList` anahtarlar tarafından sıralanan ve anahtar ve dizine göre erişilebilen anahtar ve değer çiftleri koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="977d3-128">A `SortedList` represents a collection of key-and-value pairs that are sorted by the keys and are accessible by key and by index.</span></span> <span data-ttu-id="977d3-129">Dizelerin anahtarlar olduğu bir `SortedList` kullandığınızda, sıralama ve arama `Thread.CurrentCulture` özelliğinden etkilenebilir.</span><span class="sxs-lookup"><span data-stu-id="977d3-129">When you use a `SortedList` where strings are the keys, the sorting and lookup can be affected by the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="977d3-130">`SortedList`kültüre duyarlı olmayan davranış almak için, bir `comparer` parametresi kabul eden oluşturuculardan birini kullanarak bir `SortedList` oluşturun.</span><span class="sxs-lookup"><span data-stu-id="977d3-130">To obtain culture-insensitive behavior from a `SortedList`, create a `SortedList` using one of the constructors that accepts a `comparer` parameter.</span></span> <span data-ttu-id="977d3-131">`comparer` parametresi, anahtarları karşılaştırırken kullanılacak <xref:System.Collections.IComparer> uygulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="977d3-131">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing keys.</span></span> <span data-ttu-id="977d3-132">Parametresi için, anahtarları karşılaştırmak için `CultureInfo.InvariantCulture` kullanan özel bir karşılaştırıcı sınıfı belirtin.</span><span class="sxs-lookup"><span data-stu-id="977d3-132">For the parameter, specify a custom comparer class that uses `CultureInfo.InvariantCulture` to compare keys.</span></span> <span data-ttu-id="977d3-133">Aşağıdaki örnek, bir `SortedList` oluşturucusuna `comparer` parametresi olarak belirtebileceğiniz özel bir kültür duyarsız karşılaştırıcı sınıfını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="977d3-133">The following example illustrates a custom culture-insensitive comparer class that you can specify as the `comparer` parameter to a `SortedList` constructor.</span></span>

```vb
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

<span data-ttu-id="977d3-134">Genel olarak, özel bir sabit karşılaştırıcı belirtmeden dizeler üzerinde `SortedList` kullanırsanız, liste doldurulduktan sonra `Thread.CurrentCulture` bir değişiklik listeyi geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="977d3-134">In general, if you use a `SortedList` on strings without specifying a custom invariant comparer, a change to `Thread.CurrentCulture` after the list has been populated can invalidate the list.</span></span>

## <a name="using-the-arraylistsort-method"></a><span data-ttu-id="977d3-135">ArrayList. Sort metodunu kullanma</span><span class="sxs-lookup"><span data-stu-id="977d3-135">Using the ArrayList.Sort Method</span></span>

<span data-ttu-id="977d3-136">`ArrayList.Sort` yönteminin aşırı yüklemeleri, `Thread.CurrentCulture` özelliğini kullanarak varsayılan olarak kültüre duyarlı sıralar gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="977d3-136">Overloads of the `ArrayList.Sort` method perform culture-sensitive sorts by default using the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="977d3-137">Sonuçlar farklı sıralama düzenleri nedeniyle kültüre göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="977d3-137">Results can vary by culture due to different sort orders.</span></span> <span data-ttu-id="977d3-138">Kültüre duyarlı davranışı ortadan kaldırmak için, bu yöntemin `IComparer` uygulamasını kabul eden aşırı yüklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="977d3-138">To eliminate culture-sensitive behavior, use the overloads of this method that accept an `IComparer` implementation.</span></span> <span data-ttu-id="977d3-139">`comparer` parametresi için `CultureInfo.InvariantCulture`kullanan özel bir sabit karşılaştırıcı sınıfı belirtin.</span><span class="sxs-lookup"><span data-stu-id="977d3-139">For the `comparer` parameter, specify a custom invariant comparer class that uses `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="977d3-140">Özel bir sabit karşılaştırıcı sınıfına bir örnek, [SortedList sınıfını kullanma](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) konusunun içinde verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="977d3-140">An example of a custom invariant comparer class is provided in the [Using the SortedList Class](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="977d3-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="977d3-141">See also</span></span>

- <xref:System.Collections.CaseInsensitiveComparer>
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>
- <xref:System.Collections.SortedList>
- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IComparer>
- [<span data-ttu-id="977d3-142">Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="977d3-142">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
