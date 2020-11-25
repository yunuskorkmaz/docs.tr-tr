---
title: ICorDebugChain::GetCaller Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type:
- apiref
ms.openlocfilehash: 0f616b3bae48a972c0fc8935c35add7d844a7364
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730116"
---
# <a name="icordebugchaingetcaller-method"></a>ICorDebugChain::GetCaller Metodu

Bu zinciri çağıran zinciri alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppChain`  
 dışı Çağıran zinciri temsil eden bir ıcordebugzincirleri nesnesinin adresine yönelik bir işaretçi.  
  
 Bu zincir daha önce çağrılırsa (Bu zincir veya hata ayıklayıcı çağrı yığınını başlatdıysa olduğu gibi), `ppChain` null olur.  
  
## <a name="remarks"></a>Açıklamalar  

 Çağrı iş parçacıkları arasında sıralandıysa, çağırma zinciri farklı bir iş parçacığında olabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
