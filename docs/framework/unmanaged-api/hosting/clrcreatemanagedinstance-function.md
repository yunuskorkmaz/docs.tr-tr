---
title: ClrCreateManagedInstance İşlevi
ms.date: 03/30/2017
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1ae530b8488dcd375e91058a227316dd38cf4ab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779163"
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance İşlevi
Belirli bir yönetilen türün bir örneğini oluşturur.  
  
 Bu işlev .NET Framework 4'te kullanım dışıdır. COM Etkinleştirme yönetilen türün bir örneğini oluşturmak için kullanabilir veya barındırma (bkz [CLR barındırma arabirimleri eklenmiş .NET Framework 4 ve 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pTypeName`  
 [in] İstenen örnek türünün adını bir işaretçi.  
  
 `riid`  
 [in] `IID` İstenen örnek türü.  
  
 `ppObject`  
 [out] Çağıran tarafından istenen yönetilen türü örneğine bir işaretçi işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı zaten işlem içine yüklenmiş. Örneğin, bir çağrı kullanılarak yüklenebilir [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) önce işlev `ClrCreateManagedInstance` işlevi çağrılır. Çalışma zamanı yüklü değilse `ClrCreateManagedInstance` ilk v1.0.3705 çalışma zamanı yüklemeye çalışır. Bu başarısız olursa, çalışma zamanının en son sürümünü yüklemeyi dener.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
