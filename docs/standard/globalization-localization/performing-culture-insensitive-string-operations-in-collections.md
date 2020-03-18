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
# <a name="performing-culture-insensitive-string-operations-in-collections"></a>Koleksiyonlarda Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme

<xref:System.Collections> Ad alanında varsayılan olarak kültüre duyarlı davranış sağlayan sınıflar ve üyeler vardır. Ve sınıflar için parametresiz oluşturucular <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği kullanarak yeni bir örnek başlatılması. <xref:System.Collections.CaseInsensitiveHashCodeProvider> <xref:System.Collections.CaseInsensitiveComparer> Yöntemin <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> tüm aşırı yükleri varsayılan <xref:System.Collections.Hashtable> `Thread.CurrentCulture` olarak özelliği kullanarak sınıfın yeni bir örneği oluşturun. Yöntemin <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> aşırı yükleri varsayılan olarak kültüre duyarlı sıralamaları kullanarak `Thread.CurrentCulture`gerçekleştirir. Bir dizindeki sıralama <xref:System.Collections.SortedList> ve arama, `Thread.CurrentCulture` dizelerin anahtar olarak kullanılmasından etkilenebilir. `Collections` Ad alanında bu sınıflardan ve yöntemlerden kültüre duyarsız sonuçlar almak için bu bölümde sağlanan kullanım önerilerini izleyin.

> [!NOTE]
> Karşılaştırma <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> yöntemine geçmek, kültüre duyarsız bir karşılaştırma yapar. Ancak, dosya yolları, kayıt defteri anahtarları ve ortam değişkenleri gibi dilsel olmayan bir karşılaştırmaya neden olmaz. Karşılaştırma sonucuna göre güvenlik kararlarını da desteklemez. Dilbilimsel olmayan bir karşılaştırma veya sonuç tabanlı güvenlik kararları desteği için, uygulama bir <xref:System.StringComparison> değer kabul eden bir karşılaştırma yöntemi kullanmalıdır. Uygulama daha sonra <xref:System.StringComparison>geçmelidir.

## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a>CaseInsensitiveComparer ve CaseInsensitiveHashCodeProvider Sınıfları kullanma

Parametresiz oluşturucular `CaseInsensitiveHashCodeProvider` için `CaseInsensitiveComparer` ve sınıfın yeni bir örnek `Thread.CurrentCulture`initialize kullanarak , kültüre duyarlı davranış sonuçlanan. Aşağıdaki kod örneği, kültüre duyarlı `Hashtable` bir yapının oluşturucuyu gösterir, çünkü parametresiz oluşturucuları `CaseInsensitiveHashCodeProvider` ve . `CaseInsensitiveComparer`

```vb
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)
```

```csharp
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);
```

Ve `CaseInsensitiveComparer` `CaseInsensitiveHashCodeProvider` sınıfları kullanarak kültüre `Hashtable` duyarsız bir `culture` oluşturmak istiyorsanız, parametre kabul eden oluşturucuları kullanarak bu sınıfların yeni örneklerini başharfe indirin. Parametre `culture` için. <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> Aşağıdaki kod örneği, kültüre duyarsız `Hashtable`bir yapının oluşturucuyu gösterir.

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

## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a>CollectionsUtil.CreateCaseInsensitiveHashTable Yöntemini Kullanma

Yöntem, `CollectionsUtil.CreateCaseInsensitiveHashTable` `Hashtable` dizeleri durumda yoksaçan sınıfın yeni bir örnek oluşturmak için yararlı bir kısayol. Ancak, yöntemin `CollectionsUtil.CreateCaseInsensitiveHashTable` tüm aşırı yükleri, `Thread.CurrentCulture` özelliği kullandıkları için kültüre duyarlıdır. Bu yöntemi kullanarak kültüre `Hashtable` duyarsız bir şey oluşturamazsınız. Kültüre duyarsız `Hashtable`bir şey oluşturmak `Hashtable` için, parametre `culture` kabul eden oluşturucuyu kullanın. Parametre `culture` için. `CultureInfo.InvariantCulture` Aşağıdaki kod örneği, kültüre duyarsız `Hashtable`bir yapının oluşturucuyu gösterir.

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

## <a name="using-the-sortedlist-class"></a>SıralanmışListe Sınıfını Kullanma

A, `SortedList` anahtarlara göre sıralanan ve anahtar ve dizin tarafından erişilebilen anahtar ve değer çiftleri koleksiyonunu temsil eder. Dizelerin `SortedList` anahtarlar olduğu bir yerde kullandığınızda, sıralama ve arama `Thread.CurrentCulture` özelliğinden etkilenebilir. Kültüre duyarsız davranış elde `SortedList`etmek için, bir `SortedList` `comparer` parametre kabul eden yapıcılardan birini kullanarak oluşturun. `comparer` Parametre, anahtarları karşılaştırırken kullanılacak <xref:System.Collections.IComparer> uygulamayı belirtir. Parametre için, anahtarları karşılaştırmak için `CultureInfo.InvariantCulture` kullanan özel bir karşılayıcı sınıf belirtin. Aşağıdaki örnek, bir `comparer` `SortedList` oluşturucuiçin parametre olarak belirtebileceğiniz özel bir kültüre duyarlı olmayan karşılandırıcı sınıf göstermektedir.

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

Genel olarak, özel `SortedList` bir değişmez karşılayıcı belirtmeden dizeleri üzerinde kullanırsanız, liste doldurulan sonra bir `Thread.CurrentCulture` değişiklik liste geçersiz olabilir.

## <a name="using-the-arraylistsort-method"></a>ArrayList.Sort Yöntemini Kullanma

`ArrayList.Sort` Yöntemin aşırı yükleri `Thread.CurrentCulture` özelliği kullanarak varsayılan olarak kültüre duyarlı sıralamaları gerçekleştirir. Sonuçlar, farklı sıralama emirlerine bağlı olarak kültüre göre değişebilir. Kültüre duyarlı davranışı ortadan kaldırmak için, bir `IComparer` uygulamayı kabul eden bu yöntemin aşırı yüklerini kullanın. Parametre `comparer` için, kullanan özel değişmez karşılayıcı `CultureInfo.InvariantCulture`sınıf belirtin. [Sıralanmış Liste Sınıfını Kullanma](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) konusu'nda özel değişmez karşılayıcı sınıfının bir örneği sağlanır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.CaseInsensitiveComparer>
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>
- <xref:System.Collections.SortedList>
- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IComparer>
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
