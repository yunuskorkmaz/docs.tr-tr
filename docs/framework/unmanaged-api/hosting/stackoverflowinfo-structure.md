---
title: StackOverflowInfo Yapısı
ms.date: 03/30/2017
api_name:
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c1723facca3c547c275ee44f0abefe21a177eb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572035"
---
# <a name="stackoverflowinfo-structure"></a>StackOverflowInfo Yapısı
Taşması nedeniyle oluşturulan özel durum oluştu taşma ve bilgi türünü saklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`soType`|Değerini [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) taşma türünü belirten sabit listesi.|  
|`pExceptionInfo`|Bir Win32 işaretçisi `EXCEPTION_POINTERS` bir özel durum makine bağımsız açıklamasını içeren bir özel durum kaydını ve özel durumun zaman makine bağımlı bir işlemci bağlamı açıklamasını içeren bir bağlam kaydı içeren nesne.|  
  
## <a name="remarks"></a>Açıklamalar  
 A `StackOverflowInfo` nesnesi [Iactiononclrevent::ONEVENT](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) yöntemi `Event_StackOverflow` olayları.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.idl  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Barındırma Yapıları](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
