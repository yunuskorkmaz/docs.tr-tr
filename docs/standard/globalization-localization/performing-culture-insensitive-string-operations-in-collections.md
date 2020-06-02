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
ms.openlocfilehash: 377fa58e052e8f8e35a546c21fe2b4fb00cb103d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288270"
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a><span data-ttu-id="08388-102">Koleksiyonlarda Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="08388-102">Performing Culture-Insensitive String Operations in Collections</span></span>

<span data-ttu-id="08388-103"><xref:System.Collections>Ad alanı içinde, varsayılan olarak kültüre duyarlı davranış sağlayan sınıflar ve Üyeler vardır.</span><span class="sxs-lookup"><span data-stu-id="08388-103">There are classes and members in the <xref:System.Collections> namespace that provide culture-sensitive behavior by default.</span></span> <span data-ttu-id="08388-104">Ve sınıflarının parametresiz oluşturucuları, <xref:System.Collections.CaseInsensitiveComparer> <xref:System.Collections.CaseInsensitiveHashCodeProvider> özelliğini kullanarak yeni bir örneği başlatır <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="08388-104">The parameterless constructors for the <xref:System.Collections.CaseInsensitiveComparer> and <xref:System.Collections.CaseInsensitiveHashCodeProvider> classes initialize a new instance using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="08388-105">Yönteminin tüm aşırı yüklemeleri <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> <xref:System.Collections.Hashtable> , varsayılan olarak özelliğini kullanarak sınıfının yeni bir örneğini oluşturur `Thread.CurrentCulture` .</span><span class="sxs-lookup"><span data-stu-id="08388-105">All overloads of the <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> method create a new instance of the <xref:System.Collections.Hashtable> class using the `Thread.CurrentCulture` property by default.</span></span> <span data-ttu-id="08388-106">Metodun aşırı yüklemeleri, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> kullanarak varsayılan olarak kültüre duyarlı sıralar gerçekleştirir `Thread.CurrentCulture` .</span><span class="sxs-lookup"><span data-stu-id="08388-106">Overloads of the <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> method perform culture-sensitive sorts by default using `Thread.CurrentCulture`.</span></span> <span data-ttu-id="08388-107">Bir içinde sıralama ve arama <xref:System.Collections.SortedList> `Thread.CurrentCulture` , dizeler anahtar olarak kullanıldığında etkilenebilir.</span><span class="sxs-lookup"><span data-stu-id="08388-107">Sorting and lookup in a <xref:System.Collections.SortedList> can be affected by `Thread.CurrentCulture` when strings are used as the keys.</span></span> <span data-ttu-id="08388-108">Bu sınıftan ve ad alanındaki metotlardan kültürden duyarlı sonuçlar almak için bu bölümde belirtilen kullanım önerilerini izleyin `Collections` .</span><span class="sxs-lookup"><span data-stu-id="08388-108">Follow the usage recommendations provided in this section to obtain culture-insensitive results from these classes and methods in the `Collections` namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="08388-109"><xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>Bir karşılaştırma yöntemine geçirilmesi, kültüre duyarsız bir karşılaştırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="08388-109">Passing <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="08388-110">Ancak, dosya yolları, kayıt defteri anahtarları ve ortam değişkenleri gibi dil olmayan bir karşılaştırmaya neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="08388-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="08388-111">, Karşılaştırma sonucuna göre güvenlik kararlarını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="08388-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="08388-112">Dil olmayan bir karşılaştırma veya sonuç tabanlı güvenlik kararları için destek için, uygulamanın bir değeri kabul eden bir karşılaştırma yöntemi kullanması gerekir <xref:System.StringComparison> .</span><span class="sxs-lookup"><span data-stu-id="08388-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="08388-113">Uygulama daha sonra geçmelidir <xref:System.StringComparison> .</span><span class="sxs-lookup"><span data-stu-id="08388-113">The application should then pass <xref:System.StringComparison>.</span></span>

## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a><span data-ttu-id="08388-114">CaseInsensitiveComparer ve CaseInsensitiveHashCodeProvider sınıflarını kullanma</span><span class="sxs-lookup"><span data-stu-id="08388-114">Using the CaseInsensitiveComparer and CaseInsensitiveHashCodeProvider Classes</span></span>

