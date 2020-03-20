---
title: CLR ETW Anahtar Sözcükleri ve Düzeyler
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW keywords
- CLR ETW levels
- ETW, CLR keywords
- ETW, CLR levels
ms.assetid: fdf5856d-516b-4042-849d-911c4518a6cb
ms.openlocfilehash: 2106ed0d85cd116be4d7c46396ad6e1597c4341d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400066"
---
# <a name="clr-etw-keywords-and-levels"></a>CLR ETW Anahtar Sözcükleri ve Düzeyler
Windows (ETW) olayları için olay izleme kategori ve düzeye göre filtrelenebilir. Olay [CLR ETW Anahtar Kelimeler](#clr-etw-keywords) kategoriye göre olayların filtreleme sağlar; çalışma zamanı ve tükenme sağlayıcıları için kombinasyonlarda kullanılırlar. [Olay düzeyleri](#etw-event-levels) bayraklarla tanımlanır.  
  
## <a name="clr-etw-keywords"></a>CLR ETW Anahtar Kelimeler  
 Anahtar kelimeler, değer oluşturmak için birleştirilebilen bayraklardır. Uygulamada, komut satırı yardımcı hizmetlerini çağırırken anahtar kelime adları yerine anahtar kelimelerin hexadecimal değerlerini kullanırsınız.  
  
 Anahtar kelimeler aşağıdaki tablolarda açıklanmıştır:  
  
- [CLR ETW çalışma zamanı anahtar kelimeleri](#runtime)  
  
- [CLR ETW özeti anahtar kelimeler](#rundown)  
  
- [Çalışma zamanı sağlayıcısı için sembol çözümü için anahtar kelime kombinasyonları](#runtime_combo)  
  
- [Özeti sağlayıcı için sembol çözümü için anahtar kelime kombinasyonları](#rundown_combo)  
  
<a name="runtime"></a>
### <a name="clr-etw-runtime-keywords"></a>CLR ETW Çalışma Zamanı Anahtar Kelimeleri  
 Aşağıdaki tabloda CLR ETW çalışma zamanı anahtar kelimeleri, değerleri ve ne için kullanıldıkları listelenir.  
  
|Çalışma zamanı anahtar kelime adı|Değer|Amaç|  
|--------------------------|-----------|-------------|  
|`GCKeyword`|0x00000001|[Çöp toplama olaylarının](garbage-collection-etw-events.md)toplanmasını sağlar.|  
|`LoaderKeyword`|0x00000008|[Yükleyici olaylarının](loader-etw-events.md)toplanmasını sağlar.|  
|`JITKeyword`|0x00000010|[Tam zamanında (JIT) olayların](jit-tracing-etw-events.md)toplanmasını sağlar.|  
|`NGenKeyword`|0x00000020|Yerel görüntü yöntemleri (Yerel Görüntü Üreteci, Ngen.exe tarafından işlenen yöntemler) için olayların toplanmasını sağlar; ile `StartEnumerationKeyword` kullanılan `EndEnumerationKeyword`ve . Bu anahtar kelimenin yükü yüksek. Yüklenen her NGen modülü nde her yöntem için olaylar oluşturur. Mümkün olduğunda, bu anahtar kelimeyi kullanmak yerine, NGen modüllerinden yöntemler hakkında bilgi almak için profil oluşturma araçları tarafından oluşturulan program veritabanlarını (PDBs) kullanmanızı öneririz. Daha `OverrideAndSuppressNGenEventsKeyword` sonra bu tabloda da bakın.|  
|`StartEnumerationKeyword`|0x00000040|Çalışma zamanında tüm yöntemlerin numaralandırmasını sağlar; ile `NGenKeyword`birlikte kullanılır.|  
|`EndEnumerationKeyword`|0x00000080|Çalışma zamanında yok edilen tüm yöntemlerin numaralandırmasını sağlar; ile `JITKeyword` birlikte kullanılır `NGenKeyword`ve .|  
|`SecurityKeyword`|0x00000400|[Güvenlik olaylarının](security-etw-events.md)toplanmasını sağlar.|  
|`AppDomainResourceManagementKeyword`|0x00000800|Kaynak izleme olaylarının bir uygulama etki alanı düzeyinde toplanmasını sağlar.|  
|`JITTracingKeyword`|0x00001000|[JIT izleme olaylarının](jit-tracing-etw-events.md)toplanmasını sağlar.|  
|`InteropKeyword`|0x00002000|[Interop olayların](interop-etw-events.md)toplanmasını sağlar.|  
|`ContentionKeyword`|0x00004000|[Çekişme olaylarının](contention-etw-events.md)toplanmasını sağlar.|  
|`ExceptionKeyword`|0x00008000|[Özel durum olaylarının](exception-thrown-v1-etw-event.md)toplanmasını sağlar.|  
|`ThreadingKeyword`|0x00010000|[İş parçacığı havuzu olaylarının](thread-pool-etw-events.md)toplanmasını sağlar.|  
|`OverrideAndSuppressNGenEventsKeyword`|0x00040000|(.NET Framework 4.5 ve sonrası adresinde mevcuttur.) Yüksek tepeli `NGenKeyword` anahtar kelimeyi bastırır ve NGen modüllerinin içinde olan yöntemler için olayların oluşmasını engeller. .NET Framework 4.5'ten başlayarak, `OverrideAndSuppressNGenEventsKeyword` profil `NGenKeyword` oluşturma araçları NGen modüllerinde kullanılan yöntemler için olayların oluşumunu bastırmak için birlikte kullanılmalıdır. Bu, profil oluşturma aracının NGen modüllerinde yöntemler hakkında bilgi almak için daha verimli NGen PDB'lerini kullanmasını sağlar. .NET Framework 4 ve önceki sürümlerde clr NGen PDBs oluşturulmasını desteklemez. Bu önceki sürümlerde, CLR `OverrideAndSuppressNGenEventsKeyword` Tanımaz `NGenKeyword` ve NGen modüllerinde yöntemler için olaylar oluşturmak için işlem yapacak.|  
|`PerfTrackKeyWord`|0x2000000|Olayların `ModuleLoad` ve `ModuleRange` olayların toplanmasını sağlar.|  
|`StackKeyword`|0x40000000|CLR yığın izleme [olaylarının](stack-etw-event.md)toplanmasını sağlar.|  
  
<a name="rundown"></a>
### <a name="clr-etw-rundown-keywords"></a>CLR ETW Özeti Anahtar Kelimeler  
 Aşağıdaki tabloda CLR ETW özeti anahtar kelimeleri, değerleri ve ne için kullanıldıkları listelenir.  
  
|Rundown anahtar kelime adı|Değer|Amaç|  
|--------------------------|-----------|-------------|  
|`LoaderRundownKeyword`|0x00000008|Ile kullanıldığında yükleyici olaylarının toplanmasını sağlar `StartRundownKeyword` ve. `EndRundownKeyword`|  
|`JitRundownKeyword`|0x00000010|JIT tarafından derlenen yöntemler için yöntem `DCStart` `DCEnd` `StartRundownKeyword` ve olayların toplanmasını sağlar. `EndRundownKeyword`|  
|`NGenRundownKeyword`|0x00000020|NGen yerel görüntü `DCStart` `DCEnd` yöntemleri ile `StartRundownKeyword` kullanıldığında yöntem ve olayların `EndRundownKeyword`toplanmasını sağlar. Bu anahtar kelimenin yükü yüksek. Yüklenen her NGen modülü nde her yöntem için olaylar oluşturur. Mümkün olduğunda, bu anahtar kelimeyi kullanmak yerine, NGen modüllerinden yöntemler hakkında bilgi almak için profil oluşturma araçları tarafından oluşturulan program veritabanlarını (PDBs) kullanmanızı öneririz. Daha `OverrideAndSuppressNGenEventsRundownKeyword` sonra bu tabloda da bakın.|  
|`StartRundownKeyword`|0x00000040|Başlangıç özeti sırasında sistem durumunun numaralanmasını sağlar.|  
|`EndRundownKeyword`|0x00000100|Bir son özeti sırasında sistem durumunun numaralanmasını sağlar.|  
|`AppDomainResourceManagementRundownKeyword`|0x00000800|Kaynak izleme için olayların bir <xref:System.AppDomain> düzeyde toplanmasını `StartRundownKeyword` sağlar. `EndRundownKeyword`|  
|`ThreadingKeyword`|0x00010000|İş parçacığı havuzu olaylarının toplanmasını sağlar.|  
|`OverrideAndSuppressNGenEventsRundownKeyword`|0x00040000|(.NET Framework 4.5 ve sonrası adresinde mevcuttur.) Yüksek tepeli `NGenRundownKeyword` anahtar kelimeyi bastırır ve NGen modüllerinin içinde olan yöntemler için olayların oluşmasını engeller. .NET Framework 4.5'ten başlayarak, `OverrideAndSuppressNGenEventsRundownKeyword` profil `NGenRundownKeyword` oluşturma araçları NGen modüllerinde kullanılan yöntemler için olayların oluşumunu bastırmak için birlikte kullanılmalıdır. Bu, profil oluşturma aracının NGen modüllerinde yöntemler hakkında bilgi almak için daha verimli NGen PDB'lerini kullanmasını sağlar. .NET Framework 4 ve önceki sürümlerde clr NGen PDBs oluşturulmasını desteklemez. Bu önceki sürümlerde, CLR `OverrideAndSuppressNGenEventsRundownKeyword` Tanımaz `NGenRundownKeyword` ve NGen modüllerinde yöntemler için olaylar oluşturmak için işlem yapacak.|  
|`PerfTrackKeyWord`|0x2000000|`ModuleDCStart`, , `ModuleDCEnd` `ModuleRangeDCStart`ve `ModuleRangeDCEnd` olayların toplanmasını sağlar.|
  
<a name="runtime_combo"></a>
### <a name="keyword-combinations-for-symbol-resolution-for-the-runtime-provider"></a>Çalışma Zamanı Sağlayıcısı için Sembol Çözümü için Anahtar Kelime Kombinasyonları  
  
|Anahtar kelimeler ve bayraklar|Uygulama etki alanı, montaj, modül yükleme/boşaltma olayları|Yöntem yükleme/boşaltma olayları (dinamik olaylar hariç)|Dinamik yöntem olayları yükleme/yok et|  
|------------------------|--------------------------------------------------------------|----------------------------------------------------------|-----------------------------------------|  
|`LoaderKeyword`|Olayları yükleyin ve boşaltın.|Yok.|Yok.|  
|`JITKeyword`<br /><br /> (+ `StartEnumerationKeyword` bir şey eklemez)|Yok.|Olayları yükleyin.|Olayları yükleyin ve boşaltın.|  
|`JITKeyword` +<br /><br /> `EndEnumerationKeyword`|Yok.|Olayları yükleyin ve boşaltın.|Olayları yükleyin ve boşaltın.|  
|`NGenKeyword`|Yok.|Yok.|Geçerli değildir.|  
|`NGenKeyword` +<br /><br /> `StartEnumerationKeyword`|Yok.|Olayları yükleyin.|Geçerli değildir.|  
|`NGenKeyword` +<br /><br /> `EndEnumerationKeyword`|Yok.|Olayları boşaltın.|Geçerli değildir.|  
  
<a name="rundown_combo"></a>
### <a name="keyword-combinations-for-symbol-resolution-for-the-rundown-provider"></a>Rundown Sağlayıcı için Sembol Çözümü için Anahtar Kelime Kombinasyonları  
  
|Anahtar kelimeler ve bayraklar|Uygulama etki alanı, montaj, modül DCStart/DCEnd olayları|Yöntem DCStart/DCEnd olayları (dinamik yöntem olayları dahil)|  
|------------------------|----------------------------------------------------------------|----------------------------------------------------------------------|  
|`LoaderRundownKeyword` +<br /><br /> `StartRundownKeyword`|`DCStart`Olay.|Yok.|  
|`LoaderRundownKeyword` +<br /><br /> `EndRundownKeyword`|`DCEnd`Olay.|Yok.|  
|`JITKeyword` +<br /><br /> `StartRundownKeyword`|Yok.|`DCStart`Olay.|  
|`JITKeyword` +<br /><br /> `EndRundownKeyword`|Yok.|`DCEnd`Olay.|  
|`NGenKeyword` +<br /><br /> `StartRundownKeyword`|Yok.|`DCStart`Olay.|  
|`NGenKeyword` +<br /><br /> `EndRundownKeyword`|Yok.|`DCEnd`Olay.|  

## <a name="etw-event-levels"></a>ETW Etkinlik Düzeyleri  
 ETW olayları da düzeye göre filtrelenebilir. Düzey 0x5 olarak ayarlanırsa, 0x5 ve altındaki (anahtar kelimeler aracılığıyla etkinleştirilen kategorilere ait olaylar) dahil olmak üzere tüm düzeylerdeki olaylar yükseltilir. Seviye 0x2 olarak ayarlanırsa, yalnızca 0x2 ve altındaki düzeye ait olaylar yükseltilir.  
  
 Düzeyleri aşağıdaki anlamları vardır:  
  
 0x5 - Verbose  
  
 0x4 - Bilgilendirme  
  
 0x3 - Uyarı  
  
 0x2 - Hata  
  
 0x1 - Kritik  
  
 0x0 - LogAlways  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Sağlayıcılar](clr-etw-providers.md)
- [CLR ETW Olayları](clr-etw-events.md)
- [Ortak Dil Çalışma Zamanında ETW Olayları](etw-events-in-the-common-language-runtime.md)
