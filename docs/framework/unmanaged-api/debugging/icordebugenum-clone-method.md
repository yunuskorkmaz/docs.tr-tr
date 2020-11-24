---
title: ICorDebugEnum::Clone Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Clone
helpviewer_keywords:
- Clone method, ICorDebugEnum interface [.NET Framework debugging]
- ICorDebugEnum::Clone method [.NET Framework debugging]
ms.assetid: 57eefaf3-75cf-4496-bc94-88c0706861b7
topic_type:
- apiref
ms.openlocfilehash: 28e0cded33b49e3aadc0564bae3a60bee76c4396
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677394"
---
# <a name="icordebugenumclone-method"></a>ICorDebugEnum::Clone Yöntemi

Bu ıcorı, Genum nesnesinin bir kopyasını oluşturur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppEnum`  
 dışı `ICorDebugEnum` Bu nesnenin kopyası olan bir nesnenin adresine yönelik bir işaretçi `ICorDebugEnum` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
