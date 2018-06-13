---
title: 'Nasıl yapılır: İki Aşamalı bir Bekleme İşlemini Uygulamak için SpinWait Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af6e4e8d0d754b97478788422b4dd84eeddc6491
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583285"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="128df-102">Nasıl yapılır: İki Aşamalı bir Bekleme İşlemini Uygulamak için SpinWait Kullanma</span><span class="sxs-lookup"><span data-stu-id="128df-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="128df-103">Aşağıdaki örnekte nasıl kullanılacağını gösteren bir <xref:System.Threading.SpinWait?displayProperty=nameWithType> aşamalı bir bekleme işlemini uygulamak için nesne.</span><span class="sxs-lookup"><span data-stu-id="128df-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="128df-104">İlk aşamada, eşitleme nesnesi bir `Latch`, kilit kullanılabilir hale olup olmadığını denetlerken birkaç döngüsü boyunca döner.</span><span class="sxs-lookup"><span data-stu-id="128df-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="128df-105">İkinci aşamada kilit kullanılabilir hale gelirse sonra `Wait` yöntemi döndürür kullanmadan <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> kendi bekleyin; gerçekleştirmek için Aksi halde, `Wait` bekleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="128df-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="128df-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="128df-106">Example</span></span>  
 <span data-ttu-id="128df-107">Bu örnek çok basit bir uygulama Mandal eşitleme ilkel gösterir.</span><span class="sxs-lookup"><span data-stu-id="128df-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="128df-108">Bekleme süresini çok kısa olması beklenen olduğunda, bu veri yapısını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="128df-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="128df-109">Bu örnek, yalnızca tanıtım amacıyla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="128df-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="128df-110">Programınıza tutma türü işlevsellik gerektiriyorsa kullanmayı <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="128df-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="128df-111">Mandal kullanan <xref:System.Threading.SpinWait> sonraki çağrısı kadar yalnızca yerinde dönmeye nesne `SpinOnce` neden <xref:System.Threading.SpinWait> iş parçacığının zaman dilimi elde etmek üzere.</span><span class="sxs-lookup"><span data-stu-id="128df-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="128df-112">Bu noktada, Mandal kendi içerik anahtarı çağırarak neden olan <xref:System.Threading.WaitHandle.WaitOne%2A> üzerinde <xref:System.Threading.ManualResetEvent> ve zaman aşımı değerini geri kalanı geçirme.</span><span class="sxs-lookup"><span data-stu-id="128df-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="128df-113">Mandal ne sıklıkta kullanmadan kilit alınırken tarafından performansını artırabilirsiniz günlük çıktısı gösterir <xref:System.Threading.ManualResetEvent>.</span><span class="sxs-lookup"><span data-stu-id="128df-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="128df-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="128df-114">See Also</span></span>  
 [<span data-ttu-id="128df-115">SpinWait</span><span class="sxs-lookup"><span data-stu-id="128df-115">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 [<span data-ttu-id="128df-116">İş Parçacığı Nesneleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="128df-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
