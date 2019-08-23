---
title: İş parçacıklarını yok etme
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
ms.openlocfilehash: 986b4dee17c41928327e7b2672d641bbb8b16f1d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960085"
---
# <a name="destroying-threads"></a>İş parçacıklarını yok etme
Yöntemi <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> , yönetilen bir iş parçacığını kalıcı olarak durdurmak için kullanılır. ' İ çağırdığınızda <xref:System.Threading.Thread.Abort%2A>, ortak dil çalışma zamanı hedef iş <xref:System.Threading.ThreadAbortException> parçacığında hedef iş parçacığının yakalayabileceği bir oluşturur. Daha fazla bilgi için bkz. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.  
  
> [!NOTE]
> Bir iş parçacığı <xref:System.Threading.Thread.Abort%2A> yöntemi çağrıldığında yönetilmeyen kodu yürütüp, çalışma zamanı onu <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>işaretler. Özel durum, iş parçacığı yönetilen koda döndüğünde oluşturulur.  
  
 Bir iş parçacığı iptal edildikten sonra yeniden başlatılamaz.  
  
 Yöntemi, iş parçacığı bir `finally` blokta rastgele miktarda kod <xref:System.Threading.ThreadAbortException> yakalayıp yürütebildiğinden, iş parçacığının hemen durmasına neden olmaz. <xref:System.Threading.Thread.Abort%2A> İş parçacığı sonlanana kadar beklemeniz gerekiyorsa, öğesini çağırabilirsiniz <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> . <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>, iş parçacığı gerçekten yürütmeyi durdurana veya isteğe bağlı bir zaman aşımı aralığı geçtiğinde döndürmeyen bir engelleme çağrıdır. Durdurulan iş parçacığı <xref:System.Threading.Thread.ResetAbort%2A> yöntemi çağırabilir veya bir `finally` blokta sınırsız işlem gerçekleştirebilir, bu nedenle bir zaman aşımı belirtmezseniz, bekleme işleminin bitmesi garanti edilmez.  
  
 Yöntemine yapılan bir çağrıda bekleyen iş parçacıkları, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> çağıran <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>diğer iş parçacıkları tarafından kesintiye uğratılmasını sağlayabilir.  
  
## <a name="handling-threadabortexception"></a>Threadadbortexception işleme  
 İş parçacığınızdan, kendi kodunuzun çağrılması <xref:System.Threading.Thread.Abort%2A> veya iş parçacığının çalıştığı bir uygulama etki alanının kaldırılması sonucu olarak (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> iş parçacıklarını sonlandırmak için kullanılır <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> ), iş parçacığınızdan işlem yapmanız gerekir ve <xref:System.Threading.ThreadAbortException> , aşağıdaki kodda gösterildiği gibi bir `finally` yan tümcede son işlemleri gerçekleştirir.  
  
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
  
 Temizleme kodunuz `catch` yan tümce `finally` <xref:System.Threading.ThreadAbortException> `finally` veya yan tümcesinde olmalıdır, çünkü yan tümcesinin sonunda sistem tarafından yeniden oluşturulur `finally` veya yan tümce yoksa `catch` yan tümcesinin sonunda.  
  
 <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> Yöntemini çağırarak sistemin özel durumu yeniden oluşturmasını engelleyebilirsiniz. Bununla birlikte, bunu yalnızca kendi kodunuz ' a neden <xref:System.Threading.ThreadAbortException>olursa yapmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma](../../../docs/standard/threading/using-threads-and-threading.md)
