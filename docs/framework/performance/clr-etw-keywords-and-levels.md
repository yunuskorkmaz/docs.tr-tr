---
title: CLR ETW Anahtar Sözcükleri ve Düzeyler
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW keywords
- CLR ETW levels
- ETW, CLR keywords
- ETW, CLR levels
ms.assetid: fdf5856d-516b-4042-849d-911c4518a6cb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8332eba909c3ebe475e3f364f81a676733e4e3d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="clr-etw-keywords-and-levels"></a>CLR ETW Anahtar Sözcükleri ve Düzeyler
<a name="top"></a> Windows (ETW) olayları için olay izleme, kategori ve düzey göre filtrelenebilir. Olay [CLR ETW anahtar sözcükleri](#keywords) olayları kategoriye göre filtrelemeyi sağlamak; çalışma zamanı ve özeti sağlayıcıları bileşimlerde kullanılır. [Olay düzeyleri](#levels) bayrakları tarafından tanımlanır.  
  
<a name="keywords"></a>   
## <a name="clr-etw-keywords"></a>CLR ETW anahtar sözcükleri  
 Anahtar değerlerini oluşturmak için birleştirilebilir bayrakları sözcüklerdir. Komut satırı yardımcı programlarını çağırdığınızda pratikte, onaltılık değerleri anahtar sözcüklerden biri anahtar sözcüğü adları yerine kullanırsınız.  
  
 Anahtar sözcükler aşağıdaki tabloda açıklanmıştır:  
  
-   [CLR ETW çalışma zamanı anahtar sözcükleri](#runtime)  
  
-   [CLR ETW özeti anahtar sözcükleri](#rundown)  
  
-   [Çalışma zamanı sağlayıcısı için simge çözümlemede anahtar sözcüğü birleşimler](#runtime_combo)  
  
-   [Sembol Çözümleme Özeti sağlayıcısı için anahtar sözcüğü birleşimler](#rundown_combo)  
  
<a name="runtime"></a>   
### <a name="clr-etw-runtime-keywords"></a>CLR ETW çalışma zamanı anahtar sözcükleri  
 CLR ETW çalışma zamanı anahtar sözcükler, bunların değerleri ve ne için kullanıldıkları aşağıdaki tabloda listelenmektedir.  
  
|Çalışma zamanı anahtar adı|Değer|Amaç|  
|--------------------------|-----------|-------------|  
|`GCKeyword`|0x00000001|Koleksiyonunu etkinleştirir [çöp toplama olayları](../../../docs/framework/performance/garbage-collection-etw-events.md).|  
|`LoaderKeyword`|0x00000008|Koleksiyonunu etkinleştirir [yükleyici olayları](../../../docs/framework/performance/loader-etw-events.md).|  
|`JITKeyword`|0x00000010|Koleksiyonunu etkinleştirir [tam zamanında (JIT) olayları](../../../docs/framework/performance/jit-tracing-etw-events.md).|  
|`NGenKeyword`|0x00000020|Yerel görüntü yöntemleri (yerel Görüntü Oluşturucu tarafından Ngen.exe işlenen yöntemleri); olaylarını toplama sağlar. ile kullanılan `StartEnumerationKeyword` ve `EndEnumerationKeyword`. Bu anahtar sözcük yüksek yüke sahiptir. Yüklenen her NGen modülün içinde her yöntem olayları oluşturur. Mümkün olduğunda bu anahtar sözcük kullanmak yerine, NGen modüllerden yöntemleri hakkında bilgi almak için profil oluşturma araçları tarafından oluşturulan program veritabanları (PDB) kullanmanızı öneririz. Ayrıca bkz. `OverrideAndSuppressNGenEventsKeyword` Bu tablo daha sonra.|  
|`StartEnumerationKeyword`|0x00000040|Çalışma zamanında tüm yöntemlerin etkinleştirir; ile birlikte kullanılan `NGenKeyword`.|  
|`EndEnumerationKeyword`|0x00000080|Çalışma zamanı'nda yok tüm yöntemlerin etkinleştirir; ile birlikte kullanılan `JITKeyword` ve `NGenKeyword`.|  
|`SecurityKeyword`|0x00000400|Koleksiyonunu etkinleştirir [güvenlik olaylarını](../../../docs/framework/performance/security-etw-events.md).|  
|`AppDomainResourceManagementKeyword`|0x00000800|Kaynak izleme olayları uygulama etki alanı düzeyinde bir koleksiyonunu sağlar.|  
|`JITTracingKeyword`|0x00001000|Koleksiyonunu etkinleştirir [JIT izleme olayları](../../../docs/framework/performance/jit-tracing-etw-events.md).|  
|`InteropKeyword`|0x00002000|Koleksiyonunu etkinleştirir [birlikte çalışma olayları](../../../docs/framework/performance/interop-etw-events.md).|  
|`ContentionKeyword`|0x00004000|Koleksiyonunu etkinleştirir [Çekişme olayları](../../../docs/framework/performance/contention-etw-events.md).|  
|`ExceptionKeyword`|0x00008000|Koleksiyonunu etkinleştirir [özel durum olayları](../../../docs/framework/performance/exception-thrown-v1-etw-event.md).|  
|`ThreadingKeyword`|0x00010000|Koleksiyonunu etkinleştirir [iş parçacığı havuzu olayları](../../../docs/framework/performance/thread-pool-etw-events.md).|  
|`OverrideAndSuppressNGenEventsKeyword`|0x00040000|(Bulunan [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve sonraki sürümler.) Yüksek yükünü bastırır `NGenKeyword` anahtar sözcüğü ve NGen modüller içinde yöntemleri için olayları oluşturulmasını engeller. İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], profil oluşturma araçları kullanması gereken `OverrideAndSuppressNGenEventsKeyword` ve `NGenKeyword` birlikte olayları oluşturmayı NGen modüllerinde yöntemleri için durdurmak için. NGen modülleri yöntemleri hakkında bilgi almak için daha verimli NGen pdb kullanmak profil oluşturma aracı sağlar. .NET Framework 4 ve önceki sürümlerde CLR NGen pdb oluşturulmasını desteklemiyor. Bu önceki sürümlerde, CLR değil tanıyacağı `OverrideAndSuppressNGenEventsKeyword` ve işleyecek `NGenKeyword` NGen modülleri yöntemleri için olayları oluşturmak için.|  
|`PerfTrackKeyWord`|0x2000000|Koleksiyonunu etkinleştirir `ModuleLoad` ve `ModuleRange` olaylar.|  
|`StackKeyword`|0x40000000|CLR koleksiyonunu etkinleştirir [izleme olayları yığın](../../../docs/framework/performance/stack-etw-event.md).|  
  
 [Başa dön](#top)  
  
<a name="rundown"></a>   
### <a name="clr-etw-rundown-keywords"></a>CLR ETW özeti anahtar sözcükleri  
 CLR ETW özeti anahtar sözcükler, bunların değerleri ve ne için kullanıldıkları aşağıdaki tabloda listelenmektedir.  
  
|Özeti anahtar adı|Değer|Amaç|  
|--------------------------|-----------|-------------|  
|`LoaderRundownKeyword`|0x00000008|Yükleyici olayları ile kullanıldığında koleksiyonunu sağlar `StartRundownKeyword` ve `EndRundownKeyword`.|  
|`JitRundownKeyword`|0x00000010|Yöntem koleksiyonunu etkinleştirir `DCStart` ve `DCEnd` olayları ile kullanıldığında JIT derlenmiş yöntemleri için `StartRundownKeyword` ve `EndRundownKeyword`.|  
|`NGenRundownKeyword`|0x00000020|Yöntem koleksiyonunu etkinleştirir `DCStart` ve `DCEnd` olayları ile kullanıldığında NGen yerel görüntü yöntemleri için `StartRundownKeyword` ve `EndRundownKeyword`. Bu anahtar sözcük yüksek yüke sahiptir. Yüklenen her NGen modülün içinde her yöntem olayları oluşturur. Mümkün olduğunda bu anahtar sözcük kullanmak yerine, NGen modüllerden yöntemleri hakkında bilgi almak için profil oluşturma araçları tarafından oluşturulan program veritabanları (PDB) kullanmanızı öneririz. Ayrıca bkz. `OverrideAndSuppressNGenEventsRundownKeyword` Bu tablo daha sonra.|  
|`StartRundownKeyword`|0x00000040|Sistem durumunun bir başlangıç özeti sırasında etkinleştirir.|  
|`EndRundownKeyword`|0x00000100|Sistem durumunun son özeti sırasında etkinleştirir.|  
|`AppDomainResourceManagementRundownKeyword`|0x00000800|Konumundaki kaynak izleme olaylarını toplama sağlar. bir <xref:System.AppDomain> düzey kullanıldığında `StartRundownKeyword` veya `EndRundownKeyword`.|  
|`ThreadingKeyword`|0x00010000|İş parçacığı havuzu olayları koleksiyonunu sağlar.|  
|`OverrideAndSuppressNGenEventsRundownKeyword`|0x00040000|(Bulunan [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve sonraki sürümler.) Yüksek yükünü bastırır `NGenRundownKeyword` anahtar sözcüğü ve NGen modüller içinde yöntemleri için olayları oluşturulmasını engeller. İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], profil oluşturma araçları kullanması gereken `OverrideAndSuppressNGenEventsRundownKeyword` ve `NGenRundownKeyword` birlikte olayları oluşturmayı NGen modüllerinde yöntemleri için durdurmak için. NGen modülleri yöntemleri hakkında bilgi almak için daha verimli NGen pdb kullanmak profil oluşturma aracı sağlar. .NET Framework 4 ve önceki sürümlerde CLR NGen pdb oluşturulmasını desteklemiyor. Bu önceki sürümlerde, CLR değil tanıyacağı `OverrideAndSuppressNGenEventsRundownKeyword` ve işleyecek `NGenRundownKeyword` NGen modülleri yöntemleri için olayları oluşturmak için.|  
|`PerfTrackKeyWord`|0x2000000|Koleksiyonunu etkinleştirir `ModuleDCStart`, `ModuleDCEnd`, `ModuleRangeDCStart`, ve `ModuleRangeDCEnd` olaylar.|  
  
 [Başa dön](#top)  
  
<a name="runtime_combo"></a>   
### <a name="keyword-combinations-for-symbol-resolution-for-the-runtime-provider"></a>Çalışma zamanı sağlayıcısı için simge çözümlemede anahtar sözcüğü birleşimler  
  
|Anahtar sözcükler ve bayrakları|Uygulama etki alanı, derleme, modülü yükleme ve kaldırma olaylarını|Yöntem yükleme ve kaldırma olayları (dışında dinamik olayları)|Dinamik yöntem yük/yok olayları|  
|------------------------|--------------------------------------------------------------|----------------------------------------------------------|-----------------------------------------|  
|`LoaderKeyword`|Yükleme ve kaldırma olaylar.|Yok.|Yok.|  
|`JITKeyword`<br /><br /> (+ `StartEnumerationKeyword` hiçbir şey eklemez)|Yok.|Olayları yükleyin.|Yükleme ve kaldırma olaylar.|  
|`JITKeyword` +<br /><br /> `EndEnumerationKeyword`|Yok.|Yükleme ve kaldırma olaylar.|Yükleme ve kaldırma olaylar.|  
|`NGenKeyword`|Yok.|Yok.|Yok.|  
|`NGenKeyword` +<br /><br /> `StartEnumerationKeyword`|Yok.|Olayları yükleyin.|Yok.|  
|`NGenKeyword` +<br /><br /> `EndEnumerationKeyword`|Yok.|Olayları kaldırın.|Yok.|  
  
 [Başa dön](#top)  
  
<a name="rundown_combo"></a>   
### <a name="keyword-combinations-for-symbol-resolution-for-the-rundown-provider"></a>Sembol Çözümleme Özeti sağlayıcısı için anahtar sözcüğü birleşimler  
  
|Anahtar sözcükler ve bayrakları|Uygulama etki alanı, derleme, modül DCStart/DCEnd olayları|Yöntem DCStart/DCEnd olayları (dinamik yöntem olayları dahil)|  
|------------------------|----------------------------------------------------------------|----------------------------------------------------------------------|  
|`LoaderRundownKeyword` +<br /><br /> `StartRundownKeyword`|`DCStart` olaylar.|Yok.|  
|`LoaderRundownKeyword` +<br /><br /> `EndRundownKeyword`|`DCEnd` olaylar.|Yok.|  
|`JITKeyword` +<br /><br /> `StartRundownKeyword`|Yok.|`DCStart` olaylar.|  
|`JITKeyword` +<br /><br /> `EndRundownKeyword`|Yok.|`DCEnd` olaylar.|  
|`NGenKeyword` +<br /><br /> `StartRundownKeyword`|Yok.|`DCStart` olaylar.|  
|`NGenKeyword` +<br /><br /> `EndRundownKeyword`|Yok.|`DCEnd` olaylar.|  
  
 [Başa dön](#top)  
  
<a name="levels"></a>   
## <a name="etw-event-levels"></a>ETW olay düzeyleri  
 ETW olayları düzeyine göre filtre uygulanabilir. Düzeyi 0x5 ayarlarsanız, olaylar 0x5 dahil olmak üzere tüm düzeylerinde ve (anahtar sözcükleri etkin kategoriye ait olayları olduğu) altında oluşturulur. Düzeyi 0x2 ayarlanmışsa düzeyine 0x2 ve aşağıda ait yalnızca olaylar oluşturulur.  
  
 Düzeyleri şu anlama gelir:  
  
 0x5 - verbose  
  
 0x4 - bilgilendirme  
  
 0x3 - uyarı  
  
 0x2 - hata  
  
 0x1 - kritik  
  
 0x0 - LogAlways  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CLR ETW Sağlayıcılar](../../../docs/framework/performance/clr-etw-providers.md)  
 [CLR ETW Olayları](../../../docs/framework/performance/clr-etw-events.md)  
 [Ortak Dil Çalışma Zamanı Modülünde ETW Olayları](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
