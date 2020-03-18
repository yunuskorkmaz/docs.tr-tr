---
title: Uyarılmış Koleksiyonlar
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, forced
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
ms.openlocfilehash: 604b49ef577a46204b523ebf5a8575a30b81635e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120926"
---
# <a name="induced-collections"></a>Uyarılmış Koleksiyonlar
Çoğu durumda, çöp toplayıcı bir koleksiyon gerçekleştirmek için en iyi zamanı belirleyebilir ve bağımsız çalışmasına izin vermelisiniz. Zorunlu bir koleksiyonun uygulamanızın performansını artırabileceği nadir durumlar vardır. Bu gibi durumlarda, çöp toplama zorlamak <xref:System.GC.Collect%2A?displayProperty=nameWithType> için yöntemi kullanarak çöp toplama neden olabilir.  
  
 Uygulamanızın <xref:System.GC.Collect%2A?displayProperty=nameWithType> kodunda belirli bir noktada kullanılan bellek miktarında önemli bir azalma olduğunda yöntemi kullanın. Örneğin, uygulamanız birkaç denetimi olan karmaşık bir iletişim <xref:System.GC.Collect%2A> kutusu kullanıyorsa, iletişim kutusu kapatıldığında arama yapmak, iletişim kutusu tarafından kullanılan belleği hemen geri alarak performansı artırabilir. Çöp toplayıcısı nesneleri en uygun olmayan zamanlarda geri almaya çalışıyorsa, bu performansı azaltabileceğinden, uygulamanızın çöp toplamayı çok sık uyarmadığını unutmayın. Bir sonraki <xref:System.GCCollectionMode.Optimized?displayProperty=nameWithType> bölümde belirtildiği gibi, <xref:System.GC.Collect%2A> yalnızca toplama verimli olduğunda toplamak için yönteme bir numaralandırma değeri sağlayabilirsiniz.  
  
## <a name="gc-collection-mode"></a>GC toplama modu  
 Zorlanan koleksiyonun <xref:System.GC.Collect%2A?displayProperty=nameWithType> davranışını aşağıdaki gibi <xref:System.GCCollectionMode> belirtmek için değeri içeren yöntem aşırı yüklemelerinden birini kullanabilirsiniz.  
  
|`GCCollectionMode`Değer|Açıklama|  
|------------------------------|-----------------|  
|<xref:System.GCCollectionMode.Default>|.NET'in çalışan sürümü için varsayılan çöp toplama ayarını kullanır.|  
|<xref:System.GCCollectionMode.Forced>|Çöp toplamayı hemen oluşmaya zorlar. Bu, aşırı yüklemeyi çağırmaya <xref:System.GC.Collect?displayProperty=nameWithType> eşdeğerdir. Tüm nesillerin tam bir engelleme toplama sonuçlanır.<br /><br /> Ayrıca, hemen tam engelleme çöp toplama <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> zorlamadan <xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce?displayProperty=nameWithType> önce özelliği ayarlayarak büyük nesne yığını sıkıştırabilirsiniz.|  
|<xref:System.GCCollectionMode.Optimized>|Çöp toplayıcısının nesneleri geri almak için geçerli zamanın en uygun olup olmadığını belirlemesini sağlar.<br /><br /> Çöp toplayıcı, bir koleksiyonun haklı çıkacak kadar üretken olmayacağını ve bu durumda nesneleri geri almadan geri döneceğini belirleyebilir.|  
  
## <a name="background-or-blocking-collections"></a>Arka plan veya engelleme koleksiyonları  
 İndüklenen <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=nameWithType> koleksiyonun engellenip engellemediğini belirtmek için yöntemi aşırı yükleme olarak adlandırabilirsiniz. Gerçekleştirilen toplama türü yöntem `mode` ve `blocking` parametrelerin bir kombinasyonuna bağlıdır. `mode`numaralandırmanın <xref:System.GCCollectionMode> bir üyesidir ve `blocking` bir <xref:System.Boolean> değerdir. Aşağıdaki tabloda `mode` `blocking` ve bağımsız değişkenlerin etkileşimi özetlenmiştir.  
  
|`mode`|`blocking` = `true`|`blocking` = `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode.Forced> veya <xref:System.GCCollectionMode.Default>|Engelleme koleksiyonu mümkün olan en kısa sürede gerçekleştirilir. Bir arka plan koleksiyonu devam ediyorsa ve <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> nesil 0 veya 1 ise, yöntem hemen engelleme koleksiyonunu tetikler ve koleksiyon tamamlandığında döndürür. Bir arka plan koleksiyonu devam `generation` ediyorsa ve parametre 2 ise, yöntem arka plan koleksiyonu tamamlanana kadar bekler, engelleme nesil 2 koleksiyonunu tetikler ve sonra döndürür.|Bir koleksiyon mümkün olan en kısa sürede gerçekleştirilir. Yöntem <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> bir arka plan koleksiyonu ister, ancak bu garanti edilmez; koşullara bağlı olarak, engelleme koleksiyonu yine de gerçekleştirilebilir. Bir arka plan koleksiyonu zaten devam ediyorsa, yöntem hemen döndürür.|  
|<xref:System.GCCollectionMode.Optimized>|Çöp toplayıcısının durumuna ve `generation` parametreye bağlı olarak bir engelleme koleksiyonu gerçekleştirilebilir. Çöp toplayıcı en iyi performansı sağlamaya çalışır.|Çöp toplayıcısının durumuna bağlı olarak bir koleksiyon gerçekleştirilebilir. Yöntem <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> bir arka plan koleksiyonu ister, ancak bu garanti edilmez; koşullara bağlı olarak, engelleme koleksiyonu yine de gerçekleştirilebilir. Çöp toplayıcı en iyi performansı sağlamaya çalışır. Bir arka plan koleksiyonu zaten devam ediyorsa, yöntem hemen döndürür.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gecikme Modları](../../../docs/standard/garbage-collection/latency.md)
- [Çöp Toplama](../../../docs/standard/garbage-collection/index.md)
