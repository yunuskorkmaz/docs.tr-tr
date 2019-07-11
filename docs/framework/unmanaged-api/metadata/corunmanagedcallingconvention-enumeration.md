---
title: CorUnmanagedCallingConvention Numaralandırması
ms.date: 03/30/2017
api_name:
- CorUnmanagedCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnmanagedCallingConvention
helpviewer_keywords:
- CorUnmanagedCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 83058790-160b-4703-a5eb-74b66acbdfa9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9206fbde13f457d4b2e2941ee744d645c6df9774
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781992"
---
# <a name="corunmanagedcallingconvention-enumeration"></a>CorUnmanagedCallingConvention Numaralandırması
Yönetilmeyen kod için çağırma kuralları belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CorUnmanagedCallingConvention {  
  
    IMAGE_CEE_UNMANAGED_CALLCONV_C         = 0x1,  
    IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL   = 0x2,  
    IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL  = 0x3,  
    IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL  = 0x4,  
  
    IMAGE_CEE_CS_CALLCONV_C                = 0x1,  
    IMAGE_CEE_CS_CALLCONV_STDCALL          = 0x2,  
    IMAGE_CEE_CS_CALLCONV_THISCALL         = 0x3,  
    IMAGE_CEE_CS_CALLCONV_FASTCALL         = 0x4  
  
} CorUnmanagedCallingConvention;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|C dili çağırma kuralı.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|Standart çağırma kuralı.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|"Bu" çağırma kuralı.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|"Hızlı" çağırma kuralı.|  
|`IMAGE_CEE_CS_CALLCONV_C`|Kullanılmadı.|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|Kullanılmadı.|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|Kullanılmadı.|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|Kullanılmadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, .NET Framework sürüm 1.0 "Hızlı" çağırma kuralı desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
