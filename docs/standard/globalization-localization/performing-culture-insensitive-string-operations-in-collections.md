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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353666"
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a><span data-ttu-id="bdf74-102">Koleksiyonlarda Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="bdf74-102">Performing Culture-Insensitive String Operations in Collections</span></span>

<span data-ttu-id="bdf74-103"><xref:System.Collections> Ad alanında varsayılan olarak kültüre duyarlı davranış sağlayan sınıflar ve üyeler vardır.</span><span class="sxs-lookup"><span data-stu-id="bdf74-103">There are classes and members in the <xref:System.Collections> namespace that provide culture-sensitive behavior by default.</span></span> <span data-ttu-id="bdf74-104">Ve sınıflar için parametresiz oluşturucular <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği kullanarak yeni bir örnek başlatılması. <xref:System.Collections.CaseInsensitiveHashCodeProvider> <xref:System.Collections.CaseInsensitiveComparer></span><span class="sxs-lookup"><span data-stu-id="bdf74-104">The parameterless constructors for the <xref:System.Collections.CaseInsensitiveComparer> and <xref:System.Collections.CaseInsensitiveHashCodeProvider> classes initialize a new instance using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="bdf74-105">Yöntemin <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> tüm aşırı yükleri varsayılan <xref:System.Collections.Hashtable> `Thread.CurrentCulture` olarak özelliği kullanarak sınıfın yeni bir örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bdf74-105">All overloads of the <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> method create a new instance of the <xref:System.Collections.Hashtable> class using the `Thread.CurrentCulture` property by default.</span></span> <span data-ttu-id="bdf74-106">Yöntemin <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> aşırı yükleri varsayılan olarak kültüre duyarlı sıralamaları kullanarak `Thread.CurrentCulture`gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="bdf74-106">Overloads of the <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> method perform culture-sensitive sorts by default using `Thread.CurrentCulture`.</span></span> <span data-ttu-id="bdf74-107">Bir dizindeki sıralama <xref:System.Collections.SortedList> ve arama, `Thread.CurrentCulture` dizelerin anahtar olarak kullanılmasından etkilenebilir.</span><span class="sxs-lookup"><span data-stu-id="bdf74-107">Sorting and lookup in a <xref:System.Collections.SortedList> can be affected by `Thread.CurrentCulture` when strings are used as the keys.</span></span> <span data-ttu-id="bdf74-108">`Collections` Ad alanında bu sınıflardan ve yöntemlerden kültüre duyarsız sonuçlar almak için bu bölümde sağlanan kullanım önerilerini izleyin.</span><span class="sxs-lookup"><span data-stu-id="bdf74-108">Follow the usage recommendations provided in this section to obtain culture-insensitive results from these classes and methods in the `Collections` namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="bdf74-109">Karşılaştırma <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> yöntemine geçmek, kültüre duyarsız bir karşılaştırma yapar.</span><span class="sxs-lookup"><span data-stu-id="bdf74-109">Passing <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="bdf74-110">Ancak, dosya yolları, kayıt defteri anahtarları ve ortam değişkenleri gibi dilsel olmayan bir karşılaştırmaya neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="bdf74-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="bdf74-111">Karşılaştırma sonucuna göre güvenlik kararlarını da desteklemez.</span><span class="sxs-lookup"><span data-stu-id="bdf74-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="bdf74-112">Dilbilimsel olmayan bir karşılaştırma veya sonuç tabanlı güvenlik kararları desteği için, uygulama bir <xref:System.StringComparison> değer kabul eden bir karşılaştırma yöntemi kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bdf74-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="bdf74-113">Uygulama daha sonra <xref:System.StringComparison>geçmelidir.</span><span class="sxs-lookup"><span data-stu-id="bdf74-113">The application should then pass <xref:System.StringComparison>.</span></span>

## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a><span data-ttu-id="bdf74-114">CaseInsensitiveComparer ve CaseInsensitiveHashCodeProvider Sınıfları kullanma</span><span class="sxs-lookup"><span data-stu-id="bdf74-114">Using the CaseInsensitiveComparer and CaseInsensitiveHashCodeProvider Classes</span></span>

