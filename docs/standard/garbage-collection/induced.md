---
title: Uyarılmış Koleksiyonlar
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, forced
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
ms.openlocfilehash: 36dff45587c6c28ba17fd7389dc3863893ff8f61
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286047"
---
# <a name="induced-collections"></a>Uyarılmış Koleksiyonlar
Çoğu durumda, çöp toplayıcı bir koleksiyon gerçekleştirmek için en iyi zamanı belirleyebilir ve bağımsız olarak çalışmasına izin verin. Zorunlu bir koleksiyonun uygulamanızın performansını iyileştirebileceği nadir durumlar vardır. Bu durumlarda, <xref:System.GC.Collect%2A?displayProperty=nameWithType> çöp toplamayı zorlamak için metodunu kullanarak çöp toplama işlemini gerçekleştirebilirsiniz.  
  
 <xref:System.GC.Collect%2A?displayProperty=nameWithType>Uygulamanızın kodundaki belirli bir noktada kullanılan bellek miktarı açısından önemli bir azalma olduğunda yöntemini kullanın. Örneğin, uygulamanız birkaç denetimi olan karmaşık bir iletişim kutusu kullanıyorsa, <xref:System.GC.Collect%2A> iletişim kutusu kapatıldığında arama, iletişim kutusu tarafından kullanılan belleği hemen geri kazanma performansını iyileştirebilir. Çöp toplayıcı nesneleri en iyi olmayan zamanlarda geri almaya çalışıyorsa, uygulamanızın çöp toplamayı çok sık karşılamadığından emin olun. Bir <xref:System.GCCollectionMode.Optimized?displayProperty=nameWithType> <xref:System.GC.Collect%2A> sonraki bölümde anlatıldığı gibi, yalnızca koleksiyon üretken olduğunda toplanacak yöntemine bir numaralandırma değeri sağlayabilirsiniz.  
  
## <a name="gc-collection-mode"></a>GC toplama modu  
 <xref:System.GC.Collect%2A?displayProperty=nameWithType> <xref:System.GCCollectionMode> Zorunlu bir koleksiyonun davranışını aşağıdaki gibi belirtmek için bir değer içeren yöntem aşırı yüklemelerinin birini kullanabilirsiniz.  
  
|`GCCollectionMode`deeri|Description|  
|------------------------------|-----------------|  
|<xref:System.GCCollectionMode.Default>|, .NET 'in çalışan sürümü için varsayılan çöp toplama ayarını kullanır.|  
|<xref:System.GCCollectionMode.Forced>|Çöp toplamayı hemen gerçekleşecek şekilde zorlar. Bu, aşırı yüklemeyi çağırma ile eşdeğerdir <xref:System.GC.Collect?displayProperty=nameWithType> . Tüm nesiller için tam engelleme koleksiyonuna neden olur.<br /><br /> Ayrıca, <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> <xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce?displayProperty=nameWithType> bir anlık tam engelleme çöp toplamayı zorlamak için özelliğini olarak ayarlayarak büyük nesne yığınını da genişletebilirsiniz.|  
|<xref:System.GCCollectionMode.Optimized>|Çöp toplayıcıyı, geçerli saatin nesneleri geri kazanmak için en uygun olup olmadığını belirlemesine olanak sağlar.<br /><br /> Çöp toplayıcı, bir koleksiyonun hizalı hale getirmek için yeterince üretken olacağını belirleyebilir ve bu durumda geri kazanma nesneleri olmadan geri dönecektir.|  
  
## <a name="background-or-blocking-collections"></a>Arka plan veya engelleme koleksiyonları  
 <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=nameWithType>Alınmış bir koleksiyonun engellenip engellenmeyeceğini belirtmek için yöntem aşırı yüklemesini çağırabilirsiniz. Gerçekleştirilen koleksiyonun türü, yöntemin `mode` ve parametrelerinin birleşimine bağlıdır `blocking` . `mode`, numaralandırmanın bir üyesidir <xref:System.GCCollectionMode> ve `blocking` bir <xref:System.Boolean> değerdir. Aşağıdaki tabloda `mode` ve `blocking` bağımsız değişkenlerinin etkileşimi özetlenmektedir.  
  
|`mode`|`blocking` = `true`|`blocking` = `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode.Forced> veya <xref:System.GCCollectionMode.Default>|Engelleyici bir koleksiyon mümkün olan en kısa sürede gerçekleştirilir. Bir arka plan koleksiyonu devam ediyorsa ve oluşturma 0 veya 1 ise, <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> Yöntem bir engelleme koleksiyonunu hemen tetikler ve koleksiyon bittiğinde döndürür. Bir arka plan koleksiyonu devam ediyorsa ve `generation` parametresi 2 ise, yöntem arka plan koleksiyonu tamamlanana kadar bekler, blok oluşturma 2 koleksiyonunu tetikler ve ardından döndürür.|Bir koleksiyon mümkün olan en kısa sürede gerçekleştirilir. <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29>Yöntemi bir arka plan koleksiyonu ister, ancak bu garanti edilmez; koşullara bağlı olarak, bir engelleme koleksiyonu yine de gerçekleştirilebilir. Bir arka plan koleksiyonu zaten devam ediyorsa, yöntemi hemen döndürür.|  
|<xref:System.GCCollectionMode.Optimized>|Çöp toplayıcı ve parametresinin durumuna bağlı olarak engelleme koleksiyonu gerçekleştirilebilir `generation` . Çöp toplayıcı en iyi performansı sağlamaya çalışır.|Atık toplayıcısının durumuna bağlı olarak bir koleksiyon gerçekleştirilebilir. <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29>Yöntemi bir arka plan koleksiyonu ister, ancak bu garanti edilmez; koşullara bağlı olarak, bir engelleme koleksiyonu yine de gerçekleştirilebilir. Çöp toplayıcı en iyi performansı sağlamaya çalışır. Bir arka plan koleksiyonu zaten devam ediyorsa, yöntemi hemen döndürür.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gecikme modları](latency.md)
- [Çöp toplama](index.md)
