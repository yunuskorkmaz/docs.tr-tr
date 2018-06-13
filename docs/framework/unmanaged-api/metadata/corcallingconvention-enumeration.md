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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 468ad1acf55c4d1b4fc2b53730f16ee8630cf19b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444021"
---
# <a name="corcallingconvention-enumeration"></a>CorCallingConvention Numaralandırması
Yönetilen kodda yapılan çağırma kurallarını türlerini açıklayan değerlerini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|Çağırma kuralı varsayılan gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|Yöntem değişken sayıda parametre isteyen gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|Aramanın bir alan olduğunu gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|Arama için yerel bir yöntemi gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|Çağrı özelliğe olduğunu gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|Çağrı yönetilmeyen olduğunu gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|Genel yöntem örnekleme gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|Değişken sayıda parametre isteyen bir yöntem 64-bit PInvoke çağrısı gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|Geçersiz bir 4-bit değer açıklar.|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|Çağırma kuralı alt dört BITS tarafından açıklanan gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|Üst bit açıklayan gösteren bir `this` parametresi.|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|Belirten bir `this` parametredir imzada açıkça açıklanmıştır.|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|Bir genel yöntem imza açık sayıda tür bağımsız değişkeni ile gösterir. Bu, normal parametre sayısı önce gelir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
