---
title: contextSwitchDeadlock MDA
description: Bir COM bağlam geçişi sırasında kilitlenme algılandığında etkinleştirilen, .NET 'teki Contextswitchkilitlenme yönetilen hata ayıklama Yardımcısı (MDA) hakkında bilgi edinin.
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
ms.openlocfilehash: 52db4f2c88bac4e8cac621cca989fa10acb43f94
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416024"
---
# <a name="contextswitchdeadlock-mda"></a>contextSwitchDeadlock MDA

`contextSwitchDeadlock`Yönetilen hata ayıklama Yardımcısı (MDA), denenen BIR com bağlam geçişi sırasında bir kilitlenme algılandığında etkinleştirilir.

## <a name="symptoms"></a>Belirtiler

En yaygın belirti, yönetilmeyen bir COM bileşenindeki bir çağrının yönetilen koddan döndürülmeidir.  Başka bir belirti, zaman içinde artan bellek kullanımdır.

## <a name="cause"></a>Nedeni

En olası neden, tek iş parçacıklı bir apartman (STA) iş parçacığının ileti pompalama. STA iş parçacığı, pompalama iletileri olmadan bekliyor ya da uzun işlemler gerçekleştiriyor ve ileti sırasının göndericmesine izin vermiyor.

Zaman içinde artan bellek kullanımı, `Release` yönetilmeyen BIR COM bileşenini çağırmaya çalışan ve bu bileşen döndürülmeyen Sonlandırıcı iş parçacığı nedeniyle oluşur.  Bu, sonlandırıcının geri kazanma diğer nesnelerden yapılmasını önler.

Varsayılan olarak, Visual Basic konsol uygulamalarının ana iş parçacığı için iş parçacığı modeli STA ' dır. Bir STA iş parçacığı ortak dil çalışma zamanı veya üçüncü taraf bir denetim aracılığıyla doğrudan veya dolaylı olarak COM birlikte çalışabilirliği kullanıyorsa, bu MDA etkinleştirilir.  Bu MDA öğesini bir Visual Basic konsol uygulamasında etkinleştirmeyi önlemek için, <xref:System.MTAThreadAttribute> özniteliği Main yöntemine uygulayın veya uygulamayı pompa iletileri olarak değiştirin.

Aşağıdaki koşulların tümü karşılandığında bu MDA 'ın daha seyrek etkinleştirilmesi mümkündür:

- Uygulama, doğrudan veya dolaylı olarak kitaplıklar aracılığıyla STA iş parçacıklarında COM bileşenleri oluşturur.

- Uygulama hata ayıklayıcıda durduruldu ve Kullanıcı uygulamayı devam ettirdi ya da bir adım işlemi gerçekleştirdi.

- Yönetilmeyen hata ayıklama etkin değil.

MDA 'ın daha seyrek olarak etkinleştirildiğini anlamak için, tüm kesme noktalarını devre dışı bırakın, uygulamayı yeniden başlatın ve durmadan çalışmasına izin verin. MDA etkinleştirilmemişse, ilk etkinleştirmenin yanlış olması olasıdır. Bu durumda, hata ayıklama oturumunda parazit önlemek için MDA ' ı devre dışı bırakın.

> [!NOTE]
> Bu MDA, Visual Studio için varsayılan kümesidir. MDAs 'yi devre dışı bırakma hakkında daha fazla bilgi için bkz. [yönetilen hata ayıklama yardımcıları Ile hataları tanılama](diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).

## <a name="resolution"></a>Çözüm

STA iletisi pompalama ile ilgili COM kurallarını izleyin.

## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki

Bu MDA, CLR üzerinde hiçbir etkisi yoktur. Yalnızca COM bağlamlarına ilişkin verileri raporlar.

## <a name="output"></a>Çıktı

Geçerli bağlamı ve hedef bağlamını açıklayan bir ileti.

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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma Hazırlama](../interop/interop-marshaling.md)
