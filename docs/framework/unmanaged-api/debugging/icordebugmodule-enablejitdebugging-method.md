---
title: "ICorDebugModule::EnableJITDebugging Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugModule.EnableJITDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7a699f32d8ec4b2418c6af815c22f35470bede3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduleenablejitdebugging-method"></a>ICorDebugModule::EnableJITDebugging Yöntemi
Tam zamanında (JIT) derleyici bu modül içinde yöntemleri için hata ayıklama bilgilerini korur olup olmadığını denetler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `bTrackJITInfo`  
 [in] Bu değer ayarlanırsa `true` Microsoft Ara dili (MSIL) ve bu Modülün her bir yöntemin JIT derlenmiş sürümleri arasında eşleme bilgilerini korumak JIT Derleyici etkinleştirmek için.  
  
 `bAllowJitOpts`  
 [in] Bu değer ayarlanırsa `true` hata ayıklama için belirli JIT özgü en iyi duruma getirme ile kodu oluşturmak JIT Derleyici etkinleştirmek için.  
  
## <a name="remarks"></a>Açıklamalar  
 JIT hata ayıklama hata ayıklayıcısı etkinken yüklenen tüm modülleri için varsayılan olarak etkindir. Program aracılığıyla etkinleştirme veya ayarlarını devre dışı bırakma genel ayarları geçersiz kılar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
