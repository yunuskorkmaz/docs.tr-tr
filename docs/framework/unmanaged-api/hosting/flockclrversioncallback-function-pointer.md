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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46e3356df6578f2adf2ceee00b1363b65fd014ea
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760233"
---
# <a name="flockclrversioncallback-function-pointer"></a>FLockClrVersionCallback İşlev İşaretçisi
Başlatmanın belirtmek için ortak dil çalışma zamanı (CLR) çağrıları çalışmaya veya tamamlanmış bir işleve işaret eder.  
  
 Bu işlev işaretçisi .NET Framework 4'te kullanım dışıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev, ana bilgisayar tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorWks.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LockClrVersion İşlevi](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
