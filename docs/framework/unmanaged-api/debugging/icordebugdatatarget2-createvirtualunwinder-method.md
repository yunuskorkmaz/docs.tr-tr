---
title: ICorDebugDataTarget2::CreateVirtualUnwinder Yöntemi
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c8befed8bc810344b2a3344212a6a4a854300e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763828"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a>ICorDebugDataTarget2::CreateVirtualUnwinder Yöntemi
(Bu mutlaka bir iş parçacığının yaprak olmayan) bir ilk bağlamından geriye doğru izleme başlayan yeni bir yığın unwinder oluşturur.  
  
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
  
## <a name="parameters"></a>Parametreler  
 nativeThreadID  
 [in] Yerel iş parçacığı kimliği olan yığınıdır olacak şekilde iş parçacığının geriye doğru.  
  
 contextFlags  
 [in] Hangi parçalarının bağlam içinde tanımlanan belirten bayrakları `initialContext`.  
  
 cbContext  
 [in] Boyutu `initialContext`.  
  
 initialContext  
 [in] Bağlam verileri.  
  
 ppUnwinder  
 [out] Icordebugvirtualunwinder arabirimi nesnenin adresi için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK` başarılı olursa. Diğer `HRESULT` başarısız olduğunu gösterir. Tüm başarısız `HRESULT` mscordbi tarafından alınan önemli kabul edilir ve neden [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) döndürülecek yöntemleri `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu yöntem yalnızca .NET Native ile kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugDataTarget2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
