---
title: ICorDebugChain::GetActiveFrame Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a104d4d3cc74a6c1cb343818c9b0b3e8978b97df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugchaingetactiveframe-method"></a>ICorDebugChain::GetActiveFrame Metodu
Etkin alır (yani, en son) zinciri çerçevesi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppFrame`  
 [out] Bir işaretçi etkin temsil eden Icordebugframe nesne adresine (diğer bir deyişle, en son) zinciri çerçevesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yönetilen yığın çerçeve olup olmadığını `ppFrame` ayarlanmış null.  
  
 Etkin çerçeveyi kullanılabilir durumda değilse, çağrı başarılı olur ve `ppFrame` null olur. Etkin çerçeve CHAIN_CLASS_INIT nedeniyle başlatılan bazı zincirlerini ve CHAIN_ENTER_UNMANAGED nedeniyle başlatılan zincirleri için kullanılamaz. CorDebugChainReason numaralandırması bakın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
