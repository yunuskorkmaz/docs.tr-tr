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
ms.openlocfilehash: 7a35ce025360e0ec8b7085d68e54548026b7c7fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178906"
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
 [çıkış] Bu `ICorDebugFrame` nesne `CORDB_ADDRESS` tarafından temsil edilen yığın çerçevesinin başlangıç adresini belirten bir işaretçi.  
  
 `pEnd`  
 [çıkış] Bu `ICorDebugFrame` nesne `CORDB_ADDRESS` tarafından temsil edilen yığın çerçevesinin bitiş adresini belirten bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yığının adres aralığı, birden çok hata ayıklama motorundan toplanan ara sıra yığın izlerini birleştirmek için yararlıdır. Sayısal aralık, yığın çerçevesinin içeriği hakkında bilgi sağlamaz. Yalnızca yığın çerçeve konumlarının karşılaştırılması için anlamlıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
