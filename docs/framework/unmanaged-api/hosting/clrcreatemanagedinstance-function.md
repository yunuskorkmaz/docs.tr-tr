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
ms.openlocfilehash: f82303a3d38e7a5baaf1c3edcc41518228360d34
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088463"
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance İşlevi
Belirli bir yönetilen türün bir örneğini oluşturur.  
  
 Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. COM Etkinleştirme yönetilen türün bir örneğini oluşturmak için kullanabilir veya barındırma (bkz [CLR barındırma arabirimleri eklenmiş .NET Framework 4 ve 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
