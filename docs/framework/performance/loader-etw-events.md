---
title: "Yükleyici ETW Olayları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- loader events [.NET Framework]
- ETW, loader events (CLR)
ms.assetid: cb403cc6-56f8-4609-b467-cdfa09f07909
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1643e5d645ec6c3ae35b2e57b8cb4f4bcb048379
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="loader-etw-events"></a>Yükleyici ETW Olayları
<a name="top"></a>Bu olaylar, yükleme ve kaldırma uygulama etki alanları, derlemeler ve modüller işlemeyle ilgili bilgi toplayın.  
  
 Tüm yükleyici olayları altında oluşturulan `LoaderKeyword` (0x8) anahtar sözcüğü. `DCStart` Ve `DCEnd` olayları yükseltilmiş altında `LoaderRundownKeyword` (0x8) ile `StartRundown` / `EndRundown` etkin. (Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
 Yükleyici olayları aşağıdaki alt bölümlere:  
  
-   [Uygulama etki alanı olayları](#application_domain_events)  
  
-   [CLR yükleyici derleme olayları](#clr_loader_assembly_events)  
  
-   [Modülü olayları](#module_events)  
  
-   [CLR etki alanı modülü olayları](#clr_domain_module_events)  
  
-   [Modül aralığı olayları](#module_range_events)  
  
<a name="application_domain_events"></a>   
## <a name="application-domain-events"></a>Uygulama etki alanı olayları  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Olay|Düzey|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`(0x8)|`AppDomainLoad_V1`ve`AppDomainUnLoad_V1`|Bilgilendirici (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`AppDomainDCStart_V1`|Bilgilendirici (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`AppDomainDCEnd_V1`|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`AppDomainLoad_V1`(tüm uygulama etki alanları için oturum açmış)|156|Uygulama etki alanı bir işlem ömrü boyunca oluşturulduğunda oluşturulur.|  
|`AppDomainUnLoad_V1`|157|Uygulama etki alanı bir işlem ömrü boyunca yok edildiğinde oluşturulur.|  
|`AppDomainDCStart_V1`|157|Uygulama etki alanları başlangıç özeti sırasında numaralandırır.|  
|`AppDomainDCEnd_V1`|158|Uygulama etki alanları son özeti sırasında numaralandırır.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|AppDomainID|Win: UInt64|Uygulama etki alanı için benzersiz tanımlayıcı.|  
|AppDomainFlags|Win: UInt32|0x1: varsayılan etki alanı.<br /><br /> 0x2: çalıştırılabilir.<br /><br /> 0x4: uygulama etki alanı, 28-31 bit: Bu etki alanı ilkesi paylaşımı.<br /><br /> 0: paylaşılan bir etki alanı.|  
|AppDomainName|Win: UnicodeString|Kolay uygulama etki alanı adı. İşlem ömrü boyunca değişebilir.|  
|AppDomainIndex|Win: UInt32|Bu uygulama etki alanı dizini.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="clr_loader_assembly_events"></a>   
## <a name="clr-loader-assembly-events"></a>CLR yükleyici derleme olayları  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Olay|Düzey|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`(0x8)|`AssemblyLoad`ve`AssemblyUnload`|Bilgilendirici (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`AssemblyDCStart`|Bilgilendirici (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`AssemblyDCEnd`|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`AssemblyLoad_V1`|154|Bir derleme yüklendiğinde oluşturulur.|  
|`AssemblyUnload_V1`|155|Bir derlemeyi kaldırıldığında oluşturuldu.|  
|`AssemblyDCStart_V1`|155|Derleme sırasında başlangıç özeti numaralandırır.|  
|`AssemblyDCEnd_V1`|156|Derleme sırasında son özeti numaralandırır.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|AssemblyID|Win: UInt64|Derleme için benzersiz kimlik.|  
|AppDomainID|Win: UInt64|Bu derleme etki alanının kimliği.|  
|BindingID|Win: UInt64|Derleme bağlama benzersiz olarak tanıtan kimliği.|  
|AssemblyFlags|Win: UInt32|0x1: etki alanı nötr derleme.<br /><br /> 0x2: dinamik derleme.<br /><br /> 0x4: derleme sahip yerel bir görüntü.<br /><br /> 0x8: collectible derleme.|  
|AssemblyName|Win: UnicodeString|Tam nitelikli derleme adı.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="module_events"></a>   
## <a name="module-events"></a>Modülü olayları  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Olay|Düzey|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`(0x8)|`ModuleLoad_V2`ve`ModuleUnload_V2`|Bilgilendirici (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`ModuleDCStart_V2`|Bilgilendirici (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`ModuleDCEnd_V2`|Bilgilendirici (4)|  
||||  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`ModuleLoad_V2`|152|Bir modülü bir işlem ömrü boyunca yüklendiğinde oluşturulur.|  
|`ModuleUnload_V2`|153|Bir modülü bir işlem ömrü boyunca kaldırıldığında oluşturuldu.|  
|`ModuleDCStart_V2`|153|Modülleri başlangıç özeti sırasında numaralandırır.|  
|`ModuleDCEnd_V2`|154|Modülleri son özeti sırasında numaralandırır.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Modül kimliği|Win: UInt64|Modül için benzersiz kimlik.|  
|AssemblyID|Win: UInt64|Bu modül bulunduğu derleme kimliği.|  
|ModuleFlags|Win: UInt32|0x1: etki alanı nötr modülü.<br /><br /> 0x2: modül yerel görüntü sahiptir.<br /><br /> 0x4: dinamik modül.<br /><br /> 0x8: bildirim modül.|  
|Reserved1|Win: UInt32|Ayrılmış alan.|  
|ModuleILPath|Win: UnicodeString|Modüle ya da bir dinamik derleme (boşluksuz) ise dinamik modül adı için Microsoft Ara dili (MSIL) görüntü yolu.|  
|ModuleNativePath|Win: UnicodeString|Modül yerel görüntü, varsa yolunu (boşluksuz).|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
|ManagedPdbSignature|Win: GUID|Bu modül eşleşen yönetilen program veritabanı (PDB) imzasını GUID. (Açıklamalar bakın.)|  
|ManagedPdbAge|Win: UInt32|Bu modül eşleşen yönetilen PDB yazılmış numarası geçerlilik süresi. (Açıklamalar bakın.)|  
|ManagedPdbBuildPath|Win: UnicodeString|Bu modül eşleşen yönetilen PDB burada oluşturulan konum yolu. Bazı durumlarda, bu yalnızca bir dosya adı olabilir. (Açıklamalar bakın.)|  
|NativePdbSignature|Win: GUID|Yerel görüntü varsa bu modül eşleşen oluşturucu (NGen) PDB imzasını GUID. (Açıklamalar bakın.)|  
|NativePdbAge|Win: UInt32|Bu modül eşleşen NGen PDB varsa yazılmış numarası geçerlilik süresi. (Açıklamalar bakın.)|  
|NativePdbBuildPath|Win: UnicodeString|Burada bu modül eşleşen NGen PDB, varsa oluşturulan konum yolu. Bazı durumlarda, bu yalnızca bir dosya adı olabilir. (Açıklamalar bakın.)|  
  
### <a name="remarks"></a>Açıklamalar  
  
-   Adlarında "Pdb" olan alanların profil araçları tarafından profil oluşturma oturumu sırasında yüklenen modülleri eşleşen pdb bulmak için kullanılabilir. Bu alanların değerlerini normalde yüklü modüllerin eşleşen pdb bulmanıza yardım etmek için hata ayıklayıcıları tarafından kullanılan modül IMAGE_DIRECTORY_ENTRY_DEBUG bölümlere yazılan veriler karşılık gelir.  
  
-   "ManagedPdb" ile başlayan alan adları (örneğin, C# veya Visual Basic derleyici) yönetilen derleyici tarafından üretilen MSIL modülü karşılık gelen yönetilen PDB bakın. Bu PDB yönetilen PDB biçimini kullanır ve dosyaları, satır numaralarını ve sembol adları gibi özgün yönetilen kaynak kodu öğelerinden MSIL modüle derlenmiş MSIL öğeleri nasıl eşleneceğine açıklar.  
  
-   NGen çağrılarak oluşturulan PDB "NativePdb" ile başlayan alan adları başvurmak `NGEN createPDB`. Bu PDB yerel PDB biçimini kullanır ve dosyaları, satır numaralarını ve sembol adları gibi özgün yönetilen kaynak kodu öğelerinden NGen modüle derlenmiş yerel öğeleri nasıl eşleneceğine açıklar.  
  
 [Başa dön](#top)  
  
<a name="clr_domain_module_events"></a>   
## <a name="clr-domain-module-events"></a>CLR etki alanı modülü olayları  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Olay|Düzey|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`(0x8)|`DomainModuleLoad_V1`|Bilgilendirici (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`DomainModuleDCStart_V1`|Bilgilendirici (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`DomainModuleDCEnd_V1`|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`DomainModuleLoad_V1`|151|Uygulama etki alanı için bir modül yüklendiğinde oluşturulur.|  
|`DomainModuleDCStart_V1`|151|Uygulama etki alanı için bir başlangıç özeti sırasında yüklenen modülleri numaralandırır ve tüm uygulama etki alanları için günlüğe kaydedilir.|  
|`DomainModuleDCEnd_V1`|152|Uygulama etki alanı için bir bitiş özeti sırasında yüklenen modülleri numaralandırır ve tüm uygulama etki alanları için günlüğe kaydedilir.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Modül kimliği|Win: UInt64|Bu modül ait olduğu derlemenin tanımlar.|  
|AssemblyID|Win: UInt64|Bu modül bulunduğu derleme kimliği.|  
|AppDomainID|Win: UInt64|Bu modül kullanılan uygulama etki alanı kimliği.|  
|ModuleFlags|Win: UInt32|0x1: etki alanı nötr modülü.<br /><br /> 0x2: modül yerel görüntü sahiptir.<br /><br /> 0x4: dinamik modül.<br /><br /> 0x8: bildirim modül.|  
|Reserved1|Win: UInt32|Ayrılmış alan.|  
|ModuleILPath|Win: UnicodeString|Modüle ya da bir dinamik derleme (boşluksuz) ise dinamik modül adı için MSIL görüntü yolu.|  
|ModuleNativePath|Win: UnicodeString|Modül yerel görüntü, varsa yolunu (boşluksuz).|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="module_range_events"></a>   
## <a name="module-range-events"></a>Modül aralığı olayları  
 Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.  
  
|Olay oluşturma için anahtar sözcüğü|Olay|Düzey|  
|-----------------------------------|-----------|-----------|  
|`PerfTrackKeyWord`)|`ModuleRange`|Bilgilendirici (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCStart`|Bilgilendirici (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCEnd`|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`ModuleRange`|158|Bu olay, yüklü bir yerel Görüntü Oluşturucu (NGen) görüntüsü IBC ile iyileştirilmiş ve NGen görüntü dinamik bölümleri hakkında bilgi içeren mevcut olur.|  
|`ModuleRangeDCStart`|160|A `ModuleRange` olay harekete özetlenmiştir başlangıcında.|  
|`ModuleRangeDCEnd`|161|A `ModuleRange` olay harekete özetlenmiştir sonunda.|  
  
 Aşağıdaki tabloda olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Win: UInt16|CLR birden çok örneği yüklenmişse bir işlemde CLR belirli bir örneğini benzersiz olarak tanımlar.|  
|Modül kimliği|Win: UInt64|Bu modül ait olduğu derlemenin tanımlar.|  
|RangeBegin|Win: UInt32|Belirtilen aralık türü aralığının başlangıcını temsil eden modülünde uzaklığı.|  
|RangeSize|Win: UInt32|Belirtilen aralığı bayt cinsinden boyutu.|  
|RangeType|Win: UInt32|Tek bir değer soğuk IBC aralıkları temsil etmek için 0x4. Bu alan daha fazla değer gelecekte temsil edebilir.|  
|RangeSize1|Win: UInt32|0 hatalı veri gösterir.|  
|RangeBegin2|Win: UnicodeString||  
  
### <a name="remarks"></a>Açıklamalar  
 .NET Framework sürecinde yüklenen NGen görüntü IBC ile iyileştirilmiş varsa `ModuleRange` NGen görüntü etkin aralıklardaki içeren olay ile birlikte kaydedilir, `moduleID` ve `ClrInstanceID`.  NGen görüntü ile IBC optimize edilmemiş varsa, bu olay günlüğe değil. Modül adı belirlemek için bu olay modülü yük ETW olayları ile Harmanlanmış gerekir.  
  
 Bu olay yükü boyutu değişkenidir; `Count` alan olayda yer alan aralık uzaklıkları sayısını belirtir.  Bu olay ile Windows Harmanlanmış gereken `IStart` gerçek aralıkları belirlemek için olay. Görüntü yüklenir ve yüklenen görüntü sanal adresini içeren Windows görüntü yük olay günlüğe kaydedilir.  
  
 Modülü aralık olaylarını herhangi ETW düzey 4 eşit veya daha büyük altında tetiklenir ve bilgilendirme olaylarını sınıflandırılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CLR ETW olayları](../../../docs/framework/performance/clr-etw-events.md)
