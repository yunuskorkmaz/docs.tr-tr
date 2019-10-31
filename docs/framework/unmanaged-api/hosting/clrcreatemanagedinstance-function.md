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
ms.openlocfilehash: 4e672030ae83b57da6f9ab66630513d79f28b8f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131995"
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance İşlevi
Belirtilen yönetilen türün bir örneğini oluşturur.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır. Yönetilen türün bir örneğini oluşturmak için COM etkinleştirmesini kullanın veya barındırma kullanın (bkz. [.NET Framework 4 ve 4,5 ' de eklenen clr barındırma arabirimleri](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).  
  
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
 'ndaki İstenen örnek türünün adına yönelik bir işaretçi.  
  
 `riid`  
 'ndaki İstenen örnek türünün `IID`.  
  
 `ppObject`  
 dışı Çağıran tarafından istenen yönetilen tür örneğine yönelik işaretçiye yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanının zaten bir işleme yüklenmiş olması gerekir. Örneğin, `ClrCreateManagedInstance` işlevi çağrılmadan önce [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevine yapılan bir çağrı kullanılarak yüklenebilir. Çalışma zamanı yüklü değilse, önce `ClrCreateManagedInstance` çalışma zamanının v 1.0.3705 sürümünü yüklemeye çalışır. Başarısız olursa, çalışma zamanının en son sürümünü yüklemeye çalışır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
