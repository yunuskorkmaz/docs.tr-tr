---
title: "Ağ izlemeyi etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: c4957e3ec6891dbee207c7aac5fcf1564ecd0af5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="enabling-network-tracing"></a>Ağ izlemeyi etkinleştirme
Ağ izleme yöntem çağrılarını ve yönetilen bir uygulama tarafından oluşturulan tüm ağ trafiği hakkındaki bilgilere erişim sağlar. Uygulamanızdaki ağ izlemeyi etkinleştirmek için aşağıdaki görevleri tamamlamanız gerekir:  
  
-   İzlemenin etkin kodunuzu derleyin. Bkz: [nasıl yapılır: izleme ve hata ayıklama ile koşullu derleme](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md) izlemeyi etkinleştirmek için gereken derleyici anahtarları hakkında daha fazla bilgi için.  
  
-   İzleme çıktısı için bir hedef belirtin.  
  
-   Ağ izleme davranışını yapılandırın. Bkz: [nasıl yapılır: yapılandırma ağ izleme](../../../docs/framework/network-programming/how-to-configure-network-tracing.md) ayrıntılı bilgi için.  
  
 İzleme dinleyicileri da adlandırılan en yaygın izleme hedefleri varsayılan dinleyici ve günlük dosyası ' dir.  
  
 İzleme dinleyicisi belirtmezseniz, izleme varsayılan dinleyicisi kullanır. CLR hata ayıklayıcısı .NET Framework SDK ile birlikte gelen veya DBwin32.exe Windows SDK ile birlikte gelen gibi yönetilen bir kod etkin hata ayıklayıcı'kodunuzu yürüterek varsayılan dinleyicisi gönderilen iletileri görüntüleyebilirsiniz. CLR hata ayıklayıcısı kullanarak, izleme iletilerini görünür **çıkış** penceresi.  
  
 İzlemelerini almak için bir dosya kullanmayı tercih ederseniz, bir günlük dosyası yapılandırma ayarlarını kullanarak aşağıdaki örnekte gösterildiği gibi belirtebilirsiniz. (Yapılandırma dosyaları hakkında genel bilgiler için bkz: [yapılandırma dosyalarını](../../../docs/framework/configure-apps/index.md).)  
  
 Bir günlük dosyasına izlemeleri göndermek için aşağıdaki düğüm eklemek `<system.diagnostics>` düğümü uygun yapılandırma dosyasının (uygulama veya makine). Gereksinimlerinize uygun olarak dosyanın (trace.log) adını değiştirebilirsiniz.  
  
```xml  
<system.diagnostics>  
  <trace autoflush="true" indentsize="4">  
    <listeners>  
      <add name="file" type="System.Diagnostics.TextWriterTraceListener" initializeData="trace.log"/>  
    </listeners>   
  </trace>  
</system.diagnostics>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ağ İzlemeyi Yorumlama](../../../docs/framework/network-programming/interpreting-network-tracing.md)  
 [.NET Framework'te Ağ İzleme](../../../docs/framework/network-programming/network-tracing.md)  
 [İzleme ve izleme giriş](http://msdn.microsoft.com/en-us/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)
