---
title: Ağ İzlemeyi Etkinleştirme
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
ms.openlocfilehash: 61ffd422463ca70cc34c39dd216ce8e660809dcb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180876"
---
# <a name="enabling-network-tracing"></a>Ağ İzlemeyi Etkinleştirme
Ağ izleme, yönetilen bir uygulama tarafından oluşturulan yöntem çağrıları ve ağ trafiği hakkındaki bilgilere erişim sağlar. Uygulamanızda ağ izlemesağlamak için aşağıdaki görevleri tamamlamanız gerekir:  
  
- İzleme etkinken kodunuzu derle. Bkz. Nasıl Yapılacağını Görün: İzlemeyi etkinleştirmek için gereken derleyici anahtarları hakkında daha fazla bilgi için [İzleme ve Hata Ayıklama ile Koşullu](../debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md) olarak derle.  
  
- Çıktıyı izlemek için bir hedef belirtin.  
  
- Ağ izleme davranışını yapılandırın. Bkz. Nasıl Yapılacağını ZİYAZİ: Ayrıntılı bilgi için [Ağ İzlemesini Yapılandırın.](how-to-configure-network-tracing.md)  
  
 İzleme dinleyicileri olarak da adlandırılan en yaygın izleme hedefleri varsayılan dinleyici ve günlük dosyasıdır.  
  
 İzleme, izleme dinleyicisi belirtmezseniz varsayılan dinleyiciyi kullanır. Kodunuzu ,NET Framework SDK veya Windows SDK ile gönderilen DBwin32.exe gibi yönetilen kod etkin hata ayıklayıcıda çalıştırarak varsayılan dinleyiciye gönderilen iletileri görüntüleyebilirsiniz. CLR Hata ayıklayıcısını kullanarak, izleme iletileri **Çıktı** penceresinde görünür.  
  
 İzalmak için bir dosya kullanmayı tercih ederseniz, aşağıdaki örnekte gösterildiği gibi yapılandırma ayarlarını kullanarak bir günlük dosyası belirtebilirsiniz. (Yapılandırma dosyalarının genel bir tartışması için [Yapılandırma Dosyaları'na](../configure-apps/index.md)bakın.)  
  
 Bir günlük dosyasına izleme göndermek için, uygun `<system.diagnostics>` yapılandırma dosyasının (uygulama veya makine) düğümüne aşağıdaki düğümü ekleyin. Dosyanın adını (trace.log) gereksinimlerinize uyacak şekilde değiştirebilirsiniz.  
  
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
- [İzleme ve İşaretleme Uygulamaları](../debug-trace-profile/tracing-and-instrumenting-applications.md)
