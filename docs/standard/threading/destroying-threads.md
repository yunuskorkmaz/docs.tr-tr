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
ms.openlocfilehash: 842ca4ff17f9cbab3a1518d2dea37436c9b23f9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155938"
---
# <a name="destroying-threads"></a>İş parçacıklarını yok etme

İş parçacığının yürütülmesini sonlandırmak için genellikle [kooperatif iptal modelini](cancellation-in-managed-threads.md)kullanırsınız. Bazen bir iş parçacığının kooperatif iptali için tasarlanmadığından, iş parçacığının ortaklaşa durdurulması mümkün değildir. .NET Framework'deki <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> yöntem, yönetilen bir iş parçacığının zorla sonlandırılması için kullanılabilir. Çağrı <xref:System.Threading.Thread.Abort%2A>yaptığınızda, Ortak Dil Çalışma <xref:System.Threading.ThreadAbortException> Zamanı hedef iş parçacığına bir atar ve hedef iş parçacığı yakalayabilir. Daha fazla bilgi için bkz. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. Yöntem <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> .NET Core'da desteklenmez. Üçüncü taraf kodunun yürütülmesini .NET Core'da zorla sonlandırmanız gerekiyorsa, bunu ayrı <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>bir işlemde çalıştırın ve kullanın.

> [!NOTE]
> Bir iş parçacığı, yöntemi çağrıldığında yönetilmeyen kodu çalıştırıyorsa, <xref:System.Threading.Thread.Abort%2A> çalışma zamanı onu <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>işaretler. İş parçacığı yönetilen koda döndüğünde özel durum atılır.  
  
 Bir iş parçacığı iptal edildikten sonra yeniden başlatılamaz.  
  
 Yöntem <xref:System.Threading.Thread.Abort%2A> iş parçacığının hemen iptal ineneden gelmez, çünkü <xref:System.Threading.ThreadAbortException> hedef iş parçacığı bir `finally` bloktaki rasgele kod tutarlarını yakalayabilir ve yürütebilir. İş parçacığı <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> bitene kadar beklemeniz gerekiyorsa arayabilirsiniz. <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>iş parçacığı gerçekten yürütmeyi durdurana veya isteğe bağlı bir zaman aşımı aralığı geçene kadar dönmeyen bir engelleme çağrısıdır. İptal edilen iş parçacığı <xref:System.Threading.Thread.ResetAbort%2A> yöntemi arayabilir veya bir `finally` blokta sınırsız işlem gerçekleştirebilir, bu nedenle bir zaman aşımı belirtmezseniz, beklemenin sona ermesi garanti edilmez.  
  
 Yönteme çağrı beklerken <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> bekleyen iş parçacıkları, '' yi <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>arayan diğer iş parçacıkları tarafından kesilebilir.  
  
## <a name="handling-threadabortexception"></a>ThreadAbortException işleme  
 İş parçacığınızın kendi kodunuzdan arama <xref:System.Threading.Thread.Abort%2A> sonucunda veya iş parçacığının çalıştırıldığı bir uygulama etki alanını boşaltma sı sonucunda<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> (iş parçacığısonlandırmak için <xref:System.Threading.ThreadAbortException> kullanır) olarak, iş `finally` parçacığınızın aşağıdaki kodda gösterildiği gibi bir yan tümcedeki son işlemi işlemesi ve gerçekleştirmesi gerekir.  
  
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
  
 Temizleme kodunuz `catch` yan tümcede veya `finally` yan tümcede olmalıdır, çünkü bir <xref:System.Threading.ThreadAbortException> `finally` yan tümcenin sonundaki `catch` sistem tarafından veya `finally` yan tümcenin sonunda yeniden atılır.  
  
 <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> Yöntemi arayarak sistemin özel durumu yeniden atmasını engelleyebilirsiniz. Ancak, bunu yalnızca kendi kodunuz . <xref:System.Threading.ThreadAbortException>  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [İş Parçacığı ve İş Parçacığı kullanma](../../../docs/standard/threading/using-threads-and-threading.md)
