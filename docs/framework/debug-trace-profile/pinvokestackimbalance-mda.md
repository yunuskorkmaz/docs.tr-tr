---
title: pInvokeStackImbalance MDA
description: Bir platform çağırma çağrısını yaparken veya bu işlem sırasında bir erişim ihlali veya bellek bozulması sırasında etkinleştirilebilen PInvokeStackImbalance MDA öğesini gözden geçirin.
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
ms.openlocfilehash: 89afd3fce3f2a8bffe88d45991ceeb59fc5e5b76
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803670"
---
# <a name="pinvokestackimbalance-mda"></a><span data-ttu-id="68a1d-103">PInvokeStackImbalance MDA</span><span class="sxs-lookup"><span data-stu-id="68a1d-103">PInvokeStackImbalance MDA</span></span>

<span data-ttu-id="68a1d-104">`PInvokeStackImbalance`Yönetilen hata ayıklama Yardımcısı (MDA), clr çağırma çağrısından sonra yığın derinliğini algıladığında, özniteliğinde belirtilen çağırma kuralı <xref:System.Runtime.InteropServices.DllImportAttribute> ve yönetilen İmzadaki parametrelerin bildirimi verildiğinde, beklenen yığın derinliğiyle eşleşmez.</span><span class="sxs-lookup"><span data-stu-id="68a1d-104">The `PInvokeStackImbalance` managed debugging assistant (MDA) is activated when the CLR detects that the stack depth after a platform invoke call does not match the expected stack depth, given the calling convention specified in the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute and the declaration of the parameters in the managed signature.</span></span>

