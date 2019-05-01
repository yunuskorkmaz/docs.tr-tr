---
title: IHostMemoryManager::AcquiredVirtualAddressSpace Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.AcquiredVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace method [.NET Framework hosting]
- AcquiredVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: ef2f83c2-127e-4c38-8385-306c03cd2167
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4675c34bfe8d1d79c184c43e5f7f5dd3a03be6a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935674"
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a>IHostMemoryManager::AcquiredVirtualAddressSpace Yöntemi
Konak, ortak dil çalışma zamanı (CLR) belirtilen bellek işletim sisteminden almışsa bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `startAddress`  
 [in] Bellek başlangıç adresi.  
  
 `size`  
 [in] Belleğin bayt cinsinden boyutu.  
  
## <a name="remarks"></a>Açıklamalar  
 `AcquiredVirtualAddressSpace` Yöntemi geri çağırma yöntemi olan ve uygulamanın barındırma yazıcı tarafından uygulanır. CLR tarafından çağırılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostMemoryManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
