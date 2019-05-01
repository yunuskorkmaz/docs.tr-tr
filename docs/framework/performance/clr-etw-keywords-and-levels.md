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
ms.openlocfilehash: ef621d1cbbd04421b392e64f5507fcbe23860465
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788082"
---
# <a name="clr-etw-keywords-and-levels"></a>CLR ETW Anahtar Sözcükleri ve Düzeyler
<a name="top"></a> Windows (ETW) olayları için olay izleme kategorisi ve düzeyi tarafından filtrelenebilir. Olay [CLR ETW anahtar sözcükleri](#keywords) olayları kategoriye göre filtreleme etkinleştirin; bunlar için çalışma zamanı ve Özet sağlayıcılarını bileşimlerde kullanılır. [Olay düzeyleri](#levels) bayrakları tarafından tanımlanır.  
  
<a name="keywords"></a>   
## <a name="clr-etw-keywords"></a>CLR ETW anahtar sözcükleri  
 Anahtar değerler üretmek için birleştirilebilecek bayraklar. Komut satırı yardımcı programlarını çağırdığınızda pratikte, onaltılık değerleri anahtar sözcüklerin yerine anahtar sözcük adlarından kullanırsınız.  
  
 Anahtar sözcükler aşağıdaki tablolarda açıklanmıştır:  
  
- [CLR ETW çalışma zamanı anahtar sözcükleri](#runtime)  
  
- [CLR ETW Özet anahtar sözcükleri](#rundown)  
  
- [Çalışma zamanı sağlayıcısı için Sembol çözümleme için anahtar sözcüğü birleşimleri](#runtime_combo)  
  
- [Anahtar sözcüğü birleşimlerini özeti sağlayıcısının sembol çözümleme için](#rundown_combo)  
  
<a name="runtime"></a>   
### <a name="clr-etw-runtime-keywords"></a>CLR ETW çalışma zamanı anahtar sözcükleri  
 Aşağıdaki tabloda listelenmektedir: CLR ETW çalışma zamanı anahtar sözcükleri, değerlerine ve ne için kullanılır.  
  
|Çalışma zamanı anahtar adı|Değer|Amaç|  
|--------------------------|-----------|-------------|  
|`GCKeyword`|0x00000001|Topluluğunun [çöp toplama olayları](../../../docs/framework/performance/garbage-collection-etw-events.md).|  
|`LoaderKeyword`|0x00000008|Topluluğunun [yükleyici olayları](../../../docs/framework/performance/loader-etw-events.md).|  
|`JITKeyword`|0x00000010|Topluluğunun [just-in-time (JIT) olayları](../../../docs/framework/performance/jit-tracing-etw-events.md).|  
|`NGenKeyword`|0x00000020|Yerel görüntü yöntemleri (yöntemler); yerel Görüntü Oluşturucu tarafından Ngen.exe işlenen olaylar topluluğunun ile kullanılan `StartEnumerationKeyword` ve `EndEnumerationKeyword`. Bu anahtar sözcük yüksek yüke sahiptir. Bu, her bir yöntemde her yüklenmiş bir NGen modülü olaylarını oluşturur. Mümkün olduğunda bu anahtar sözcük kullanmak yerine, NGen modüllerden yöntemleri hakkında bilgi almak için profil oluşturma araçları tarafından oluşturulan program veritabanı (PDB) kullanmanızı öneririz. Ayrıca bkz: `OverrideAndSuppressNGenEventsKeyword` daha sonra bu tablodaki.|  
|`StartEnumerationKeyword`|0x00000040|Çalışma zamanında tüm yöntemlerin etkinleştirir; ile birlikte kullanılan `NGenKeyword`.|  
|`EndEnumerationKeyword`|0x00000080|Çalışma zamanı'nda yok tüm yöntemlerin etkinleştirir; ile birlikte kullanılan `JITKeyword` ve `NGenKeyword`.|  
|`SecurityKeyword`|0x00000400|Topluluğunun [güvenlik olaylarını](../../../docs/framework/performance/security-etw-events.md).|  
|`AppDomainResourceManagementKeyword`|0x00000800|İzleme olayları bir uygulama etki alanı düzeyinde kaynak koleksiyonunu etkinleştirir.|  
|`JITTracingKeyword`|0x00001000|Topluluğunun [JIT izleme olayları](../../../docs/framework/performance/jit-tracing-etw-events.md).|  
|`InteropKeyword`|0x00002000|Topluluğunun [birlikte çalışma olayları](../../../docs/framework/performance/interop-etw-events.md).|  
|`ContentionKeyword`|0x00004000|Topluluğunun [Çekişme olayları](../../../docs/framework/performance/contention-etw-events.md).|  
|`ExceptionKeyword`|0x00008000|Topluluğunun [özel durum olaylarının](../../../docs/framework/performance/exception-thrown-v1-etw-event.md).|  
|`ThreadingKeyword`|0x00010000|Topluluğunun [iş parçacığı havuzu olayları](../../../docs/framework/performance/thread-pool-etw-events.md).|  
|`OverrideAndSuppressNGenEventsKeyword`|0x00040000|(Kullanılabilir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve daha sonra.) Yüksek yükü bastırır `NGenKeyword` anahtar sözcüğü ve NGen modüller içinde yöntemleri için olayları oluşturulmasını engeller. İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], profil oluşturma araçları kullanması gereken `OverrideAndSuppressNGenEventsKeyword` ve `NGenKeyword` birlikte NGen modüllerdeki yöntemleri için olayları oluşturulmasını engellemek için. Bu, daha verimli NGen Pdb'lerin NGen modüllerde yöntemleri hakkında bilgi almak için profil oluşturma aracı sağlar. .NET Framework 4 ve önceki sürümlerinde CLR NGen Pdb'lerin oluşturulmasını desteklemiyor. Bu önceki sürümlerde, CLR algılamayacak `OverrideAndSuppressNGenEventsKeyword` ve işleyecek `NGenKeyword` NGen modüllerde olayları yöntemleri için oluşturulacak.|  
|`PerfTrackKeyWord`|0x2000000|Topluluğunun `ModuleLoad` ve `ModuleRange` olayları.|  
|`StackKeyword`|0x40000000|CLR topluluğunun [yığın izleme olayları](../../../docs/framework/performance/stack-etw-event.md).|  
  
 [Başa dön](#top)  
  
<a name="rundown"></a>   
### <a name="clr-etw-rundown-keywords"></a>CLR ETW Özet anahtar sözcükleri  
 Aşağıdaki tabloda listelenmektedir: Özet CLR ETW anahtar sözcükleri, değerleri ve ne için kullanılır.  
  
|Özet anahtar adı|Değer|Amaç|  
|--------------------------|-----------|-------------|  
|`LoaderRundownKeyword`|0x00000008|Yükleyici olayları ile kullanıldığında topluluğunun `StartRundownKeyword` ve `EndRundownKeyword`.|  
|`JitRundownKeyword`|0x00000010|Yöntem topluluğunun `DCStart` ve `DCEnd` olayları ile kullanıldığında JIT olarak derlenmiş metotlar için `StartRundownKeyword` ve `EndRundownKeyword`.|  
|`NGenRundownKeyword`|0x00000020|Yöntem topluluğunun `DCStart` ve `DCEnd` olayları ile kullanıldığında NGen yerel görüntü yöntemleri için `StartRundownKeyword` ve `EndRundownKeyword`. Bu anahtar sözcük yüksek yüke sahiptir. Bu, her bir yöntemde her yüklenmiş bir NGen modülü olaylarını oluşturur. Mümkün olduğunda bu anahtar sözcük kullanmak yerine, NGen modüllerden yöntemleri hakkında bilgi almak için profil oluşturma araçları tarafından oluşturulan program veritabanı (PDB) kullanmanızı öneririz. Ayrıca bkz: `OverrideAndSuppressNGenEventsRundownKeyword` daha sonra bu tablodaki.|  
|`StartRundownKeyword`|0x00000040|Sistem durumunun bir başlangıç özeti sırasında etkinleştirir.|  
|`EndRundownKeyword`|0x00000100|Sistem durumunun Özet sonu sırasında etkinleştirir.|  
|`AppDomainResourceManagementRundownKeyword`|0x00000800|Kaynak konumunda izleme olaylarını topluluğunun bir <xref:System.AppDomain> düzeyi ile kullanıldığında `StartRundownKeyword` veya `EndRundownKeyword`.|  
|`ThreadingKeyword`|0x00010000|İş parçacığı havuzu olayları toplanmasını etkinleştirir.|  
|`OverrideAndSuppressNGenEventsRundownKeyword`|0x00040000|(Kullanılabilir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve daha sonra.) Yüksek yükü bastırır `NGenRundownKeyword` anahtar sözcüğü ve NGen modüller içinde yöntemleri için olayları oluşturulmasını engeller. İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], profil oluşturma araçları kullanması gereken `OverrideAndSuppressNGenEventsRundownKeyword` ve `NGenRundownKeyword` birlikte NGen modüllerdeki yöntemleri için olayları oluşturulmasını engellemek için. Bu, daha verimli NGen Pdb'lerin NGen modüllerde yöntemleri hakkında bilgi almak için profil oluşturma aracı sağlar. .NET Framework 4 ve önceki sürümlerinde CLR NGen Pdb'lerin oluşturulmasını desteklemiyor. Bu önceki sürümlerde, CLR algılamayacak `OverrideAndSuppressNGenEventsRundownKeyword` ve işleyecek `NGenRundownKeyword` NGen modüllerde olayları yöntemleri için oluşturulacak.|  
|`PerfTrackKeyWord`|0x2000000|Topluluğunun `ModuleDCStart`, `ModuleDCEnd`, `ModuleRangeDCStart`, ve `ModuleRangeDCEnd` olayları.|  
  
 [Başa dön](#top)  
  
<a name="runtime_combo"></a>   
### <a name="keyword-combinations-for-symbol-resolution-for-the-runtime-provider"></a>Çalışma zamanı sağlayıcısı için Sembol çözümleme için anahtar sözcüğü birleşimleri  
  
|Anahtar sözcükleri ve bayrakları|Uygulama etki alanı, derleme, modül yükleme/yüklemeyi kaldırma olayları|Yöntem yükleme/yüklemeyi kaldırma olayları (dışında dinamik olay)|Dinamik yöntem yük/yok etme olayları|  
|------------------------|--------------------------------------------------------------|----------------------------------------------------------|-----------------------------------------|  
|`LoaderKeyword`|Yükleme ve kaldırma olayları.|Yok.|Yok.|  
|`JITKeyword`<br /><br /> (+ `StartEnumerationKeyword` herhangi bir şey eklemez)|Yok.|Olayları yükleyin.|Yükleme ve kaldırma olayları.|  
|`JITKeyword` +<br /><br /> `EndEnumerationKeyword`|Yok.|Yükleme ve kaldırma olayları.|Yükleme ve kaldırma olayları.|  
|`NGenKeyword`|Yok.|Yok.|Geçerli değildir.|  
|`NGenKeyword` +<br /><br /> `StartEnumerationKeyword`|Yok.|Olayları yükleyin.|Geçerli değildir.|  
|`NGenKeyword` +<br /><br /> `EndEnumerationKeyword`|Yok.|Olayları kaldırın.|Geçerli değildir.|  
  
 [Başa dön](#top)  
  
<a name="rundown_combo"></a>   
### <a name="keyword-combinations-for-symbol-resolution-for-the-rundown-provider"></a>Anahtar sözcüğü birleşimlerini özeti sağlayıcısının sembol çözümleme için  
  
|Anahtar sözcükleri ve bayrakları|Uygulama etki alanı, derleme, modül DCStart/DCEnd olayları|Yöntemi DCStart/DCEnd olayları (dinamik yöntem olayları dahil)|  
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
 ETW olayları da düzeyine göre filtrelenebilir. 0x5 düzeyinde ayarlarsanız, olaylar 0x5 dahil olmak üzere tüm düzeylerinde ve (anahtar sözcükleri ile etkin kategorilerine ait olayları olan) altında oluşturulur. 0x2 düzeyinde ayarlarsanız, düzeyine 0x2 ve aşağıda ait yalnızca olaylar oluşturulur.  
  
 Düzeyleri, aşağıdaki anlamlara sahiptir:  
  
 0x5 - verbose  
  
 0x4 - bilgilendirme  
  
 0x3 - uyarı  
  
 0x2 - hata  
  
 0x1 - kritik  
  
 0x0 - LogAlways  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Sağlayıcılar](../../../docs/framework/performance/clr-etw-providers.md)
- [CLR ETW Olayları](../../../docs/framework/performance/clr-etw-events.md)
- [Ortak Dil Çalışma Zamanı Modülünde ETW Olayları](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
