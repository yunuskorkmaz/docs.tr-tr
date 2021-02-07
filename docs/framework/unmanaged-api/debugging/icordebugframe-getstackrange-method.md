---
description: ': ICorDebugFrame:: GetStackRange metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 1f1278e0c00addc3c14f4e1c8d3ed5aad0381526
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692907"
---
# <a name="icordebugframegetstackrange-method"></a>ICorDebugFrame::GetStackRange Yöntemi

Bu yığın çerçevesinin mutlak adres aralığını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pStart`  
 dışı `CORDB_ADDRESS` Bu nesne tarafından temsil edilen yığın çerçevesinin başlangıç adresini belirten bir işaretçisi `ICorDebugFrame` .  
  
 `pEnd`  
 dışı `CORDB_ADDRESS` Bu nesne tarafından temsil edilen yığın çerçevesinin bitiş adresini belirten bir işaretçisi `ICorDebugFrame` .  
  
## <a name="remarks"></a>Açıklamalar  

 Yığının adres aralığı, birden çok hata ayıklama altyapılarından toplanan araya eklemeli yığın izlemeleri piecing için faydalıdır. Sayısal Aralık, yığın çerçevesinin içeriğiyle ilgili bilgi sağlamaz. Yalnızca yığın çerçeve konumlarının karşılaştırılmasının anlamı vardır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
