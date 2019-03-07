---
title: ICorDebugModule::EnableJITDebugging Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 642c4fd600d10ef89a08aa32bef5c8e7455552c7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473836"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a>ICorDebugModule::EnableJITDebugging Yöntemi
Just-ın-time (JIT) derleyicinin bu modül içindeki yöntemler için hata ayıklama bilgilerini korur olup olmadığını denetler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `bTrackJITInfo`  
 [in] Bu değer kümesine `true` Microsoft Ara dil (MSIL) ve bu modüldeki her yöntemi JIT olarak derlenmiş sürümleri arasında eşleme bilgilerini korumak JIT derleyicisi etkinleştirmek için.  
  
 `bAllowJitOpts`  
 [in] Bu değer kümesine `true` JIT Derleyici kodu ile hata ayıklama için belirli özel JIT iyileştirmelerini etkinleştirmek için.  
  
## <a name="remarks"></a>Açıklamalar  
 JIT hata ayıklama, hata ayıklayıcısı etkinken, yüklenen tüm modüller için varsayılan olarak etkindir. Program aracılığıyla etkinleştirme veya ayarları devre dışı bırakma genel ayarları geçersiz kılar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
