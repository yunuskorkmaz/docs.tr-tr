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
ms.openlocfilehash: f7aa9699e9929608c90020c6b2d66c301fc11955
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732716"
---
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType Numaralandırması

`reloc` [ICeeGen:: AddSectionReloc](iceegen-addsectionreloc-method.md)çağrısında bulunan yönergenin türünü etkilemek için değerler sağlar.  
  
## <a name="syntax"></a>Syntax  
  
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
|`srRelocAbsolute`|Yalnızca bir bölüm-göreli `reloc` , bir. reloc bölümü göndermek için bir öğe gönderir.|  
|`srRelocHighLow`|`reloc`İşaretçi boyutunda bir konum için oluşturur. Bu, platforma bağlı olarak BASED_HIGHLOW veya BASED_DIR64 dönüştürülür.|  
|`srRelocHighAdj`|`reloc`32 bitlik bir sayının ilk 16 biti için bir oluşturur; burada alt 16 bit,. reloc tablosundaki sonraki sözcüğe dahil edilir.|  
|`srRelocMapToken`|Bir. reloc bölümüne hiçbir şey göndermek için bir belirteç eşlemesi konum değişikliği üretir.|  
|`srRelocRelative`|Değerin bir göreli adres düzeltmesi olduğunu gösterir.|  
|`srRelocFilePos`|Yalnızca bir bölüm-göreli `reloc` , bir. reloc bölümü göndermek için bir öğe gönderir. Bu, bölümün `reloc` sanal adresini değil, bölümünün dosya konumuyla ilişkilidir.|  
|`srRelocCodeRelative`|Kod göreli bir adres düzeltmesini belirtir.|  
|`srRelocIA64Imm64`|`reloc`IA64 yönergesinde 64 bitlik bir adres için bir üretir `movl` .|  
|`srRelocDir64`|`reloc`64 bitlik bir adres için bir üretir.|  
|`srRelocIA64PcRel25`|`reloc`IA64 yönergesinde 25 BIT bilgisayar göreli adresi için oluşturun `br.call` .|  
|`srRelocIA64PcRel64`|`reloc`IA64 yönergesinde 64 bitlik BIR bilgisayar göreli adresi için bir üretir `brl.call` .|  
|`srRelocAbsoluteTagged`|Etiketli işaretçi değerleri için kullanılan 30 bitlik bir bölüm-göreli oluşturur `reloc` .|  
|`srRelocSentinel`|Bu sabit listesine yapılan eklerin iç ad dizisine yansıtıldığından emin olmak için Sentinel değeri `reloc` .|  
|`srNoBaseReloc`|Temel bir taban yaymamalıdır `reloc` .|  
|`srRelocPtr`|Bellek ön düzeltme içeriğinin, Bölüm boşluğu yerine bir işaretçi olduğunu gösteren bir değer.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
- [ICeeGen Arabirimi](iceegen-interface.md)
- [AddSectionReloc Yöntemi](iceegen-addsectionreloc-method.md)
