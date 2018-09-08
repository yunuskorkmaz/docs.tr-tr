---
title: "Nasıl yapılır: SpinLock'ta İş Parçacığı İzleme Modunu Etkinleştirme"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3b9671c10889287bc22d64df1fb5c3a2984bd55
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195286"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a><span data-ttu-id="40dee-102">Nasıl yapılır: SpinLock'ta İş Parçacığı İzleme Modunu Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="40dee-102">How to: Enable Thread-Tracking Mode in SpinLock</span></span>
<span data-ttu-id="40dee-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> çok kısa bekleme süresini sahip senaryolar için kullanabileceğiniz bir alt düzey karşılıklı dışlama kilidini olur.</span><span class="sxs-lookup"><span data-stu-id="40dee-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> is a low-level mutual exclusion lock that you can use for scenarios that have very short wait times.</span></span> <span data-ttu-id="40dee-104"><xref:System.Threading.SpinLock> a değil.</span><span class="sxs-lookup"><span data-stu-id="40dee-104"><xref:System.Threading.SpinLock> is not re-entrant.</span></span> <span data-ttu-id="40dee-105">Bir iş parçacığı kilit girdikten sonra yeniden girmeden önce kilit doğru çıkmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="40dee-105">After a thread enters the lock, it must exit the lock correctly before it can enter again.</span></span> <span data-ttu-id="40dee-106">Genellikle, her türlü girişim, kilit yeniden girmek için kilitlenmeye neden olabilir ve kilitlenmeler, hata ayıklamak oldukça zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="40dee-106">Typically, any attempt to re-enter the lock would cause deadlock, and deadlocks can be very difficult to debug.</span></span> <span data-ttu-id="40dee-107">Geliştirmeye yardımcı olarak <xref:System.Threading.SpinLock?displayProperty=nameWithType> bir özel bir iş parçacığı zaten tutan bir kilit znovu girişiminde bulunduğunda durum neden olan bir iş parçacığı izleme modunu destekler.</span><span class="sxs-lookup"><span data-stu-id="40dee-107">As an aid to development, <xref:System.Threading.SpinLock?displayProperty=nameWithType> supports a thread-tracking mode that causes an exception to be thrown when a thread attempts to re-enter a lock that it already holds.</span></span> <span data-ttu-id="40dee-108">Bu, daha kolayca bulun, kilit doğru bir şekilde çıkıldı değil noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="40dee-108">This lets you more easily locate the point at which the lock was not exited correctly.</span></span> <span data-ttu-id="40dee-109">İş parçacığı izleme modunu kullanarak açabilirsiniz <xref:System.Threading.SpinLock> bir Boole değeri alan oluşturucu giriş parametresi ve bir bağımsız değişkeninde geçirme `true`.</span><span class="sxs-lookup"><span data-stu-id="40dee-109">You can turn on thread-tracking mode by using the <xref:System.Threading.SpinLock> constructor that takes a Boolean input parameter, and passing in an argument of `true`.</span></span> <span data-ttu-id="40dee-110">Geliştirme ve test aşamaları tamamladıktan sonra daha iyi performans için iş parçacığı izleme modunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="40dee-110">After you complete the development and testing phases, turn off thread-tracking mode for better performance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40dee-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="40dee-111">Example</span></span>  
 <span data-ttu-id="40dee-112">Aşağıdaki örnek, iş parçacığı izleme modunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="40dee-112">The following example demonstrates thread-tracking mode.</span></span> <span data-ttu-id="40dee-113">Doğru kilit çıkmak satırları aşağıdaki sonuçlardan birini neden olan bir kodlama hatası benzetimini yapmak için dışı bırakılır:</span><span class="sxs-lookup"><span data-stu-id="40dee-113">The lines that correctly exit the lock are commented out to simulate a coding error that causes one of the following results:</span></span>  
  
-   <span data-ttu-id="40dee-114">Bir özel durum <xref:System.Threading.SpinLock> bağımsız değişkeninin kullanılarak oluşturulmuş `true` (`True` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="40dee-114">An exception is thrown if the <xref:System.Threading.SpinLock> was created by using an argument of `true` (`True` in Visual Basic).</span></span>  
  
-   <span data-ttu-id="40dee-115">Kilitlenme <xref:System.Threading.SpinLock> bağımsız değişkeninin kullanılarak oluşturulmuş `false` (`False` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="40dee-115">Deadlock if the <xref:System.Threading.SpinLock> was created by using an argument of `false` (`False` in Visual Basic).</span></span>  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="40dee-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40dee-116">See also</span></span>

- [<span data-ttu-id="40dee-117">SpinLock</span><span class="sxs-lookup"><span data-stu-id="40dee-117">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)
