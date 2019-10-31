---
title: ICorDebugThread2::GetConnectionID Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetConnectionID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetConnectionID
helpviewer_keywords:
- ICorDebugThread2::GetConnectionID method [.NET Framework debugging]
- GetConnectionID method [.NET Framework debugging]
ms.assetid: 9c76b587-f941-4fa1-8b86-f3494fb10c8e
topic_type:
- apiref
ms.openlocfilehash: a81842132769934a6f5f34e6dc462bba77b3854a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138683"
---
# <a name="icordebugthread2getconnectionid-method"></a>ICorDebugThread2::GetConnectionID Yöntemi
Bu ICorDebugThread2 nesnesi için bağlantı tanımlayıcısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pdwConnectionId`  
 dışı Bağlantı tanımlayıcısını temsil eden bir `CONNID`.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetConnectionID` yöntemi, bu iş parçacığı bir bağlantının parçası değilse `pdwConnectionId` parametresinde sıfır döndürür.  
  
 Bu iş parçacığı bir Microsoft SQL Server 2005 Analysis Services (SSAS) örneğine bağlıysa `CONNID` bir sunucu işlem tanımlayıcısına (SPID) eşlenir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
