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
ms.openlocfilehash: 222376e220bf74274082dfc6b76dc861d4f8ddc5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855977"
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a><span data-ttu-id="b2747-102">Koleksiyonlarda Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="b2747-102">Performing Culture-Insensitive String Operations in Collections</span></span>

<span data-ttu-id="b2747-103">Ad alanı içinde, <xref:System.Collections> varsayılan olarak kültüre duyarlı davranış sağlayan sınıflar ve Üyeler vardır.</span><span class="sxs-lookup"><span data-stu-id="b2747-103">There are classes and members in the <xref:System.Collections> namespace that provide culture-sensitive behavior by default.</span></span> <span data-ttu-id="b2747-104"><xref:System.Collections.CaseInsensitiveComparer> <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> Ve sınıflarınınparametresizoluşturucuları,özelliğinikullanarakyenibirörneğibaşlatır.<xref:System.Collections.CaseInsensitiveHashCodeProvider></span><span class="sxs-lookup"><span data-stu-id="b2747-104">The parameterless constructors for the <xref:System.Collections.CaseInsensitiveComparer> and <xref:System.Collections.CaseInsensitiveHashCodeProvider> classes initialize a new instance using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="b2747-105"><xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> Yönteminin tüm aşırı yüklemeleri, `Thread.CurrentCulture` varsayılan olarak özelliğini kullanarak <xref:System.Collections.Hashtable> sınıfının yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b2747-105">All overloads of the <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> method create a new instance of the <xref:System.Collections.Hashtable> class using the `Thread.CurrentCulture` property by default.</span></span> <span data-ttu-id="b2747-106">Metodun aşırı yüklemeleri <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> , kullanarak `Thread.CurrentCulture`varsayılan olarak kültüre duyarlı sıralar gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="b2747-106">Overloads of the <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> method perform culture-sensitive sorts by default using `Thread.CurrentCulture`.</span></span> <span data-ttu-id="b2747-107">Bir <xref:System.Collections.SortedList> içinde sıralama ve arama, dizeler anahtar olarak `Thread.CurrentCulture` kullanıldığında etkilenebilir.</span><span class="sxs-lookup"><span data-stu-id="b2747-107">Sorting and lookup in a <xref:System.Collections.SortedList> can be affected by `Thread.CurrentCulture` when strings are used as the keys.</span></span> <span data-ttu-id="b2747-108">Bu sınıftan ve `Collections` ad alanındaki metotlardan kültürden duyarlı sonuçlar almak için bu bölümde belirtilen kullanım önerilerini izleyin.</span><span class="sxs-lookup"><span data-stu-id="b2747-108">Follow the usage recommendations provided in this section to obtain culture-insensitive results from these classes and methods in the `Collections` namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="b2747-109">Bir <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> karşılaştırma yöntemine geçirilmesi, kültüre duyarsız bir karşılaştırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="b2747-109">Passing <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="b2747-110">Ancak, dosya yolları, kayıt defteri anahtarları ve ortam değişkenleri gibi dil olmayan bir karşılaştırmaya neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="b2747-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="b2747-111">, Karşılaştırma sonucuna göre güvenlik kararlarını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b2747-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="b2747-112">Dil olmayan bir karşılaştırma veya sonuç tabanlı güvenlik kararları için destek için, uygulamanın bir <xref:System.StringComparison> değeri kabul eden bir karşılaştırma yöntemi kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b2747-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="b2747-113">Uygulama daha sonra geçmelidir <xref:System.StringComparison>.</span><span class="sxs-lookup"><span data-stu-id="b2747-113">The application should then pass <xref:System.StringComparison>.</span></span>

## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a><span data-ttu-id="b2747-114">CaseInsensitiveComparer ve CaseInsensitiveHashCodeProvider sınıflarını kullanma</span><span class="sxs-lookup"><span data-stu-id="b2747-114">Using the CaseInsensitiveComparer and CaseInsensitiveHashCodeProvider Classes</span></span>

