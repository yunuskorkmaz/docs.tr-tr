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
ms.openlocfilehash: 44a4b5903cec2249eb1e176381fe3d8e600dd5e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046117"
---
# <a name="corcallingconvention-enumeration"></a>CorCallingConvention Numaralandırması
Yönetilen kodda yapılan çağrı kuralları türlerini açıklayan değerlerini içerir.  
  
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
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|Varsayılan çağırma kuralını belirtir.|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|Yöntem değişik sayıda parametreyi alır gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|Arama için bir alan olduğunu gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|Arama için yerel bir yöntem olduğunu gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|Arama için bir özellik olduğunu gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|Çağrı yönetilmeyen olduğunu gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|Bir genel yöntem örnekleme gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|Bir 64-bit PInvoke çağrısına değişken sayıda parametre isteyen bir yöntemi gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|Geçersiz 4-bit bir değer tanımlar.|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|Çağırma kuralı alt dört bitleri tarafından açıklanan gösterir.|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|Üst bit açıklayan gösteren bir `this` parametresi.|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|Bildiren bir `this` parametredir imzasında açıkça açıklanmıştır.|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|Açık bir tür bağımsız değişkeni sayısına sahip bir genel metot imzasını gösterir. Bu, bir sıradan parametre sayısı önce gelir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
