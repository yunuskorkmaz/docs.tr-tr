---
title: FLockClrVersionCallback İşlev İşaretçisi
ms.date: 03/30/2017
api_name:
- FLockClrVersionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FLockClrVersionCallback
helpviewer_keywords:
- FLockClrVersionCallback function pointer [.NET Framework hosting]
ms.assetid: 98a4762d-9ad2-45bd-9d03-39064a028b44
topic_type:
- apiref
ms.openlocfilehash: f1ad414c30788801e14a33e98a0893e2a0f58d0c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136515"
---
# <a name="flockclrversioncallback-function-pointer"></a>FLockClrVersionCallback İşlev İşaretçisi
Ortak dil çalışma zamanının (CLR) başlatmanın başlatıldığını veya tamamlandığını göstermek için çağırdığı bir işleve işaret eder.  
  
 Bu işlev işaretçisi .NET Framework 4 ' te kullanım dışı bırakıldı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev, ana bilgisayar tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorWks. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LockClrVersion İşlevi](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
