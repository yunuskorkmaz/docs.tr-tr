---
description: ': ICorDebugProcess:: GetHandle Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugProcess::GetHandle Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
ms.openlocfilehash: fbc92be53b30d3c70f85fea36e05c6a5514b0f03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722132"
---
# <a name="icordebugprocessgethandle-method"></a>ICorDebugProcess::GetHandle Metodu

İşlem için bir tanıtıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a>Parametreler  

 `phProcessHandle`  
 dışı `HPROCESS` İşlemin tutamacı olan bir işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  

 Alınan tanıtıcı, hata ayıklama arabirimine aittir. Hata ayıklayıcı, kullanılmadan önce tanıtıcıyı yinelememelidir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
