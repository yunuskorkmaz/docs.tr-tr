---
title: Yükleyici ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- loader events [.NET Framework]
- ETW, loader events (CLR)
ms.assetid: cb403cc6-56f8-4609-b467-cdfa09f07909
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87ec70b2b27c8886ac9b567498d75f9294437bed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949272"
---
# <a name="loader-etw-events"></a>Yükleyici ETW Olayları
<a name="top"></a> Bu olaylar, yükleme ve kaldırma uygulama etki alanları, derlemeler ve modüller için ilgili bilgileri toplayın.  
  
 Altında oluşturulan tüm yükleyici olayları `LoaderKeyword` (0x8) anahtar sözcüğü. `DCStart` Ve `DCEnd` altında tetiklenen olayları `LoaderRundownKeyword` (0x8) ile `StartRundown` / `EndRundown` etkin. (Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
 Yükleyici olayları aşağıdaki alt bölümlere:  
  
- [Uygulama etki alanı olayları](#application_domain_events)  
  
- [CLR yükleyici derleme olayları](#clr_loader_assembly_events)  
  
- [Modülü olayları](#module_events)  
  
- [CLR etki alanı modülü olayları](#clr_domain_module_events)  
  
- [Aralık modülü olayları](#module_range_events)  
  
<a name="application_domain_events"></a>   
## <a name="application-domain-events"></a>Uygulama etki alanı olayları  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Olay|Düzey|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`AppDomainLoad_V1` ve `AppDomainUnLoad_V1`|Bilgilendirici (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`AppDomainDCStart_V1`|Bilgilendirici (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`AppDomainDCEnd_V1`|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`AppDomainLoad_V1` (tüm uygulama etki alanları için oturum açmış)|156|Her uygulama etki alanı, bir işlem yaşam süresi boyunca oluşturulduğunda oluşturulur.|  
|`AppDomainUnLoad_V1`|157|Uygulama etki alanı bir işlem yaşam süresi boyunca yok edildiğinde oluşturulur.|  
|`AppDomainDCStart_V1`|157|Uygulama etki alanları sırasında başlangıç özeti numaralandırır.|  
|`AppDomainDCEnd_V1`|158|Uygulama etki alanları sırasında süre sonu numaralandırır.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|AppDomainID|Kazanma: UInt64|Uygulama etki alanı için benzersiz tanımlayıcı.|  
|AppDomainFlags|Kazanma: UInt32|0x1: Varsayılan etki alanı.<br /><br /> 0x2: Yürütülebilir.<br /><br /> 0x4: Uygulama etki alanı, 28-31 bit: Bu etki alanı ilkesi paylaşma.<br /><br /> 0: Paylaşılan bir etki alanı.|  
|AppDomainName|Kazanma: UnicodeString|Kolay uygulama etki alanı adı. İşlem ömrü sırasında değişebilir.|  
|AppDomainIndex|Win:UInt32|Bu uygulama etki alanı dizini.|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="clr_loader_assembly_events"></a>   
## <a name="clr-loader-assembly-events"></a>CLR yükleyici derleme olayları  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Olay|Düzey|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`AssemblyLoad` ve `AssemblyUnload`|Bilgilendirici (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`AssemblyDCStart`|Bilgilendirici (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`AssemblyDCEnd`|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`AssemblyLoad_V1`|154|Bir derleme yüklendiğinde oluşturulur.|  
|`AssemblyUnload_V1`|155|Bir derlemeyi kaldırıldığında oluşturulur.|  
|`AssemblyDCStart_V1`|155|Başlangıç özeti sırasında derlemeleri listeler.|  
|`AssemblyDCEnd_V1`|156|Bir Özet sonu sırasında derlemeleri listeler.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|AssemblyID|Kazanma: UInt64|Derleme için benzersiz kimliği.|  
|AppDomainID|Kazanma: UInt64|Bu derlemenin etki alanı kimliği.|  
|BindingID|Kazanma: UInt64|Derleme bağlama benzersiz olarak tanımlayan kimliği.|  
|AssemblyFlags|Kazanma: UInt32|0x1: Etki alanı nötr derleme.<br /><br /> 0x2: Dinamik derleme.<br /><br /> 0x4: Derleme yerel görüntü sahiptir.<br /><br /> 0x8: Toplanabilir derleme.|  
|AssemblyName|Kazanma: UnicodeString|Tam derleme adı.|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="module_events"></a>   
## <a name="module-events"></a>Modülü olayları  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Olay|Düzey|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`ModuleLoad_V2` ve `ModuleUnload_V2`|Bilgilendirici (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`ModuleDCStart_V2`|Bilgilendirici (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`ModuleDCEnd_V2`|Bilgilendirici (4)|  
||||  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`ModuleLoad_V2`|152|Bir işlem yaşam süresi boyunca bir modül yüklendiğinde oluşturulur.|  
|`ModuleUnload_V2`|153|Bir modülü bir işlem yaşam süresi boyunca kaldırıldığında oluşturulur.|  
|`ModuleDCStart_V2`|153|Modüller sırasında başlangıç özeti numaralandırır.|  
|`ModuleDCEnd_V2`|154|Modüller sırasında süre sonu numaralandırır.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Modül kimliği|Kazanma: UInt64|Modül için benzersiz kimliği.|  
|AssemblyID|Kazanma: UInt64|Bu modül bulunduğu derleme kimliği.|  
|ModuleFlags|Kazanma: UInt32|0x1: Etki alanı nötr modülü.<br /><br /> 0x2: Modül bir doğal görüntü içerir.<br /><br /> 0x4: Dinamik modül.<br /><br /> 0x8: Modül bildirimindeki.|  
|Reserved1|Kazanma: UInt32|Ayrılmış alan.|  
|ModuleILPath|Kazanma: UnicodeString|Modül veya dinamik bir derleme (null ile sonlandırılmış) ise dinamik modül adı için Microsoft Ara dili (MSIL) görüntü yolu.|  
|ModuleNativePath|Kazanma: UnicodeString|Yol görüntünün modülü yerel varsa (boşluksuz).|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
|ManagedPdbSignature|Kazanma: GUID|Bu modül eşleşen yönetilen program veritabanı (PDB) GUID imzası. (Açıklamalara bakın.)|  
|ManagedPdbAge|Kazanma: UInt32|Bu modül eşleşen yönetilen PDB yazılan numarası geçerlilik süresi. (Açıklamalara bakın.)|  
|ManagedPdbBuildPath|Kazanma: UnicodeString|Bu modül eşleşen yönetilen PDB burada oluşturulmuş konumu yolu. Bazı durumlarda, bu yalnızca bir dosya adı olabilir. (Açıklamalara bakın.)|  
|NativePdbSignature|Kazanma: GUID|Yerel görüntü varsa bu modül eşleşen oluşturucu (NGen) PDB imzası GUID. (Açıklamalara bakın.)|  
|NativePdbAge|Kazanma: UInt32|Bu modül eşleşen NGen PDB'ye yazılmaz numarası geçerlilik süresi. (Açıklamalara bakın.)|  
|NativePdbBuildPath|Kazanma: UnicodeString|Burada bu modül eşleşen NGen PDB, varsa oluşturulmuş konumu yolu. Bazı durumlarda, bu yalnızca bir dosya adı olabilir. (Açıklamalara bakın.)|  
  
### <a name="remarks"></a>Açıklamalar  
  
- "Pdb" adlarında sahip alanlar profil oluşturma araçları tarafından profil oluşturma oturumu sırasında yüklenen modülleri eşleşen pdb bulmak için kullanılabilir. Bu alanların değerlerini normalde yüklü modüllerin eşleşen pdb bulmak için hata ayıklayıcıları tarafından kullanılan modül IMAGE_DIRECTORY_ENTRY_DEBUG bölümlere yazılan veriler karşılık gelir.  
  
- Yönetilen derleyici tarafından oluşturulan MSIL modülü için karşılık gelen yönetilen PDB "ManagedPdb" ile başlayan alan adları bakın (gibi C# veya Visual Basic Derleyicisi). Bu PDB yönetilen PDB biçimi kullanır ve özgün yönetilen kaynak kodu, dosya ve satır numaralarını sembol adları gibi öğeleri MSIL modülü ile derlenmiş MSIL öğeleri nasıl eşleneceğine açıklar.  
  
- NGen çağrılarak oluşturulan PDB "NativePdb" ile başlayan alan adları başvurmak `NGEN createPDB`. Bu PDB yerel PDB biçimi kullanır ve özgün yönetilen kaynak kodu, dosya ve satır numaralarını sembol adları gibi öğeleri NGen modüle derlenmiş yerel öğeleri nasıl eşleneceğine açıklar.  
  
 [Başa dön](#top)  
  
<a name="clr_domain_module_events"></a>   
## <a name="clr-domain-module-events"></a>CLR etki alanı modülü olayları  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Olay|Düzey|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|Bilgilendirici (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`DomainModuleDCStart_V1`|Bilgilendirici (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`DomainModuleDCEnd_V1`|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`DomainModuleLoad_V1`|151|Bir uygulama etki alanı için bir modül yüklendiğinde oluşturulur.|  
|`DomainModuleDCStart_V1`|151|Bir uygulama etki alanı için bir başlangıç özeti sırasında yüklenen modülleri numaralandırır ve tüm uygulama etki alanları için günlüğe kaydedilir.|  
|`DomainModuleDCEnd_V1`|152|Bir uygulama etki alanı için bir Özet sonu sırasında yüklenen modülleri numaralandırır ve tüm uygulama etki alanları için günlüğe kaydedilir.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|Modül kimliği|Kazanma: UInt64|Bu modül ait olduğu bütünleştirilmiş kodu tanımlar.|  
|AssemblyID|Kazanma: UInt64|Bu modül bulunduğu derleme kimliği.|  
|AppDomainID|Kazanma: UInt64|Bu modül kullanıldığı uygulama etki alanı kimliği.|  
|ModuleFlags|Kazanma: UInt32|0x1: Etki alanı nötr modülü.<br /><br /> 0x2: Modül bir doğal görüntü içerir.<br /><br /> 0x4: Dinamik modül.<br /><br /> 0x8: Modül bildirimindeki.|  
|Reserved1|Kazanma: UInt32|Ayrılmış alan.|  
|ModuleILPath|Kazanma: UnicodeString|Modül veya dinamik bir derleme (null ile sonlandırılmış) ise dinamik modül adı için MSIL görüntüsü yolu.|  
|ModuleNativePath|Kazanma: UnicodeString|Yol görüntünün modülü yerel varsa (boşluksuz).|  
|ClrInstanceID|Kazanma: UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
  
 [Başa dön](#top)  
  
<a name="module_range_events"></a>   
## <a name="module-range-events"></a>Aralık modülü olayları  
 Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.  
  
|Olayı için anahtar sözcüğü|Olay|Düzey|  
|-----------------------------------|-----------|-----------|  
|`PerfTrackKeyWord`)|`ModuleRange`|Bilgilendirici (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCStart`|Bilgilendirici (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCEnd`|Bilgilendirici (4)|  
  
 Aşağıdaki tabloda, olay bilgileri gösterilmektedir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`ModuleRange`|158|Bu olay, yüklenen Native Image Generator (NGen) görüntü ile IBC iyileştirilmiştir ve NGen resmi sık erişimli bölümleri hakkında bilgi içeren mevcut olur.|  
|`ModuleRangeDCStart`|160|A `ModuleRange` olay harekete bir özeti başında.|  
|`ModuleRangeDCEnd`|161|A `ModuleRange` olay harekete bir özeti sonunda.|  
  
 Aşağıdaki tabloda, olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Kazanma: UInt16|CLR'nin birden çok örneği yüklenmişse bir işlemde CLR'nin belirli bir örneğini benzersiz şekilde tanımlar.|  
|Modül kimliği|Kazanma: UInt64|Bu modül ait olduğu bütünleştirilmiş kodu tanımlar.|  
|RangeBegin|Kazanma: UInt32|Belirtilen aralık türü için Aralık başlangıcını temsil eden modüldeki uzaklığı.|  
|RangeSize|Kazanma: UInt32|Belirtilen aralık bayt cinsinden boyutu.|  
|RangeType|Kazanma: UInt32|Tek bir değer olarak 0x4, soğuk IBC aralıklarını temsil etmek için. Bu alan, gelecekte daha fazla değer gösterebilir.|  
|RangeSize1|Kazanma: UInt32|0, bozuk veriler gösterir.|  
|RangeBegin2|Kazanma: UnicodeString||  
  
### <a name="remarks"></a>Açıklamalar  
 Bir .NET Framework işlemdeki yüklenmiş bir NGen görüntü IBC ile iyileştirilmiştir, `ModuleRange` NGen görüntüde sık erişimli aralıkları içeren olay ile birlikte kaydedilir, `moduleID` ve `ClrInstanceID`.  NGen resmi ile IBC optimize edilmemiş varsa, bu olay günlüğe değil. Modül adı belirlemek için bu olay modülü yük ETW olayları ile Harmanlanmış gerekir.  
  
 Bu olay yükü boyutu değişkenidir; `Count` alanı aralığı uzaklık olayda yer alan sayısını belirtir.  Bu olay ile Windows harmanlanmasını sahip `IStart` gerçek aralıkları belirlemek için olay. Görüntü yüklenir ve yüklenen görüntü sanal adresini içeren her Windows görüntü yükleme olayı günlüğe kaydedilir.  
  
 Modülü aralık olaylarını altında herhangi bir ETW düzeyi en az 4 tetiklenir ve bilgilendirici bir olay olarak sınıflandırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](../../../docs/framework/performance/clr-etw-events.md)
