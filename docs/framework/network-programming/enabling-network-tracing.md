---
title: Ağ İzlemeyi Etkinleştirme
description: .NET Framework yönetilen bir uygulama için yöntem etkinleştirmeleri ve ağ trafiği hakkında bilgi sağlayan ağ izlemeyi nasıl etkinleştirebileceğinizi öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- trace destinations
- sending traces to log file
- trace listeners, network tracing
- network tracing, enabling
- CLR Debugger
- default listeners
- logs, trace
- destination for tracing output
ms.assetid: 5fff458c-51a6-4134-ba47-8a6137ddc41e
ms.openlocfilehash: 246a975ead3cb9c1acb4fe0512dfa91d1b8a00c0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287429"
---
# <a name="enabling-network-tracing"></a>Ağ İzlemeyi Etkinleştirme

Ağ izleme, yönetilen bir uygulama tarafından oluşturulan Yöntem çağrıları ve ağ trafiği hakkındaki bilgilere erişim sağlar. Uygulamanızda ağ izlemeyi etkinleştirmek için aşağıdaki görevleri gerçekleştirmeniz gerekir:  
  
- İzleme etkinken kodunuzu derleyin. İzlemeyi etkinleştirmek için gereken derleyici anahtarları hakkında daha fazla bilgi için bkz. [nasıl yapılır: izleme ve hata ayıklama Ile koşullu derleme](../debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md) .  
  
- İzleme çıktısı için bir hedef belirtin.  
  
- Ağ izlemenin davranışını yapılandırın. Ayrıntılı bilgi için bkz. [nasıl yapılır: ağ Izlemeyi yapılandırma](how-to-configure-network-tracing.md) .  
  
 İzleme dinleyicileri olarak da adlandırılan en yaygın izleme hedefleri, varsayılan dinleyici ve günlük dosyasıdır.  
  
 İzleme dinleyicisi belirtmezseniz, izleme varsayılan dinleyiciyi kullanır. Kodunuzu .NET Framework SDK ile gönderilen CLR hata ayıklayıcı veya Windows SDK birlikte gelen DBwin32.exe gibi yönetilen kod etkin bir hata ayıklayıcıda yürüterek varsayılan dinleyiciye gönderilen iletileri görüntüleyebilirsiniz. CLR hata ayıklayıcısını kullanarak, izleme iletileri **Çıkış** penceresinde görüntülenir.  
  
 İzlemeleri almak için bir dosya kullanmayı tercih ederseniz, aşağıdaki örnekte gösterildiği gibi yapılandırma ayarlarını kullanarak bir günlük dosyası belirtebilirsiniz. (Yapılandırma dosyalarının genel bir tartışması için bkz. [yapılandırma dosyaları](../configure-apps/index.md).)  
  
 İzlemeleri bir günlük dosyasına göndermek için, `<system.diagnostics>` uygun yapılandırma dosyasının (uygulama veya makine) düğümüne aşağıdaki düğümü ekleyin. Dosyanın adını (Trace. log) gereksinimlerinize uyacak şekilde değiştirebilirsiniz.  
  
```xml  
<system.diagnostics>  
  <trace autoflush="true" indentsize="4">  
    <listeners>  
      <add name="file" type="System.Diagnostics.TextWriterTraceListener" initializeData="trace.log"/>  
    </listeners>
  </trace>  
</system.diagnostics>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ İzlemeyi Yorumlama](interpreting-network-tracing.md)
- [.NET Framework'te Ağ İzleme](network-tracing.md)
- [Uygulamaları izleme ve İşaretleme](../debug-trace-profile/tracing-and-instrumenting-applications.md)
