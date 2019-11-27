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
ms.openlocfilehash: 58d30e71929d314ee36adb9f83270858ff8a161b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442443"
---
# <a name="corunmanagedcallingconvention-enumeration"></a>CorUnmanagedCallingConvention Numaralandırması
Yönetilmeyen kod için çağrı kurallarını belirtir.  
  
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
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|"This" çağırma kuralı.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|"Hızlı" çağırma kuralı.|  
|`IMAGE_CEE_CS_CALLCONV_C`|Kullanılmadı.|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|Kullanılmadı.|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|Kullanılmadı.|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|Kullanılmadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, .NET Framework sürüm 1,0 ' de "hızlı" çağırma kuralını desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
