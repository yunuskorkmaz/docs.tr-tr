---
description: ': ICorDebugThread:: GetHandle Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugThread::GetHandle Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type:
- apiref
ms.openlocfilehash: 378bb395e56f0fc287a480d67d2047e082d0796f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659107"
---
# <a name="icordebugthreadgethandle-method"></a>ICorDebugThread::GetHandle Yöntemi

Bu ICorDebugThread 'in etkin bölümü için geçerli tanıtıcıyı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `phThreadHandle`  
 dışı Bu iş parçacığının etkin bölümünün tanıtıcısı olan bir HTHREAD için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Tanıtıcı, işlem yürütüldüğü gibi değişebilir ve iş parçacığının farklı parçaları için farklı olabilir.  
  
 Bu tanıtıcının sahibi hata ayıklama API 'sidir. Hata ayıklayıcı, kullanmadan önce onu çoğaltmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
