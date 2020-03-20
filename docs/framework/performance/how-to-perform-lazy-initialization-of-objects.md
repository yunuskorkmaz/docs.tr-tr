---
title: 'Nasıl yapılır: Nesnelerin Yavaş Başlatılmasını Gerçekleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, how to perform
ms.assetid: 8cd68620-dcc3-4f20-8835-c728a6820e71
ms.openlocfilehash: d89d19a7a3edb57dcd6c0e37e6688701da8b3713
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180592"
---
# <a name="how-to-perform-lazy-initialization-of-objects"></a>Nasıl yapılır: Nesnelerin Yavaş Başlatılmasını Gerçekleştirme
Sınıf, <xref:System.Lazy%601?displayProperty=nameWithType> nesnelerin tembel başlatılması nı ve anlık olarak gerçekleştirme işini basitleştirir. Nesneleri tembel bir şekilde başharfe alarak, hiç ihtiyaç duyulmamışsa bunları oluşturmak zorunda kalmaktan kaçınabilir veya ilk erişilene kadar başlatmalarını erteleyebilirsiniz. Daha fazla bilgi [için, Lazy Initialization](lazy-initialization.md)bakın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, <xref:System.Lazy%601>bir değerin nasıl başlağlaştırılanın. `someCondition` Değişkeni doğru veya yanlış olarak ayarlayan başka bir koda bağlı olarak, tembel değişkenin gerekli olmayabileceğini varsayalım.  
  
```vb  
Dim someCondition As Boolean = False  
  
Sub Main()  
    'Initializing a value with a big computation, computed in parallel  
    Dim _data As Lazy(Of Integer) = New Lazy(Of Integer)(Function()  
                                                             Dim result =  
                                                                 ParallelEnumerable.Range(0, 1000).  
                                                                 Aggregate(Function(x, y)  
                                                                               Return x + y  
                                                                           End Function)  
                                                             Return result  
                                                         End Function)  
  
    '  do work that may or may not set someCondition to True  
    ' ...  
    '  Initialize the data only if needed  
    If someCondition = True Then  
  
        If (_data.Value > 100) Then  
  
            Console.WriteLine("Good data")  
        End If  
    End If  
End Sub  
```  
  
```csharp  
  static bool someCondition = false;
  //Initializing a value with a big computation, computed in parallel  
  Lazy<int> _data = new Lazy<int>(delegate  
  {  
      return ParallelEnumerable.Range(0, 1000).  
          Select(i => Compute(i)).Aggregate((x,y) => x + y);  
  }, LazyExecutionMode.EnsureSingleThreadSafeExecution);  
  
  // Do some work that may or may not set someCondition to true.  
  //  ...  
  // Initialize the data only if necessary  
  if (someCondition)  
  {  
    if (_data.Value > 100)  
      {  
          Console.WriteLine("Good data");  
      }  
  }  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yalnızca geçerli <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> iş parçacığındaki geçerli nesne örneğinde görünen bir türü başlatmayı yapmak için sınıfın nasıl kullanılacağını gösterir.  
  
 [!code-csharp[CDS#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds2.cs#13)]
 [!code-vb[CDS#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/lazyhowto.vb#13)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.LazyInitializer?displayProperty=nameWithType>
- [Yavaş Başlatma](lazy-initialization.md)
