---
title: ICorDebugFrame::GetStackRange Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 43532888d181adcb7a7e3760f2a5e3d8f664a35c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492289"
---
# <a name="icordebugframegetstackrange-method"></a>ICorDebugFrame::GetStackRange Yöntemi
Bu yığın çerçevesinin mutlak adres aralığını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pStart`  
 [out] Bir işaretçi bir `CORDB_ADDRESS` bu tarafından temsil edilen yığın çerçevesinin başlangıç adresini belirten `ICorDebugFrame` nesne.  
  
 `pEnd`  
 [out] Bir işaretçi bir `CORDB_ADDRESS` bitiş adresini bu tarafından temsil edilen yığın çerçevesinin belirten `ICorDebugFrame` nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 Yığın adres aralığı, birden çok hata ayıklama motorlarından toplanan Aralanmış yığın izlemelerini birbirine eklemekten için kullanışlıdır. Sayısal Aralık yığın çerçevesi bir içeriği hakkında bilgi sağlar. Bu, yalnızca yığın çerçeve konumu bir karşılaştırması için anlamlı olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
