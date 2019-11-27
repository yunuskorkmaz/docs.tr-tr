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
# <a name="performing-culture-insensitive-string-operations-in-collections"></a>Koleksiyonlarda Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme

<xref:System.Collections> ad alanında, varsayılan olarak kültüre duyarlı davranış sağlayan sınıflar ve Üyeler vardır. <xref:System.Collections.CaseInsensitiveComparer> ve <xref:System.Collections.CaseInsensitiveHashCodeProvider> sınıflarının parametresiz oluşturucuları <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliğini kullanarak yeni bir örnek başlatır. <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> yönteminin tüm aşırı yüklemeleri, varsayılan olarak `Thread.CurrentCulture` özelliğini kullanarak <xref:System.Collections.Hashtable> sınıfının yeni bir örneğini oluşturur. <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> yönteminin aşırı yüklemeleri, varsayılan olarak `Thread.CurrentCulture`kullanarak kültüre duyarlı sıralar gerçekleştirir. Bir <xref:System.Collections.SortedList> sıralama ve arama, dizeler anahtarlar olarak kullanıldığında `Thread.CurrentCulture` etkileyebilir. `Collections` ad alanındaki bu sınıflardan ve metotlardan kültürden duyarlı sonuçlar almak için bu bölümde belirtilen kullanım önerilerini izleyin.

> [!NOTE]
> Karşılaştırma yöntemine <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> geçirmek, kültüre duyarsız bir karşılaştırma gerçekleştirir. Ancak, dosya yolları, kayıt defteri anahtarları ve ortam değişkenleri gibi dil olmayan bir karşılaştırmaya neden olmaz. , Karşılaştırma sonucuna göre güvenlik kararlarını desteklemez. Dil olmayan bir karşılaştırma veya sonuç tabanlı güvenlik kararları için destek için, uygulamanın <xref:System.StringComparison> değeri kabul eden bir karşılaştırma yöntemi kullanması gerekir. Uygulamanın <xref:System.StringComparison>geçmesi gerekir.

## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a>CaseInsensitiveComparer ve CaseInsensitiveHashCodeProvider sınıflarını kullanma

`CaseInsensitiveHashCodeProvider` ve `CaseInsensitiveComparer` için parametresiz oluşturucular, `Thread.CurrentCulture`kullanarak sınıfının yeni bir örneğini başlatır ve kültüre duyarlı davranışa neden olur. Aşağıdaki kod örneği, `CaseInsensitiveHashCodeProvider` ve `CaseInsensitiveComparer`için parametresiz oluşturucular kullandığından, kültüre duyarlı bir `Hashtable` için olan oluşturucuyu gösterir.

```vb
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)
```

```csharp
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);
```

`CaseInsensitiveComparer` ve `CaseInsensitiveHashCodeProvider` sınıfları kullanarak kültüre duyarsız `Hashtable` oluşturmak istiyorsanız, bir `culture` parametresi kabul eden oluşturucuları kullanarak bu sınıfların yeni örneklerini başlatın. `culture` parametresi için <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>belirtin. Aşağıdaki kod örneği, kültüre duyarsız `Hashtable`için oluşturucuyu gösterir.

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

`CollectionsUtil.CreateCaseInsensitiveHashTable` yöntemi, dizelerin durumunu yok sayan `Hashtable` sınıfının yeni bir örneğini oluşturmaya yönelik faydalı bir kısayoldur. Ancak, `CollectionsUtil.CreateCaseInsensitiveHashTable` yönteminin tüm aşırı yüklemeleri, `Thread.CurrentCulture` özelliğini kullandıkları için kültüre duyarlıdır. Bu yöntemi kullanarak kültüre duyarsız `Hashtable` oluşturamazsınız. Kültüre duyarsız `Hashtable`oluşturmak için bir `culture` parametresi kabul eden `Hashtable` oluşturucusunu kullanın. `culture` parametresi için `CultureInfo.InvariantCulture`belirtin. Aşağıdaki kod örneği, kültüre duyarsız `Hashtable`için oluşturucuyu gösterir.

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

`SortedList` anahtarlar tarafından sıralanan ve anahtar ve dizine göre erişilebilen anahtar ve değer çiftleri koleksiyonunu temsil eder. Dizelerin anahtarlar olduğu bir `SortedList` kullandığınızda, sıralama ve arama `Thread.CurrentCulture` özelliğinden etkilenebilir. `SortedList`kültüre duyarlı olmayan davranış almak için, bir `comparer` parametresi kabul eden oluşturuculardan birini kullanarak bir `SortedList` oluşturun. `comparer` parametresi, anahtarları karşılaştırırken kullanılacak <xref:System.Collections.IComparer> uygulamasını belirtir. Parametresi için, anahtarları karşılaştırmak için `CultureInfo.InvariantCulture` kullanan özel bir karşılaştırıcı sınıfı belirtin. Aşağıdaki örnek, bir `SortedList` oluşturucusuna `comparer` parametresi olarak belirtebileceğiniz özel bir kültür duyarsız karşılaştırıcı sınıfını göstermektedir.

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

Genel olarak, özel bir sabit karşılaştırıcı belirtmeden dizeler üzerinde `SortedList` kullanırsanız, liste doldurulduktan sonra `Thread.CurrentCulture` bir değişiklik listeyi geçersiz kılabilir.

## <a name="using-the-arraylistsort-method"></a>ArrayList. Sort metodunu kullanma

`ArrayList.Sort` yönteminin aşırı yüklemeleri, `Thread.CurrentCulture` özelliğini kullanarak varsayılan olarak kültüre duyarlı sıralar gerçekleştirir. Sonuçlar farklı sıralama düzenleri nedeniyle kültüre göre farklılık gösterebilir. Kültüre duyarlı davranışı ortadan kaldırmak için, bu yöntemin `IComparer` uygulamasını kabul eden aşırı yüklerini kullanın. `comparer` parametresi için `CultureInfo.InvariantCulture`kullanan özel bir sabit karşılaştırıcı sınıfı belirtin. Özel bir sabit karşılaştırıcı sınıfına bir örnek, [SortedList sınıfını kullanma](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) konusunun içinde verilmiştir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.CaseInsensitiveComparer>
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>
- <xref:System.Collections.SortedList>
- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IComparer>
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
