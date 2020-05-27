---
title: CorCallingConvention Numaralandırması
ms.date: 03/30/2017
api_name:
- CorCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallingConvention
helpviewer_keywords:
- CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type:
- apiref
ms.openlocfilehash: 310319e8fefe80017c58706e2beaee5eb1e78422
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007916"
---
# <a name="corcallingconvention-enumeration"></a>CorCallingConvention Numaralandırması
Yönetilen kodda yapılan çağırma kurallarının türlerini tanımlayan değerleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CorCallingConvention  
{  
    IMAGE_CEE_CS_CALLCONV_DEFAULT       = 0x0,  
  
    IMAGE_CEE_CS_CALLCONV_VARARG        = 0x5,  
    IMAGE_CEE_CS_CALLCONV_FIELD         = 0x6,  
    IMAGE_CEE_CS_CALLCONV_LOCAL_SIG     = 0x7,  
    IMAGE_CEE_CS_CALLCONV_PROPERTY      = 0x8,  
    IMAGE_CEE_CS_CALLCONV_UNMGD         = 0x9,  
    IMAGE_CEE_CS_CALLCONV_GENERICINST   = 0xa,  
    IMAGE_CEE_CS_CALLCONV_NATIVEVARARG  = 0xb,  
    IMAGE_CEE_CS_CALLCONV_MAX           = 0xc,  
  
    IMAGE_CEE_CS_CALLCONV_MASK          = 0x0f,  
    IMAGE_CEE_CS_CALLCONV_HASTHIS       = 0x20,  
    IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS  = 0x40,  
    IMAGE_CEE_CS_CALLCONV_GENERIC       = 0x10  
  
} CorCallingConvention;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|Varsayılan bir çağırma kuralını gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|Yöntemin değişken sayıda parametre aldığını gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|Çağrının bir alana olduğunu gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|Çağrının yerel bir yönteme olduğunu gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|Çağrının bir özelliğe olduğunu gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|Çağrının yönetilmeyen olduğunu gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|Genel bir yöntem örneklemeyi gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|Değişken sayıda parametre alan bir yönteme 64 bitlik bir PInvoke çağrısını gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|Geçersiz 4 bitlik bir değeri açıklar.|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|Çağırma kuralının en alttaki dört bit tarafından açıklandığını gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|En üstteki bitin bir parametreyi tanımlıyor olduğunu gösterir `this` .|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|Bir `this` parametrenin İmzada açıkça açıklandığını gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|Açık sayıda tür bağımsız değişkeni olan bir genel yöntem imzasını gösterir. Bu, normal bir parametre sayısından önce gelir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
