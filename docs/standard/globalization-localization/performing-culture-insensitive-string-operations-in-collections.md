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
# <a name="performing-culture-insensitive-string-operations-in-collections"></a>Koleksiyonlarda Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme

<xref:System.Collections>Ad alanı içinde, varsayılan olarak kültüre duyarlı davranış sağlayan sınıflar ve Üyeler vardır. Ve sınıflarının parametresiz oluşturucuları, <xref:System.Collections.CaseInsensitiveComparer> <xref:System.Collections.CaseInsensitiveHashCodeProvider> özelliğini kullanarak yeni bir örneği başlatır <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> . Yönteminin tüm aşırı yüklemeleri <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> <xref:System.Collections.Hashtable> , varsayılan olarak özelliğini kullanarak sınıfının yeni bir örneğini oluşturur `Thread.CurrentCulture` . Metodun aşırı yüklemeleri, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> kullanarak varsayılan olarak kültüre duyarlı sıralar gerçekleştirir `Thread.CurrentCulture` . Bir içinde sıralama ve arama <xref:System.Collections.SortedList> `Thread.CurrentCulture` , dizeler anahtar olarak kullanıldığında etkilenebilir. Bu sınıftan ve ad alanındaki metotlardan kültürden duyarlı sonuçlar almak için bu bölümde belirtilen kullanım önerilerini izleyin `Collections` .

> [!NOTE]
> <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>Bir karşılaştırma yöntemine geçirilmesi, kültüre duyarsız bir karşılaştırma gerçekleştirir. Ancak, dosya yolları, kayıt defteri anahtarları ve ortam değişkenleri gibi dil olmayan bir karşılaştırmaya neden olmaz. , Karşılaştırma sonucuna göre güvenlik kararlarını desteklemez. Dil olmayan bir karşılaştırma veya sonuç tabanlı güvenlik kararları için destek için, uygulamanın bir değeri kabul eden bir karşılaştırma yöntemi kullanması gerekir <xref:System.StringComparison> . Uygulama daha sonra geçmelidir <xref:System.StringComparison> .

## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a>CaseInsensitiveComparer ve CaseInsensitiveHashCodeProvider sınıflarını kullanma

Parametresiz oluşturucular, `CaseInsensitiveHashCodeProvider` ve `CaseInsensitiveComparer` kullanarak sınıfının yeni bir örneğini başlatır. Bu, `Thread.CurrentCulture` kültüre duyarlı davranışa neden olur. Aşağıdaki kod örneği, `Hashtable` ve için parametresiz oluşturucular kullandığından kültüre duyarlı olan öğesine ilişkin oluşturucuyu gösterir `CaseInsensitiveHashCodeProvider` `CaseInsensitiveComparer` .

```vb
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)
```

```csharp
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);
```

Ve sınıflarını kullanarak kültüre duyarsız bir kültür oluşturmak istiyorsanız `Hashtable` `CaseInsensitiveComparer` `CaseInsensitiveHashCodeProvider` , bir parametreyi kabul eden oluşturucuları kullanarak bu sınıfların yeni örneklerini başlatın `culture` . Parametresi için `culture` , belirtin <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> . Aşağıdaki kod örneği, bir kültür duyarlığını için oluşturucuyu gösterir `Hashtable` .

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

## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a>CollectionsUtil. CreateCaseInsensitiveHashTable yöntemini kullanma

`CollectionsUtil.CreateCaseInsensitiveHashTable`Yöntemi, `Hashtable` sınıfının dize durumunu yok sayan yeni bir örneğini oluşturmaya yönelik yararlı bir kısayoldur. Ancak, özelliği kullandığından, yöntemin tüm aşırı yüklemeleri `CollectionsUtil.CreateCaseInsensitiveHashTable` kültüre duyarlıdır `Thread.CurrentCulture` . Bu yöntemi kullanarak kültüre duyarlı olmayan bir şekilde oluşturamazsınız `Hashtable` . Kültüre duyarsız `Hashtable` `Hashtable` olması için bir parametreyi kabul eden oluşturucuyu kullanın `culture` . Parametresi için `culture` , belirtin `CultureInfo.InvariantCulture` . Aşağıdaki kod örneği, bir kültür duyarlığını için oluşturucuyu gösterir `Hashtable` .

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

## <a name="using-the-sortedlist-class"></a>SortedList sınıfını kullanma

`SortedList`, Anahtarlar tarafından sıralanan ve anahtar ve dizine göre erişilebilen anahtar ve değer çiftleri koleksiyonunu temsil eder. `SortedList`Anahtarlar olduğu yerde dizeler kullandığınızda sıralama ve arama `Thread.CurrentCulture` özelliğinden etkilenebilir. Kültüre duyarsız bir davranış elde etmek için bir `SortedList` `SortedList` parametre kabul eden oluşturuculardan birini kullanarak oluşturun `comparer` . `comparer`Parametresi, <xref:System.Collections.IComparer> anahtarları karşılaştırırken kullanılacak uygulamayı belirtir. Parametresi için, anahtarları karşılaştırmak için kullanan özel bir karşılaştırıcı sınıfı belirtin `CultureInfo.InvariantCulture` . Aşağıdaki örnek, bir oluşturucuya parametre olarak belirtebileceğiniz özel bir kültür duyarsız karşılaştırıcı sınıfını göstermektedir `comparer` `SortedList` .

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

Genel olarak, `SortedList` özel bir sabit karşılaştırıcı belirtmeden dize üzerinde kullanırsanız, `Thread.CurrentCulture` liste doldurulduktan sonra yapılan bir değişiklik listeyi geçersiz kılabilir.

## <a name="using-the-arraylistsort-method"></a>ArrayList. Sort metodunu kullanma

Metodun aşırı yüklemeleri, `ArrayList.Sort` özelliği kullanılarak varsayılan olarak kültüre duyarlı sıralar gerçekleştirir `Thread.CurrentCulture` . Sonuçlar farklı sıralama düzenleri nedeniyle kültüre göre farklılık gösterebilir. Kültüre duyarlı davranışı ortadan kaldırmak için, bu yöntemin bir uygulamayı kabul eden aşırı yüklerini kullanın `IComparer` . Parametresi için `comparer` , tarafından kullanılan özel bir sabit karşılaştırıcı sınıfı belirtin `CultureInfo.InvariantCulture` . Özel bir sabit karşılaştırıcı sınıfına bir örnek, [SortedList sınıfını kullanma](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) konusunun içinde verilmiştir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.CaseInsensitiveComparer>
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>
- <xref:System.Collections.SortedList>
- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IComparer>
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](performing-culture-insensitive-string-operations.md)
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
