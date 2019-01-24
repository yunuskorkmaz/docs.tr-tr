---
title: contextSwitchDeadlock MDA
ms.date: 03/30/2017
helpviewer_keywords:
- deadlocks [.NET Framework]
- pumping messages
- STA message pumping
- single-threaded COM components
- MDAs (managed debugging assistants), context switching deadlocks
- managed debugging assistants (MDAs), context switching deadlocks
- ContextSwitchDeadlock MDA
- message pumping
- context switching deadlocks
ms.assetid: 26dfaa15-9ddb-4b0a-b6da-999bba664fa6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43404ba24f6308d8da17b03df9997e893799c8d5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643149"
---
# <a name="contextswitchdeadlock-mda"></a>contextSwitchDeadlock MDA

`contextSwitchDeadlock` Denenen bir COM içerik geçişi sırasında karşılıklı bir kilitlenme tespit edildiğinde yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilir.

## <a name="symptoms"></a>Belirtiler

En yaygın yönetilen koddan yönetilmeyen COM bileşeni üzerinde bir çağrı döndürmez belirtisidir.  Zaman içinde artan bellek kullanımı başka bir belirtisidir.

## <a name="cause"></a>Sebep

En olası nedeni, bir tek iş parçacıklı grup (STA) iş parçacığı iletileri Pompalama değil ' dir. STA iş parçacığı Pompalama olmadan ya da bekleyen iletileri veya uzun işlemlerini gerçekleştirme ve ileti kuyruğuna pompa izin vermiyor ' dir.

Zaman içinde artan bellek kullanımı arama girişimi Sonlandırıcı iş parçacığı tarafından neden `Release` bir yönetilmeyen COM bileşeni ve söz konusu bileşen döndürmez.  Bu, sonlandırıcının diğer nesnelerin tekrar kullanılabilir hale engeller.

Varsayılan olarak, Visual Basic konsol uygulamaları ana iş parçacığı için iş parçacığı modeli STA. olur. Bir STA iş parçacığı COM birlikte çalışabilirlik doğrudan veya dolaylı olarak ortak dil çalışma zamanı veya bir üçüncü taraf denetimi kullanıyorsa, bu mda'nın etkin hale gelir.  Bir Visual Basic konsol uygulamasında bu MDA etkinleştirme önlemek için uygulama <xref:System.MTAThreadAttribute> özniteliğini main yöntemine veya iletileri göndermek için değiştirin.

Bu MDA aşağıdaki koşulların tümü karşılandığında, yanlışlıkla etkinleştirilecek mümkündür:

-   Bir uygulama STA iş parçacığı için COM bileşenlerini kitaplıkları doğrudan veya dolaylı olarak oluşturur.

-   Uygulama hata ayıklayıcıda durduruldu ve kullanıcı uygulamanın devam veya adım işlemi gerçekleştirildi.

-   Yönetilemeyen hata ayıklama etkin değil.

MDA yanlışlıkla etkinleştirilip etkinleştirilmediğini belirlemek için tüm kesme noktalarını devre dışı bırakmak, uygulamayı yeniden başlatın ve durmadan çalışmasına izin. MDA etkinleştirilmemesi halinde ilk etkinleştirme false olasıdır. Bu durumda, hata ayıklama oturumu ile önlemek için MDA devre dışı bırakın.

> [!NOTE]
> Bu mda'nın varsayılan Visual Studio için kullanılıyor. Mda'leri devre dışı bırakma hakkında daha fazla bilgi için bkz: [yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).

## <a name="resolution"></a>Çözüm

STA ileti Pompalama ilgili COM kuralları uygulayın.

## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi

Bu mda'nın CLR üzerinde etkisi yoktur. Yalnızca veri COM bağlamları hakkında raporlar.

## <a name="output"></a>Çıkış

Geçerli bağlamı ve hedef bağlamı açıklayan bir ileti.

## <a name="configuration"></a>Yapılandırma

```xml
<mdaConfig>
  <assistants>
    <contextSwitchDeadlock />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
