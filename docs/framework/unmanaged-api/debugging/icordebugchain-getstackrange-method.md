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
ms.openlocfilehash: ac40927ac9469e4a2fb74fb550287130b9bb9f83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989462"
---
# <a name="icordebugchaingetstackrange-method"></a>ICorDebugChain::GetStackRange Metodu
Yığın kesiminin adres aralığı için bu zincir alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pStart`  
 [out] Bir işaretçi bir `CORDB_ADDRESS` yığın kesimin başlangıç adresi olan değer.  
  
 `pEnd`  
 [out] Bir işaretçi bir `CORDB_ADDRESS` yığın kesiminin bitiş adresi olan değer.  
  
## <a name="remarks"></a>Açıklamalar  
 Sayısal Aralık yalnızca yığın çerçeve konumu bir karşılaştırması için anlamlı. Aslında yığın üzerinde depolanan hakkında varsayımlar yapamazsınız.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