<span data-ttu-id="b2747-115">Parametresiz oluşturucular `CaseInsensitiveHashCodeProvider` , ve `CaseInsensitiveComparer` kullanarak `Thread.CurrentCulture`sınıfının yeni bir örneğini başlatır. Bu, kültüre duyarlı davranışa neden olur.</span><span class="sxs-lookup"><span data-stu-id="b2747-115">The parameterless constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer` initialize a new instance of the class using the `Thread.CurrentCulture`, resulting in culture-sensitive behavior.</span></span> <span data-ttu-id="b2747-116">Aşağıdaki kod örneği, ve `Hashtable` `CaseInsensitiveComparer`için `CaseInsensitiveHashCodeProvider` parametresiz oluşturucular kullandığından kültüre duyarlı olan öğesine ilişkin oluşturucuyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2747-116">The following code example demonstrates the constructor for a `Hashtable` that is culture-sensitive because it uses the parameterless constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer`.</span></span>

```vb
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)
```

```csharp
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);
```

<span data-ttu-id="b2747-117">`Hashtable` `culture` Ve sınıflarını`CaseInsensitiveHashCodeProvider` kullanarak kültüre duyarsız bir kültür oluşturmak istiyorsanız, bir parametreyi kabul eden oluşturucuları kullanarak bu sınıfların yeni örneklerini başlatın. `CaseInsensitiveComparer`</span><span class="sxs-lookup"><span data-stu-id="b2747-117">If you want to create a culture-insensitive `Hashtable` using the `CaseInsensitiveComparer` and `CaseInsensitiveHashCodeProvider` classes, initialize new instances of these classes using the constructors that accept a `culture` parameter.</span></span> <span data-ttu-id="b2747-118">Parametresi için, belirtin <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. `culture`</span><span class="sxs-lookup"><span data-stu-id="b2747-118">For the `culture` parameter, specify <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b2747-119">Aşağıdaki kod örneği, bir kültür duyarlığını `Hashtable`için oluşturucuyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2747-119">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>

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

## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a><span data-ttu-id="b2747-120">CollectionsUtil. CreateCaseInsensitiveHashTable yöntemini kullanma</span><span class="sxs-lookup"><span data-stu-id="b2747-120">Using the CollectionsUtil.CreateCaseInsensitiveHashTable Method</span></span>

<span data-ttu-id="b2747-121">Yöntemi, `Hashtable` sınıfının dize durumunu yok sayan yeni bir örneğini oluşturmaya yönelik yararlı bir kısayoldur. `CollectionsUtil.CreateCaseInsensitiveHashTable`</span><span class="sxs-lookup"><span data-stu-id="b2747-121">The `CollectionsUtil.CreateCaseInsensitiveHashTable` method is a useful shortcut for creating a new instance of the `Hashtable` class that ignores the case of strings.</span></span> <span data-ttu-id="b2747-122">Ancak, `CollectionsUtil.CreateCaseInsensitiveHashTable` `Thread.CurrentCulture` özelliği kullandığından, yöntemin tüm aşırı yüklemeleri kültüre duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="b2747-122">However, all overloads of the `CollectionsUtil.CreateCaseInsensitiveHashTable` method are culture-sensitive because they use the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="b2747-123">Bu yöntemi kullanarak kültüre duyarlı `Hashtable` olmayan bir şekilde oluşturamazsınız.</span><span class="sxs-lookup"><span data-stu-id="b2747-123">You cannot create a culture-insensitive `Hashtable` using this method.</span></span> <span data-ttu-id="b2747-124">Kültüre duyarsız `Hashtable`olması için bir `culture` parametreyi kabul eden `Hashtable` oluşturucuyu kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2747-124">To create a culture-insensitive `Hashtable`, use the `Hashtable` constructor that accepts a `culture` parameter.</span></span> <span data-ttu-id="b2747-125">Parametresi için, belirtin `CultureInfo.InvariantCulture`. `culture`</span><span class="sxs-lookup"><span data-stu-id="b2747-125">For the `culture` parameter, specify `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="b2747-126">Aşağıdaki kod örneği, bir kültür duyarlığını `Hashtable`için oluşturucuyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2747-126">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>

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

## <a name="using-the-sortedlist-class"></a><span data-ttu-id="b2747-127">SortedList sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="b2747-127">Using the SortedList Class</span></span>

