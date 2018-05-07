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
ms.openlocfilehash: c8972a8e9d73adc60e073a5eab9388260c907b68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a>Koleksiyonlarda Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme
Sınıflar ve üyeleri <xref:System.Collections> varsayılan kültüre duyarlı davranışı sağlamak ad alanı. Varsayılan Oluşturucu için <xref:System.Collections.CaseInsensitiveComparer> ve <xref:System.Collections.CaseInsensitiveHashCodeProvider> sınıfları başlatma kullanarak yeni bir örneğini <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği. Tüm aşırı <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> yöntemi yeni bir örneğini oluşturmak <xref:System.Collections.Hashtable> kullanarak sınıfı `Thread.CurrentCulture` özelliği varsayılan olarak. Overloads <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> yöntemi kullanarak varsayılan kültüre duyarlı sıralar gerçekleştirmek `Thread.CurrentCulture`. Sıralama ve arama bir <xref:System.Collections.SortedList> tarafından etkilenen `Thread.CurrentCulture` dizeleri anahtar olarak kullanılan zaman. Bu sınıflar ve yöntemler de kültüre duyarsız sonuçları almak için bu bölümde sağlanan kullanım önerilere uyun `Collections` ad alanı.  
  
 **Not** geçirme <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> karşılaştırma yöntemi kültüre duyarsız bir karşılaştırma işlemini gerçekleştirir. Ancak, bu dile ait olmayan bir karşılaştırma, örneğin, dosya yolları, kayıt defteri anahtarları ve ortam değişkenleri için neden olmaz. Güvenlik kararları karşılaştırma sonucuna desteklemiyor. Dil olmayan karşılaştırma veya sonuç tabanlı güvenlik kararları desteği için uygulama kabul eden bir karşılaştırma yöntemi kullanması gereken bir <xref:System.StringComparison> değeri. Uygulama sonra geçirmelisiniz <xref:System.StringComparison>.  
  
## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a>Caseınsensitivecomparer ve Caseınsensitivehashcodeprovider sınıfları kullanma  
 Varsayılan Oluşturucu için `CaseInsensitiveHashCodeProvider` ve `CaseInsensitiveComparer` sınıfı kullanarak yeni bir örneği başlatmak `Thread.CurrentCulture`, sonuçta elde edilen kültüre duyarlı davranış. Aşağıdaki kod örneğinde Oluşturucusu gösteren bir `Hashtable` olan kültüre duyarlı için varsayılan oluşturucu kullandığından `CaseInsensitiveHashCodeProvider` ve `CaseInsensitiveComparer`.  
  
```vb  
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)  
```  
  
```csharp  
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);  
```  
  
 Bir kültüre duyarsız oluşturmak istiyorsanız `Hashtable` kullanarak `CaseInsensitiveComparer` ve `CaseInsensitiveHashCodeProvider` sınıfları başlatma yeni kabul oluşturucuları kullanarak bu sınıfların örnekleri bir `culture` parametresi. İçin `culture` parametresini belirtin <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Aşağıdaki kod örneğinde bir kültüre duyarsız oluşturucusu gösterilmektedir `Hashtable`.  
  
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
  
## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a>Collectionsutil.createcaseınsensitivehashtable yöntemi kullanılarak  
 `CollectionsUtil.CreateCaseInsensitiveHashTable` Yöntemdir yeni bir örneğini oluşturmak için yararlı bir kısayol `Hashtable` dizeleri küçük büyük harf duyarlı sınıfı. Ancak, tüm overloads `CollectionsUtil.CreateCaseInsensitiveHashTable` yöntemi kültüre duyarlı kullandıkları için `Thread.CurrentCulture` özelliği. Bir kültüre duyarsız oluşturulamıyor `Hashtable` bu yöntemi kullanarak. Bir kültüre duyarsız oluşturmak için `Hashtable`, kullanın `Hashtable` kabul Oluşturucusu bir `culture` parametresi. İçin `culture` parametresini belirtin `CultureInfo.InvariantCulture`. Aşağıdaki kod örneğinde bir kültüre duyarsız oluşturucusu gösterilmektedir `Hashtable`.  
  
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
## <a name="using-the-sortedlist-class"></a>SortedList sınıfı kullanma  
 A `SortedList` anahtarlara göre sıralanır ve anahtar ve dizini tarafından erişilebilir olan anahtar ve değer çiftlerinin koleksiyonunu temsil eder. Kullandığınızda, bir `SortedList` dizeleri anahtarları bulunduğu, sıralama ve arama tarafından etkilenebilir `Thread.CurrentCulture` özelliği. Kültüre duyarsız bir davranış elde etmek için bir `SortedList`, oluşturma bir `SortedList` kabul oluşturucular birini kullanarak bir `comparer` parametresi. `comparer` Parametresi belirtir <xref:System.Collections.IComparer> anahtarları karşılaştırılırken kullanmak için uygulama. Kullanan bir özel karşılaştırıcı sınıfı parametresi için belirlediğiniz `CultureInfo.InvariantCulture` anahtarları karşılaştırmak için. Aşağıdaki örnek olarak belirleyebilirsiniz özel kültüre duyarsız karşılaştırıcı sınıfı gösterilmektedir `comparer` parametresi için bir `SortedList` Oluşturucusu.  
  
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
  
 Genel olarak kullanırsanız, bir `SortedList` özel sabit bir karşılaştırıcı olan bir değişiklik belirtmeden dizelerde `Thread.CurrentCulture` liste doldurulduktan sonra listesi geçersiz kılabilir.  
  
## <a name="using-the-arraylistsort-method"></a>ArrayList.Sort yöntemi kullanma  
 Overloads `ArrayList.Sort` yöntemi kullanarak varsayılan kültüre duyarlı sıralar gerçekleştirmek `Thread.CurrentCulture` özelliği. Sonuçları farklı sıralamalar nedeniyle kültür göre farklılık gösterebilir. Kültüre duyarlı davranışı ortadan kaldırmak için bu yöntemin kabul aşırı kullanmak bir `IComparer` uygulaması. İçin `comparer` parametresini kullanan bir özel değişmez karşılaştırıcı sınıfı belirtin `CultureInfo.InvariantCulture`. Özel sabit karşılaştırıcı sınıfı örneği sağlanan [SortedList sınıfı kullanarak](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) konu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.CaseInsensitiveComparer>  
 <xref:System.Collections.CaseInsensitiveHashCodeProvider>  
 <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Collections.SortedList>  
 <xref:System.Collections.Hashtable>  
 <xref:System.Collections.IComparer>  
 [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)  
 <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
