---
title: ICorDebugILFrame::GetArgument Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugILFrame.GetArgument
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetArgument
helpviewer_keywords:
- GetArgument method [.NET Framework debugging]
- ICorDebugILFrame::GetArgument method [.NET Framework debugging]
ms.assetid: 4e2fd423-f643-4c27-ba5f-41b5ebc3b416
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c6b1c097d830af4e68035f79670983002c15c16d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframegetargument-method"></a>ICorDebugILFrame::GetArgument Metodu
Belirtilen bağımsız değişkenin değeri bu Microsoft Ara dili (MSIL) yığın çerçevesinde bulunan alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwIndex`  
 [in] Bu MSIL yığın çerçevesi değişkeninde dizini.  
  
 `ppValue`  
 [out] Alınan değerin temsil eden Icordebugvalue nesne adresini gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetArgument` MSIL yığın çerçevesi veya tam zamanında (JIT) derlenmiş çerçeve yöntemi kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
