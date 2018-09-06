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
ms.openlocfilehash: 5cd6e85dca7c4c32361b964573f318b165e8d683
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861175"
---
# <a name="destroying-threads"></a>İş parçacıklarını yok etme
<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> Yöntemi, bir yönetilen iş parçacığı kalıcı olarak durdurmak için kullanılır. Çağırdığınızda <xref:System.Threading.Thread.Abort%2A>, ortak dil çalışma zamanı bir <xref:System.Threading.ThreadAbortException> hedef iş parçacığı, hedef iş parçacığı yakalayabilir. Daha fazla bilgi için bkz. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.  
  
> [!NOTE]
>  Bir iş parçacığı yürütülüyorsa yönetilmeyen kod zaman kendi <xref:System.Threading.Thread.Abort%2A> yöntemi çağrıldığında, çalışma zamanı Bu işaretler <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>. İş parçacığı yönetilen koda geri döndüğünde, özel durum oluşturulur.  
  
 Bir iş parçacığı durduruldu sonra yeniden başlatılamıyor.  
  
 <xref:System.Threading.Thread.Abort%2A> Yöntemi neden olmaz hemen iptal etmek iş parçacığı çünkü hedef iş parçacığı yakalayabilir <xref:System.Threading.ThreadAbortException> ve rastgele miktarda kod yürütme bir `finally` blok. Çağırabilirsiniz <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> iş parçacığının sona erinceye kadar beklenecek gerekiyorsa. <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> yürütme iş parçacığını gerçekten bitirene kadar döndürmeyen engelleyici bir çağrıdır veya isteğe bağlı zaman aşımı aralığı geçti. Durdurulan iş parçacığı çağırabilir <xref:System.Threading.Thread.ResetAbort%2A> yöntemi veya sınırsız yönlendirilmeden bir `finally` engellemek için bir zaman aşımı belirtmezseniz, beklemeyi sona erdirmek için garanti edilmez.  
  
 Çağırması için bekleyen iş parçacıklarının <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> yöntemi çağıran başka iş parçacıklarının engellemelerinden kesintiye <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.  
  
## <a name="handling-threadabortexception"></a>ThreadAbortException işleme  
 İş parçacığınıza, arama sonucu olarak ya da iptal bekliyorsanız <xref:System.Threading.Thread.Abort%2A> kendi kodunuzu veya iş parçacığı çalıştığı uygulama etki alanı kaldırılması sonucunda (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> kullanır <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> iş parçacıkları sonlandırmak için), kendi iş parçacığı işlemesi gerekir <xref:System.Threading.ThreadAbortException> ve herhangi bir son işlem olarak bir `finally` yan tümcesi, aşağıdaki kodda gösterildiği gibi.  
  
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
  
 Temizleme kodunuzun olmalıdır `catch` yan tümcesi veya `finally` yan tümcesi, çünkü bir <xref:System.Threading.ThreadAbortException> sonunda, sistem tarafından tekrar fırlatılan `finally` yan tümcesi ya da sonunda `catch` varsa yan tümcesi yok `finally` yan tümcesi.  
  
 Özel durum gelen yeniden atma çağırarak sistem engelleyebilir <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> yöntemi. Ancak, bu yalnızca, neden kendi kodunuzu yapmalısınız <xref:System.Threading.ThreadAbortException>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 [İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma](../../../docs/standard/threading/using-threads-and-threading.md)
