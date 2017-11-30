---
title: "CustomDumpItem Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CustomDumpItem
api_location: mscoree.dll
api_type: COM
f1_keywords: CustomDumpItem
helpviewer_keywords: CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 547204385b20d5b7e64bda9ea0a9e790f2ba3471
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="customdumpitem-structure"></a>CustomDumpItem Yapısı
Hata Raporlama özel bir döküm eklenmesi için bir öğe açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`itemKind`|Bir [Ecustomdumpıtemkind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) eklenecek öğe türünü belirten değer.|  
|`pReserved`|Şu anda kullanılmıyor. UNION eklenen tüm öğeler işaretçi boyutundan daha büyük olmalıdır. Varsa bir `struct` olan gerekli, ayrı ayrı ayırın ve gerekir kendisine noktası.|  
  
## <a name="remarks"></a>Açıklamalar  
 [Iclrerrorreportingmanager::begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) türünde bir parametre alan `CustomDumpItem`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.idl  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma yapıları](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
