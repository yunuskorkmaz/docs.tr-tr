---
title: "Nasıl yapılır: Nesnelerin Yavaş Başlatılmasını Gerçekleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: lazy initialization in .NET, how to perform
ms.assetid: 8cd68620-dcc3-4f20-8835-c728a6820e71
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1728165dbed9a011afe6e621df86be7b372a684f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-perform-lazy-initialization-of-objects"></a>Nasıl yapılır: Nesnelerin Yavaş Başlatılmasını Gerçekleştirme
<xref:System.Lazy%601?displayProperty=nameWithType> Sınıfı geç başlatma ve nesne örneğini oluşturmada gerçekleştirme işlemlerini basitleştirir. Yavaş bir şekilde nesneleri başlatarak bunları hiçbir zaman gerekli ya da ilk erişim kadar kendi başlatma erteleyebilirsiniz hiç oluşturmak zorunda önleyebilirsiniz. Daha fazla bilgi için bkz: [geç başlatma](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir değerle başlatmak gösterilmiştir <xref:System.Lazy%601>. Yavaş değişkeni, ayarlar bazı diğer kod bağlı olarak gerekmeyeceğini değil varsayın `someCondition` değişken true veya false.  
  
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
 Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> sınıfı yalnızca geçerli iş parçacığının geçerli nesne örneğinde görünür olan bir türü başlatılamadı.  
  
 [!code-csharp[CDS#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds2.cs#13)]
 [!code-vb[CDS#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/lazyhowto.vb#13)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.LazyInitializer?displayProperty=nameWithType>  
 [Geç Başlatma](../../../docs/framework/performance/lazy-initialization.md)
