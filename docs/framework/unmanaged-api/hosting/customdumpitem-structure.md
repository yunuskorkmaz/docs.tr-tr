---
title: CustomDumpItem Yapısı
ms.date: 03/30/2017
api_name:
- CustomDumpItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CustomDumpItem
helpviewer_keywords:
- CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type:
- apiref
ms.openlocfilehash: 154beef9398029f31dcb4d081019b9f292238af4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176480"
---
# <a name="customdumpitem-structure"></a>CustomDumpItem Yapısı
Hata bildiriminde özel bir döküme eklenecek bir öğeyi açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`itemKind`|Eklenecek öğe türünü gösteren [bir ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) değeri.|  
|`pReserved`|Şu anda kullanılmaz. Birliğe eklenen öğeler işaretçi boyutundan büyük olmamalıdır. A `struct` gerekiyorsa, ayrı ayrı ayırmanız ve işaret etmeniz gerekir.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) türünden `CustomDumpItem`bir parametre alır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MSCorEE.idl  
  
 **Kütüphane:** MSCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Yapıları](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
