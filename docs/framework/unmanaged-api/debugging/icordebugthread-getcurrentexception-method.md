---
title: ICorDebugThread::GetCurrentException Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a6d53ebfebb8c883065ce119c2338a2225f0472
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762486"
---
# <a name="icordebugthreadgetcurrentexception-method"></a>ICorDebugThread::GetCurrentException Metodu
Icordebugvalue nesneye şu anda yönetilen kod tarafından oluşturulan bir özel durumu temsil eden bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppExceptionObject`  
 [out] Adresine bir işaretçi bir `ICorDebugValue` yönetilen kod tarafından şu anda oluşturulan özel durumu temsil eden nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 Özel durum nesnesi özel durum oluştu sonuna kadar zamandan sunulacaktır `catch` blok. Icordebugeval yöntemler tarafından gerçekleştirilen bir işlev değerlendirmesi özel durum nesneyi kurulumunu temizleyin ve tamamlanma geri yükleyin.  
  
 Özel durumlar iç içe geçirilemez (örneğin, bir özel durum bir filtre veya bir işlev değerlendirmesi oluşturulursa), olabilir bu nedenle tek bir iş parçacığı üzerinde bekleyen birden çok özel durum. `GetCurrentException` en geçerli özel durumun döndürür.  
  
 Tür ve özel durum nesnesi özel durum ömrü değişebilir. Örneğin, x türünde bir özel durum oluştuktan sonra ortak dil çalışma zamanı (CLR) bellek taşmasına uğruyor ve bir bellek yetersiz özel durum Yükselt.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