<span data-ttu-id="08388-115">Parametresiz oluşturucular, `CaseInsensitiveHashCodeProvider` ve `CaseInsensitiveComparer` kullanarak sınıfının yeni bir örneğini başlatır. Bu, `Thread.CurrentCulture` kültüre duyarlı davranışa neden olur.</span><span class="sxs-lookup"><span data-stu-id="08388-115">The parameterless constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer` initialize a new instance of the class using the `Thread.CurrentCulture`, resulting in culture-sensitive behavior.</span></span> <span data-ttu-id="08388-116">Aşağıdaki kod örneği, `Hashtable` ve için parametresiz oluşturucular kullandığından kültüre duyarlı olan öğesine ilişkin oluşturucuyu gösterir `CaseInsensitiveHashCodeProvider` `CaseInsensitiveComparer` .</span><span class="sxs-lookup"><span data-stu-id="08388-116">The following code example demonstrates the constructor for a `Hashtable` that is culture-sensitive because it uses the parameterless constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer`.</span></span>

```vb
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)
```

```csharp
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);
```

<span data-ttu-id="08388-117">Ve sınıflarını kullanarak kültüre duyarsız bir kültür oluşturmak istiyorsanız `Hashtable` `CaseInsensitiveComparer` `CaseInsensitiveHashCodeProvider` , bir parametreyi kabul eden oluşturucuları kullanarak bu sınıfların yeni örneklerini başlatın `culture` .</span><span class="sxs-lookup"><span data-stu-id="08388-117">If you want to create a culture-insensitive `Hashtable` using the `CaseInsensitiveComparer` and `CaseInsensitiveHashCodeProvider` classes, initialize new instances of these classes using the constructors that accept a `culture` parameter.</span></span> <span data-ttu-id="08388-118">Parametresi için `culture` , belirtin <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="08388-118">For the `culture` parameter, specify <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="08388-119">Aşağıdaki kod örneği, bir kültür duyarlığını için oluşturucuyu gösterir `Hashtable` .</span><span class="sxs-lookup"><span data-stu-id="08388-119">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>

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

## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a><span data-ttu-id="08388-120">CollectionsUtil. CreateCaseInsensitiveHashTable yöntemini kullanma</span><span class="sxs-lookup"><span data-stu-id="08388-120">Using the CollectionsUtil.CreateCaseInsensitiveHashTable Method</span></span>

