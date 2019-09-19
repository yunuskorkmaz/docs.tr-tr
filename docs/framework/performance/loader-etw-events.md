---
title: Yükleyici ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- loader events [.NET Framework]
- ETW, loader events (CLR)
ms.assetid: cb403cc6-56f8-4609-b467-cdfa09f07909
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6177bdff873feb75eb15dba53bcdb5197260fa9d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046400"
---
# <a name="loader-etw-events"></a>Yükleyici ETW Olayları
<a name="top"></a>Bu olaylar, uygulama etki alanlarını, derlemeleri ve modülleri yükleme ve kaldırma ile ilgili bilgiler toplar.  
  
 Tüm yükleyici olayları `LoaderKeyword` (0x8) anahtar sözcüğü altında oluşturulur. `DCStart` `LoaderRundownKeyword` Veolayları,`StartRundown` etkin ile/ (0x8) altındaoluşturulur`EndRundown` . `DCEnd` (Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)  
  
 Yükleyici olayları aşağıdaki bölümlere ayrılmıştır:  
  
- [Uygulama etki alanı olayları](#application_domain_events)  
  
- [CLR yükleyicisi derleme olayları](#clr_loader_assembly_events)  
  
- [Modül olayları](#module_events)  
  
- [CLR etki alanı modülü olayları](#clr_domain_module_events)  
  
- [Modül aralığı olayları](#module_range_events)  
  
<a name="application_domain_events"></a>   
## <a name="application-domain-events"></a>Uygulama etki alanı olayları  
 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.  
  
|Olayı yükseltmek için anahtar sözcük|Olay|Düzey|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`0x8|`AppDomainLoad_V1` ve `AppDomainUnLoad_V1`|Bilgilendirici (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`AppDomainDCStart_V1`|Bilgilendirici (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`AppDomainDCEnd_V1`|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`AppDomainLoad_V1`(tüm uygulama etki alanları için günlüğe kaydedilir)|156|Bir işlemin ömrü boyunca her bir uygulama etki alanı oluşturulduğunda tetiklenir.|  
|`AppDomainUnLoad_V1`|157|Bir işlemin ömrü boyunca her uygulama etki alanı yok edildiğinde tetiklenir.|  
|`AppDomainDCStart_V1`|157|Başlangıç özeti sırasında uygulama etki alanlarını numaralandırır.|  
|`AppDomainDCEnd_V1`|158|Bir son özeti sırasında uygulama etki alanlarını numaralandırır.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|AppDomainID|Win: UInt64|Bir uygulama etki alanı için benzersiz tanımlayıcı.|  
|AppDomainFlags|Win: UInt32|0x1 Varsayılan etki alanı.<br /><br /> 0x2 Yürütülür.<br /><br /> 4, Uygulama etki alanı, bit 28-31: Bu etki alanının ilkesi paylaşılıyor.<br /><br /> 0: Paylaşılan bir etki alanı.|  
|AppDomainName|Win: UnicodeString|Kolay uygulama etki alanı adı. İşlemin ömrü boyunca değişebilir.|  
|Appdomainındex|Win: UInt32|Bu uygulama etki alanının dizini.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
  
 [Başa dön](#top)  
  
<a name="clr_loader_assembly_events"></a>   
## <a name="clr-loader-assembly-events"></a>CLR yükleyicisi derleme olayları  
 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.  
  
|Olayı yükseltmek için anahtar sözcük|Olay|Düzey|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`0x8|`AssemblyLoad` ve `AssemblyUnload`|Bilgilendirici (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`AssemblyDCStart`|Bilgilendirici (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`AssemblyDCEnd`|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`AssemblyLoad_V1`|154|Bir derleme yüklendiğinde tetiklenir.|  
|`AssemblyUnload_V1`|155|Bir derleme kaldırıldığında tetiklenir.|  
|`AssemblyDCStart_V1`|155|Bir başlangıç Özeti sırasında derlemeleri numaralandırır.|  
|`AssemblyDCEnd_V1`|156|Bir son özeti sırasında derlemeleri sıralar.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|AssemblyId|Win: UInt64|Derlemenin benzersiz KIMLIĞI.|  
|AppDomainID|Win: UInt64|Bu derlemenin etki alanının KIMLIĞI.|  
|BindingID|Win: UInt64|Derleme bağlamasını benzersiz bir şekilde tanımlayan KIMLIK.|  
|AssemblyFlags|Win: UInt32|0x1 Etki alanı bağımsız derlemesi.<br /><br /> 0x2 Dinamik derleme.<br /><br /> 4, Derlemenin yerel bir görüntüsü vardır.<br /><br /> 0x8 Toplanabilir derleme.|  
|AssemblyName|Win: UnicodeString|Tam derleme adı.|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
  
 [Başa dön](#top)  
  
<a name="module_events"></a>   
## <a name="module-events"></a>Modül olayları  
 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.  
  
|Olayı yükseltmek için anahtar sözcük|Olay|Düzey|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`0x8|`ModuleLoad_V2` ve `ModuleUnload_V2`|Bilgilendirici (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`ModuleDCStart_V2`|Bilgilendirici (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`ModuleDCEnd_V2`|Bilgilendirici (4)|  
||||  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`ModuleLoad_V2`|152|Bir işlemin ömrü boyunca bir modül yüklendiğinde tetiklenir.|  
|`ModuleUnload_V2`|153|Bir işlem süresince bir modül kaldırıldığında tetiklenir.|  
|`ModuleDCStart_V2`|153|Bir başlangıç Özeti sırasında modülleri numaralandırır.|  
|`ModuleDCEnd_V2`|154|Bir son özeti sırasında modülleri numaralandırır.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Modül kimliği|Win: UInt64|Modülün benzersiz KIMLIĞI.|  
|AssemblyId|Win: UInt64|Bu modülün bulunduğu derlemenin KIMLIĞI.|  
|ModuleFlags|Win: UInt32|0x1 Etki alanı nötr modülü.<br /><br /> 0x2 Modülün yerel bir görüntüsü vardır.<br /><br /> 4, Dinamik modül.<br /><br /> 0x8 Bildirim modülü.|  
|Reserved1|Win: UInt32|Ayrılmış alan.|  
|Moduleılpath|Win: UnicodeString|Modül için Microsoft ara dili (MSIL) görüntüsünün yolu veya dinamik bir derlemedir (null sonlandırılmış).|  
|ModuleNativePath|Win: UnicodeString|Varsa, modül yerel görüntüsünün yolu (null sonlandırılmış).|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
|ManagedPdbSignature|Win: GUID|Bu modülle eşleşen yönetilen program veritabanının (PDB) GUID imzası. (Bkz. açıklamalar.)|  
|ManagedPdbAge|Win: UInt32|Bu modülle eşleşen yönetilen PDB 'ye yazılan yaş numarası. (Bkz. açıklamalar.)|  
|ManagedPdbBuildPath|Win: UnicodeString|Bu modülle eşleşen yönetilen PDB 'nin oluşturulduğu konumun yolu. Bazı durumlarda bu yalnızca bir dosya adı olabilir. (Bkz. açıklamalar.)|  
|NativePdbSignature|Win: GUID|Varsa, bu modülle eşleşen yerel görüntü Oluşturucu (NGen) PDB GUID imzası. (Bkz. açıklamalar.)|  
|NativePdbAge|Win: UInt32|Varsa, bu modülle eşleşen NGen PDB 'ye yazılan yaş numarası. (Bkz. açıklamalar.)|  
|NativePdbBuildPath|Win: UnicodeString|Geçerliyse, bu modülle eşleşen NGen PDB 'nin oluşturulduğu konumun yolu. Bazı durumlarda bu yalnızca bir dosya adı olabilir. (Bkz. açıklamalar.)|  
  
### <a name="remarks"></a>Açıklamalar  
  
- Adlarında "pdb" olan alanlar, profil oluşturma oturumu sırasında yüklenen modüllerle eşleşen pdb 'leri bulmak için profil oluşturma araçları tarafından kullanılabilir. Bu alanların değerleri, normalde hata ayıklayıcılar tarafından, yüklenen modüllerle eşleşen pdb 'leri bulmaya yardımcı olmak için kullanılan modülün IMAGE_DIRECTORY_ENTRY_DEBUG bölümlerine yazılan verilere karşılık gelir.  
  
- "ManagedPdb" ile başlayan alan adları, yönetilen derleyici tarafından oluşturulan ( C# veya Visual Basic Derleyicisi gıbı) MSIL modülüne karşılık gelen yönetilen PDB 'ye başvurur. Bu PDB yönetilen PDB biçimini kullanır ve dosyalar, satır numaraları ve sembol adları gibi orijinal yönetilen kaynak kodundaki öğelerin MSIL modülüne derlenen MSIL öğelerine nasıl eşlendiğini açıklar.  
  
- "NativePdb" ile başlayan alan adları, çağırarak `NGEN createPDB`oluşturulan NGen pdb öğesine başvurur. Bu PDB yerel PDB biçimini kullanır ve dosyalar, satır numaraları ve sembol adları gibi orijinal yönetilen kaynak kodundaki öğelerin NGen modülüne derlenen yerel öğelerle nasıl eşlendiğini açıklar.  
  
 [Başa dön](#top)  
  
<a name="clr_domain_module_events"></a>   
## <a name="clr-domain-module-events"></a>CLR etki alanı modülü olayları  
 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.  
  
|Olayı yükseltmek için anahtar sözcük|Olay|Düzey|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`0x8|`DomainModuleLoad_V1`|Bilgilendirici (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`DomainModuleDCStart_V1`|Bilgilendirici (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`DomainModuleDCEnd_V1`|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`DomainModuleLoad_V1`|151|Bir uygulama etki alanı için bir modül yüklendiğinde tetiklenir.|  
|`DomainModuleDCStart_V1`|151|Başlangıç özeti sırasında bir uygulama etki alanı için yüklenen modülleri numaralandırır ve tüm uygulama etki alanları için günlüğe kaydedilir.|  
|`DomainModuleDCEnd_V1`|152|Bir uygulama etki alanı için yüklenen modülleri, son açılan bir özet sırasında sıralar ve tüm uygulama etki alanları için günlüğe kaydedilir.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Modül kimliği|Win: UInt64|Bu modülün ait olduğu derlemeyi tanımlar.|  
|AssemblyId|Win: UInt64|Bu modülün bulunduğu derlemenin KIMLIĞI.|  
|AppDomainID|Win: UInt64|Bu modülün kullanıldığı uygulama etki alanının KIMLIĞI.|  
|ModuleFlags|Win: UInt32|0x1 Etki alanı nötr modülü.<br /><br /> 0x2 Modülün yerel bir görüntüsü vardır.<br /><br /> 4, Dinamik modül.<br /><br /> 0x8 Bildirim modülü.|  
|Reserved1|Win: UInt32|Ayrılmış alan.|  
|Moduleılpath|Win: UnicodeString|Modül için MSIL görüntüsünün yolu veya dinamik bir derlemedir (null sonlandırılmış).|  
|ModuleNativePath|Win: UnicodeString|Varsa, modül yerel görüntüsünün yolu (null sonlandırılmış).|  
|ClrInstanceID|Win: UInt16|CLR veya CoreCLR örneği için benzersiz KIMLIK.|  
  
 [Başa dön](#top)  
  
<a name="module_range_events"></a>   
## <a name="module-range-events"></a>Modül aralığı olayları  
 Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.  
  
|Olayı yükseltmek için anahtar sözcük|Olay|Düzey|  
|-----------------------------------|-----------|-----------|  
|`PerfTrackKeyWord`)|`ModuleRange`|Bilgilendirici (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCStart`|Bilgilendirici (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCEnd`|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`ModuleRange`|158|Bu olay, yüklü bir yerel görüntü Oluşturucu (NGen) görüntüsü IBC ile iyileştirilildiğinde ve NGen görüntüsünün sık kullanılan bölümleri hakkında bilgi içeriyorsa vardır.|  
|`ModuleRangeDCStart`|160|Bir `ModuleRange` Özeti başlangıcında tetiklenen bir olay.|  
|`ModuleRangeDCEnd`|161|Bir `ModuleRange` Özeti sonunda tetiklenen bir olay.|  
  
 Aşağıdaki tabloda olay verileri gösterilmektedir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Win: UInt16|CLR 'nin birden fazla örneği yüklenirse, bir işlemde CLR 'nin belirli bir örneğini benzersiz şekilde tanımlar.|  
|Modül kimliği|Win: UInt64|Bu modülün ait olduğu derlemeyi tanımlar.|  
|Rangebegın|Win: UInt32|Modüldeki, belirtilen Aralık türü için aralığın başlangıcını temsil eden konum.|  
|RangeSize|Win: UInt32|Belirtilen aralığın bayt cinsinden boyutu.|  
|RangeType|Win: UInt32|Tek bir değer, 0x4, soğuk IBC aralıklarını temsil eder. Bu alan gelecekte daha fazla değer temsil edebilir.|  
|RangeSize1|Win: UInt32|0 bozuk verileri gösterir.|  
|RangeBegin2|Win: UnicodeString||  
  
### <a name="remarks"></a>Açıklamalar  
 .NET Framework bir işlemde yüklü bir Ngen görüntüsü ibc ile iyileştirildiğinden, `ModuleRange` Ngen görüntüsündeki etkin aralıkları içeren olay, `moduleID` ve `ClrInstanceID`ile birlikte kaydedilir.  NGen resmi IBC ile iyileştirilmemişse bu olay günlüğe kaydedilmez. Modül adını öğrenmek için, bu olay modül yük ETW olayları ile harmanlanmalıdır.  
  
 Bu olay için yük boyutu değişkendir; `Count` alan, olayda yer alan Aralık uzaklıksayısını gösterir.  Bu olay, gerçek aralıkları belirlemede Windows `IStart` olayı ile harmanlanmalıdır. Windows görüntü yükleme olayı, bir görüntü her yüklendiğinde günlüğe kaydedilir ve yüklenen görüntünün sanal adresini içerir.  
  
 Modül aralığı olayları, 4 ' ten büyük veya buna eşit olan ve bilgilendirici olaylar olarak sınıflandırılan herhangi bir ETW düzeyi altında tetiklenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](clr-etw-events.md)
