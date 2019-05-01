---
title: ICorDebugProcess2::GetDesiredNGENCompilerFlags Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags method [.NET Framework debugging]
- GetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: fc834580-3a90-4315-95d2-349b6bb7d059
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a59067f72005e87152680e4f990fc74e4acdaa9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948947"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a>ICorDebugProcess2::GetDesiredNGENCompilerFlags Metodu
Ortak dil çalışma zamanı (CLR) önceden derlenmiş doğru seçmek için kullandığı bayrağı ayarları geçerli derleyici alır (diğer bir deyişle, yerel) görüntü bu işleme yüklenecek.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pdwFlags`  
 [out] Bitsel bir birleşimi için bir işaretçi [Cordebugjıtcompilerflags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) yüklenecek önceden derlenmiş doğru görüntüyü seçmek için kullanılan sabit listesi değerleri.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanma [Icordebugprocess2::setdesiredngencompilerflags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md) CLR yüklemek için önceden derlenmiş doğru görüntüyü seçmek için kullanacağı bayrakları ayarlamanızı yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
