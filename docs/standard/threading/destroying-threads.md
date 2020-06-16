---
title: İş parçacıklarını yok etme
description: .NET 'teki bir iş parçacığını yok etmeniz gerektiğinde, birlikte çalışırken iptal veya Thread. Abort yöntemi gibi seçeneklerinizi öğrenin. Threadadbortexception işlemesini öğrenin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
ms.openlocfilehash: baf9289413de0e99533f121eb2a404ff0d873511
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768514"
---
# <a name="destroying-threads"></a>İş parçacıklarını yok etme

İş parçacığının yürütülmesini sonlandırmak için genellikle [birlikte bulunan iptal modelini](cancellation-in-managed-threads.md)kullanırsınız. Bazen iş parçacığı işbirliği yapmak mümkün değildir, çünkü birlikte çalışma iptali için tasarlanmamış üçüncü taraf kodu çalıştırır. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.NET Framework yöntemi, yönetilen bir iş parçacığını zorla sonlandırmak için kullanılabilir. <xref:System.Threading.Thread.Abort%2A>' İ çağırdığınızda, ortak dil çalışma zamanı hedef iş parçacığında <xref:System.Threading.ThreadAbortException> hedef iş parçacığının yakalayabileceği bir oluşturur. Daha fazla bilgi için bkz. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Yöntem .NET Core 'da desteklenmez. .NET Core 'da üçüncü taraf kod yürütmeyi zorla sonlandırmak isterseniz, ayrı bir işlemde çalıştırın ve kullanın <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType> .

> [!NOTE]
> Bir iş parçacığı yöntemi çağrıldığında yönetilmeyen kodu yürütüp <xref:System.Threading.Thread.Abort%2A> , çalışma zamanı onu işaretler <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType> . Özel durum, iş parçacığı yönetilen koda döndüğünde oluşturulur.  
  
 Bir iş parçacığı iptal edildikten sonra yeniden başlatılamaz.  
  
 <xref:System.Threading.Thread.Abort%2A>Yöntemi, iş parçacığı <xref:System.Threading.ThreadAbortException> bir blokta rastgele miktarda kod yakalayıp yürütebildiğinden, iş parçacığının hemen durmasına neden olmaz `finally` . <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>İş parçacığı sonlanana kadar beklemeniz gerekiyorsa, öğesini çağırabilirsiniz. <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>, iş parçacığı gerçekten yürütmeyi durdurana veya isteğe bağlı bir zaman aşımı aralığı geçtiğinde döndürmeyen bir engelleme çağrıdır. Durdurulan iş parçacığı <xref:System.Threading.Thread.ResetAbort%2A> yöntemi çağırabilir veya bir blokta sınırsız işlem gerçekleştirebilir, bu `finally` nedenle bir zaman aşımı belirtmezseniz, bekleme işleminin bitmesi garanti edilmez.  
  
 Yöntemine yapılan bir çağrıda bekleyen iş parçacıkları, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> çağıran diğer iş parçacıkları tarafından kesintiye uğratılmasını sağlayabilir <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> .  
  
## <a name="handling-threadabortexception"></a>Threadadbortexception işleme  
 İş parçacığınızdan, <xref:System.Threading.Thread.Abort%2A> kendi kodunuzun çağrılması veya iş parçacığının çalıştığı bir uygulama etki alanının kaldırılması sonucu olarak (iş <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> parçacıklarını sonlandırmak için kullanır), iş parçacığınızdan <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> , <xref:System.Threading.ThreadAbortException> `finally` aşağıdaki kodda gösterildiği gibi, bir yan tümcede herhangi bir son işlem gerçekleştirmesi gerekir.  
  
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
  
 Temizleme kodunuz yan tümce `catch` veya yan tümcesinde olmalıdır `finally` , çünkü <xref:System.Threading.ThreadAbortException> yan tümcesinin sonunda sistem tarafından yeniden oluşturulur veya yan tümce yoksa `finally` `catch` yan tümcesinin sonunda `finally` .  
  
 Yöntemini çağırarak sistemin özel durumu yeniden oluşturmasını engelleyebilirsiniz <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> . Bununla birlikte, bunu yalnızca kendi kodunuz ' a neden olursa yapmanız gerekir <xref:System.Threading.ThreadAbortException> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [Iş parçacıkları ve Iş parçacığı kullanma](using-threads-and-threading.md)
