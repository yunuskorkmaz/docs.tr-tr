---
title: contextSwitchDeadlock MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "22"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e67c5c47dbe95d7c2b804f0ae87200db489d0306
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="contextswitchdeadlock-mda"></a>contextSwitchDeadlock MDA
`contextSwitchDeadlock` Yönetilen hata ayıklama Yardımcısı (MDA) bir kilitlenme denenen COM içerik geçişi sırasında algılandığında etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Yönetilen koddan yönetilmeyen bir COM bileşeni üzerinde bir çağrı döndürmez en yaygın belirti olmasıdır.  Başka bir belirti zaman içerisinde arttığını bellek kullanımı olmasıdır.  
  
## <a name="cause"></a>Sebep  
 Tek iş parçacıklı (STA) iş parçacığı iletileri Pompalama değil en olası nedeni oluşturur. STA iş parçacığı Pompalama olmadan ya da bekleme iletileri veya uzun işlemlerini gerçekleştirme ve pompa ileti kuyruğuna izin vermeyen ' dir.  
  
 Çağrı girişimi sonlandırıcıyı iş parçacığı tarafından zaman içerisinde arttığını bellek kullanımı nedeniyle `Release` yönetilmeyen bir COM bileşeni ve bu bileşeni döndürmez.  Bu, diğer nesneleri geri kazanma sonlandırıcıyı önler.  
  
 Varsayılan olarak, Visual Basic konsol uygulamaları ana iş parçacığı için iş parçacığı modelini STA şeklindedir. STA iş parçacığı COM birlikte çalışabilirliği doğrudan veya dolaylı olarak ortak dil çalışma zamanı veya bir üçüncü taraf denetim kullanıyorsa, bu MDA etkinleştirilir.  Visual Basic konsol uygulamasındaki bu MDA etkinleştirmeyi önlemek için uygulama <xref:System.MTAThreadAttribute> özniteliği main yöntemini veya pompa iletileri uygulamaya değiştirin.  
  
 Aşağıdaki koşulların hepsi gerçekleştiğinde yanlışlıkla etkinleştirilmesi ya da MDA mümkündür:  
  
-   Uygulama COM bileşenlerini STA iş parçacıklarından kitaplıkları doğrudan veya dolaylı olarak oluşturur.  
  
-   Uygulama Hata Ayıklayıcısı'ndaki durduruldu ve kullanıcı uygulamayı devam veya bir adım işlemi gerçekleştirilir.  
  
-   Yönetilmeyen hata ayıklama etkin değil.  
  
 MDA yanlışlıkla etkinleştirilip etkinleştirilmediğini belirlemek için tüm kesme noktaları devre dışı bırakmak, uygulamayı yeniden başlatın ve durmadan çalışmasına izin verin. MDA etkinleştirilmemişse, ilk etkinleştirme false olasıdır. Bu durumda, mda'sı ile hata ayıklama oturumu önlemek için devre dışı bırakın.  
  
> [!NOTE]
>  Bu mda'sı için varsayılan olarak [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] ve sonraki sürümler. İçinde barındırma işlemi etkinleştirildiğinde [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], varsayılan olarak ayarlanmış olan Mda'lar devre dışı bırakılamıyor. Barındırma işlemi varsayılan olarak etkindir, bu nedenle açıkça devre dışı bırakılması gerekir. Mda'lar devre dışı bırakma hakkında daha fazla bilgi için bkz: "Mda'lar etkinleştirme ve devre dışı bırakma" [yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="resolution"></a>Çözüm  
 STA ileti Pompalama ilgili COM kuralları izleyin.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA CLR üzerinde etkisi yoktur. Yalnızca veri COM bağlamları hakkında raporlar.  
  
## <a name="output"></a>Çıkış  
 Geçerli içerik ve hedef bağlamı açıklayan bir ileti.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <contextSwitchDeadlock />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte çalışma hazırlama](../../../docs/framework/interop/interop-marshaling.md)
