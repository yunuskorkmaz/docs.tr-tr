---
description: ': Icorı, Genum:: Clone yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 18219757980870dcf9663477d195068a76814de1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694584"
---
# <a name="icordebugenumclone-method"></a>ICorDebugEnum::Clone Yöntemi

Bu ıcorı, Genum nesnesinin bir kopyasını oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
