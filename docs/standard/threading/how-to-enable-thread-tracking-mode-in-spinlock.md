---
title: "Nasıl yapılır: SpinLock'ta İş Parçacığı İzleme Modunu Etkinleştirme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
ms.openlocfilehash: 83aebc45cdeaa2330c49ef6e90dcbedcd36de6b5
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826462"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a><span data-ttu-id="e648d-102">Nasıl yapılır: SpinLock'ta İş Parçacığı İzleme Modunu Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="e648d-102">How to: Enable Thread-Tracking Mode in SpinLock</span></span>
<span data-ttu-id="e648d-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> , çok kısa bekleme süreleriyle ilgili senaryolar için kullanabileceğiniz alt düzey bir karşılıklı dışlama kilidindedir.</span><span class="sxs-lookup"><span data-stu-id="e648d-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> is a low-level mutual exclusion lock that you can use for scenarios that have very short wait times.</span></span> <span data-ttu-id="e648d-104"><xref:System.Threading.SpinLock> yeniden entrant.</span><span class="sxs-lookup"><span data-stu-id="e648d-104"><xref:System.Threading.SpinLock> is not re-entrant.</span></span> <span data-ttu-id="e648d-105">Bir iş parçacığı kilidi girdikten sonra, yeniden girmeden önce kilidi doğru bir şekilde çıkmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e648d-105">After a thread enters the lock, it must exit the lock correctly before it can enter again.</span></span> <span data-ttu-id="e648d-106">Genellikle kilidi yeniden girmeye yönelik her türlü girişim kilitlenmeye neden olur ve kilitlenmeleri hata ayıklama için çok zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="e648d-106">Typically, any attempt to re-enter the lock would cause deadlock, and deadlocks can be very difficult to debug.</span></span> <span data-ttu-id="e648d-107">Geliştirmeye yardımcı olarak, <xref:System.Threading.SpinLock?displayProperty=nameWithType> bir iş parçacığı zaten tuttuğu bir kilidi yeniden girmeye çalıştığında bir özel durumun oluşturulmasına neden olan bir iş parçacığı izleme modunu destekler.</span><span class="sxs-lookup"><span data-stu-id="e648d-107">As an aid to development, <xref:System.Threading.SpinLock?displayProperty=nameWithType> supports a thread-tracking mode that causes an exception to be thrown when a thread attempts to re-enter a lock that it already holds.</span></span> <span data-ttu-id="e648d-108">Bu, kilidin doğru bir şekilde çıkış yapılmadığını daha kolay bir şekilde bulmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e648d-108">This lets you more easily locate the point at which the lock was not exited correctly.</span></span> <span data-ttu-id="e648d-109"><xref:System.Threading.SpinLock>Bir Boole giriş parametresi alan ve bağımsız değişkenini geçirerek iş parçacığı izleme modunu açabilirsiniz `true` .</span><span class="sxs-lookup"><span data-stu-id="e648d-109">You can turn on thread-tracking mode by using the <xref:System.Threading.SpinLock> constructor that takes a Boolean input parameter, and passing in an argument of `true`.</span></span> <span data-ttu-id="e648d-110">Geliştirme ve test aşamalarını tamamladıktan sonra, daha iyi performans için iş parçacığı izleme modunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="e648d-110">After you complete the development and testing phases, turn off thread-tracking mode for better performance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e648d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="e648d-111">Example</span></span>  
 <span data-ttu-id="e648d-112">Aşağıdaki örnek, iş parçacığı izleme modunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e648d-112">The following example demonstrates thread-tracking mode.</span></span> <span data-ttu-id="e648d-113">Kilitden doğru çıkış yapan satırlar, aşağıdaki sonuçlardan birine neden olan bir kodlama hatasının benzetimini yapmak için açıklama yapılır:</span><span class="sxs-lookup"><span data-stu-id="e648d-113">The lines that correctly exit the lock are commented out to simulate a coding error that causes one of the following results:</span></span>  
  
- <span data-ttu-id="e648d-114"><xref:System.Threading.SpinLock> `true` (Visual Basic) bir bağımsız değişkeni kullanılarak oluşturulduysa bir özel durum oluşturulur `True` .</span><span class="sxs-lookup"><span data-stu-id="e648d-114">An exception is thrown if the <xref:System.Threading.SpinLock> was created by using an argument of `true` (`True` in Visual Basic).</span></span>  
  
- <span data-ttu-id="e648d-115"><xref:System.Threading.SpinLock>Bir bağımsız değişkeni kullanılarak oluşturulduysa `false` ( `False` Visual Basic) kilitlenme.</span><span class="sxs-lookup"><span data-stu-id="e648d-115">Deadlock if the <xref:System.Threading.SpinLock> was created by using an argument of `false` (`False` in Visual Basic).</span></span>  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="e648d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e648d-116">See also</span></span>

- [<span data-ttu-id="e648d-117">SpinLock</span><span class="sxs-lookup"><span data-stu-id="e648d-117">SpinLock</span></span>](spinlock.md)
