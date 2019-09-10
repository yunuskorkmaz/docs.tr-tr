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
# <a name="performing-culture-insensitive-string-operations-in-collections"></a>Koleksiyonlarda Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme

Ad alanı içinde, <xref:System.Collections> varsayılan olarak kültüre duyarlı davranış sağlayan sınıflar ve Üyeler vardır. <xref:System.Collections.CaseInsensitiveComparer> <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> Ve sınıflarınınparametresizoluşturucuları,özelliğinikullanarakyenibirörneğibaşlatır.<xref:System.Collections.CaseInsensitiveHashCodeProvider> <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> Yönteminin tüm aşırı yüklemeleri, `Thread.CurrentCulture` varsayılan olarak özelliğini kullanarak <xref:System.Collections.Hashtable> sınıfının yeni bir örneğini oluşturur. Metodun aşırı yüklemeleri <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> , kullanarak `Thread.CurrentCulture`varsayılan olarak kültüre duyarlı sıralar gerçekleştirir. Bir <xref:System.Collections.SortedList> içinde sıralama ve arama, dizeler anahtar olarak `Thread.CurrentCulture` kullanıldığında etkilenebilir. Bu sınıftan ve `Collections` ad alanındaki metotlardan kültürden duyarlı sonuçlar almak için bu bölümde belirtilen kullanım önerilerini izleyin.

> [!NOTE]
> Bir <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> karşılaştırma yöntemine geçirilmesi, kültüre duyarsız bir karşılaştırma gerçekleştirir. Ancak, dosya yolları, kayıt defteri anahtarları ve ortam değişkenleri gibi dil olmayan bir karşılaştırmaya neden olmaz. , Karşılaştırma sonucuna göre güvenlik kararlarını desteklemez. Dil olmayan bir karşılaştırma veya sonuç tabanlı güvenlik kararları için destek için, uygulamanın bir <xref:System.StringComparison> değeri kabul eden bir karşılaştırma yöntemi kullanması gerekir. Uygulama daha sonra geçmelidir <xref:System.StringComparison>.

## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a>CaseInsensitiveComparer ve CaseInsensitiveHashCodeProvider sınıflarını kullanma

Parametresiz oluşturucular `CaseInsensitiveHashCodeProvider` , ve `CaseInsensitiveComparer` kullanarak `Thread.CurrentCulture`sınıfının yeni bir örneğini başlatır. Bu, kültüre duyarlı davranışa neden olur. Aşağıdaki kod örneği, ve `Hashtable` `CaseInsensitiveComparer`için `CaseInsensitiveHashCodeProvider` parametresiz oluşturucular kullandığından kültüre duyarlı olan öğesine ilişkin oluşturucuyu gösterir.

```vb
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)
```

```csharp
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);
```

`Hashtable` `culture` Ve sınıflarını`CaseInsensitiveHashCodeProvider` kullanarak kültüre duyarsız bir kültür oluşturmak istiyorsanız, bir parametreyi kabul eden oluşturucuları kullanarak bu sınıfların yeni örneklerini başlatın. `CaseInsensitiveComparer` Parametresi için, belirtin <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. `culture` Aşağıdaki kod örneği, bir kültür duyarlığını `Hashtable`için oluşturucuyu gösterir.

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

Yöntemi, `Hashtable` sınıfının dize durumunu yok sayan yeni bir örneğini oluşturmaya yönelik yararlı bir kısayoldur. `CollectionsUtil.CreateCaseInsensitiveHashTable` Ancak, `CollectionsUtil.CreateCaseInsensitiveHashTable` `Thread.CurrentCulture` özelliği kullandığından, yöntemin tüm aşırı yüklemeleri kültüre duyarlıdır. Bu yöntemi kullanarak kültüre duyarlı `Hashtable` olmayan bir şekilde oluşturamazsınız. Kültüre duyarsız `Hashtable`olması için bir `culture` parametreyi kabul eden `Hashtable` oluşturucuyu kullanın. Parametresi için, belirtin `CultureInfo.InvariantCulture`. `culture` Aşağıdaki kod örneği, bir kültür duyarlığını `Hashtable`için oluşturucuyu gösterir.

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

, Anahtarlar tarafından sıralanan ve anahtar ve dizine göre erişilebilen anahtar ve değer çiftleri koleksiyonunu temsileder.`SortedList` Anahtarlar olduğu yerde dizeler kullandığınızda sıralama ve arama `Thread.CurrentCulture` özelliğinden etkilenebilir. `SortedList` Kültüre duyarsız bir davranış elde etmek için bir `SortedList` `comparer` parametre kabul eden `SortedList` oluşturuculardan birini kullanarak oluşturun. Parametresi `comparer` , anahtarları karşılaştırırken <xref:System.Collections.IComparer> kullanılacak uygulamayı belirtir. Parametresi için, anahtarları karşılaştırmak için kullanan `CultureInfo.InvariantCulture` özel bir karşılaştırıcı sınıfı belirtin. Aşağıdaki örnek, bir `comparer` `SortedList` oluşturucuya parametre olarak belirtebileceğiniz özel bir kültür duyarsız karşılaştırıcı sınıfını göstermektedir.

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

Genel olarak, özel bir sabit karşılaştırıcı `SortedList` belirtmeden dize üzerinde kullanırsanız, liste doldurulduktan sonra yapılan `Thread.CurrentCulture` bir değişiklik listeyi geçersiz kılabilir.

## <a name="using-the-arraylistsort-method"></a>ArrayList. Sort metodunu kullanma

Metodun aşırı yüklemeleri, `Thread.CurrentCulture` özelliği kullanılarak varsayılan olarak kültüre duyarlı sıralar gerçekleştirir. `ArrayList.Sort` Sonuçlar farklı sıralama düzenleri nedeniyle kültüre göre farklılık gösterebilir. Kültüre duyarlı davranışı ortadan kaldırmak için, bu yöntemin bir `IComparer` uygulamayı kabul eden aşırı yüklerini kullanın. Parametresi için, tarafından kullanılan `CultureInfo.InvariantCulture`özel bir sabit karşılaştırıcı sınıfı belirtin. `comparer` Özel bir sabit karşılaştırıcı sınıfına bir örnek, [SortedList sınıfını kullanma](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) konusunun içinde verilmiştir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.CaseInsensitiveComparer>
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>
- <xref:System.Collections.SortedList>
- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IComparer>
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
