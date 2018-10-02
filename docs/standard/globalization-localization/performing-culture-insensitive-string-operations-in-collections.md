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
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48032406"
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a>Koleksiyonlarda Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme
Sınıfları ve üyeleri <xref:System.Collections> varsayılan olarak kültüre duyarlı davranış sağlayan ad alanı. İçin varsayılan oluşturucular <xref:System.Collections.CaseInsensitiveComparer> ve <xref:System.Collections.CaseInsensitiveHashCodeProvider> sınıfları başlatma kullanarak yeni bir örneğini <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği. Tüm aşırı yüklemeler, <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> yöntemi yeni bir örneğini oluşturma <xref:System.Collections.Hashtable> kullanarak `Thread.CurrentCulture` özelliği varsayılan olarak. Overloads biri <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> yöntemi gerçekleştirmek varsayılan kullanarak kültüre duyarlı sıralamaları `Thread.CurrentCulture`. Sıralama ve arama bir <xref:System.Collections.SortedList> etkilenebilir `Thread.CurrentCulture` dizeleri anahtar olarak kullanılan zaman. Bu sınıfları ve yöntemleri kültüre duyarlı olmayan sonuçlar elde etmek için bu bölümde sağlanan kullanım önerilere uyun `Collections` ad alanı.  
  
 **Not** geçirme <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> karşılaştırma yöntemi kültüre duyarsız bir karşılaştırma gerçekleştirir. Ancak, bir dilsel karşılaştırma örneğin dosya yolları, kayıt defteri anahtarları ve ortam değişkenleri için neden olmaz. Karşılaştırma sonucuna dayalı güvenlik kararları diğerinden destekler. Uygulama, bir dilsel karşılaştırma veya sonuç dayalı güvenlik kararları desteği için kabul eden bir karşılaştırma yöntemi kullanmalıdır bir <xref:System.StringComparison> değeri. Uygulama ardından geçmelidir <xref:System.StringComparison>.  
  
## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a>Caseınsensitivecomparer ve Caseınsensitivehashcodeprovider sınıfları kullanma  
 İçin varsayılan oluşturucular `CaseInsensitiveHashCodeProvider` ve `CaseInsensitiveComparer` sınıfı kullanarak yeni bir örneği başlatmak `Thread.CurrentCulture`, sonuçta elde edilen kültüre duyarlı davranış. Aşağıdaki kod örneği için oluşturucu gösteren bir `Hashtable` , kültüre duyarlı için varsayılan oluşturucular kullandığından `CaseInsensitiveHashCodeProvider` ve `CaseInsensitiveComparer`.  
  
```vb  
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)  
```  
  
```csharp  
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);  
```  
  
 Bir kültüre duyarsız oluşturmak istiyorsanız `Hashtable` kullanarak `CaseInsensitiveComparer` ve `CaseInsensitiveHashCodeProvider` sınıfları başlatma kabul oluşturucular kullanarak bu sınıfların yeni örnekleri bir `culture` parametresi. İçin `culture` parametresi belirtin <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Aşağıdaki kod örneği bir kültüre duyarsız Oluşturucusu gösterir `Hashtable`.  
  
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
  
## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a>Collectionsutil.createcaseınsensitivehashtable metodu kullanma  
 `CollectionsUtil.CreateCaseInsensitiveHashTable` Yöntemidir, yeni bir örneğini oluşturmak için yararlı bir kısayol `Hashtable` dizelerinin büyük/küçük harfleri sınıfı. Ancak, tüm aşırı yüklemeler `CollectionsUtil.CreateCaseInsensitiveHashTable` yöntemi kültüre duyarlı kullandıkları için `Thread.CurrentCulture` özelliği. Bir kültüre duyarsız oluşturulamıyor `Hashtable` bu yöntemi kullanarak. Bir kültüre duyarsız oluşturmak için `Hashtable`, kullanın `Hashtable` kabul eden Oluşturucu bir `culture` parametresi. İçin `culture` parametresi belirtin `CultureInfo.InvariantCulture`. Aşağıdaki kod örneği bir kültüre duyarsız Oluşturucusu gösterir `Hashtable`.  
  
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
 A `SortedList` anahtarlara göre sıralanır ve anahtar ve dizin tarafından erişilebilir olan anahtar-değer çifti koleksiyonunu temsil eder. Kullandığınızda, bir `SortedList` dizeleri anahtarların bulunduğu, sıralama ve arama etkilenebilir `Thread.CurrentCulture` özelliği. Kültüre duyarsız davranış elde etmek için bir `SortedList`, oluşturun bir `SortedList` kabul oluşturucular birini kullanarak bir `comparer` parametresi. `comparer` Parametresinin belirttiği <xref:System.Collections.IComparer> anahtarları karşılaştırırken kullanılacak uygulama. Parametresi, kullanan özel bir karşılaştırıcı sınıf belirtin `CultureInfo.InvariantCulture` anahtarları karşılaştırmak için. Aşağıdaki örnek olarak belirleyebileceğiniz bir özel bir karşılaştırıcı kültüre duyarsız sınıfı göstermektedir `comparer` parametresine bir `SortedList` Oluşturucusu.  
  
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
  
 Genel olarak kullanırsanız, bir `SortedList` özel sabit bir karşılaştırıcı olan bir değişiklik belirtmeden dizelerde `Thread.CurrentCulture` listesi doldurulur sonra listenin geçersiz kılabilir.  
  
## <a name="using-the-arraylistsort-method"></a>ArrayList.Sort yöntemi kullanarak  
 Overloads biri `ArrayList.Sort` yöntemi gerçekleştirmek varsayılan kullanarak kültüre duyarlı sıralamaları `Thread.CurrentCulture` özelliği. Sonuçları nedeniyle farklı sıralamalar kültüre göre değişebilir. Kültüre duyarlı davranışı ortadan kaldırmak için kabul eden aşırı yüklemeleri bu yöntemi kullanın. bir `IComparer` uygulaması. İçin `comparer` parametresini kullanan bir özel sabit karşılaştırıcısı sınıfı belirtin `CultureInfo.InvariantCulture`. Sabit özel bir karşılaştırıcı sınıfı örneği sağlanan [SortedList sınıfı kullanarak](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) konu.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.CaseInsensitiveComparer>  
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>  
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>  
- <xref:System.Collections.SortedList>  
- <xref:System.Collections.Hashtable>  
- <xref:System.Collections.IComparer>  
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)  
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
