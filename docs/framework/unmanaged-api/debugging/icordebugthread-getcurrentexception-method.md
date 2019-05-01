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
ms.openlocfilehash: c4baa4eb4da48b923ab0137ca25d9d819c94e33d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994038"
---
# <a name="icordebugthreadgetcurrentexception-method"></a>ICorDebugThread::GetCurrentException Metodu
Icordebugvalue nesneye şu anda yönetilen kod tarafından oluşturulan bir özel durumu temsil eden bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
