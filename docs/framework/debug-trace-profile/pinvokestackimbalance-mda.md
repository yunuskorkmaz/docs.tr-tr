---
title: pInvokeStackImbalance MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b33a3edc5780ecf07e7809ca327a304d748110f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="pinvokestackimbalance-mda"></a><span data-ttu-id="aa975-102">pInvokeStackImbalance MDA</span><span class="sxs-lookup"><span data-stu-id="aa975-102">pInvokeStackImbalance MDA</span></span>
<span data-ttu-id="aa975-103">`pInvokeStackImbalance` CLR bir platform çağırma sonra çağrı yığını derinlik belirtilen çağırma verilen beklenen Yığın derinliği eşleşmiyor algıladığında yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilirse <xref:System.Runtime.InteropServices.DllImportAttribute> özniteliği yanı sıra Yönetilen imza parametrelerinde bildirimi.</span><span class="sxs-lookup"><span data-stu-id="aa975-103">The `pInvokeStackImbalance` managed debugging assistant (MDA) is activated when the CLR detects that the stack depth after a platform invoke call does not match the expected stack depth, given the calling convention specified in the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute as well as the declaration of the parameters in the managed signature.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa975-104">`pInvokeStackImbalance` MDA yalnızca 32-bit x86 için uygulanan platformlar.</span><span class="sxs-lookup"><span data-stu-id="aa975-104">The `pInvokeStackImbalance` MDA is implemented only for 32-bit x86 platforms.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa975-105">.NET Framework sürüm 3.5, `pInvokeStackImbalance` MDA varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="aa975-105">In the .NET Framework version 3.5, the `pInvokeStackImbalance` MDA is disabled by default.</span></span> <span data-ttu-id="aa975-106">Visual Studio 2005 ile .NET Framework sürüm 3.5 kullandığınızda `pInvokeStackImbalance` MDA görünür **yönetilen hata ayıklama Yardımcıları** listesinde **özel durumları** iletişim kutusu (olduğu durumlarda görüntülenir tıklattığınız **özel durumları** üzerinde **hata ayıklama** menüsü).</span><span class="sxs-lookup"><span data-stu-id="aa975-106">When you use the .NET Framework version 3.5 with Visual Studio 2005, the `pInvokeStackImbalance` MDA will appear in the **Managed Debugging Assistants** list in the **Exceptions** dialog box (which is displayed when you click **Exceptions** on the **Debug** menu).</span></span> <span data-ttu-id="aa975-107">Ancak, seçerek veya temizleyerek **sayıcı** onay kutusunu `pInvokeStackImbalance` etkinleştirmez veya MDA; devre dışı yalnızca Visual Studio MDA etkinleştirildiğinde, bir özel durum oluşturur olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="aa975-107">However, selecting or clearing the **Thrown** check box for `pInvokeStackImbalance` does not enable or disable the MDA; it only controls whether Visual Studio throws an exception when the MDA is activated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="aa975-108">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="aa975-108">Symptoms</span></span>  
 <span data-ttu-id="aa975-109">Bir uygulama, bir erişim ihlali veya yapma veya bir platform aşağıdaki Bozulması çağırma çağrısı bellek karşılaşır.</span><span class="sxs-lookup"><span data-stu-id="aa975-109">An application encounters an access violation or memory corruption when making or following a platform invoke call.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="aa975-110">Sebep</span><span class="sxs-lookup"><span data-stu-id="aa975-110">Cause</span></span>  
 <span data-ttu-id="aa975-111">Platform yönetilen imzası çağırma çağrısı çağrılan yöntem yönetilmeyen imzası eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="aa975-111">The managed signature of the platform invoke call might not match the unmanaged signature of the method being called.</span></span>  <span data-ttu-id="aa975-112">Bu uyuşmazlık parametreleri doğru sayıda bildirme değil veya parametreler için uygun boyutu belirtmeden yönetilen imza neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="aa975-112">This mismatch can be caused by the managed signature not declaring the correct number of parameters or not specifying the appropriate size for the parameters.</span></span>  <span data-ttu-id="aa975-113">Çağırma kuralı büyük olasılıkla tarafından belirtilmediğinden MDA de etkinleştirebilirsiniz <xref:System.Runtime.InteropServices.DllImportAttribute> özniteliği, yönetilmeyen çağırma eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="aa975-113">The MDA can also activate because the calling convention, possibly specified by the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute, does not match the unmanaged calling convention.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="aa975-114">Çözüm</span><span class="sxs-lookup"><span data-stu-id="aa975-114">Resolution</span></span>  
 <span data-ttu-id="aa975-115">Gözden geçirme yönetilen platform imza ve imza ve yerel hedef çağırma kuralının eşleşen onaylamak için çağırma çağırır.</span><span class="sxs-lookup"><span data-stu-id="aa975-115">Review the managed platform invoke signature and calling convention to confirm it matches the signature and calling convention of the native target.</span></span>  <span data-ttu-id="aa975-116">Çağırma kuralı iki yönetilen ve yönetilmeyen tarafta açıkça belirtmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="aa975-116">Try explicitly specifying the calling convention on both the managed and unmanaged sides.</span></span> <span data-ttu-id="aa975-117">Ayrıca değil olarak büyük olasılıkla olsa da, yönetilmeyen işlev yönetilmeyen derleyici hatada gibi diğer bazı nedenle yığının dengesini, mümkündür.</span><span class="sxs-lookup"><span data-stu-id="aa975-117">It is also possible, although not as likely, that the unmanaged function unbalanced the stack for some other reason, such as a bug in the unmanaged compiler.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="aa975-118">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="aa975-118">Effect on the Runtime</span></span>  
 <span data-ttu-id="aa975-119">Zorlar, tüm platform CLR nonoptimized yolu yapılacak çağrıları çağırma.</span><span class="sxs-lookup"><span data-stu-id="aa975-119">Forces all platform invoke calls to take the nonoptimized path in the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="aa975-120">Çıkış</span><span class="sxs-lookup"><span data-stu-id="aa975-120">Output</span></span>  
 <span data-ttu-id="aa975-121">Platform adı MDA mesajıyla Çağırma yığını dengesizliği neden yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="aa975-121">The MDA message gives the name of the platform invoke method call that is causing the stack imbalance.</span></span>  <span data-ttu-id="aa975-122">Bir örnek ileti bir platform çağırma yöntemi çağrıda `SampleMethod` değil:</span><span class="sxs-lookup"><span data-stu-id="aa975-122">A sample message of a platform invoke call on method `SampleMethod` is:</span></span>  
  
```  
A call to PInvoke function 'SampleMethod' has unbalanced the stack.   
This is likely because the managed PInvoke signature does not match   
the unmanaged target signature. Check that the calling convention and   
parameters of the PInvoke signature match the target unmanaged signature.  
```  
  
## <a name="configuration"></a><span data-ttu-id="aa975-123">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="aa975-123">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeStackImbalance />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa975-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aa975-124">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="aa975-125">Yönetilen hata ayıklama Yardımcıları ile hataları tanılama</span><span class="sxs-lookup"><span data-stu-id="aa975-125">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="aa975-126">Birlikte çalışma hazırlama</span><span class="sxs-lookup"><span data-stu-id="aa975-126">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
