---
title: ICorDebugChain::GetStackRange Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 226f8c431b90d53366aa5e504101e7de581ec570
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402476"
---
# <a name="icordebugchaingetstackrange-method"></a>ICorDebugChain::GetStackRange Metodu
Yığın kesiminin adres aralığı için bu zincirini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pStart`  
 [out] Bir işaretçi bir `CORDB_ADDRESS` yığın kesiminin başlangıç adresi değer.  
  
 `pEnd`  
 [out] Bir işaretçi bir `CORDB_ADDRESS` yığın kesiminin bitiş adresi değer.  
  
## <a name="remarks"></a>Açıklamalar  
 Sayısal aralığın yalnızca yığın çerçeve konumları bir karşılaştırması için anlamlıdır. Yığında gerçekte depolanan hakkında varsayımlar yapamazsınız.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
