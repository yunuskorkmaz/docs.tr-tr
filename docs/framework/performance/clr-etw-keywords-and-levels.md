---
title: CLR ETW Anahtar Sözcükleri ve Düzeyler
description: Windows için ortak dil çalışma zamanı (CLR) olay izleme (ETW) anahtar sözcüklerini ve düzeylerini gözden geçirin. Olay CLR ETW anahtar sözcükleri, olayların kategoriye göre filtrelenmesini etkinleştirir.
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW keywords
- CLR ETW levels
- ETW, CLR keywords
- ETW, CLR levels
ms.assetid: fdf5856d-516b-4042-849d-911c4518a6cb
ms.openlocfilehash: dfbe047640a3a640cf37adeea6fa3656cfd9ec6d
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309683"
---
# <a name="clr-etw-keywords-and-levels"></a>CLR ETW Anahtar Sözcükleri ve Düzeyler
Windows için olay izleme (ETW) olayları, kategoriye ve düzeye göre filtrelenebilir. Olay [CLR ETW anahtar sözcükleri](#clr-etw-keywords) kategoriye göre olayların filtrelenmesini sağlar; çalışma zamanı ve Özet sağlayıcıları için kombinasyonlarda kullanılırlar. [Olay düzeyleri](#etw-event-levels) bayraklar tarafından tanımlanır.  
  
## <a name="clr-etw-keywords"></a>CLR ETW anahtar sözcükleri  
 Anahtar sözcükler, değerler oluşturmak için birleştirilebilen bayraklardır. Uygulamada, komut satırı yardımcı programlarını çağırdığınızda anahtar sözcük adları yerine anahtar sözcüklerin onaltılık değerlerini kullanırsınız.  
  
 Anahtar sözcükler aşağıdaki tablolarda açıklanmıştır:  
  
- [CLR ETW çalışma zamanı anahtar sözcükleri](#runtime)  
  
- [CLR ETW Özeti anahtar sözcükleri](#rundown)  
  
- [Çalışma zamanı sağlayıcısı için sembol çözümlemesi için anahtar sözcük birleşimleri](#runtime_combo)  
  
- [Özet sağlayıcının sembol çözünürlüğü için anahtar sözcük birleşimleri](#rundown_combo)  
  
<a name="runtime"></a>
### <a name="clr-etw-runtime-keywords"></a>CLR ETW çalışma zamanı anahtar sözcükleri  
 Aşağıdaki tabloda CLR ETW çalışma zamanı anahtar sözcükleri, değerleri ve bunların için kullanıldıkları özellikler listelenmiştir.  
  
|Çalışma zamanı anahtar sözcük adı|Değer|Amaç|  
|--------------------------|-----------|-------------|  
|`GCKeyword`|0x00000001|[Çöp toplama olaylarının](garbage-collection-etw-events.md)toplanmasını mümkün.|  
|`LoaderKeyword`|0x00000008|[Yükleyici olaylarının](loader-etw-events.md)toplanmasını etkinleştirilir.|  
|`JITKeyword`|0x00000010|[Tam zamanında (JIT) olayları](jit-tracing-etw-events.md)toplamayı mümkün.|  
|`NGenKeyword`|0x00000020|Yerel görüntü yöntemlerine yönelik olay koleksiyonunu (Ngen.exe yerel görüntü Oluşturucu tarafından işlenen Yöntemler) sunar; ve ile `StartEnumerationKeyword` kullanılır `EndEnumerationKeyword` . Bu anahtar kelimesinin yüksek bir yükü vardır. Her yüklenen NGen modülünün içindeki her yöntem için olaylar oluşturur. Mümkün olduğunda, bu anahtar sözcüğünü kullanmak yerine, NGen modüllerinden yöntemler hakkında bilgi almak için profil oluşturma araçları tarafından oluşturulan program veritabanlarını (pdb 'leri) kullanmanızı öneririz. `OverrideAndSuppressNGenEventsKeyword`Bu tabloda daha sonra Ayrıca bkz..|  
|`StartEnumerationKeyword`|0x00000040|Çalışma zamanındaki tüm yöntemlerin numaralandırılmasına izin vermez; ile birlikte kullanılır `NGenKeyword` .|  
|`EndEnumerationKeyword`|0x00000080|Çalışma zamanında yok edilecek tüm yöntemlerin numaralandırılmasını sunar; ve ile birlikte kullanılır `JITKeyword` `NGenKeyword` .|  
|`SecurityKeyword`|0x00000400|[Güvenlik olaylarının](security-etw-events.md)toplanmasını mümkün.|  
|`AppDomainResourceManagementKeyword`|0x00000800|Uygulama etki alanı düzeyindeki kaynak izleme olaylarının toplanmasını mümkün bir şekilde sunar.|  
|`JITTracingKeyword`|0x00001000|[JIT izleme olaylarının](jit-tracing-etw-events.md)toplanmasını mümkün.|  
|`InteropKeyword`|0x00002000|[Birlikte çalışma olaylarının](interop-etw-events.md)toplanmasını izin vermez.|  
|`ContentionKeyword`|0x00004000|[Çekişme olaylarının](contention-etw-events.md)toplanmasını mümkün.|  
|`ExceptionKeyword`|0x00008000|[Özel durum olaylarının](exception-thrown-v1-etw-event.md)toplanmasını izin vermez.|  
|`ThreadingKeyword`|0x00010000|[İş parçacığı havuzu olaylarının](thread-pool-etw-events.md)toplanmasını izin vermez.|  
|`OverrideAndSuppressNGenEventsKeyword`|0x00040000|(.NET Framework 4,5 ve üzeri sürümlerde kullanılabilir.) Yüksek tavan `NGenKeyword` anahtar sözcüğünü bastırır ve Ngen modülleri içinde olan yöntemler için olayların oluşturulmasını engeller. .NET Framework 4,5 ' den başlayarak, profil oluşturma araçları, `OverrideAndSuppressNGenEventsKeyword` `NGenKeyword` Ngen modüllerinde yöntemler için olay oluşturmayı bastırmak için ve birlikte kullanılmalıdır. Bu, profil oluşturma aracının NGen modüllerdeki yöntemler hakkında bilgi almak için daha verimli NGen pdb 'leri kullanmasını sağlar. .NET Framework 4 ve önceki sürümlerde CLR, NGen pdb 'leri oluşturmayı desteklemez. Bu önceki sürümlerde CLR tanımaz `OverrideAndSuppressNGenEventsKeyword` ve `NGenKeyword` Ngen modüllerinde yöntemler için olay oluşturmayı işleyecek.|  
|`PerfTrackKeyWord`|0x2000000|`ModuleLoad`Ve olaylarının toplanmasını mümkün `ModuleRange` .|  
|`StackKeyword`|0x40000000|CLR [Stack izleme olaylarının](stack-etw-event.md)toplanmasını etkinleştirilir.|  
  
<a name="rundown"></a>
### <a name="clr-etw-rundown-keywords"></a>CLR ETW Özeti anahtar sözcükleri  
 Aşağıdaki tabloda CLR ETW Özeti anahtar kelimeleri, değerleri ve için kullanıldıkları özellikler listelenmiştir.  
  
|Runaşağı anahtar sözcük adı|Değer|Amaç|  
|--------------------------|-----------|-------------|  
|`LoaderRundownKeyword`|0x00000008|Ve ile kullanıldığında yükleyici olaylarının toplanmasını mümkün bir şekilde `StartRundownKeyword` sunar `EndRundownKeyword` .|  
|`JitRundownKeyword`|0x00000010|`DCStart` `DCEnd` Ve Ile kullanıldığında JIT ile derlenen yöntemler için yöntem ve olay koleksiyonunu sunar `StartRundownKeyword` `EndRundownKeyword` .|  
|`NGenRundownKeyword`|0x00000020|`DCStart` `DCEnd` Ve Ile kullanıldığında NGEN yerel görüntü yöntemlerine yönelik Yöntem ve olay koleksiyonunu etkinleştirilir `StartRundownKeyword` `EndRundownKeyword` . Bu anahtar kelimesinin yüksek bir yükü vardır. Her yüklenen NGen modülünün içindeki her yöntem için olaylar oluşturur. Mümkün olduğunda, bu anahtar sözcüğünü kullanmak yerine, NGen modüllerinden yöntemler hakkında bilgi almak için profil oluşturma araçları tarafından oluşturulan program veritabanlarını (pdb 'leri) kullanmanızı öneririz. `OverrideAndSuppressNGenEventsRundownKeyword`Bu tabloda daha sonra Ayrıca bkz..|  
|`StartRundownKeyword`|0x00000040|Başlangıç özeti sırasında sistem durumunun numaralandırılmasına izin vermez.|  
|`EndRundownKeyword`|0x00000100|Bir son özeti sırasında sistem durumunun numaralandırılmasına izin vermez.|  
|`AppDomainResourceManagementRundownKeyword`|0x00000800|Veya ile kullanıldığında bir düzeyde kaynak izlemeye yönelik olayların toplanmasını mümkün bir <xref:System.AppDomain> şekilde sunar `StartRundownKeyword` `EndRundownKeyword` .|  
|`ThreadingKeyword`|0x00010000|İş parçacığı havuzu olaylarının toplanmasını izin vermez.|  
|`OverrideAndSuppressNGenEventsRundownKeyword`|0x00040000|(.NET Framework 4,5 ve üzeri sürümlerde kullanılabilir.) Yüksek tavan `NGenRundownKeyword` anahtar sözcüğünü bastırır ve Ngen modülleri içinde olan yöntemler için olayların oluşturulmasını engeller. .NET Framework 4,5 ' den başlayarak, profil oluşturma araçları, `OverrideAndSuppressNGenEventsRundownKeyword` `NGenRundownKeyword` Ngen modüllerinde yöntemler için olay oluşturmayı bastırmak için ve birlikte kullanılmalıdır. Bu, profil oluşturma aracının NGen modüllerdeki yöntemler hakkında bilgi almak için daha verimli NGen pdb 'leri kullanmasını sağlar. .NET Framework 4 ve önceki sürümlerde CLR, NGen pdb 'leri oluşturmayı desteklemez. Bu önceki sürümlerde CLR tanımaz `OverrideAndSuppressNGenEventsRundownKeyword` ve `NGenRundownKeyword` Ngen modüllerinde yöntemler için olay oluşturmayı işleyecek.|  
|`PerfTrackKeyWord`|0x2000000|`ModuleDCStart`,, `ModuleDCEnd` `ModuleRangeDCStart` Ve olaylarının toplanmasını mümkün `ModuleRangeDCEnd` .|
  
<a name="runtime_combo"></a>
### <a name="keyword-combinations-for-symbol-resolution-for-the-runtime-provider"></a>Çalışma zamanı sağlayıcısı için sembol çözümlemesi için anahtar sözcük birleşimleri  
  
|Anahtar sözcükler ve bayraklar|Uygulama etki alanı, derleme, modül yükleme/kaldırma olayları|Yöntem yükleme/kaldırma olayları (dinamik olaylar hariç)|Dinamik yöntem yükleme/yok etme olayları|  
|------------------------|--------------------------------------------------------------|----------------------------------------------------------|-----------------------------------------|  
|`LoaderKeyword`|Olayları yükleyin ve kaldırın.|Yok.|Yok.|  
|`JITKeyword`<br /><br /> (+ `StartEnumerationKeyword` hiçbir şey eklemez)|Yok.|Olayları yükle.|Olayları yükleyin ve kaldırın.|  
|`JITKeyword` +<br /><br /> `EndEnumerationKeyword`|Yok.|Olayları yükleyin ve kaldırın.|Olayları yükleyin ve kaldırın.|  
|`NGenKeyword`|Yok.|Yok.|Geçerli değildir.|  
|`NGenKeyword` +<br /><br /> `StartEnumerationKeyword`|Yok.|Olayları yükle.|Geçerli değildir.|  
|`NGenKeyword` +<br /><br /> `EndEnumerationKeyword`|Yok.|Olayları kaldırma.|Geçerli değildir.|  
  
<a name="rundown_combo"></a>
### <a name="keyword-combinations-for-symbol-resolution-for-the-rundown-provider"></a>Özet sağlayıcının sembol çözünürlüğü için anahtar sözcük birleşimleri  
  
|Anahtar sözcükler ve bayraklar|Uygulama etki alanı, derleme, modül DCStart/DCEnd olayları|DCStart/DCEnd olayları yöntemi (dinamik yöntem olayları dahil)|  
|------------------------|----------------------------------------------------------------|----------------------------------------------------------------------|  
|`LoaderRundownKeyword` +<br /><br /> `StartRundownKeyword`|`DCStart`olayları.|Yok.|  
|`LoaderRundownKeyword` +<br /><br /> `EndRundownKeyword`|`DCEnd`olayları.|Yok.|  
|`JITKeyword` +<br /><br /> `StartRundownKeyword`|Yok.|`DCStart`olayları.|  
|`JITKeyword` +<br /><br /> `EndRundownKeyword`|Yok.|`DCEnd`olayları.|  
|`NGenKeyword` +<br /><br /> `StartRundownKeyword`|Yok.|`DCStart`olayları.|  
|`NGenKeyword` +<br /><br /> `EndRundownKeyword`|Yok.|`DCEnd`olayları.|  

## <a name="etw-event-levels"></a>ETW olay düzeyleri  
 ETW olayları da düzeye göre filtrelenebilir. Düzey 0x5 ' de ayarlanırsa, 0x5 ve Below dahil olmak üzere tüm düzeylerin olayları (anahtar sözcükler aracılığıyla etkinleştirilen kategorilere ait olaylar) tetiklenir. Düzey 0x2 ' de ayarlandıysa, yalnızca 0x2 ve aşağıdaki düzeye ait olaylar oluşturulur.  
  
 Düzeyler aşağıdaki anlamlara sahiptir:  
  
 0x5-ayrıntılı  
  
 0x4-bilgilendirici  
  
 0x3-uyarı  
  
 0x2-hata  
  
 0x1-kritik  
  
 0x0-LogAlways  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Sağlayıcılar](clr-etw-providers.md)
- [CLR ETW Olayları](clr-etw-events.md)
- [Ortak Dil Çalışma Zamanında ETW Olayları](etw-events-in-the-common-language-runtime.md)
