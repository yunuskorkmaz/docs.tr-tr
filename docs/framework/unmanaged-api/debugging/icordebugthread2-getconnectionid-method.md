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
ms.openlocfilehash: 1507715e80761c871dfdb0b8d25dc708a2130678
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678694"
---
# <a name="icordebugthread2getconnectionid-method"></a>ICorDebugThread2::GetConnectionID Yöntemi

Bu ICorDebugThread2 nesnesi için bağlantı tanımlayıcısını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pdwConnectionId`  
 dışı `CONNID` Bağlantı tanımlayıcısını temsil eden bir.  
  
## <a name="remarks"></a>Açıklamalar  

 `GetConnectionID`Yöntemi, `pdwConnectionId` Bu iş parçacığı bir bağlantının parçası değilse, parametresinde sıfır döndürür.  
  
 Bu iş parçacığı bir Microsoft SQL Server 2005 Analysis Services (SSAS) örneğine bağlıysa, `CONNID` sunucu işlem tanımlayıcısına (SPID) eşlenir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
