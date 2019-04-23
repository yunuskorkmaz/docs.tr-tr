---
title: IHostMemoryManager::ReleasedVirtualAddressSpace Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.ReleasedVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::ReleasedVirtualAddressSpace
helpviewer_keywords:
- ReleasedVirtualAddressSpace method [.NET Framework hosting]
- IHostMemoryManager::ReleasedVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: d1876601-6ab9-48e1-8ebd-184af1d0cd76
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0acbf4163e98b1171510260c4fac72c3d6f6fb1d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189293"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a>IHostMemoryManager::ReleasedVirtualAddressSpace Yöntemi
Konak, ortak dil çalışma zamanı (CLR) belirtilen bellek kullanarak tamamlandığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `startAddress`  
 [in] Başlangıç adresi serbest bırakılacak bellek işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 `ReleasedVirtualAddressSpace` Yöntemi geri çağırma yöntemi olan ve uygulamanın barındırma yazıcı tarafından uygulanır. CLR tarafından çağırılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostMemoryManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
