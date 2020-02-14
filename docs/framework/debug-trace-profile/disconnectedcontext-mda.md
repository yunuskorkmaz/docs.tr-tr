---
title: disconnectedContext MDA
ms.date: 03/30/2017
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
ms.openlocfilehash: 3d04e304a6b30fe6fd4deeda5a97007f11ee7b13
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216542"
---
# <a name="disconnectedcontext-mda"></a>disconnectedContext MDA
`disconnectedContext` yönetilen hata ayıklama Yardımcısı (MDA), CLR bir COM nesnesiyle ilgili bir istek sunarken, bağlantısı kesilen bir gruba veya içeriğe geçişe çalıştığında etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 [Çalışma zamanında çağrılabilir sarmalayıcı](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) üzerinde yapılan çağrılar, mevcut grubun veya bağlamdaki temel alınan com bileşenine sahip oldukları bir yerine, geçerli grupta veya bağlamda dağıtılır. Bu, tek iş parçacıklı apartman (STA) bileşenlerinde olduğu gibi COM bileşeni çok iş parçacıklı değilse bozulma ve veri kaybına neden olabilir. Alternatif olarak, RCW kendisi bir ara sunucu ise, çağrı, HRESULT RPC_E_WRONG_THREAD bir <xref:System.Runtime.InteropServices.COMException> oluşturmama yol açabilir.  
  
## <a name="cause"></a>Nedeni  
 CLR kendisine geçişe çalıştığında OLE Apartmanı veya bağlamı kapatıldı. Bu en yaygın olarak, grubun sahip olduğu tüm COM bileşenleri tamamen serbest bırakılmadan, bu durum genellikle, bir RCW 'daki kullanıcı kodundan gelen açık çağrının veya CLR 'nin COM bileşenini düzenleme yaptığı sırada gerçekleşebilir. Örneğin, CLR, ilişkili RCW atık olarak toplandığında COM bileşeni serbest bırakıldığında.  
  
## <a name="resolution"></a>Çözüm  
 Bu sorundan kaçınmak için, STA sahip olan iş parçacığının, uygulama, grupta bulunan tüm nesnelerle tamamlanmadan önce sonlandırılmadığından emin olun. Aynı bağlamda geçerlidir; uygulamanın, bağlam içinde yaşayan herhangi bir COM bileşeni ile tamamen bitmeden önce bağlamların kapanmadığından emin olun.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, CLR üzerinde hiçbir etkisi yoktur. Yalnızca bağlantısı kesilen bağlamla ilgili verileri raporlar.  
  
## <a name="output"></a>Çıktı  
 Bağlantısı kesilen grubun veya bağlamın bağlam tanımlama bilgisini raporlar.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../interop/interop-marshaling.md)
