---
title: Uyarılmış Koleksiyonlar
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, forced
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
ms.openlocfilehash: 604b49ef577a46204b523ebf5a8575a30b81635e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120926"
---
# <a name="induced-collections"></a>Uyarılmış Koleksiyonlar
Çoğu durumda, çöp toplayıcı bir koleksiyon gerçekleştirmek için en iyi zamanı belirleyebilir ve bağımsız olarak çalışmasına izin verin. Zorunlu bir koleksiyonun uygulamanızın performansını iyileştirebileceği nadir durumlar vardır. Bu durumlarda, atık toplamayı bir çöp toplamayı zorlamak için <xref:System.GC.Collect%2A?displayProperty=nameWithType> metodunu kullanarak yazabilirsiniz.  
  
 Uygulamanızın kodundaki belirli bir noktada kullanılan bellek miktarı açısından önemli bir azalma olduğunda <xref:System.GC.Collect%2A?displayProperty=nameWithType> yöntemini kullanın. Örneğin, uygulamanız birkaç denetimi olan karmaşık bir iletişim kutusu kullanıyorsa, iletişim kutusu kapalıyken <xref:System.GC.Collect%2A> çağırmak, iletişim kutusu tarafından kullanılan belleğin hemen geri kazanma performansını iyileştirebilir. Çöp toplayıcı nesneleri en iyi olmayan zamanlarda geri almaya çalışıyorsa, uygulamanızın çöp toplamayı çok sık karşılamadığından emin olun. Bir sonraki bölümde anlatıldığı gibi, yalnızca koleksiyon üretken olduğunda toplanacak <xref:System.GC.Collect%2A> yöntemine <xref:System.GCCollectionMode.Optimized?displayProperty=nameWithType> bir numaralandırma değeri sağlayabilirsiniz.  
  
## <a name="gc-collection-mode"></a>GC toplama modu  
 Zorunlu bir koleksiyonun davranışını aşağıdaki gibi belirtmek için bir <xref:System.GCCollectionMode> değeri içeren <xref:System.GC.Collect%2A?displayProperty=nameWithType> yöntemi aşırı yüklemelerinin birini kullanabilirsiniz.  
  
|`GCCollectionMode` değeri|Açıklama|  
|------------------------------|-----------------|  
|<xref:System.GCCollectionMode.Default>|, .NET 'in çalışan sürümü için varsayılan çöp toplama ayarını kullanır.|  
|<xref:System.GCCollectionMode.Forced>|Çöp toplamayı hemen gerçekleşecek şekilde zorlar. Bu, <xref:System.GC.Collect?displayProperty=nameWithType> aşırı yüküne çağrı ile eşdeğerdir. Tüm nesiller için tam engelleme koleksiyonuna neden olur.<br /><br /> Ayrıca, bir anlık tam engelleme çöp toplamayı zorlamak için <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> özelliğini <xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce?displayProperty=nameWithType> olarak ayarlayarak büyük nesne yığınını da genişletebilirsiniz.|  
|<xref:System.GCCollectionMode.Optimized>|Çöp toplayıcıyı, geçerli saatin nesneleri geri kazanmak için en uygun olup olmadığını belirlemesine olanak sağlar.<br /><br /> Çöp toplayıcı, bir koleksiyonun hizalı hale getirmek için yeterince üretken olacağını belirleyebilir ve bu durumda geri kazanma nesneleri olmadan geri dönecektir.|  
  
## <a name="background-or-blocking-collections"></a>Arka plan veya engelleme koleksiyonları  
 Alınmış bir koleksiyonun engellenip engellenmeyeceğini belirtmek için <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=nameWithType> yöntemi aşırı yüklemesini çağırabilirsiniz. Gerçekleştirilen koleksiyonun türü yöntemin `mode` ve `blocking` parametrelerinin birleşimine bağlıdır. `mode` <xref:System.GCCollectionMode> numaralandırmanın bir üyesidir ve `blocking` bir <xref:System.Boolean> değeridir. Aşağıdaki tabloda `mode` ve `blocking` bağımsız değişkenlerinin etkileşimi özetlenmektedir.  
  
|`mode`|`blocking` = `true`|`blocking` = `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode.Forced> veya <xref:System.GCCollectionMode.Default>|Engelleyici bir koleksiyon mümkün olan en kısa sürede gerçekleştirilir. Bir arka plan koleksiyonu devam ediyorsa ve oluşturma 0 veya 1 ise, <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> yöntemi bir engelleme koleksiyonunu hemen tetikler ve koleksiyon bittiğinde döndürür. Bir arka plan koleksiyonu devam ediyorsa ve `generation` parametresi 2 ise, yöntem arka plan koleksiyonu tamamlanana kadar bekler, bir engelleme 2 toplamayı tetikler ve ardından döndürür.|Bir koleksiyon mümkün olan en kısa sürede gerçekleştirilir. <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> yöntemi bir arka plan koleksiyonu ister, ancak bu garanti edilmez; koşullara bağlı olarak, engelleyici bir koleksiyon yine de gerçekleştirilebilir. Bir arka plan koleksiyonu zaten devam ediyorsa, yöntemi hemen döndürür.|  
|<xref:System.GCCollectionMode.Optimized>|Çöp toplayıcının durumuna ve `generation` parametresine bağlı olarak engelleme koleksiyonu gerçekleştirilebilir. Çöp toplayıcı en iyi performansı sağlamaya çalışır.|Atık toplayıcısının durumuna bağlı olarak bir koleksiyon gerçekleştirilebilir. <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> yöntemi bir arka plan koleksiyonu ister, ancak bu garanti edilmez; koşullara bağlı olarak, engelleyici bir koleksiyon yine de gerçekleştirilebilir. Çöp toplayıcı en iyi performansı sağlamaya çalışır. Bir arka plan koleksiyonu zaten devam ediyorsa, yöntemi hemen döndürür.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gecikme Modları](../../../docs/standard/garbage-collection/latency.md)
- [Atık Toplama](../../../docs/standard/garbage-collection/index.md)
