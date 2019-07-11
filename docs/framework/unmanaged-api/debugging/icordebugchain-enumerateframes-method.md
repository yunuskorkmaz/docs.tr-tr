---
title: ICorDebugChain::EnumerateFrames Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc647805fcb7d8354a2540ac9424dc7155853444
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745041"
---
# <a name="icordebugchainenumerateframes-method"></a>ICorDebugChain::EnumerateFrames Yöntemi
En son çerçeve ile başlayan zincirindeki tüm yönetilen yığın çerçevesi içeren bir numaralandırıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppFrames`  
 [out] Yığın çerçevesi için Numaralandırıcı Icordebugframeenum nesnenin adresi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Zinciri, iş parçacığı için fiziksel çağrı yığınını temsil eder.  
  
 `EnumerateFrames` Yöntemi yalnızca yönetilen zincirleri için çağrılabilir. Hata ayıklama API yöntemleri yönetilmeyen zincirde bulunan çerçeveleri almak için sağlamaz. Hata ayıklayıcı bu bilgiyi elde etmek için başka bir yolla kullanmanız gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
