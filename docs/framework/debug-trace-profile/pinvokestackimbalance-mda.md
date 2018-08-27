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
ms.openlocfilehash: 5594166081c36fbda1e5d1a62e017aaceb7a553d
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42912120"
---
# <a name="pinvokestackimbalance-mda"></a>PInvokeStackImbalance MDA

`PInvokeStackImbalance` Yönetilen hata ayıklama Yardımcısı (MDA) etkin olduğu bir platform çağırma sonra çağrı Yığın derinliği belirtilen çağırma kuralı verilen beklenen Yığın derinliği, eşleşmiyor CLR algıladığında <xref:System.Runtime.InteropServices.DllImportAttribute> özniteliği ve Yönetilen imzayı parametrelerinde bildirimi.

`PInvokeStackImbalance` MDA yalnızca 32-bit x86 için uygulanan platformlar.

> [!NOTE]
> `PInvokeStackImbalance` MDA, varsayılan olarak devre dışıdır. Visual Studio 2017'de `PInvokeStackImbalance` MDA görünür **yönetilen hata ayıklama Yardımcıları** listesinde **özel durum ayarları** iletişim kutusu (belirlediğinizde görüntülenen **hataayıklama**  >  **Windows** > **özel durum ayarları**). Ancak, seçerek veya temizleyerek **Break When Thrown** onay kutusunu etkinleştirmeyin veya MDA devre dışı bırak; yalnızca bir MDA etkinleştirildiğinde, Visual Studio bir özel durum oluşturur olup olmadığını denetler.

## <a name="symptoms"></a>Belirtiler

Bir uygulama, bir erişim ihlali veya çağrı yapma veya bir platform takip Bozulması çağırma bellek karşılaşır.

## <a name="cause"></a>Sebep

Yönetilen imzayı platform çağırma çağrısı yönetilmeyen çağrılan yöntemin imzası eşleşmiyor olabilir.  Bu uyumsuzluk parametreleri doğru sayıda bildirmeyerek veya parametreler için uygun boyutta değil belirterek yönetilen imzayı neden olabilir.  Çağırma kuralı, büyük olasılıkla tarafından belirttiğinden MDA de etkinleştirebilirsiniz <xref:System.Runtime.InteropServices.DllImportAttribute> özniteliği, yönetilmeyen çağırma kuralı ile eşleşmiyor.

## <a name="resolution"></a>Çözüm

Gözden geçirme yönetilen bir platform imzası ve imza ve yerel hedef çağırma kuralının eşleşen onaylamak için çağırma kuralı çağırır.  Çağırma kuralı hem yönetilen hem de yönetilmeyen yüzüne açıkça belirtmeyi deneyin. Ayrıca değil olarak olası olsa da, yönetilmeyen işlev başka bir nedenle, gibi yönetilmeyen derleyici bir hata için yığın dengesiz, mümkündür.

## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi

Zorlar, tüm platform CLR'de nonoptimized yoldan çağrıları çağırma.

## <a name="output"></a>Çıkış

Platformun adını MDA mesajıyla Çağırma yığını dengesizliği neden olan yöntem çağrısı. Bir örnek ileti platform çağırma yöntemi çağrısında `SampleMethod` olan:

**PInvoke 'SampleMethod' işlevine bir çağrı yığını dengesiz. Yönetilen PInvoke imza yönetilmeyen hedef imza eşleşmediği için büyük olasılıkla budur. Çağırma kuralı ve parametreleri PInvoke imza hedef yönetilmeyen imza eşleştiğinden emin olun.**

## <a name="configuration"></a>Yapılandırma

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
