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
# <a name="pinvokestackimbalance-mda"></a>PInvokeStackImbalance MDA

Yönetilen hata ayıklama Yardımcısı (MDA), clr çağırma çağrısından sonra yığın derinliğini algıladığında etkinleştirilir ve bu, <xref:System.Runtime.InteropServices.DllImportAttribute> özniteliğinde belirtilen çağırma kuralı ve `PInvokeStackImbalance` yönetilen İmzadaki parametrelerin bildirimi.

`PInvokeStackImbalance` MDA yalnızca 32 bit x86 platformları için uygulanır.

> [!NOTE]
> MDA `PInvokeStackImbalance` , varsayılan olarak devre dışıdır. Visual Studio 2017 ' de, `PInvokeStackImbalance` MDA, **özel durum ayarları** iletişim kutusundaki **yönetilen hata ayıklama yardımcıları** listesinde görüntülenir ( **hata ayıklama** > **pencerelerini**  >   **seçtiğinizde görüntülenir Özel durum ayarları**). Ancak, **oluşturulduğunda kesmeyi** seçme veya temizleme onay kutusu, MDA ' ı etkinleştirmez veya devre dışı bırakır. Bu yalnızca, MDA etkinleştirildiğinde Visual Studio 'Nun bir özel durum oluşturulup oluşturulmayacağını denetler.

## <a name="symptoms"></a>Belirtiler

Bir uygulama, bir platform çağırma çağrısını yaparken veya takip edildiğinde bir erişim ihlali veya bellek bozulması ile karşılaşır.

## <a name="cause"></a>Sebep

Platform çağırma çağrısının yönetilen imzası, çağrılan metodun yönetilmeyen imzasıyla eşleşmeyebilir.  Bu uyuşmazlığın nedeni, yönetilen imzanın doğru parametre sayısını bildirmemesi veya parametreler için uygun boyutu belirtmemesidir.  Ayrıca, <xref:System.Runtime.InteropServices.DllImportAttribute> özniteliği tarafından belirtilen çağırma kuralı yönetilmeyen çağrı kuralıyla eşleşmediğinden, MDA da etkinleştirilebilir.

## <a name="resolution"></a>Çözüm

Yönetilen platform çağırma imzasını ve çağırma kuralını inceleyerek yerel hedefin imza ve çağırma kuralına uyduğundan emin olun.  Hem yönetilen hem de yönetilmeyen tarafta çağırma kuralını açıkça belirtmeyi deneyin. Yönetilmeyen işlevin, yönetilmeyen derleyicide oluşan bir hata gibi başka bir nedenle yığına dengesiz olması mümkün olmasa da mümkündür.

## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki

Tüm platform çağırma çağrılarını CLR 'de iyileştirilmemiş olmayan yolu alacak şekilde zorlar.

## <a name="output"></a>Çıkış

MDA iletisi, yığın dengesizlenmesi için yol açan platform çağırma yöntemi çağrısının adını verir. Bir platform çağırma çağrısında `SampleMethod` bir örnek ileti:

**PInvoke işlevi ' SampleMethod ' çağrısı yığına dengesiz. Bu, yönetilen PInvoke imzasının yönetilmeyen hedef imzasıyla eşleşmemesi nedeniyle olasıdır. PInvoke imzasının çağırma kuralı ve parametrelerinin hedef yönetilmeyen imzayla eşleşip eşleştiğinden emin olun.**

## <a name="configuration"></a>Yapılandırma

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../interop/interop-marshaling.md)
