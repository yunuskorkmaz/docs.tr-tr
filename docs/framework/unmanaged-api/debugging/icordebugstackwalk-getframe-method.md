---
title: ICorDebugStackWalk::GetFrame Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk.GetFrame Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk::GetFrame
helpviewer_keywords:
- GetFrame method [.NET Framework debugging]
- ICorDebugStackWalk::GetFrame method [.NET Framework debugging]
ms.assetid: 4083b505-5b59-44fb-8c5d-129db6a96c10
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c095afd0513360876e5330a130a4d938e30f8db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstackwalkgetframe-method"></a>ICorDebugStackWalk::GetFrame Metodu
Geçerli çerçeve alır [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) nesnesi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pFrame`  
 [in] Geçerli yığın çerçevesinde temsil eden oluşturulan çerçeve nesnesinin adresi için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Çalışma zamanı, geçerli çerçeve başarıyla döndürüldü.|  
|E_FAIL|Geçerli çerçeve döndürülmedi.|  
|S_FALSE|Geçerli bir yerel yığın çerçevesi çerçevedir.|  
|E_INVALIDARG|`pFrame`null şeklindedir.|  
|CORDBG_E_PAST_END_OF_STACK|Çerçeve işaretçisi yığının sonuna zaten; Bu nedenle, hiçbir ek çerçeve erişilebilir.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugStackWalk`yalnızca gerçek yığın çerçeveleri döndürür. Kullanım [Icordebugthread3::getactiveınternalframes](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) iç çerçeveler döndürülecek yöntemi. İç çerçeveler yığına geçici verileri depolamak için çalışma zamanı tarafından gönderilen veri yapılarını dışında (.)  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugStackWalk Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