<span data-ttu-id="b2747-128">, Anahtarlar tarafından sıralanan ve anahtar ve dizine göre erişilebilen anahtar ve değer çiftleri koleksiyonunu temsileder.`SortedList`</span><span class="sxs-lookup"><span data-stu-id="b2747-128">A `SortedList` represents a collection of key-and-value pairs that are sorted by the keys and are accessible by key and by index.</span></span> <span data-ttu-id="b2747-129">Anahtarlar olduğu yerde dizeler kullandığınızda sıralama ve arama `Thread.CurrentCulture` özelliğinden etkilenebilir. `SortedList`</span><span class="sxs-lookup"><span data-stu-id="b2747-129">When you use a `SortedList` where strings are the keys, the sorting and lookup can be affected by the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="b2747-130">Kültüre duyarsız bir davranış elde etmek için bir `SortedList` `comparer` parametre kabul eden `SortedList` oluşturuculardan birini kullanarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b2747-130">To obtain culture-insensitive behavior from a `SortedList`, create a `SortedList` using one of the constructors that accepts a `comparer` parameter.</span></span> <span data-ttu-id="b2747-131">Parametresi `comparer` , anahtarları karşılaştırırken <xref:System.Collections.IComparer> kullanılacak uygulamayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2747-131">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing keys.</span></span> <span data-ttu-id="b2747-132">Parametresi için, anahtarları karşılaştırmak için kullanan `CultureInfo.InvariantCulture` özel bir karşılaştırıcı sınıfı belirtin.</span><span class="sxs-lookup"><span data-stu-id="b2747-132">For the parameter, specify a custom comparer class that uses `CultureInfo.InvariantCulture` to compare keys.</span></span> <span data-ttu-id="b2747-133">Aşağıdaki örnek, bir `comparer` `SortedList` oluşturucuya parametre olarak belirtebileceğiniz özel bir kültür duyarsız karşılaştırıcı sınıfını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b2747-133">The following example illustrates a custom culture-insensitive comparer class that you can specify as the `comparer` parameter to a `SortedList` constructor.</span></span>

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

<span data-ttu-id="b2747-134">Genel olarak, özel bir sabit karşılaştırıcı `SortedList` belirtmeden dize üzerinde kullanırsanız, liste doldurulduktan sonra yapılan `Thread.CurrentCulture` bir değişiklik listeyi geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="b2747-134">In general, if you use a `SortedList` on strings without specifying a custom invariant comparer, a change to `Thread.CurrentCulture` after the list has been populated can invalidate the list.</span></span>

## <a name="using-the-arraylistsort-method"></a><span data-ttu-id="b2747-135">ArrayList. Sort metodunu kullanma</span><span class="sxs-lookup"><span data-stu-id="b2747-135">Using the ArrayList.Sort Method</span></span>

<span data-ttu-id="b2747-136">Metodun aşırı yüklemeleri, `Thread.CurrentCulture` özelliği kullanılarak varsayılan olarak kültüre duyarlı sıralar gerçekleştirir. `ArrayList.Sort`</span><span class="sxs-lookup"><span data-stu-id="b2747-136">Overloads of the `ArrayList.Sort` method perform culture-sensitive sorts by default using the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="b2747-137">Sonuçlar farklı sıralama düzenleri nedeniyle kültüre göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="b2747-137">Results can vary by culture due to different sort orders.</span></span> <span data-ttu-id="b2747-138">Kültüre duyarlı davranışı ortadan kaldırmak için, bu yöntemin bir `IComparer` uygulamayı kabul eden aşırı yüklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2747-138">To eliminate culture-sensitive behavior, use the overloads of this method that accept an `IComparer` implementation.</span></span> <span data-ttu-id="b2747-139">Parametresi için, tarafından kullanılan `CultureInfo.InvariantCulture`özel bir sabit karşılaştırıcı sınıfı belirtin. `comparer`</span><span class="sxs-lookup"><span data-stu-id="b2747-139">For the `comparer` parameter, specify a custom invariant comparer class that uses `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="b2747-140">Özel bir sabit karşılaştırıcı sınıfına bir örnek, [SortedList sınıfını kullanma](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) konusunun içinde verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b2747-140">An example of a custom invariant comparer class is provided in the [Using the SortedList Class](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2747-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2747-141">See also</span></span>

- <xref:System.Collections.CaseInsensitiveComparer>
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>
- <xref:System.Collections.SortedList>
- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IComparer>
- [<span data-ttu-id="b2747-142">Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="b2747-142">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
