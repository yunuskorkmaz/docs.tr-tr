---
title: "ClrCreateManagedInstance İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: ClrCreateManagedInstance
helpviewer_keywords: ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2d27a881f84121f0d096eae7c693dec5b674caec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance İşlevi
Belirtilen yönetilen türü örneğini oluşturur.  
  
 Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. COM Etkinleştirme yönetilen türü örneği oluşturun veya barındırma kullanın (bkz [CLR barındırma arabirimleri eklenen .NET Framework 4 ve 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pTypeName`  
 [in] İstenen örneği türünün adı için bir işaretçi.  
  
 `riid`  
 [in] `IID` İstenen örneği türü.  
  
 `ppObject`  
 [out] Çağıran tarafından istendi yönetilen türünün bir örneği için bir işaretçi bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı süreç içine önceden yüklenmiş. Örneğin, bunu bir çağrı kullanılarak yüklenebilir [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) önce işlev `ClrCreateManagedInstance` işlevi çağrılır. Çalışma zamanı yüklenmezse `ClrCreateManagedInstance` önce çalışma zamanının v1.0.3705 yüklemeye çalışır. Başarısız olursa, çalışma zamanı en son sürümünü yüklemeye çalışır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanım dışı CLR barındırma işlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
 [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
