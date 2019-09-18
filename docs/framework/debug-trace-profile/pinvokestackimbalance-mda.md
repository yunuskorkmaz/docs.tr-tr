---
title: pInvokeStackImbalance MDA
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dc4a48c79fc39b12f8231bd913b4ca8970c0f46f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052361"
---
# <a name="pinvokestackimbalance-mda"></a><span data-ttu-id="962fc-102">PInvokeStackImbalance MDA</span><span class="sxs-lookup"><span data-stu-id="962fc-102">PInvokeStackImbalance MDA</span></span>

<span data-ttu-id="962fc-103">Yönetilen hata ayıklama Yardımcısı (MDA), clr çağırma çağrısından sonra yığın derinliğini algıladığında etkinleştirilir ve bu, <xref:System.Runtime.InteropServices.DllImportAttribute> özniteliğinde belirtilen çağırma kuralı ve `PInvokeStackImbalance` yönetilen İmzadaki parametrelerin bildirimi.</span><span class="sxs-lookup"><span data-stu-id="962fc-103">The `PInvokeStackImbalance` managed debugging assistant (MDA) is activated when the CLR detects that the stack depth after a platform invoke call does not match the expected stack depth, given the calling convention specified in the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute and the declaration of the parameters in the managed signature.</span></span>

<span data-ttu-id="962fc-104">`PInvokeStackImbalance` MDA yalnızca 32 bit x86 platformları için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="962fc-104">The `PInvokeStackImbalance` MDA is implemented only for 32-bit x86 platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="962fc-105">MDA `PInvokeStackImbalance` , varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="962fc-105">The `PInvokeStackImbalance` MDA is disabled by default.</span></span> <span data-ttu-id="962fc-106">Visual Studio 2017 ' de, `PInvokeStackImbalance` MDA, **özel durum ayarları** iletişim kutusundaki **yönetilen hata ayıklama yardımcıları** listesinde görüntülenir ( **hata ayıklama** > **pencerelerini**  >   **seçtiğinizde görüntülenir Özel durum ayarları**).</span><span class="sxs-lookup"><span data-stu-id="962fc-106">In Visual Studio 2017, The `PInvokeStackImbalance` MDA appears in the **Managed Debugging Assistants** list in the **Exception Settings** dialog box (which is displayed when you select **Debug** > **Windows** > **Exception Settings**).</span></span> <span data-ttu-id="962fc-107">Ancak, **oluşturulduğunda kesmeyi** seçme veya temizleme onay kutusu, MDA ' ı etkinleştirmez veya devre dışı bırakır. Bu yalnızca, MDA etkinleştirildiğinde Visual Studio 'Nun bir özel durum oluşturulup oluşturulmayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="962fc-107">However, selecting or clearing the **Break When Thrown** check box does not enable or disable the MDA; it only controls whether Visual Studio throws an exception when the MDA is activated.</span></span>

## <a name="symptoms"></a><span data-ttu-id="962fc-108">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="962fc-108">Symptoms</span></span>

<span data-ttu-id="962fc-109">Bir uygulama, bir platform çağırma çağrısını yaparken veya takip edildiğinde bir erişim ihlali veya bellek bozulması ile karşılaşır.</span><span class="sxs-lookup"><span data-stu-id="962fc-109">An application encounters an access violation or memory corruption when making or following a platform invoke call.</span></span>

## <a name="cause"></a><span data-ttu-id="962fc-110">Sebep</span><span class="sxs-lookup"><span data-stu-id="962fc-110">Cause</span></span>

<span data-ttu-id="962fc-111">Platform çağırma çağrısının yönetilen imzası, çağrılan metodun yönetilmeyen imzasıyla eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="962fc-111">The managed signature of the platform invoke call might not match the unmanaged signature of the method being called.</span></span>  <span data-ttu-id="962fc-112">Bu uyuşmazlığın nedeni, yönetilen imzanın doğru parametre sayısını bildirmemesi veya parametreler için uygun boyutu belirtmemesidir.</span><span class="sxs-lookup"><span data-stu-id="962fc-112">This mismatch can be caused by the managed signature not declaring the correct number of parameters or not specifying the appropriate size for the parameters.</span></span>  <span data-ttu-id="962fc-113">Ayrıca, <xref:System.Runtime.InteropServices.DllImportAttribute> özniteliği tarafından belirtilen çağırma kuralı yönetilmeyen çağrı kuralıyla eşleşmediğinden, MDA da etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="962fc-113">The MDA can also activate because the calling convention, possibly specified by the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute, does not match the unmanaged calling convention.</span></span>

## <a name="resolution"></a><span data-ttu-id="962fc-114">Çözüm</span><span class="sxs-lookup"><span data-stu-id="962fc-114">Resolution</span></span>

<span data-ttu-id="962fc-115">Yönetilen platform çağırma imzasını ve çağırma kuralını inceleyerek yerel hedefin imza ve çağırma kuralına uyduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="962fc-115">Review the managed platform invoke signature and calling convention to confirm it matches the signature and calling convention of the native target.</span></span>  <span data-ttu-id="962fc-116">Hem yönetilen hem de yönetilmeyen tarafta çağırma kuralını açıkça belirtmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="962fc-116">Try explicitly specifying the calling convention on both the managed and unmanaged sides.</span></span> <span data-ttu-id="962fc-117">Yönetilmeyen işlevin, yönetilmeyen derleyicide oluşan bir hata gibi başka bir nedenle yığına dengesiz olması mümkün olmasa da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="962fc-117">It is also possible, although not as likely, that the unmanaged function unbalanced the stack for some other reason, such as a bug in the unmanaged compiler.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="962fc-118">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="962fc-118">Effect on the Runtime</span></span>

<span data-ttu-id="962fc-119">Tüm platform çağırma çağrılarını CLR 'de iyileştirilmemiş olmayan yolu alacak şekilde zorlar.</span><span class="sxs-lookup"><span data-stu-id="962fc-119">Forces all platform invoke calls to take the nonoptimized path in the CLR.</span></span>

## <a name="output"></a><span data-ttu-id="962fc-120">Çıkış</span><span class="sxs-lookup"><span data-stu-id="962fc-120">Output</span></span>

<span data-ttu-id="962fc-121">MDA iletisi, yığın dengesizlenmesi için yol açan platform çağırma yöntemi çağrısının adını verir.</span><span class="sxs-lookup"><span data-stu-id="962fc-121">The MDA message gives the name of the platform invoke method call that is causing the stack imbalance.</span></span> <span data-ttu-id="962fc-122">Bir platform çağırma çağrısında `SampleMethod` bir örnek ileti:</span><span class="sxs-lookup"><span data-stu-id="962fc-122">A sample message of a platform invoke call on method `SampleMethod` is:</span></span>

<span data-ttu-id="962fc-123">**PInvoke işlevi ' SampleMethod ' çağrısı yığına dengesiz. Bu, yönetilen PInvoke imzasının yönetilmeyen hedef imzasıyla eşleşmemesi nedeniyle olasıdır. PInvoke imzasının çağırma kuralı ve parametrelerinin hedef yönetilmeyen imzayla eşleşip eşleştiğinden emin olun.**</span><span class="sxs-lookup"><span data-stu-id="962fc-123">**A call to PInvoke function 'SampleMethod' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="configuration"></a><span data-ttu-id="962fc-124">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="962fc-124">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="962fc-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="962fc-125">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="962fc-126">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="962fc-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="962fc-127">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="962fc-127">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
