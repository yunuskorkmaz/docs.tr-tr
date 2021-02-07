---
description: 'Daha fazla bilgi edinin: CorUnmanagedCallingConvention numaralandırması'
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
ms.openlocfilehash: a4b5c70b7dcb4750d641540662941ed3cc08c94b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707299"
---
# <a name="corunmanagedcallingconvention-enumeration"></a>CorUnmanagedCallingConvention Numaralandırması

Yönetilmeyen kod için çağrı kurallarını belirtir.  
  
## <a name="syntax"></a>Syntax  
  
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
  
|Üye|Description|  
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

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
