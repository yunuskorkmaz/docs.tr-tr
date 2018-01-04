---
title: "CeeSectionRelocType Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CeeSectionRelocType
api_location: mscoree.dll
api_type: COM
f1_keywords: CeeSectionRelocType
helpviewer_keywords: CeeSectionRelocType enumeration [.NET Framework metadata]
ms.assetid: 124656f6-0dad-4ceb-9043-d3869ab65cde
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d257778a9a05e2654d7f91c0205424d001f5ae3e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType Numaralandırması
Türü etkilemek için değerler sağlar `reloc` çağrıda yayılan yönerge [Iceegen::addsectionreloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).  
  
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
|`srRelocHighLow`|Oluşturan bir `reloc` işaretçi ölçekli konumu. Platforma bağlı olarak bu BASED_HIGHLOW veya BASED_DIR64 uygulamasına dönüştürülür.|  
|`srRelocHighAdj`|Oluşturan bir `reloc` en üst burada 16 bit alt dahil edilmiştir .reloc tablosundaki Sonraki sözcüğü 32-bit sayının 16 bit.|  
|`srRelocMapToken`|Hiçbir şey .reloc bölüme gönderme bir belirteç harita yeniden konumlandırma oluşturur.|  
|`srRelocRelative`|Değer göreli adresi düzeltmesi olduğunu gösterir.|  
|`srRelocFilePos`|Yalnızca bir bölüm göreli oluşturur `reloc`, gönderen bir .reloc bölüme hiçbir şey yok. Bu `reloc` bölümünde, bölümün sanal adres dosya konumuna göre değil.|  
|`srRelocCodeRelative`|Kod göreli adresi düzeltmesi belirtir.|  
|`srRelocIA64Imm64`|Oluşturan bir `reloc` bir IA64 bir 64 bit adresi için `movl` yönergesi.|  
|`srRelocDir64`|Oluşturan bir `reloc` bir 64-bit adresi için.|  
|`srRelocIA64PcRel25`|Oluştur bir `reloc` bir IA64 bir 25 bit PC göreli adresi için `br.call` yönergesi.|  
|`srRelocIA64PcRel64`|Oluşturan bir `reloc` bir IA64 bir 64-bit PC göreli adresi için `brl.call` yönergesi.|  
|`srRelocAbsoluteTagged`|30 bit'lik bir bölüm-göreli oluşturur `reloc`, etiketli işaretçi değerleri için kullanılır.|  
|`srRelocSentinel`|Bu numaralandırma herhangi eklemeler sağlamaya yardımcı olmak için bir sentinel değer iç ağa yansıtılır `reloc` adı dizi.|  
|`srNoBaseReloc`|Bir taban yayma değil belirtir `reloc`.|  
|`srRelocPtr`|Bellek öncesi düzeltmesi içeriğinin bir bölümü yerine bir işaretçi olduğunu belirten bir değer uzaklığı.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [ICeeGen Arabirimi](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 [AddSectionReloc Yöntemi](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
