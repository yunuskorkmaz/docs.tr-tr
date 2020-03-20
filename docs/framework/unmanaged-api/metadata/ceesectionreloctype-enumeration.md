---
title: CeeSectionRelocType Numaralandırması
ms.date: 03/30/2017
api_name:
- CeeSectionRelocType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocType
helpviewer_keywords:
- CeeSectionRelocType enumeration [.NET Framework metadata]
ms.assetid: 124656f6-0dad-4ceb-9043-d3869ab65cde
topic_type:
- apiref
ms.openlocfilehash: 44a84e0752eecc1c694f3b8cf6e568b72b7d0f5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176220"
---
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType Numaralandırması
`reloc` [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)için bir çağrıda yayılan talimat türünü etkilemek için değerler sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum  {  
    srRelocAbsolute,  
    srRelocHighLow          = 3,  
    srRelocHighAdj,
    srRelocMapToken,  
    srRelocRelative,  
    srRelocFilePos,  
    srRelocCodeRelative,  
    srRelocIA64Imm64,  
    srRelocDir64,  
    srRelocIA64PcRel25,  
    srRelocIA64PcRel64,    srRelocAbsoluteTagged,    srRelocSentinel,    srNoBaseReloc       = 0x4000,  
    srRelocPtr          = 0x8000,  
    srRelocAbsolutePtr      = srRelocPtr + srRelocAbsolute,  
    srRelocHighLowPtr       = srRelocPtr + srRelocHighLow,  
    srRelocRelativePtr      = srRelocPtr + srRelocRelative,  
    srRelocIA64Imm64Ptr     = srRelocPtr + srRelocIA64Imm64,  
    srRelocDir64Ptr         = srRelocPtr + srRelocDir64  
    } CeeSectionRelocType;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`srRelocAbsolute`|Yalnızca bir bölüm görelisi `reloc`oluşturur, .reloc bölümüne hiçbir şey göndermez.|  
|`srRelocHighLow`|İşaretçi `reloc` boyutunda bir konum için bir konum oluşturur. Bu platforma bağlı olarak BASED_HIGHLOW veya BASED_DIR64 dönüştürülür.|  
|`srRelocHighAdj`|32 `reloc` bitlik bir sayının en üst 16 biti için bir sayı oluşturur ve burada en alttaki 16 bit .reloc tablosundaki bir sonraki sözcükte yer eder.|  
|`srRelocMapToken`|Bir .reloc bölümüne hiçbir şey göndermeden bir belirteç eşemi yer değiştirme oluşturur.|  
|`srRelocRelative`|Değerin göreceli bir adres düzeltmesi olduğunu gösterir.|  
|`srRelocFilePos`|Yalnızca bir bölüm görelisi `reloc`oluşturur, .reloc bölümüne hiçbir şey göndermez. Bu, `reloc` bölümün sanal adresine değil, bölümün dosya konumuna göredir.|  
|`srRelocCodeRelative`|Kod göreli adres düzeltmesi belirtir.|  
|`srRelocIA64Imm64`|`reloc` ia64 `movl` yönergesinde 64 bitlik bir adres oluşturur.|  
|`srRelocDir64`|64 `reloc` bitlik bir adres oluşturur.|  
|`srRelocIA64PcRel25`|ia64 `reloc` `br.call` yönergesinde 25 bit PC göreli bir adres için bir adres oluşturun.|  
|`srRelocIA64PcRel64`|ia64 `reloc` `brl.call` yönergesinde 64 bit PC göreli bir adres oluşturur.|  
|`srRelocAbsoluteTagged`|Etiketlenmiş işaretçi değerleri için `reloc`kullanılan 30 bitlik bir bölüm görelisi oluşturur.|  
|`srRelocSentinel`|Bu enum a eklemeler iç `reloc` ad dizisine yansıtılır sağlamak için bir sentinel değeri.|  
|`srNoBaseReloc`|Bir baz `reloc`yayan değil belirtir.|  
|`srRelocPtr`|Belleğin ön düzeltme içeriğinin bir bölüm ofset yerine işaretçi olduğunu belirten bir değer.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [ICeeGen Arabirimi](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [AddSectionReloc Yöntemi](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