<span data-ttu-id="08388-121">`CollectionsUtil.CreateCaseInsensitiveHashTable`Yöntemi, `Hashtable` sınıfının dize durumunu yok sayan yeni bir örneğini oluşturmaya yönelik yararlı bir kısayoldur.</span><span class="sxs-lookup"><span data-stu-id="08388-121">The `CollectionsUtil.CreateCaseInsensitiveHashTable` method is a useful shortcut for creating a new instance of the `Hashtable` class that ignores the case of strings.</span></span> <span data-ttu-id="08388-122">Ancak, özelliği kullandığından, yöntemin tüm aşırı yüklemeleri `CollectionsUtil.CreateCaseInsensitiveHashTable` kültüre duyarlıdır `Thread.CurrentCulture` .</span><span class="sxs-lookup"><span data-stu-id="08388-122">However, all overloads of the `CollectionsUtil.CreateCaseInsensitiveHashTable` method are culture-sensitive because they use the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="08388-123">Bu yöntemi kullanarak kültüre duyarlı olmayan bir şekilde oluşturamazsınız `Hashtable` .</span><span class="sxs-lookup"><span data-stu-id="08388-123">You cannot create a culture-insensitive `Hashtable` using this method.</span></span> <span data-ttu-id="08388-124">Kültüre duyarsız `Hashtable` `Hashtable` olması için bir parametreyi kabul eden oluşturucuyu kullanın `culture` .</span><span class="sxs-lookup"><span data-stu-id="08388-124">To create a culture-insensitive `Hashtable`, use the `Hashtable` constructor that accepts a `culture` parameter.</span></span> <span data-ttu-id="08388-125">Parametresi için `culture` , belirtin `CultureInfo.InvariantCulture` .</span><span class="sxs-lookup"><span data-stu-id="08388-125">For the `culture` parameter, specify `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="08388-126">Aşağıdaki kod örneği, bir kültür duyarlığını için oluşturucuyu gösterir `Hashtable` .</span><span class="sxs-lookup"><span data-stu-id="08388-126">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>

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

## <a name="using-the-sortedlist-class"></a><span data-ttu-id="08388-127">SortedList sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="08388-127">Using the SortedList Class</span></span>

<span data-ttu-id="08388-128">`SortedList`, Anahtarlar tarafından sıralanan ve anahtar ve dizine göre erişilebilen anahtar ve değer çiftleri koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="08388-128">A `SortedList` represents a collection of key-and-value pairs that are sorted by the keys and are accessible by key and by index.</span></span> <span data-ttu-id="08388-129">`SortedList`Anahtarlar olduğu yerde dizeler kullandığınızda sıralama ve arama `Thread.CurrentCulture` özelliğinden etkilenebilir.</span><span class="sxs-lookup"><span data-stu-id="08388-129">When you use a `SortedList` where strings are the keys, the sorting and lookup can be affected by the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="08388-130">Kültüre duyarsız bir davranış elde etmek için bir `SortedList` `SortedList` parametre kabul eden oluşturuculardan birini kullanarak oluşturun `comparer` .</span><span class="sxs-lookup"><span data-stu-id="08388-130">To obtain culture-insensitive behavior from a `SortedList`, create a `SortedList` using one of the constructors that accepts a `comparer` parameter.</span></span> <span data-ttu-id="08388-131">`comparer`Parametresi, <xref:System.Collections.IComparer> anahtarları karşılaştırırken kullanılacak uygulamayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="08388-131">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing keys.</span></span> <span data-ttu-id="08388-132">Parametresi için, anahtarları karşılaştırmak için kullanan özel bir karşılaştırıcı sınıfı belirtin `CultureInfo.InvariantCulture` .</span><span class="sxs-lookup"><span data-stu-id="08388-132">For the parameter, specify a custom comparer class that uses `CultureInfo.InvariantCulture` to compare keys.</span></span> <span data-ttu-id="08388-133">Aşağıdaki örnek, bir oluşturucuya parametre olarak belirtebileceğiniz özel bir kültür duyarsız karşılaştırıcı sınıfını göstermektedir `comparer` `SortedList` .</span><span class="sxs-lookup"><span data-stu-id="08388-133">The following example illustrates a custom culture-insensitive comparer class that you can specify as the `comparer` parameter to a `SortedList` constructor.</span></span>

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

<span data-ttu-id="08388-134">Genel olarak, `SortedList` özel bir sabit karşılaştırıcı belirtmeden dize üzerinde kullanırsanız, `Thread.CurrentCulture` liste doldurulduktan sonra yapılan bir değişiklik listeyi geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="08388-134">In general, if you use a `SortedList` on strings without specifying a custom invariant comparer, a change to `Thread.CurrentCulture` after the list has been populated can invalidate the list.</span></span>

## <a name="using-the-arraylistsort-method"></a><span data-ttu-id="08388-135">ArrayList. Sort metodunu kullanma</span><span class="sxs-lookup"><span data-stu-id="08388-135">Using the ArrayList.Sort Method</span></span>

<span data-ttu-id="08388-136">Metodun aşırı yüklemeleri, `ArrayList.Sort` özelliği kullanılarak varsayılan olarak kültüre duyarlı sıralar gerçekleştirir `Thread.CurrentCulture` .</span><span class="sxs-lookup"><span data-stu-id="08388-136">Overloads of the `ArrayList.Sort` method perform culture-sensitive sorts by default using the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="08388-137">Sonuçlar farklı sıralama düzenleri nedeniyle kültüre göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="08388-137">Results can vary by culture due to different sort orders.</span></span> <span data-ttu-id="08388-138">Kültüre duyarlı davranışı ortadan kaldırmak için, bu yöntemin bir uygulamayı kabul eden aşırı yüklerini kullanın `IComparer` .</span><span class="sxs-lookup"><span data-stu-id="08388-138">To eliminate culture-sensitive behavior, use the overloads of this method that accept an `IComparer` implementation.</span></span> <span data-ttu-id="08388-139">Parametresi için `comparer` , tarafından kullanılan özel bir sabit karşılaştırıcı sınıfı belirtin `CultureInfo.InvariantCulture` .</span><span class="sxs-lookup"><span data-stu-id="08388-139">For the `comparer` parameter, specify a custom invariant comparer class that uses `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="08388-140">Özel bir sabit karşılaştırıcı sınıfına bir örnek, [SortedList sınıfını kullanma](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) konusunun içinde verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="08388-140">An example of a custom invariant comparer class is provided in the [Using the SortedList Class](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="08388-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08388-141">See also</span></span>

- <xref:System.Collections.CaseInsensitiveComparer>
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>
- <xref:System.Collections.SortedList>
- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IComparer>
- [<span data-ttu-id="08388-142">Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="08388-142">Performing Culture-Insensitive String Operations</span></span>](performing-culture-insensitive-string-operations.md)
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