<span data-ttu-id="68a1d-105">`PInvokeStackImbalance`MDA yalnızca 32 bit x86 platformları için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="68a1d-105">The `PInvokeStackImbalance` MDA is implemented only for 32-bit x86 platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="68a1d-106">`PInvokeStackImbalance`MDA, varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="68a1d-106">The `PInvokeStackImbalance` MDA is disabled by default.</span></span> <span data-ttu-id="68a1d-107">Visual Studio 2017 ve sonraki sürümlerinde `PInvokeStackImbalance` MDA, **özel durum ayarları** iletişim kutusundaki **yönetilen hata ayıklama yardımcıları** listesinde görüntülenir ( **Debug**  >  **Windows**  >  **özel durum ayarlarını**hata ayıkla ' yı seçtiğinizde görüntülenir).</span><span class="sxs-lookup"><span data-stu-id="68a1d-107">In Visual Studio 2017 and later versions, the `PInvokeStackImbalance` MDA appears in the **Managed Debugging Assistants** list in the **Exception Settings** dialog box (which is displayed when you select **Debug** > **Windows** > **Exception Settings**).</span></span> <span data-ttu-id="68a1d-108">Ancak, **oluşturulduğunda kesmeyi** seçme veya temizleme onay kutusu, MDA ' ı etkinleştirmez veya devre dışı bırakır. Bu yalnızca, MDA etkinleştirildiğinde Visual Studio 'Nun bir özel durum oluşturulup oluşturulmayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="68a1d-108">However, selecting or clearing the **Break When Thrown** check box does not enable or disable the MDA; it only controls whether Visual Studio throws an exception when the MDA is activated.</span></span>

## <a name="symptoms"></a><span data-ttu-id="68a1d-109">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="68a1d-109">Symptoms</span></span>

<span data-ttu-id="68a1d-110">Bir uygulama, bir platform çağırma çağrısını yaparken veya takip edildiğinde bir erişim ihlali veya bellek bozulması ile karşılaşır.</span><span class="sxs-lookup"><span data-stu-id="68a1d-110">An application encounters an access violation or memory corruption when making or following a platform invoke call.</span></span>

## <a name="cause"></a><span data-ttu-id="68a1d-111">Nedeni</span><span class="sxs-lookup"><span data-stu-id="68a1d-111">Cause</span></span>

<span data-ttu-id="68a1d-112">Platform çağırma çağrısının yönetilen imzası, çağrılan metodun yönetilmeyen imzasıyla eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="68a1d-112">The managed signature of the platform invoke call might not match the unmanaged signature of the method being called.</span></span>  <span data-ttu-id="68a1d-113">Bu uyuşmazlığın nedeni, yönetilen imzanın doğru parametre sayısını bildirmemesi veya parametreler için uygun boyutu belirtmemesidir.</span><span class="sxs-lookup"><span data-stu-id="68a1d-113">This mismatch can be caused by the managed signature not declaring the correct number of parameters or not specifying the appropriate size for the parameters.</span></span>  <span data-ttu-id="68a1d-114">Ayrıca, özniteliği tarafından belirtilen çağırma kuralı <xref:System.Runtime.InteropServices.DllImportAttribute> yönetilmeyen çağrı kuralıyla eşleşmediğinden, MDA da etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="68a1d-114">The MDA can also activate because the calling convention, possibly specified by the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute, does not match the unmanaged calling convention.</span></span>

## <a name="resolution"></a><span data-ttu-id="68a1d-115">Çözüm</span><span class="sxs-lookup"><span data-stu-id="68a1d-115">Resolution</span></span>

<span data-ttu-id="68a1d-116">Yönetilen platform çağırma imzasını ve çağırma kuralını inceleyerek yerel hedefin imza ve çağırma kuralına uyduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="68a1d-116">Review the managed platform invoke signature and calling convention to confirm it matches the signature and calling convention of the native target.</span></span>  <span data-ttu-id="68a1d-117">Hem yönetilen hem de yönetilmeyen tarafta çağırma kuralını açıkça belirtmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="68a1d-117">Try explicitly specifying the calling convention on both the managed and unmanaged sides.</span></span> <span data-ttu-id="68a1d-118">Yönetilmeyen işlevin, yönetilmeyen derleyicide oluşan bir hata gibi başka bir nedenle yığına dengesiz olması mümkün olmasa da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="68a1d-118">It is also possible, although not as likely, that the unmanaged function unbalanced the stack for some other reason, such as a bug in the unmanaged compiler.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="68a1d-119">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="68a1d-119">Effect on the Runtime</span></span>

<span data-ttu-id="68a1d-120">Tüm platform çağırma çağrılarını CLR 'de iyileştirilmemiş olmayan yolu alacak şekilde zorlar.</span><span class="sxs-lookup"><span data-stu-id="68a1d-120">Forces all platform invoke calls to take the nonoptimized path in the CLR.</span></span>

## <a name="output"></a><span data-ttu-id="68a1d-121">Çıktı</span><span class="sxs-lookup"><span data-stu-id="68a1d-121">Output</span></span>

<span data-ttu-id="68a1d-122">MDA iletisi, yığın dengesizlenmesi için yol açan platform çağırma yöntemi çağrısının adını verir.</span><span class="sxs-lookup"><span data-stu-id="68a1d-122">The MDA message gives the name of the platform invoke method call that is causing the stack imbalance.</span></span> <span data-ttu-id="68a1d-123">Bir platform çağırma çağrısında bir örnek ileti `SampleMethod` :</span><span class="sxs-lookup"><span data-stu-id="68a1d-123">A sample message of a platform invoke call on method `SampleMethod` is:</span></span>

<span data-ttu-id="68a1d-124">**PInvoke işlevi ' SampleMethod ' çağrısı yığına dengesiz. Bu, yönetilen PInvoke imzasının yönetilmeyen hedef imzasıyla eşleşmemesi nedeniyle olasıdır. PInvoke imzasının çağırma kuralı ve parametrelerinin hedef yönetilmeyen imzayla eşleşip eşleştiğinden emin olun.**</span><span class="sxs-lookup"><span data-stu-id="68a1d-124">**A call to PInvoke function 'SampleMethod' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="configuration"></a><span data-ttu-id="68a1d-125">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="68a1d-125">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="68a1d-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68a1d-126">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="68a1d-127">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="68a1d-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="68a1d-128">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="68a1d-128">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
