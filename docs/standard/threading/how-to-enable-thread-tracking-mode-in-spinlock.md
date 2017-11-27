---
title: "Nasıl yapılır: SpinLock'ta İş Parçacığı İzleme Modunu Etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca5f1b6eace7a24a6bbb7fd541858246828fa757
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a><span data-ttu-id="b0372-102">Nasıl yapılır: SpinLock'ta İş Parçacığı İzleme Modunu Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b0372-102">How to: Enable Thread-Tracking Mode in SpinLock</span></span>
<span data-ttu-id="b0372-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType>çok kısa bekleme süresini sahip senaryolar için kullanabileceğiniz bir alt düzey karşılıklı dışlama kilidi var.</span><span class="sxs-lookup"><span data-stu-id="b0372-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> is a low-level mutual exclusion lock that you can use for scenarios that have very short wait times.</span></span> <span data-ttu-id="b0372-104"><xref:System.Threading.SpinLock>içe değil.</span><span class="sxs-lookup"><span data-stu-id="b0372-104"><xref:System.Threading.SpinLock> is not re-entrant.</span></span> <span data-ttu-id="b0372-105">Bir iş parçacığı kilidi girdikten sonra yeniden girmeden önce kilidi doğru çıkmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="b0372-105">After a thread enters the lock, it must exit the lock correctly before it can enter again.</span></span> <span data-ttu-id="b0372-106">Genellikle, her türlü girişim kilidi yeniden girmek için kilitlenme neden olur ve kilitlenmeleri hata ayıklamak oldukça zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="b0372-106">Typically, any attempt to re-enter the lock would cause deadlock, and deadlocks can be very difficult to debug.</span></span> <span data-ttu-id="b0372-107">Geliştirme, bir Yardım olarak <xref:System.Threading.SpinLock?displayProperty=nameWithType> bir iş parçacığı zaten tutan bir kilit yeniden girmek çalıştığında durum için bir özel duruma neden olan bir iş parçacığı izleme modunu destekler.</span><span class="sxs-lookup"><span data-stu-id="b0372-107">As an aid to development, <xref:System.Threading.SpinLock?displayProperty=nameWithType> supports a thread-tracking mode that causes an exception to be thrown when a thread attempts to re-enter a lock that it already holds.</span></span> <span data-ttu-id="b0372-108">Bu, daha kolay hangi kilidi doğru bir şekilde çıkıldı değil noktasını bulun sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0372-108">This lets you more easily locate the point at which the lock was not exited correctly.</span></span> <span data-ttu-id="b0372-109">İş parçacığı izleme modunu kullanarak bırakabilir <xref:System.Threading.SpinLock> bir Boole değeri alan oluşturucu giriş parametresi ve bağımsız değişkeninin bilgilerinde `true`.</span><span class="sxs-lookup"><span data-stu-id="b0372-109">You can turn on thread-tracking mode by using the <xref:System.Threading.SpinLock> constructor that takes a Boolean input parameter, and passing in an argument of `true`.</span></span> <span data-ttu-id="b0372-110">İş parçacığı izleme modunu daha iyi performans için geliştirme ve sınama aşaması tamamlandıktan sonra kapatın.</span><span class="sxs-lookup"><span data-stu-id="b0372-110">After you complete the development and testing phases, turn off thread-tracking mode for better performance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0372-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0372-111">Example</span></span>  
 <span data-ttu-id="b0372-112">Aşağıdaki örnek, iş parçacığı izleme modunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b0372-112">The following example demonstrates thread-tracking mode.</span></span> <span data-ttu-id="b0372-113">Doğru kilit çıkış satırları aşağıdaki sonuçları biri neden olan bir kodlama hatası benzetimini yapmak için dışı bırakılır:</span><span class="sxs-lookup"><span data-stu-id="b0372-113">The lines that correctly exit the lock are commented out to simulate a coding error that causes one of the following results:</span></span>  
  
-   <span data-ttu-id="b0372-114">Bir özel durum <xref:System.Threading.SpinLock> bağımsız değişkeninin kullanılarak oluşturulmuş `true` (`True` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="b0372-114">An exception is thrown if the <xref:System.Threading.SpinLock> was created by using an argument of `true` (`True` in Visual Basic).</span></span>  
  
-   <span data-ttu-id="b0372-115">Varsa kilitlenme <xref:System.Threading.SpinLock> bağımsız değişkeninin kullanılarak oluşturulmuş `false` (`False` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="b0372-115">Deadlock if the <xref:System.Threading.SpinLock> was created by using an argument of `false` (`False` in Visual Basic).</span></span>  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="b0372-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b0372-116">See Also</span></span>  
 [<span data-ttu-id="b0372-117">SpinLock</span><span class="sxs-lookup"><span data-stu-id="b0372-117">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)
