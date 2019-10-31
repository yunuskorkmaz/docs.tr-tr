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
ms.openlocfilehash: 1852135e9b7f48d6556e27f16819ddd48805af21
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138087"
---
# <a name="destroying-threads"></a>İş parçacıklarını yok etme
<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> yöntemi, yönetilen bir iş parçacığını kalıcı olarak durdurmak için kullanılır. <xref:System.Threading.Thread.Abort%2A>çağırdığınızda, ortak dil çalışma zamanı hedef iş parçacığında hedef iş parçacığının yakalayabileceği bir <xref:System.Threading.ThreadAbortException> oluşturur. Daha fazla bilgi için bkz. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.  
  
> [!NOTE]
> Bir iş parçacığı <xref:System.Threading.Thread.Abort%2A> yöntemi çağrıldığında yönetilmeyen kodu yürütüp, çalışma zamanı <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>işaretler. Özel durum, iş parçacığı yönetilen koda döndüğünde oluşturulur.  
  
 Bir iş parçacığı iptal edildikten sonra yeniden başlatılamaz.  
  
 Hedef iş parçacığı <xref:System.Threading.ThreadAbortException> yakalayıp `finally` bloğunda rastgele miktarda kod yürütebildiğinden <xref:System.Threading.Thread.Abort%2A> yöntemi iş parçacığının hemen iptal edilmesini sağlamaz. İş parçacığı sonlanana kadar beklemeniz gerekiyorsa <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> çağırabilirsiniz. <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>, iş parçacığı gerçekten yürütmeyi durdurana veya isteğe bağlı bir zaman aşımı aralığı geçtiğinde döndürmeyen bir engelleme çağrıdır. Durdurulan iş parçacığı <xref:System.Threading.Thread.ResetAbort%2A> yöntemi çağırabilir veya bir `finally` bloğunda sınırsız işlem gerçekleştirebilir, bu nedenle bir zaman aşımı belirtmezseniz, bekleme işleminin bitmesi garanti edilmez.  
  
 <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> yöntemine yapılan bir çağrıda bekleyen iş parçacıkları, <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>çağıran diğer iş parçacıkları tarafından kesintiye uğrar.  
  
## <a name="handling-threadabortexception"></a>Threadadbortexception işleme  
 İş parçacığınızdan, kendi kodunuzun <xref:System.Threading.Thread.Abort%2A> çağrılması veya iş parçacığının çalıştığı bir uygulama etki alanının kaldırılması sonucu olarak (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> iş parçacıklarını sonlandırmak için <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> kullanıyorsa) , iş parçacığın <xref:System.Threading.ThreadAbortException> işlemesi ve aşağıdaki kodda gösterildiği gibi `finally` yan tümcesinde son işlemleri gerçekleştirmesi gerekir.  
  
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
  
 `finally` yan tümcesinin sonunda veya `catch` yan tümcesi yoksa `finally` yan tümcesinin sonunda bir <xref:System.Threading.ThreadAbortException> yeniden oluşturulduğu için, temizleme kodunuzun `catch` yan tümcesinde veya `finally` yan tümcesinde olması gerekir.  
  
 <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> yöntemini çağırarak sistemin özel durumu yeniden oluşturmasını engelleyebilirsiniz. Ancak, bunu yalnızca kendi kodunuz <xref:System.Threading.ThreadAbortException>neden olduysa yapmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma](../../../docs/standard/threading/using-threads-and-threading.md)
