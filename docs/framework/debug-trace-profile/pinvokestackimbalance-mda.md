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
ms.openlocfilehash: 9ecdfd708217f260b0c02383159fab88948029c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61874217"
---
# <a name="pinvokestackimbalance-mda"></a><span data-ttu-id="faeaf-102">PInvokeStackImbalance MDA</span><span class="sxs-lookup"><span data-stu-id="faeaf-102">PInvokeStackImbalance MDA</span></span>

<span data-ttu-id="faeaf-103">`PInvokeStackImbalance` Yönetilen hata ayıklama Yardımcısı (MDA) etkin olduğu bir platform çağırma sonra çağrı Yığın derinliği belirtilen çağırma kuralı verilen beklenen Yığın derinliği, eşleşmiyor CLR algıladığında <xref:System.Runtime.InteropServices.DllImportAttribute> özniteliği ve Yönetilen imzayı parametrelerinde bildirimi.</span><span class="sxs-lookup"><span data-stu-id="faeaf-103">The `PInvokeStackImbalance` managed debugging assistant (MDA) is activated when the CLR detects that the stack depth after a platform invoke call does not match the expected stack depth, given the calling convention specified in the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute and the declaration of the parameters in the managed signature.</span></span>

<span data-ttu-id="faeaf-104">`PInvokeStackImbalance` MDA yalnızca 32-bit x86 için uygulanan platformlar.</span><span class="sxs-lookup"><span data-stu-id="faeaf-104">The `PInvokeStackImbalance` MDA is implemented only for 32-bit x86 platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="faeaf-105">`PInvokeStackImbalance` MDA, varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="faeaf-105">The `PInvokeStackImbalance` MDA is disabled by default.</span></span> <span data-ttu-id="faeaf-106">Visual Studio 2017'de `PInvokeStackImbalance` MDA görünür **yönetilen hata ayıklama Yardımcıları** listesinde **özel durum ayarları** iletişim kutusu (belirlediğinizde görüntülenen **hataayıklama**  >  **Windows** > **özel durum ayarları**).</span><span class="sxs-lookup"><span data-stu-id="faeaf-106">In Visual Studio 2017, The `PInvokeStackImbalance` MDA appears in the **Managed Debugging Assistants** list in the **Exception Settings** dialog box (which is displayed when you select **Debug** > **Windows** > **Exception Settings**).</span></span> <span data-ttu-id="faeaf-107">Ancak, seçerek veya temizleyerek **Break When Thrown** onay kutusunu etkinleştirmeyin veya MDA devre dışı bırak; yalnızca bir MDA etkinleştirildiğinde, Visual Studio bir özel durum oluşturur olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="faeaf-107">However, selecting or clearing the **Break When Thrown** check box does not enable or disable the MDA; it only controls whether Visual Studio throws an exception when the MDA is activated.</span></span>

## <a name="symptoms"></a><span data-ttu-id="faeaf-108">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="faeaf-108">Symptoms</span></span>

<span data-ttu-id="faeaf-109">Bir uygulama, bir erişim ihlali veya çağrı yapma veya bir platform takip Bozulması çağırma bellek karşılaşır.</span><span class="sxs-lookup"><span data-stu-id="faeaf-109">An application encounters an access violation or memory corruption when making or following a platform invoke call.</span></span>

## <a name="cause"></a><span data-ttu-id="faeaf-110">Sebep</span><span class="sxs-lookup"><span data-stu-id="faeaf-110">Cause</span></span>

<span data-ttu-id="faeaf-111">Yönetilen imzayı platform çağırma çağrısı yönetilmeyen çağrılan yöntemin imzası eşleşmiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="faeaf-111">The managed signature of the platform invoke call might not match the unmanaged signature of the method being called.</span></span>  <span data-ttu-id="faeaf-112">Bu uyumsuzluk parametreleri doğru sayıda bildirmeyerek veya parametreler için uygun boyutta değil belirterek yönetilen imzayı neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="faeaf-112">This mismatch can be caused by the managed signature not declaring the correct number of parameters or not specifying the appropriate size for the parameters.</span></span>  <span data-ttu-id="faeaf-113">Çağırma kuralı, büyük olasılıkla tarafından belirttiğinden MDA de etkinleştirebilirsiniz <xref:System.Runtime.InteropServices.DllImportAttribute> özniteliği, yönetilmeyen çağırma kuralı ile eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="faeaf-113">The MDA can also activate because the calling convention, possibly specified by the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute, does not match the unmanaged calling convention.</span></span>

## <a name="resolution"></a><span data-ttu-id="faeaf-114">Çözüm</span><span class="sxs-lookup"><span data-stu-id="faeaf-114">Resolution</span></span>

<span data-ttu-id="faeaf-115">Gözden geçirme yönetilen bir platform imzası ve imza ve yerel hedef çağırma kuralının eşleşen onaylamak için çağırma kuralı çağırır.</span><span class="sxs-lookup"><span data-stu-id="faeaf-115">Review the managed platform invoke signature and calling convention to confirm it matches the signature and calling convention of the native target.</span></span>  <span data-ttu-id="faeaf-116">Çağırma kuralı hem yönetilen hem de yönetilmeyen yüzüne açıkça belirtmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="faeaf-116">Try explicitly specifying the calling convention on both the managed and unmanaged sides.</span></span> <span data-ttu-id="faeaf-117">Ayrıca değil olarak olası olsa da, yönetilmeyen işlev başka bir nedenle, gibi yönetilmeyen derleyici bir hata için yığın dengesiz, mümkündür.</span><span class="sxs-lookup"><span data-stu-id="faeaf-117">It is also possible, although not as likely, that the unmanaged function unbalanced the stack for some other reason, such as a bug in the unmanaged compiler.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="faeaf-118">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="faeaf-118">Effect on the Runtime</span></span>

<span data-ttu-id="faeaf-119">Zorlar, tüm platform CLR'de nonoptimized yoldan çağrıları çağırma.</span><span class="sxs-lookup"><span data-stu-id="faeaf-119">Forces all platform invoke calls to take the nonoptimized path in the CLR.</span></span>

## <a name="output"></a><span data-ttu-id="faeaf-120">Çıkış</span><span class="sxs-lookup"><span data-stu-id="faeaf-120">Output</span></span>

<span data-ttu-id="faeaf-121">Platformun adını MDA mesajıyla Çağırma yığını dengesizliği neden olan yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="faeaf-121">The MDA message gives the name of the platform invoke method call that is causing the stack imbalance.</span></span> <span data-ttu-id="faeaf-122">Bir örnek ileti platform çağırma yöntemi çağrısında `SampleMethod` olan:</span><span class="sxs-lookup"><span data-stu-id="faeaf-122">A sample message of a platform invoke call on method `SampleMethod` is:</span></span>

<span data-ttu-id="faeaf-123">**PInvoke 'SampleMethod' işlevine bir çağrı yığını dengesiz. Yönetilen PInvoke imza yönetilmeyen hedef imza eşleşmediği için büyük olasılıkla budur. Çağırma kuralı ve parametreleri PInvoke imza hedef yönetilmeyen imza eşleştiğinden emin olun.**</span><span class="sxs-lookup"><span data-stu-id="faeaf-123">**A call to PInvoke function 'SampleMethod' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="configuration"></a><span data-ttu-id="faeaf-124">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="faeaf-124">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="faeaf-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="faeaf-125">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="faeaf-126">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="faeaf-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="faeaf-127">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="faeaf-127">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
