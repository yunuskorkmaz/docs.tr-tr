---
title: Uyarılmış Koleksiyonlar
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, forced
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69590b0efc924132d149621c135ef0816cac7d1e
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003073"
---
# <a name="induced-collections"></a>Uyarılmış Koleksiyonlar
Çoğu durumda, çöp toplayıcı bir toplama işlemi gerçekleştirmek için en iyi zamanı belirleyebilir ve bunun bağımsız olarak çalışmasına izin vermelisiniz. Zorlanmış bir koleksiyonun, uygulamanızın performansını iyileştirebileceği bazı nadir durumlar vardır. Bu durumlarda, çöp toplama kullanarak zorlarsınız <xref:System.GC.Collect%2A?displayProperty=nameWithType> Çöp toplamayı zorlamak için yöntemi.  
  
 Kullanım <xref:System.GC.Collect%2A?displayProperty=nameWithType> uygulamanızın kodunda, belirli bir noktada kullanılan bellek miktarında önemli ölçüde azalma olduğunda yöntemi. Örneğin, uygulamanız çeşitli denetimler içeren karmaşık bir iletişim kutusu kullanıyorsa, çağırma <xref:System.GC.Collect%2A> iletişim kutusu kapatıldığında performans hemen iletişim kutusu tarafından kullanılan bellek kazanılarak. Çöp toplayıcı uygun olmayan zamanlarda nesneleri geri kazanmaya çalışırsa, performansı düşürebileceğinden uygulamanızın Çöp toplamayı çok sık harekete geçirmediğinden emin olun. Verebilirsiniz bir <xref:System.GCCollectionMode.Optimized?displayProperty=nameWithType> numaralandırma değerini <xref:System.GC.Collect%2A> yalnızca koleksiyon sonraki bölümde açıklandığı gibi verimli olduğunda toplamak için yöntemi.  
  
## <a name="gc-collection-mode"></a>GC toplama modu  
 Birini kullanabilirsiniz <xref:System.GC.Collect%2A?displayProperty=nameWithType> içeren yöntemi aşırı bir <xref:System.GCCollectionMode> aşağıdaki gibi zorlanan bir koleksiyon davranışını belirtmek için değer.  
  
|`GCCollectionMode` Değer|Açıklama|  
|------------------------------|-----------------|  
|<xref:System.GCCollectionMode.Default>|Varsayılan çöp toplama ayarını çalışan .NET sürümü için kullanır.|  
|<xref:System.GCCollectionMode.Forced>|Hemen oluşmasını zorlar çöp toplama. Bu çağırmakla eşdeğerdir <xref:System.GC.Collect?displayProperty=nameWithType> aşırı yükleme. Bu, tüm nesillerdeki bir tam engelleme koleksiyondaki sonuçlanır.<br /><br /> Ayarlayarak büyük nesne yığınını da sıkıştırabilirsiniz <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> özelliğini <xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce?displayProperty=nameWithType> önce bir anında tam engelleme çöp toplama zorlanıyor.|  
|<xref:System.GCCollectionMode.Optimized>|Geçerli zamanın nesneleri geri kazanmak için optimum olup olmadığını belirlemek çöp toplayıcısını etkinleştirir.<br /><br /> Atık toplayıcı bir koleksiyon, bu durumda nesneleri geri kazanmadan döndürür açısından haklı bir gerekçesi için üretken olmaz belirleyebilir.|  
  
## <a name="background-or-blocking-collections"></a>Arka plan veya engelleme koleksiyonları  
 Çağırabilirsiniz <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=nameWithType> yöntemi aşırı yüklemesini, bir koleksiyonun engellenip veya engelleyip engellemediğini belirlemek için. Gerçekleştirilen koleksiyonun türü yöntemin üzerindeki bir birleşimini bağlıdır `mode` ve `blocking` parametreleri. `mode` bir üyesidir <xref:System.GCCollectionMode> numaralandırma ve `blocking` olduğu bir <xref:System.Boolean> değeri. Aşağıdaki tabloda etkileşimi özetlenmektedir `mode` ve `blocking` bağımsız değişkenler.  
  
|`mode`|`blocking` = `true`|`blocking` = `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode.Forced> veya <xref:System.GCCollectionMode.Default>|Engelleyici bir koleksiyon mümkün olan en kısa sürede gerçekleştirilir. Arka plan koleksiyonu devam ediyor ve üretimi ise 0 veya 1, <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> yöntemi hemen durdurma koleksiyonu tetikler ve koleksiyon bittiği zaman verir. Arka plan koleksiyonu sürüyorsa ve `generation` parametresi, 2, arka plan koleksiyonu tamamlandı, bir engelleme üretimi 2 toplama tetikler ve ardından döndürür kadar yöntemi bekler.|Bir koleksiyon mümkün olan en kısa sürede gerçekleştirilir. <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> Yöntemi bir arka plan koleksiyonu ister, ancak bu garanti edilmez; şartlara bağlı olarak engelleyici bir koleksiyon da yapılabilir. Arka plan koleksiyonu zaten sürüyor ise, yöntem hemen döner.|  
|<xref:System.GCCollectionMode.Optimized>|Engelleyici bir koleksiyon, atık toplayıcının durumuna göre gerçekleştirilebilir ve `generation` parametresi. Çöp toplayıcı en iyi performansı sağlamaya çalışır.|Bir koleksiyon, atık toplayıcının durumuna göre gerçekleştirilebilir. <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> Yöntemi bir arka plan koleksiyonu ister, ancak bu garanti edilmez; şartlara bağlı olarak engelleyici bir koleksiyon da yapılabilir. Çöp toplayıcı en iyi performansı sağlamaya çalışır. Arka plan koleksiyonu zaten sürüyor ise, yöntem hemen döner.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gecikme Modları](../../../docs/standard/garbage-collection/latency.md)  
- [Atık Toplama](../../../docs/standard/garbage-collection/index.md)
