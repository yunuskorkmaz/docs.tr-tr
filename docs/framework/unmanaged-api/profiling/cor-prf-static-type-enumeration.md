---
title: COR_PRF_STATIC_TYPE Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_STATIC_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_STATIC_TYPE
helpviewer_keywords:
- COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 34a2ca5b505c504115af47402c3d92a05ec0676f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737643"
---
# <a name="corprfstatictype-enumeration"></a>COR_PRF_STATIC_TYPE Numaralandırması
Bir statik alandır ve statik kalite bu durumda, alana uygulanan olup olmadığını gösterir. Bu değerler alan birden çok olduğunu belirtmek için bit düzeyinde OR işlemi kullanılarak birleştirilebilir. farklı bir statik kalitelerini.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|Alanı statik değil.|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|Uygulama etki alanı statik alandır.|  
|`COR_PRF_FIELD_THREAD_STATIC`|İş parçacığı statik alandır.|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|Bağlam statik alandır.|  
|`COR_PRF_FIELD_RVA_STATIC`|Göreli sanal adres (RVA) alandır-statik.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Profil Oluşturma Sabit Listeleri](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