<span data-ttu-id="bdf74-115">Parametresiz oluşturucular `CaseInsensitiveHashCodeProvider` için `CaseInsensitiveComparer` ve sınıfın yeni bir örnek `Thread.CurrentCulture`initialize kullanarak , kültüre duyarlı davranış sonuçlanan.</span><span class="sxs-lookup"><span data-stu-id="bdf74-115">The parameterless constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer` initialize a new instance of the class using the `Thread.CurrentCulture`, resulting in culture-sensitive behavior.</span></span> <span data-ttu-id="bdf74-116">Aşağıdaki kod örneği, kültüre duyarlı `Hashtable` bir yapının oluşturucuyu gösterir, çünkü parametresiz oluşturucuları `CaseInsensitiveHashCodeProvider` ve . `CaseInsensitiveComparer`</span><span class="sxs-lookup"><span data-stu-id="bdf74-116">The following code example demonstrates the constructor for a `Hashtable` that is culture-sensitive because it uses the parameterless constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer`.</span></span>

```vb
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)
```

```csharp
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);
```

<span data-ttu-id="bdf74-117">Ve `CaseInsensitiveComparer` `CaseInsensitiveHashCodeProvider` sınıfları kullanarak kültüre `Hashtable` duyarsız bir `culture` oluşturmak istiyorsanız, parametre kabul eden oluşturucuları kullanarak bu sınıfların yeni örneklerini başharfe indirin.</span><span class="sxs-lookup"><span data-stu-id="bdf74-117">If you want to create a culture-insensitive `Hashtable` using the `CaseInsensitiveComparer` and `CaseInsensitiveHashCodeProvider` classes, initialize new instances of these classes using the constructors that accept a `culture` parameter.</span></span> <span data-ttu-id="bdf74-118">Parametre `culture` için. <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="bdf74-118">For the `culture` parameter, specify <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bdf74-119">Aşağıdaki kod örneği, kültüre duyarsız `Hashtable`bir yapının oluşturucuyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bdf74-119">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>

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

## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a><span data-ttu-id="bdf74-120">CollectionsUtil.CreateCaseInsensitiveHashTable Yöntemini Kullanma</span><span class="sxs-lookup"><span data-stu-id="bdf74-120">Using the CollectionsUtil.CreateCaseInsensitiveHashTable Method</span></span>

