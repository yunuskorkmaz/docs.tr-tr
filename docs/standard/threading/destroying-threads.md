---
title: İş Parçacıklarını Yok Etme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e6eff0caa76349ce441a662428e37e25e2a6518
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582951"
---
# <a name="destroying-threads"></a>İş Parçacıklarını Yok Etme
<xref:System.Threading.Thread.Abort%2A> Yöntemi yönetilen iş parçacığı kalıcı olarak durdurmak için kullanılır. Çağırdığınızda <xref:System.Threading.Thread.Abort%2A>, ortak dil çalışma zamanı oluşturur bir <xref:System.Threading.ThreadAbortException> hedef iş parçacığı yakalayabilir hedef iş parçacığında. Daha fazla bilgi için bkz. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.  
  
> [!NOTE]
>  Bir iş parçacığı çalıştırıldığında yönetilmeyen ne zaman kod kendi <xref:System.Threading.Thread.Abort%2A> yöntemi çağrıldığında, çalışma zamanı Bu işaretler <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>. İş parçacığı için yönetilen kodu döndürdüğünde özel durum oluşur.  
  
 Bir iş parçacığı durduruldu sonra yeniden başlatılamıyor.  
  
 <xref:System.Threading.Thread.Abort%2A> Yöntemi neden olmaz hemen durdurmak iş parçacığı hedef iş parçacığı yakalayabilir çünkü <xref:System.Threading.ThreadAbortException> ve kodda rasgele miktarda yürütme bir `finally` bloğu. Çağırabilirsiniz <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> iş parçacığı sona erinceye kadar bekleyin gerekiyorsa. <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> iş parçacığı yürütülmesi gerçekte durdurulana kadar döndürmeyen bir engelleme çağrısı veya bir isteğe bağlı zaman aşımı aralığı geçti. Durdurulan iş parçacığı çağırabilirsiniz <xref:System.Threading.Thread.ResetAbort%2A> yöntemi veya sınırsız yönlendirilmeden bir `finally` engellemek için zaman aşımı belirtmezseniz beklemeyi sona erdirmek için kesin değildir.  
  
 Çağrı sırasında bekleyen iş parçacığı <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> yöntemini çağıran başka bir iş parçacığı tarafından kesintiye <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.  
  
## <a name="handling-threadabortexception"></a>ThreadAbortException işleme  
 İş parçacığı, arama sonucu olarak da durdurulacak bekliyorsanız <xref:System.Threading.Thread.Abort%2A> kendi kodunuzu veya iş parçacığı çalışıyor uygulama etki alanı kaldırılması sonucunda (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> kullanan <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> iş parçacığı sonlandırmak için), iş parçacığı işlemesi gerekir <xref:System.Threading.ThreadAbortException> ve tüm son yönlendirilmeden bir `finally` aşağıdaki kodda gösterildiği gibi yan tümcesi.  
  
```vb  
Try  
    ' Code that is executing when the thread is aborted.  
Catch ex As ThreadAbortException  
    ' Clean-up code can go here.  
    ' If there is no Finally clause, ThreadAbortException is  
    ' re-thrown by the system at the end of the Catch clause.   
Finally  
    ' Clean-up code can go here.  
End Try  
' Do not put clean-up code here, because the exception   
' is rethrown at the end of the Finally clause.  
```  
  
```csharp  
try   
{  
    // Code that is executing when the thread is aborted.  
}   
catch (ThreadAbortException ex)   
{  
    // Clean-up code can go here.  
    // If there is no Finally clause, ThreadAbortException is  
    // re-thrown by the system at the end of the Catch clause.   
}  
// Do not put clean-up code here, because the exception   
// is rethrown at the end of the Finally clause.  
```  
  
 Temizleme kodunuzun olmalıdır `catch` yan tümcesi veya `finally` yan tümcesi, çünkü bir <xref:System.Threading.ThreadAbortException> sonunda sistem tarafından işlenemezse `finally` yan tümcesi veya sonunda `catch` varsa yan tümcesi yok `finally` yan tümcesi.  
  
 Özel durum gelen yeniden atma çağırarak sistem engelleyebilirsiniz <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> yöntemi. Ancak, bu yalnızca, kendi kodunuzu neden yapmalısınız <xref:System.Threading.ThreadAbortException>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 [İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma](../../../docs/standard/threading/using-threads-and-threading.md)
