---
title: "ICorDebugDataTarget2::CreateVirtualUnwinder Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bffbf95fc38cba6f311e0641b35e2696bd34099
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a>ICorDebugDataTarget2::CreateVirtualUnwinder Yöntemi
Geriye doğru izleme (hangi mutlaka bir iş parçacığı yaprak olmayan) bir ilk bağlamından başlayan yeni bir yığın unwinder oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
#### <a name="parameters"></a>Parametreler  
 nativeThreadID  
 [in] Yığın olduğu olması için iş parçacığı yerel iş parçacığı kimliği unwound.  
  
 contextFlags  
 [in] Bağlam hangi kısımlarının tanımlanan belirtin bayrakları `initialContext`.  
  
 cbContext  
 [in] Boyutunu `initialContext`.  
  
 initialContext  
 [in] Bağlam verileri.  
  
 ppUnwinder  
 [out] Icordebugvirtualunwinder arabirimi nesnenin adresini gösteren bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`başarılı olursa. Diğer `HRESULT` başarısız olduğunu gösterir. Tüm başarısız `HRESULT` mscordbi tarafından alınan önemli kabul edilir ve neden [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) dönmek için yöntemleri `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET yerel ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugDataTarget2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
