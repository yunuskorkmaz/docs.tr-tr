---
title: ICorDebugNativeFrame2::GetStackParameterSize Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.GetStackParameterSize Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize
helpviewer_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize method [.NET Framework debugging]
- GetStackParameterSize method [.NET Framework debugging]
ms.assetid: f6a449c8-a941-43ba-9a90-c98b29ae3c36
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47968d7550c3d16d201680caab705c0d7c85c784
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994584"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a>ICorDebugNativeFrame2::GetStackParameterSize Yöntemi
İşletim sistemlerini x86 yığındaki parametreleri toplam boyutu döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a>Parametreler  
 `pSize`  
 [out] Toplam boyutu, yığındaki parametreleri için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yığın boyutu başarıyla döndürüldü.|  
|S_FALSE|`GetStackParameterSize` x86 olmayan platformunda çağrıldı.|  
|E_FAIL|`The size of the parameters could not be returned`.|  
|E_INVALIDARG|`pSize` olan `null`.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  
 [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) yöntemleri yığına itildi parametreleri için yığın işaretçisi ayarlama değil. Tarafından döndürülen değeri, bunun yerine kullanabileceğiniz `GetStackParameterSize` parametrelerini ayarla bir yerel unwinder sağlamak için yığın işaretçisi ayarlamak için.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugNativeFrame2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