<span data-ttu-id="bdf74-121">Yöntem, `CollectionsUtil.CreateCaseInsensitiveHashTable` `Hashtable` dizeleri durumda yoksaçan sınıfın yeni bir örnek oluşturmak için yararlı bir kısayol.</span><span class="sxs-lookup"><span data-stu-id="bdf74-121">The `CollectionsUtil.CreateCaseInsensitiveHashTable` method is a useful shortcut for creating a new instance of the `Hashtable` class that ignores the case of strings.</span></span> <span data-ttu-id="bdf74-122">Ancak, yöntemin `CollectionsUtil.CreateCaseInsensitiveHashTable` tüm aşırı yükleri, `Thread.CurrentCulture` özelliği kullandıkları için kültüre duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="bdf74-122">However, all overloads of the `CollectionsUtil.CreateCaseInsensitiveHashTable` method are culture-sensitive because they use the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="bdf74-123">Bu yöntemi kullanarak kültüre `Hashtable` duyarsız bir şey oluşturamazsınız.</span><span class="sxs-lookup"><span data-stu-id="bdf74-123">You cannot create a culture-insensitive `Hashtable` using this method.</span></span> <span data-ttu-id="bdf74-124">Kültüre duyarsız `Hashtable`bir şey oluşturmak `Hashtable` için, parametre `culture` kabul eden oluşturucuyu kullanın.</span><span class="sxs-lookup"><span data-stu-id="bdf74-124">To create a culture-insensitive `Hashtable`, use the `Hashtable` constructor that accepts a `culture` parameter.</span></span> <span data-ttu-id="bdf74-125">Parametre `culture` için. `CultureInfo.InvariantCulture`</span><span class="sxs-lookup"><span data-stu-id="bdf74-125">For the `culture` parameter, specify `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="bdf74-126">Aşağıdaki kod örneği, kültüre duyarsız `Hashtable`bir yapının oluşturucuyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bdf74-126">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>

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

## <a name="using-the-sortedlist-class"></a><span data-ttu-id="bdf74-127">SıralanmışListe Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="bdf74-127">Using the SortedList Class</span></span>

<span data-ttu-id="bdf74-128">A, `SortedList` anahtarlara göre sıralanan ve anahtar ve dizin tarafından erişilebilen anahtar ve değer çiftleri koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bdf74-128">A `SortedList` represents a collection of key-and-value pairs that are sorted by the keys and are accessible by key and by index.</span></span> <span data-ttu-id="bdf74-129">Dizelerin `SortedList` anahtarlar olduğu bir yerde kullandığınızda, sıralama ve arama `Thread.CurrentCulture` özelliğinden etkilenebilir.</span><span class="sxs-lookup"><span data-stu-id="bdf74-129">When you use a `SortedList` where strings are the keys, the sorting and lookup can be affected by the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="bdf74-130">Kültüre duyarsız davranış elde `SortedList`etmek için, bir `SortedList` `comparer` parametre kabul eden yapıcılardan birini kullanarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bdf74-130">To obtain culture-insensitive behavior from a `SortedList`, create a `SortedList` using one of the constructors that accepts a `comparer` parameter.</span></span> <span data-ttu-id="bdf74-131">`comparer` Parametre, anahtarları karşılaştırırken kullanılacak <xref:System.Collections.IComparer> uygulamayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="bdf74-131">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing keys.</span></span> <span data-ttu-id="bdf74-132">Parametre için, anahtarları karşılaştırmak için `CultureInfo.InvariantCulture` kullanan özel bir karşılayıcı sınıf belirtin.</span><span class="sxs-lookup"><span data-stu-id="bdf74-132">For the parameter, specify a custom comparer class that uses `CultureInfo.InvariantCulture` to compare keys.</span></span> <span data-ttu-id="bdf74-133">Aşağıdaki örnek, bir `comparer` `SortedList` oluşturucuiçin parametre olarak belirtebileceğiniz özel bir kültüre duyarlı olmayan karşılandırıcı sınıf göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="bdf74-133">The following example illustrates a custom culture-insensitive comparer class that you can specify as the `comparer` parameter to a `SortedList` constructor.</span></span>

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

<span data-ttu-id="bdf74-134">Genel olarak, özel `SortedList` bir değişmez karşılayıcı belirtmeden dizeleri üzerinde kullanırsanız, liste doldurulan sonra bir `Thread.CurrentCulture` değişiklik liste geçersiz olabilir.</span><span class="sxs-lookup"><span data-stu-id="bdf74-134">In general, if you use a `SortedList` on strings without specifying a custom invariant comparer, a change to `Thread.CurrentCulture` after the list has been populated can invalidate the list.</span></span>

## <a name="using-the-arraylistsort-method"></a><span data-ttu-id="bdf74-135">ArrayList.Sort Yöntemini Kullanma</span><span class="sxs-lookup"><span data-stu-id="bdf74-135">Using the ArrayList.Sort Method</span></span>

<span data-ttu-id="bdf74-136">`ArrayList.Sort` Yöntemin aşırı yükleri `Thread.CurrentCulture` özelliği kullanarak varsayılan olarak kültüre duyarlı sıralamaları gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="bdf74-136">Overloads of the `ArrayList.Sort` method perform culture-sensitive sorts by default using the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="bdf74-137">Sonuçlar, farklı sıralama emirlerine bağlı olarak kültüre göre değişebilir.</span><span class="sxs-lookup"><span data-stu-id="bdf74-137">Results can vary by culture due to different sort orders.</span></span> <span data-ttu-id="bdf74-138">Kültüre duyarlı davranışı ortadan kaldırmak için, bir `IComparer` uygulamayı kabul eden bu yöntemin aşırı yüklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bdf74-138">To eliminate culture-sensitive behavior, use the overloads of this method that accept an `IComparer` implementation.</span></span> <span data-ttu-id="bdf74-139">Parametre `comparer` için, kullanan özel değişmez karşılayıcı `CultureInfo.InvariantCulture`sınıf belirtin.</span><span class="sxs-lookup"><span data-stu-id="bdf74-139">For the `comparer` parameter, specify a custom invariant comparer class that uses `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="bdf74-140">[Sıralanmış Liste Sınıfını Kullanma](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) konusu'nda özel değişmez karşılayıcı sınıfının bir örneği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="bdf74-140">An example of a custom invariant comparer class is provided in the [Using the SortedList Class](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="bdf74-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bdf74-141">See also</span></span>

- <xref:System.Collections.CaseInsensitiveComparer>
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>
- <xref:System.Collections.SortedList>
- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IComparer>
- [<span data-ttu-id="bdf74-142">Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="bdf74-142">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
