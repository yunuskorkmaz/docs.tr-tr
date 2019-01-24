---
title: raceOnRCWCleanup MDA
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b2fe4a5a2886fdbbd36ee491ea66dbce353fb034
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717252"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="fa0ed-102">raceOnRCWCleanup MDA</span><span class="sxs-lookup"><span data-stu-id="fa0ed-102">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="fa0ed-103">`raceOnRCWCleanup` Yönetilen hata ayıklama Yardımcısı (MDA) ortak dil çalışma zamanı (CLR) algıladığında etkin olduğu bir [çalışma zamanı çağrılabilir sarmalayıcı](../../../docs/framework/interop/runtime-callable-wrapper.md) gibibirkomutkullanarakbunuserbestbırakmakiçinbirçağrıyapıldığında(RCW)kullanılıyor<xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fa0ed-103">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="fa0ed-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="fa0ed-104">Symptoms</span></span>  
 <span data-ttu-id="fa0ed-105">Erişim ihlalleri veya Bellek Bozulması sırasında veya sonrasında RCW kullanarak bir boşaltma <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> veya benzer bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="fa0ed-105">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="fa0ed-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="fa0ed-106">Cause</span></span>  
 <span data-ttu-id="fa0ed-107">RCW boşaltma iş parçacığı yığınının veya başka bir iş parçacığı üzerinde kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="fa0ed-107">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="fa0ed-108">Kullanımda olan bir RCW bırakılamıyor.</span><span class="sxs-lookup"><span data-stu-id="fa0ed-108">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="fa0ed-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="fa0ed-109">Resolution</span></span>  
 <span data-ttu-id="fa0ed-110">Geçerli ya da diğer iş parçacıklarını kullanımda olabilecek bir RCW boş değil.</span><span class="sxs-lookup"><span data-stu-id="fa0ed-110">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="fa0ed-111">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="fa0ed-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="fa0ed-112">Bu mda'nın CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="fa0ed-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="fa0ed-113">Çıkış</span><span class="sxs-lookup"><span data-stu-id="fa0ed-113">Output</span></span>  
 <span data-ttu-id="fa0ed-114">Hatayı açıklayan ileti.</span><span class="sxs-lookup"><span data-stu-id="fa0ed-114">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="fa0ed-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fa0ed-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fa0ed-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa0ed-116">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="fa0ed-117">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="fa0ed-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="fa0ed-118">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="fa0ed-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
