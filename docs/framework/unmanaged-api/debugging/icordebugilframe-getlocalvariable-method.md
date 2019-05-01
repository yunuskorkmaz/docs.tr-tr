---
title: ICorDebugILFrame::GetLocalVariable Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetLocalVariable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetLocalVariable
helpviewer_keywords:
- ICorDebugILFrame::GetLocalVariable method [.NET Framework debugging]
- GetLocalVariable method [.NET Framework debugging]
ms.assetid: c8706356-d50b-4f87-a40c-39c3b7f4fd38
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ebd36f01297f24c050f84fb67e7673f8641fe206
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789733"
---
# <a name="icordebugilframegetlocalvariable-method"></a>ICorDebugILFrame::GetLocalVariable Metodu
Bu Microsoft Ara dili (MSIL) yığın çerçevesi içinde belirtilen yerel değişkenin değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwIndex`  
 [in] Bu MSIL yığın çerçevesinde yerel değişken dizini.  
  
 `ppValue`  
 [out] Alınan değeri temsil eden bir Icordebugvalue nesnenin adresi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetLocalVariable` Bir MSIL yığın çerçevesinde veya just-in-time (JIT) derlenmiş çerçevesinde yöntemi kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
