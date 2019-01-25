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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1541c6fa2b1d307fc8e854a67b7cc3068b7bb4d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580726"
---
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType Numaralandırması
Türünü etkilemek için değerler sağlayan `reloc` çağrıda yayılan yönerge [Iceegen::addsectionreloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`srRelocAbsolute`|Yalnızca bir bölüm göreli oluşturur `reloc`, gönderen bir .reloc bölüme hiçbir şey yok.|  
|`srRelocHighLow`|Oluşturur bir `reloc` işaretçi boyutlu konumu. Platforma bağlı olarak bu BASED_HIGHLOW ya da BASED_DIR64 dönüştürülür.|  
|`srRelocHighAdj`|Oluşturur bir `reloc` üst burada alt 16 bit dahil edilecek .reloc tabloda sonraki sözcüğe 32 bit sayı, 16 bit için.|  
|`srRelocMapToken`|Hiçbir şey .reloc bölüme gönderirken bir belirteç Haritası yeniden konumlandırma oluşturur.|  
|`srRelocRelative`|Göreli adres düzeltme değeri olduğunu gösterir.|  
|`srRelocFilePos`|Yalnızca bir bölüm göreli oluşturur `reloc`, gönderen bir .reloc bölüme hiçbir şey yok. Bu `reloc` bölümünde, sanal adres bölümün göreli dosya konumu.|  
|`srRelocCodeRelative`|Bir kod göreli adres düzeltmesi belirtir.|  
|`srRelocIA64Imm64`|Oluşturur bir `reloc` bir IA64 bir 64 bit adresi `movl` yönergesi.|  
|`srRelocDir64`|Oluşturur bir `reloc` 64-bit adresi.|  
|`srRelocIA64PcRel25`|Oluşturmak bir `reloc` bir IA64 25-bit bir PC göreli adresi `br.call` yönergesi.|  
|`srRelocIA64PcRel64`|Oluşturur bir `reloc` bir IA64 bir 64 bit bilgisayar göreli adresi `brl.call` yönergesi.|  
|`srRelocAbsoluteTagged`|30 bit'lik bir bölümü-göreli oluşturur `reloc`etiketli işaretçi değerleri için kullanılır.|  
|`srRelocSentinel`|Bu sabit listesi üzerindeki herhangi bir ek sağlamaya yardımcı olmak için bir sentinel değer iç ağa yansıtılır `reloc` ad dizisi.|  
|`srNoBaseReloc`|Temel yayma değil belirtir `reloc`.|  
|`srRelocPtr`|Bellek öncesi düzeltme içeriğinin bir bölüm yerine bir işaretçi olduğunu belirten bir değer uzaklığı.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [ICeeGen Arabirimi](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [AddSectionReloc Yöntemi](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
