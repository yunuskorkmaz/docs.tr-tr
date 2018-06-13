---
title: ICorDebugFrame::GetStackRange Metodu
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
ms.openlocfilehash: 5da87071bc23ac17a3077049cd77f0fb8611439f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413026"
---
# <a name="icordebugframegetstackrange-method"></a>ICorDebugFrame::GetStackRange Metodu
Bu yığın çerçevesi mutlak bir adres aralığını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pStart`  
 [out] Bir işaretçi bir `CORDB_ADDRESS` bu tarafından temsil edilen yığın çerçevesi başlangıç adresini belirtir `ICorDebugFrame` nesnesi.  
  
 `pEnd`  
 [out] Bir işaretçi bir `CORDB_ADDRESS` bu tarafından temsil edilen yığın çerçevesi bitiş adresini belirtir `ICorDebugFrame` nesnesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yığın adres aralığı, birden çok hata ayıklama motorlarından toplanan araya eklemeli Yığın izlemeleri birlikte eklemekten için yararlıdır. Sayısal aralığın yığın çerçevesi içeriği hakkında hiçbir bilgi verilmektedir. Yalnızca yığın çerçeve konumları bir karşılaştırması için anlamlıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
