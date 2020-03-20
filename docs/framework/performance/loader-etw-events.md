---
title: Yükleyici ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- loader events [.NET Framework]
- ETW, loader events (CLR)
ms.assetid: cb403cc6-56f8-4609-b467-cdfa09f07909
ms.openlocfilehash: 0f8f96cf73882ef6556e5b9e64cf9adf389a2318
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180558"
---
# <a name="loader-etw-events"></a>Yükleyici ETW Olayları
Bu olaylar, uygulama etki alanlarının, derlemelerin ve modüllerin yüklenmesi ve boşaltılmasıyla ilgili bilgileri toplar.  
  
 Tüm yükleyici olayları `LoaderKeyword` (0x8) anahtar kelimesi altında yükseltilir. Ve `DCStart` `DCEnd` olaylar (0x8) altında `LoaderRundownKeyword` etkin `StartRundown` / `EndRundown` yükseltilir. (Daha fazla bilgi [için, CLR ETW Anahtar Kelimeler ve Düzeyleri](clr-etw-keywords-and-levels.md)bakın.)  

## <a name="application-domain-events"></a>Uygulama Etki Alanı Etkinlikleri
 Aşağıdaki tabloda anahtar kelime ve düzey gösterilmektedir.  
  
|Etkinliği yükseltmek için anahtar kelime|Olay|Düzey|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`(0x8)|`AppDomainLoad_V1` ve `AppDomainUnLoad_V1`|Bilgilendirme (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`AppDomainDCStart_V1`|Bilgilendirme (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`AppDomainDCEnd_V1`|Bilgilendirme (4)|  
  
 Aşağıdaki tabloolay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`AppDomainLoad_V1`(tüm uygulama etki alanları için günlüğe kaydedilmiştir)|156|Bir uygulama etki alanı bir işlemin ömrü boyunca oluşturulduğunda yükseltilir.|  
|`AppDomainUnLoad_V1`|157|Bir uygulama etki alanı bir işlemin ömrü boyunca yok edildiğinde yükseltilir.|  
|`AppDomainDCStart_V1`|157|Başlangıç özeti sırasında uygulama etki alanlarını oyalar.|  
|`AppDomainDCEnd_V1`|158|Bir son özeti sırasında uygulama etki alanlarını oyalar.|  
  
 Aşağıdaki tablo olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|AppDomainID|kazanmak:UInt64|Bir uygulama etki alanı için benzersiz tanımlayıcı.|  
|AppDomainFlags|kazanmak:UInt32|0x1: Varsayılan etki alanı.<br /><br /> 0x2: Çalıştırılabilir.<br /><br /> 0x4: Uygulama etki alanı, bit 28-31: Bu etki alanının paylaşım ilkesi.<br /><br /> 0: Paylaşılan etki alanı.|  
|AppDomainName|kazanmak:UnicodeString|Dostu uygulama etki alanı adı. İşlemin ömrü boyunca değişebilir.|  
|AppDomainIndex|Kazandı:UInt32|Bu uygulama etki alanının dizin.|  
|ClrInstanceID|kazanmak:UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  

## <a name="clr-loader-assembly-events"></a>CLR Yükleyici Montaj Etkinlikleri  
 Aşağıdaki tabloda anahtar kelime ve düzey gösterilmektedir.  
  
|Etkinliği yükseltmek için anahtar kelime|Olay|Düzey|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`(0x8)|`AssemblyLoad` ve `AssemblyUnload`|Bilgilendirme (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`AssemblyDCStart`|Bilgilendirme (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`AssemblyDCEnd`|Bilgilendirme (4)|  
  
 Aşağıdaki tabloolay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`AssemblyLoad_V1`|154|Bir derleme yüklendiğinde yükseltilir.|  
|`AssemblyUnload_V1`|155|Bir derleme boşaltıldığında yükseltilir.|  
|`AssemblyDCStart_V1`|155|Başlangıç özeti sırasında montajları oyalar.|  
|`AssemblyDCEnd_V1`|156|Bir son özeti sırasında derlemeleri osayılar.|  
  
 Aşağıdaki tablo olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|AssemblyID|kazanmak:UInt64|Derleme için benzersiz kimlik.|  
|AppDomainID|kazanmak:UInt64|Bu derlemenin etki alanının kimliği.|  
|BindingID|kazanmak:UInt64|Derleme bağlamayı benzersiz olarak tanımlayan kimlik.|  
|Montaj Bayrakları|kazanmak:UInt32|0x1: Etki alanı nötr montaj.<br /><br /> 0x2: Dinamik montaj.<br /><br /> 0x4: Montaj yerel bir görüntüye sahiptir.<br /><br /> 0x8: Tahsil montaj.|  
|Assemblyname|kazanmak:UnicodeString|Tam nitelikli montaj adı.|  
|ClrInstanceID|kazanmak:UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|

## <a name="module-events"></a>Modül Etkinlikleri
 Aşağıdaki tabloda anahtar kelime ve düzey gösterilmektedir.  
  
|Etkinliği yükseltmek için anahtar kelime|Olay|Düzey|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`(0x8)|`ModuleLoad_V2` ve `ModuleUnload_V2`|Bilgilendirme (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`ModuleDCStart_V2`|Bilgilendirme (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`ModuleDCEnd_V2`|Bilgilendirme (4)|  
||||  
  
 Aşağıdaki tabloolay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`ModuleLoad_V2`|152|Bir modül bir işlemin ömrü boyunca yüklendiğinde yükseltilir.|  
|`ModuleUnload_V2`|153|Bir modül bir işlemin ömrü boyunca boşaltıldığında yükseltilir.|  
|`ModuleDCStart_V2`|153|Başlangıç özeti sırasında modülleri oyalar.|  
|`ModuleDCEnd_V2`|154|Bir son özet sırasında modülleri oyalar.|  
  
 Aşağıdaki tablo olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|ModülID|kazanmak:UInt64|Modül için benzersiz kimlik.|  
|AssemblyID|kazanmak:UInt64|Bu modülün bulunduğu derlemenin kimliği.|  
|Modül Bayrakları|kazanmak:UInt32|0x1: Etki alanı nötr modülü.<br /><br /> 0x2: Modül yerel bir görüntüye sahiptir.<br /><br /> 0x4: Dinamik modül.<br /><br /> 0x8: Manifesto modülü.|  
|Ayrılmış1|kazanmak:UInt32|Ayrılmış alan.|  
|ModuleILPath|kazanmak:UnicodeString|Modül için Microsoft ara dili (MSIL) görüntüsünün yolu veya dinamik bir derleme (null-terminated) ise dinamik modül adı.|  
|ModuleNativePath|kazanmak:UnicodeString|Varsa modül yerel görüntünün yolu (null-terminated).|  
|ClrInstanceID|kazanmak:UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  
|YönetilenPdbSignature|kazanmak:GUID|Yönetilen program veritabanının (PDB) bu modülle eşleşen GUID imzası. (Bkz. Açıklamalar.)|  
|YönetilenPdbAge|kazanmak:UInt32|Bu modülle eşleşen yönetilen PDB'ye yazılan yaş numarası. (Bkz. Açıklamalar.)|  
|YönetilenPdbBuildPath|kazanmak:UnicodeString|Bu modülle eşleşen yönetilen PDB'nin oluşturulduğu konuma giden yol. Bazı durumlarda, bu sadece bir dosya adı olabilir. (Bkz. Açıklamalar.)|  
|NativePdbSignature|kazanmak:GUID|Varsa bu modülle eşleşen Yerel Görüntü Jeneratörü (NGen) PDB'nin GUID imzası. (Bkz. Açıklamalar.)|  
|NativePdbAge|kazanmak:UInt32|Varsa bu modülle eşleşen NGen PDB'ye yazılan yaş numarası. (Bkz. Açıklamalar.)|  
|NativePdbBuildPath|kazanmak:UnicodeString|Varsa, bu modülle eşleşen NGen PDB'nin inşa edildiği konuma giden yol. Bazı durumlarda, bu sadece bir dosya adı olabilir. (Bkz. Açıklamalar.)|  
  
### <a name="remarks"></a>Açıklamalar  
  
- Adlarında "Pdb" bulunan alanlar, profil oluşturma oturumu sırasında yüklenen modüllerle eşleşen PDB'leri bulmak için profil oluşturma araçları tarafından kullanılabilir. Bu alanların değerleri, yüklenen modüllerle eşleşen PDB'lerin bulunmasına yardımcı olmak için normalde hata ayıklayıcılar tarafından kullanılan modülün IMAGE_DIRECTORY_ENTRY_DEBUG bölümlerine yazılan verilere karşılık gelir.  
  
- "ManagedPdb" ile başlayan alan adları, yönetilen derleyici (C# veya Visual Basic derleyicisi gibi) tarafından oluşturulan MSIL modülüne karşılık gelen yönetilen PDB'ye başvurur. Bu PDB yönetilen PDB biçimini kullanır ve dosyalar, satır numaraları ve sembol adları gibi özgün yönetilen kaynak kodundaki öğelerin MSIL modülüne derlenen MSIL öğeleriyle nasıl eşlenecek olduğunu açıklar.  
  
- "NativePdb" ile başlayan alan adları, arayarak `NGEN createPDB`oluşturulan NGen PDB'ye atıfta bulunur. Bu PDB yerel PDB biçimini kullanır ve dosyalar, satır numaraları ve sembol adları gibi özgün yönetilen kaynak kodundaki öğelerin NGen modülünde derlenen yerel öğelerle nasıl eşlenecek olduğunu açıklar.  

## <a name="clr-domain-module-events"></a>CLR Etki Alanı Modülü Etkinlikleri
 Aşağıdaki tabloda anahtar kelime ve düzey gösterilmektedir.  
  
|Etkinliği yükseltmek için anahtar kelime|Olay|Düzey|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword`(0x8)|`DomainModuleLoad_V1`|Bilgilendirme (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `StartRundownKeyword`|`DomainModuleDCStart_V1`|Bilgilendirme (4)|  
|`LoaderRundownKeyword`(0x8) +<br /><br /> `EndRundownKeyword`|`DomainModuleDCEnd_V1`|Bilgilendirme (4)|  
  
 Aşağıdaki tabloolay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`DomainModuleLoad_V1`|151|Bir uygulama etki alanı için bir modül yüklendiğinde yükseltilir.|  
|`DomainModuleDCStart_V1`|151|Başlangıç özeti sırasında bir uygulama etki alanı için yüklenen modülleri oyalar ve tüm uygulama etki alanları için günlüğe kaydedilir.|  
|`DomainModuleDCEnd_V1`|152|Bir son özet sırasında bir uygulama etki alanı için yüklenen modülleri oyalar ve tüm uygulama etki alanları için günlüğe kaydedilir.|  
  
 Aşağıdaki tablo olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|ModülID|kazanmak:UInt64|Bu modülün ait olduğu derlemeyi tanımlar.|  
|AssemblyID|kazanmak:UInt64|Bu modülün bulunduğu derlemenin kimliği.|  
|AppDomainID|kazanmak:UInt64|Bu modülün kullanıldığı uygulama etki alanının kimliği.|  
|Modül Bayrakları|kazanmak:UInt32|0x1: Etki alanı nötr modülü.<br /><br /> 0x2: Modül yerel bir görüntüye sahiptir.<br /><br /> 0x4: Dinamik modül.<br /><br /> 0x8: Manifesto modülü.|  
|Ayrılmış1|kazanmak:UInt32|Ayrılmış alan.|  
|ModuleILPath|kazanmak:UnicodeString|Modül için MSIL görüntüsünün yolu veya dinamik bir derleme (null-terminated) ise dinamik modül adı.|  
|ModuleNativePath|kazanmak:UnicodeString|Varsa modül yerel görüntünün yolu (null-terminated).|  
|ClrInstanceID|kazanmak:UInt16|CLR veya CoreCLR örneği için benzersiz kimlik.|  

## <a name="module-range-events"></a>Modül Aralığı Etkinlikleri
 Aşağıdaki tabloda anahtar kelime ve düzey gösterilmektedir.  
  
|Etkinliği yükseltmek için anahtar kelime|Olay|Düzey|  
|-----------------------------------|-----------|-----------|  
|`PerfTrackKeyWord`)|`ModuleRange`|Bilgilendirme (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCStart`|Bilgilendirme (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCEnd`|Bilgilendirme (4)|  
  
 Aşağıdaki tabloolay bilgilerini gösterir.  
  
|Olay|Olay Kimliği|Açıklama|  
|-----------|--------------|-----------------|  
|`ModuleRange`|158|Yüklü bir Yerel Görüntü Üreteci (NGen) görüntü IBC ile optimize edilmiş ve NGen görüntünün sıcak bölümleri hakkında bilgi içeriyorsa bu olay vardır.|  
|`ModuleRangeDCStart`|160|Bir `ModuleRange` olay bir özetin başında ateşlendi.|  
|`ModuleRangeDCEnd`|161|Bir `ModuleRange` olay bir özetsonunda ateşledi.|  
  
 Aşağıdaki tablo olay verilerini gösterir.  
  
|Alan adı|Veri türü|Açıklama|  
|----------------|---------------|-----------------|  
|ClrInstanceID|kazanmak:UInt16|CLR'nin birden çok örneği yüklendiğinde, bir işlemdeki CLR'nin belirli bir örneğini benzersiz olarak tanımlar.|  
|ModülID|kazanmak:UInt64|Bu modülün ait olduğu derlemeyi tanımlar.|  
|AralıkBaşlangıç|kazanmak:UInt32|Belirtilen aralık türü için aralığın başlangıcını temsil eden modüldeki ofset.|  
|Aralık Boyutu|kazanmak:UInt32|Baytlarda belirtilen aralığın boyutu.|  
|RangeType|kazanmak:UInt32|Soğuk IBC aralıklarını temsil eden tek bir değer, 0x4. Bu alan gelecekte daha fazla değeri temsil edebilir.|  
|AralıkBoyutu1|kazanmak:UInt32|0, hatalı verileri gösterir.|  
|AralıkBaşlangıç2|kazanmak:UnicodeString||  
  
### <a name="remarks"></a>Açıklamalar  
 Bir .NET Framework işleminde yüklü bir NGen görüntüsü IBC `ModuleRange` ile optimize edilmişse, NGen görüntüsündeki sıcak `moduleID` aralıkları içeren olay onun ki ve `ClrInstanceID`.  NGen görüntüsü IBC ile optimize edilmediyse, bu olay günlüğe kaydedilmez. Modül adını belirlemek için, bu olay modül yük ETW olayları ile harmanlanmış olmalıdır.  
  
 Bu olay için yük boyutu değişkendir; `Count` alan, etkinlikte yer alan aralık uzaklıklarının sayısını gösterir.  Bu olay, gerçek aralıkları `IStart` belirlemek için Windows olayı ile harmanlanmış olması gerekir. Bir görüntü yüklendiğinde Windows Image Load olayı günlüğe kaydedilir ve yüklenen görüntünün sanal adresini içerir.  
  
 Modül aralığı olayları, 4'ten büyük veya eşit herhangi bir ETW düzeyi altında ateşlenir ve bilgilendirme olayları olarak sınıflandırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CLR ETW Olayları](clr-etw-events.md)
