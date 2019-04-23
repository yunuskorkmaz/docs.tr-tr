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
ms.openlocfilehash: 628790bb8229dc519589c122235f07a38ba57c1c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100242"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="96b7a-102">raceOnRCWCleanup MDA</span><span class="sxs-lookup"><span data-stu-id="96b7a-102">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="96b7a-103">`raceOnRCWCleanup` Yönetilen hata ayıklama Yardımcısı (MDA) ortak dil çalışma zamanı (CLR) algıladığında etkin olduğu bir [çalışma zamanı çağrılabilir sarmalayıcı](../../../docs/framework/interop/runtime-callable-wrapper.md) gibibirkomutkullanarakbunuserbestbırakmakiçinbirçağrıyapıldığında(RCW)kullanılıyor<xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>yöntemi.</span><span class="sxs-lookup"><span data-stu-id="96b7a-103">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="96b7a-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="96b7a-104">Symptoms</span></span>  
 <span data-ttu-id="96b7a-105">Erişim ihlalleri veya Bellek Bozulması sırasında veya sonrasında RCW kullanarak bir boşaltma <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> veya benzer bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="96b7a-105">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="96b7a-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="96b7a-106">Cause</span></span>  
 <span data-ttu-id="96b7a-107">RCW boşaltma iş parçacığı yığınının veya başka bir iş parçacığı üzerinde kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="96b7a-107">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="96b7a-108">Kullanımda olan bir RCW bırakılamıyor.</span><span class="sxs-lookup"><span data-stu-id="96b7a-108">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="96b7a-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="96b7a-109">Resolution</span></span>  
 <span data-ttu-id="96b7a-110">Geçerli ya da diğer iş parçacıklarını kullanımda olabilecek bir RCW boş değil.</span><span class="sxs-lookup"><span data-stu-id="96b7a-110">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="96b7a-111">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="96b7a-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="96b7a-112">Bu mda'nın CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="96b7a-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="96b7a-113">Çıkış</span><span class="sxs-lookup"><span data-stu-id="96b7a-113">Output</span></span>  
 <span data-ttu-id="96b7a-114">Hatayı açıklayan ileti.</span><span class="sxs-lookup"><span data-stu-id="96b7a-114">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="96b7a-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="96b7a-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="96b7a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96b7a-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="96b7a-117">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="96b7a-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="96b7a-118">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="96b7a-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
