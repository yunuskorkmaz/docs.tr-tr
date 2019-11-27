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
ms.openlocfilehash: efce0c13944b383c42cbff6a6af4795293ee2989
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444163"
---
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType Numaralandırması
[ICeeGen:: AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)çağrısında yayılan `reloc` yönergesinin türünü etkilemek için değerler sağlar.  
  
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
  
## <a name="members"></a>Üyeleri  
  
|Üyesi|Açıklama|  
|------------|-----------------|  
|`srRelocAbsolute`|Bir. reloc bölümüne hiçbir şey göndermek için yalnızca bölüm göreli bir `reloc`oluşturur.|  
|`srRelocHighLow`|İşaretçi boyutunda bir konum için bir `reloc` oluşturur. Bu, platforma bağlı olarak BASED_HIGHLOW veya BASED_DIR64 dönüştürülür.|  
|`srRelocHighAdj`|32 bitlik bir sayının ilk 16 biti için bir `reloc` üretir, burada alt 16 bit,. reloc tablosundaki sonraki sözcüğe dahil edilir.|  
|`srRelocMapToken`|Bir. reloc bölümüne hiçbir şey göndermek için bir belirteç eşlemesi konum değişikliği üretir.|  
|`srRelocRelative`|Değerin bir göreli adres düzeltmesi olduğunu gösterir.|  
|`srRelocFilePos`|Bir. reloc bölümüne hiçbir şey göndermek için yalnızca bölüm göreli bir `reloc`oluşturur. Bu `reloc`, bölümün sanal adresini değil, bölümün dosya konumuyla ilişkilidir.|  
|`srRelocCodeRelative`|Kod göreli bir adres düzeltmesini belirtir.|  
|`srRelocIA64Imm64`|IA64 `movl` yönergesinde 64 bitlik bir adres için `reloc` üretir.|  
|`srRelocDir64`|64 bitlik bir adres için `reloc` üretir.|  
|`srRelocIA64PcRel25`|IA64 `br.call` yönergesinde 25 bit bılgısayar göreli adresi için `reloc` oluşturun.|  
|`srRelocIA64PcRel64`|IA64 `brl.call` yönergesinde 64 bitlik bılgısayar göreli adresi için bir `reloc` oluşturur.|  
|`srRelocAbsoluteTagged`|Etiketli işaretçi değerleri için kullanılan 30 bitlik bölüm göreli `reloc`üretir.|  
|`srRelocSentinel`|Bu sabit listesine yapılan eklerin iç `reloc` adı dizisine yansıtıldığından emin olmak için Sentinel değeri.|  
|`srNoBaseReloc`|Temel `reloc`yaymamalıdır.|  
|`srRelocPtr`|Bellek ön düzeltme içeriğinin, Bölüm boşluğu yerine bir işaretçi olduğunu gösteren bir değer.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [ICeeGen Arabirimi](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [AddSectionReloc Yöntemi](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
