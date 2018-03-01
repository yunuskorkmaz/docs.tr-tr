---
title: "Uyarılmış Koleksiyonlar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- garbage collection, forced
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6c3093a14fe5186df086cb5b63d20a7eb309c7ba
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="induced-collections"></a>Uyarılmış Koleksiyonlar
Çoğu durumda, atık toplayıcı bir koleksiyon gerçekleştirmek için en iyi zaman belirleyebilir ve bağımsız olarak çalışmasına izin vermemelisiniz. Bazı nadir durumlarda zorlanmış koleksiyonu uygulamanızın performansını iyileştirebilir. Bu durumlarda, atık toplama kullanarak anlamına <xref:System.GC.Collect%2A?displayProperty=nameWithType> çöp toplama zorlamak için yöntem.  
  
 Kullanım <xref:System.GC.Collect%2A?displayProperty=nameWithType> uygulamanızın kodda belirli bir noktada kullanılan bellek miktarında önemli ölçüde azalma olduğunda yöntemi. Örneğin, uygulamanızın birkaç denetimleri olan bir karmaşık iletişim kutusu kullanıyorsa, çağırma <xref:System.GC.Collect%2A> iletişim kutusu kapatıldığında hemen iletişim kutusu tarafından kullanılan bellek geri kazanma performansı. En iyi olmayan zamanlarda nesneleri geri kazanmak atık toplayıcı çalışırsa, performansı düşürebilir gerektiğinden, uygulamanızın çöp toplama çok sık inducing olduğunu değil, emin olun. Size sağlayabilir bir <xref:System.GCCollectionMode.Optimized?displayProperty=nameWithType> numaralandırma değeri <xref:System.GC.Collect%2A> yalnızca koleksiyonu bir sonraki bölümde açıklandığı gibi üretken olacaktır, toplamak için yöntem.  
  
## <a name="gc-collection-mode"></a>GC koleksiyon modu  
 Aşağıdakilerden birini kullanabilirsiniz <xref:System.GC.Collect%2A?displayProperty=nameWithType> içeren yöntemi aşırı bir <xref:System.GCCollectionMode> değeri davranışı zorunlu bir koleksiyon için aşağıdaki gibi belirtin.  
  
|`GCCollectionMode`değer|Açıklama|  
|------------------------------|-----------------|  
|<xref:System.GCCollectionMode.Default>|Varsayılan atık toplama ayar çalışan .NET sürümü için kullanır.|  
|<xref:System.GCCollectionMode.Forced>|Hemen gerçekleşmesi için atık toplama zorlar. Bu arama için eşdeğerdir <xref:System.GC.Collect?displayProperty=nameWithType> aşırı yükleme. Tüm nesli bir tam engelleme koleksiyonunda sonuçlanır.<br /><br /> Ayarlayarak büyük nesne yığın sıkıştırabilirsiniz <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> özelliğine <xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce?displayProperty=nameWithType> bir anında tam engelleme çöp toplama zorlama önce.|  
|<xref:System.GCCollectionMode.Optimized>|Geçerli saati nesneleri geri kazanmak için uygun olup olmadığını belirlemek atık toplayıcı sağlar.<br /><br /> Çöp toplayıcı bir koleksiyon, bu durumda nesneleri geri kazanma olmadan döndürür hizalı için üretken olmaz belirlenemedi.|  
  
## <a name="background-or-blocking-collections"></a>Arka plan veya engelleme koleksiyonları  
 Çağırabilirsiniz <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=nameWithType> uyarılmış bir koleksiyon veya engelleyip engellemediğini belirlemek için yöntemi aşırı yüklemesini. Yöntemin bir birleşimini gerçekleştirilen koleksiyon türüne bağlıdır `mode` ve `blocking` parametreleri. `mode`üye <xref:System.GCCollectionMode> numaralandırma, ve `blocking` olan bir <xref:System.Boolean> değeri. Aşağıdaki tabloda özetlenmiştir etkileşimini `mode` ve `blocking` bağımsız değişkenler.  
  
|`mode`|`blocking` = `true`|`blocking` = `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode.Forced>veya<xref:System.GCCollectionMode.Default>|Bir engelleme koleksiyonu mümkün olan en kısa sürede gerçekleştirilir. Arka plan toplama devam ediyor ve nesil ise 0 veya 1, <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> yöntemi hemen engelleme koleksiyonu tetikler ve toplama işlemi tamamlandığında döndürür. Arka plan koleksiyonu işlemi devam ediyorsa ve `generation` parametresi, 2, arka plan toplama tamamlandı, engelleme 2. nesil koleksiyonu tetikler ve ardından döndürür kadar yöntemi bekler.|Bir koleksiyonu mümkün olan en kısa sürede gerçekleştirilir. <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> Yöntemi isteklerini bir arka plan koleksiyon, ancak bu garanti edilmez; koşullara bağlı olarak bir engelleme koleksiyonu hala gerçekleştirilebilir. Arka plan koleksiyonu zaten devam ediyor durumunda, bu yöntem hemen döndürür.|  
|<xref:System.GCCollectionMode.Optimized>|Çöp toplayıcı durumuna bağlı olarak bir engelleme koleksiyonu gerçekleştirilebilir ve `generation` parametresi. En iyi performansı sağlamak atık toplayıcı çalışır.|Çöp toplayıcı durumuna bağlı olarak bir koleksiyon gerçekleştirilebilir. <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> Yöntemi isteklerini bir arka plan koleksiyon, ancak bu garanti edilmez; koşullara bağlı olarak bir engelleme koleksiyonu hala gerçekleştirilebilir. En iyi performansı sağlamak atık toplayıcı çalışır. Arka plan koleksiyonu zaten devam ediyor durumunda, bu yöntem hemen döndürür.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gecikme Modları](../../../docs/standard/garbage-collection/latency.md)  
 [Atık Toplama](../../../docs/standard/garbage-collection/index.md)
