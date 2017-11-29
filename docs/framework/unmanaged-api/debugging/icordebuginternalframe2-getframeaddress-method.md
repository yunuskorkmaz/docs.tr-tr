---
title: ICorDebugInternalFrame2::GetFrameAddress Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame2.GetFrameAddress Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame2::GetFrameAddress
helpviewer_keywords:
- GetFrameAddress method [.NET Framework debugging]
- ICorDebugInternalFrame2::GetFrameAddress method [.NET Framework debugging]
ms.assetid: 4ee8d058-ffc8-4967-9133-a5adfef4e518
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9ee867afe99fc5d2f2eb27bb1e6888aef8341d71
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginternalframe2getframeaddress-method"></a>ICorDebugInternalFrame2::GetFrameAddress Metodu
İç çerçeve yığını adresini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pAddress`  
 [out] İşaretçi `CORDB_ADDRESS` iç çerçevesi için.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|İç çerçeve adresini başarıyla döndürüldü.|  
|E_FAIL|İç çerçeve adresini döndürülemedi.|  
|E_INVALIDARG|`pAddress`olan `null`.|  
  
## <a name="remarks"></a>Açıklamalar  
 Döndürülen değerin `pAddress` iç çerçeve diğer çerçeveler yığında göreli konumunu belirlemek için kullanılabilir. Hatta IA-64 tabanlı bilgisayarlar iç çerçeve yalnızca yığın üzerinde bulunacağı ve yedekleme deposu için karşılık gelen bir işaretçi yok.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icordebugınternalframe2 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
