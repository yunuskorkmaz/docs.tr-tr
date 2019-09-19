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
ms.openlocfilehash: dce8c58f94c66bcf2336d3708ebc64699148d556
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046714"
---
# <a name="clr-etw-keywords-and-levels"></a>CLR ETW Anahtar Sözcükleri ve Düzeyler
<a name="top"></a>Windows için olay izleme (ETW) olayları, kategoriye ve düzeye göre filtrelenebilir. Olay [CLR ETW anahtar sözcükleri](#keywords) kategoriye göre olayların filtrelenmesini sağlar; çalışma zamanı ve Özet sağlayıcıları için kombinasyonlarda kullanılırlar. [Olay düzeyleri](#levels) bayraklar tarafından tanımlanır.  
  
<a name="keywords"></a>   
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
|`NGenKeyword`|0x00000020|Yerel görüntü yöntemlerine yönelik olayların toplanmasını (yerel görüntü Oluşturucu, Ngen. exe tarafından işlenen Yöntemler) sunar; `StartEnumerationKeyword` ve`EndEnumerationKeyword`ile kullanılır. Bu anahtar kelimesinin yüksek bir yükü vardır. Her yüklenen NGen modülünün içindeki her yöntem için olaylar oluşturur. Mümkün olduğunda, bu anahtar sözcüğünü kullanmak yerine, NGen modüllerinden yöntemler hakkında bilgi almak için profil oluşturma araçları tarafından oluşturulan program veritabanlarını (pdb 'leri) kullanmanızı öneririz. Bu tabloda `OverrideAndSuppressNGenEventsKeyword` daha sonra Ayrıca bkz.|  
|`StartEnumerationKeyword`|0x00000040|Çalışma zamanındaki tüm yöntemlerin numaralandırılmasına izin vermez; ile `NGenKeyword`birlikte kullanılır.|  
|`EndEnumerationKeyword`|0x00000080|Çalışma zamanında yok edilecek tüm yöntemlerin numaralandırılmasını sunar; `JITKeyword` ve`NGenKeyword`ile birlikte kullanılır.|  
|`SecurityKeyword`|0x00000400|[Güvenlik olaylarının](security-etw-events.md)toplanmasını mümkün.|  
|`AppDomainResourceManagementKeyword`|0x00000800|Uygulama etki alanı düzeyindeki kaynak izleme olaylarının toplanmasını mümkün bir şekilde sunar.|  
|`JITTracingKeyword`|0x00001000|[JIT izleme olaylarının](jit-tracing-etw-events.md)toplanmasını mümkün.|  
|`InteropKeyword`|0x00002000|[Birlikte çalışma olaylarının](interop-etw-events.md)toplanmasını izin vermez.|  
|`ContentionKeyword`|0x00004000|[Çekişme olaylarının](contention-etw-events.md)toplanmasını mümkün.|  
|`ExceptionKeyword`|0x00008000|[Özel durum olaylarının](exception-thrown-v1-etw-event.md)toplanmasını izin vermez.|  
|`ThreadingKeyword`|0x00010000|[İş parçacığı havuzu olaylarının](thread-pool-etw-events.md)toplanmasını izin vermez.|  
|`OverrideAndSuppressNGenEventsKeyword`|0x00040000|(.NET Framework 4,5 ve üzeri sürümlerde kullanılabilir.) Yüksek tavan `NGenKeyword` anahtar sözcüğünü bastırır ve Ngen modülleri içinde olan yöntemler için olayların oluşturulmasını engeller. .NET Framework 4,5 ' den başlayarak, profil oluşturma araçları `OverrideAndSuppressNGenEventsKeyword` , Ngen modüllerinde yöntemler için olay oluşturmayı bastırmak için ve `NGenKeyword` birlikte kullanılmalıdır. Bu, profil oluşturma aracının NGen modüllerdeki yöntemler hakkında bilgi almak için daha verimli NGen pdb 'leri kullanmasını sağlar. .NET Framework 4 ve önceki sürümlerde CLR, NGen pdb 'leri oluşturmayı desteklemez. Bu önceki sürümlerde clr tanımaz `OverrideAndSuppressNGenEventsKeyword` ve Ngen modüllerinde yöntemler için olay oluşturmayı işleyecek. `NGenKeyword`|  
|`PerfTrackKeyWord`|0x2000000|`ModuleLoad` Ve`ModuleRange` olaylarının toplanmasını mümkün.|  
|`StackKeyword`|0x40000000|CLR [Stack izleme olaylarının](stack-etw-event.md)toplanmasını etkinleştirilir.|  
  
 [Başa dön](#top)  
  
<a name="rundown"></a>   
### <a name="clr-etw-rundown-keywords"></a>CLR ETW Özeti anahtar sözcükleri  
 Aşağıdaki tabloda CLR ETW Özeti anahtar kelimeleri, değerleri ve için kullanıldıkları özellikler listelenmiştir.  
  
|Runaşağı anahtar sözcük adı|Değer|Amaç|  
|--------------------------|-----------|-------------|  
|`LoaderRundownKeyword`|0x00000008|`StartRundownKeyword` Ve`EndRundownKeyword`ile kullanıldığında yükleyici olaylarının toplanmasını mümkün bir şekilde sunar.|  
|`JitRundownKeyword`|0x00000010|Ve `DCStart` `DCEnd` `StartRundownKeyword` ile kullanıldığında JIT ile derlenen yöntemler için yöntem ve olay koleksiyonunu sunar. `EndRundownKeyword`|  
|`NGenRundownKeyword`|0x00000020|`DCStart` `DCEnd` Ve ile`StartRundownKeyword`kullanıldığında NGEN yerel görüntü yöntemlerine yönelik Yöntem ve olay koleksiyonunu etkinleştirilir. `EndRundownKeyword` Bu anahtar kelimesinin yüksek bir yükü vardır. Her yüklenen NGen modülünün içindeki her yöntem için olaylar oluşturur. Mümkün olduğunda, bu anahtar sözcüğünü kullanmak yerine, NGen modüllerinden yöntemler hakkında bilgi almak için profil oluşturma araçları tarafından oluşturulan program veritabanlarını (pdb 'leri) kullanmanızı öneririz. Bu tabloda `OverrideAndSuppressNGenEventsRundownKeyword` daha sonra Ayrıca bkz.|  
|`StartRundownKeyword`|0x00000040|Başlangıç özeti sırasında sistem durumunun numaralandırılmasına izin vermez.|  
|`EndRundownKeyword`|0x00000100|Bir son özeti sırasında sistem durumunun numaralandırılmasına izin vermez.|  
|`AppDomainResourceManagementRundownKeyword`|0x00000800|Veya `StartRundownKeyword` <xref:System.AppDomain> ilekullanıldığındabirdüzeydekaynakizlemeyeyönelikolaylarıntoplanmasınımümkünbirşekildesunar.`EndRundownKeyword`|  
|`ThreadingKeyword`|0x00010000|İş parçacığı havuzu olaylarının toplanmasını izin vermez.|  
|`OverrideAndSuppressNGenEventsRundownKeyword`|0x00040000|(.NET Framework 4,5 ve üzeri sürümlerde kullanılabilir.) Yüksek tavan `NGenRundownKeyword` anahtar sözcüğünü bastırır ve Ngen modülleri içinde olan yöntemler için olayların oluşturulmasını engeller. .NET Framework 4,5 ' den başlayarak, profil oluşturma araçları `OverrideAndSuppressNGenEventsRundownKeyword` , Ngen modüllerinde yöntemler için olay oluşturmayı bastırmak için ve `NGenRundownKeyword` birlikte kullanılmalıdır. Bu, profil oluşturma aracının NGen modüllerdeki yöntemler hakkında bilgi almak için daha verimli NGen pdb 'leri kullanmasını sağlar. .NET Framework 4 ve önceki sürümlerde CLR, NGen pdb 'leri oluşturmayı desteklemez. Bu önceki sürümlerde clr tanımaz `OverrideAndSuppressNGenEventsRundownKeyword` ve Ngen modüllerinde yöntemler için olay oluşturmayı işleyecek. `NGenRundownKeyword`|  
|`PerfTrackKeyWord`|0x2000000|`ModuleDCStart` ,`ModuleDCEnd`, Ve olaylarının`ModuleRangeDCEnd` toplanmasını mümkün. `ModuleRangeDCStart`|  
  
 [Başa dön](#top)  
  
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
  
 [Başa dön](#top)  
  
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
  
 [Başa dön](#top)  
  
<a name="levels"></a>   
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
- [Ortak Dil Çalışma Zamanı Modülünde ETW Olayları](etw-events-in-the-common-language-runtime.md)
