---
description: ': ICorDebugThread:: GetRegisterSet Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugThread::GetRegisterSet Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetRegisterSet
helpviewer_keywords:
- ICorDebugThread::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3b9b6260-98ac-4cfd-88e5-5d7614f94a0c
topic_type:
- apiref
ms.openlocfilehash: f61ccb34eabc1f4d8b8db8a0b78e3ddde9aa136d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658912"
---
# <a name="icordebugthreadgetregisterset-method"></a>ICorDebugThread::GetRegisterSet Metodu

Bu ICorDebugThread nesnesinin etkin bölümüyle ilişkili kayıt kümesine bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppRegisters`  
 dışı Bu iş parçacığının etkin bölümü için yazmaç kümesini temsil eden bir [ICorDebugRegisterSet](icordebugregisterset-interface.md) arabirimi nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
