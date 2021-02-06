---
description: ': ICorDebugThread:: GetID Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugThread::GetID Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetID
helpviewer_keywords:
- ICorDebugThread::GetID method [.NET Framework debugging]
- GetID method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: f1de4584-92df-42f3-9da4-fca03a1c6821
topic_type:
- apiref
ms.openlocfilehash: d089201527da67299b64cdf074bdd331f22375a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659094"
---
# <a name="icordebugthreadgetid-method"></a>ICorDebugThread::GetID Yöntemi

Bu ICorDebugThread 'in etkin bölümünün geçerli işletim sistemi tanımlayıcısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pdwThreadId`  
 dışı İş parçacığının tanımlayıcısı.  
  
## <a name="remarks"></a>Açıklamalar  

 İşletim sistemi tanımlayıcısı bir işlemin yürütülmesi sırasında muhtemelen değişebilir ve iş parçacığının farklı bölümleri için farklı bir değer olabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
