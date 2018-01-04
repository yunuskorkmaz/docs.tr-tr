---
title: "ICorDebugFrame::CreateStepper Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.CreateStepper
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 93f6741a030e72406fb8099c6373896d14cb9332
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframecreatestepper-method"></a>ICorDebugFrame::CreateStepper Yöntemi
Hata ayıklayıcı bu Icordebugframe göre sürüm işlemlerini gerçekleştirmek imkan tanıyan Adımlayıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppStepper`  
 [out] Hata ayıklayıcı geçerli çerçeve göre sürüm işlemlerini gerçekleştirmek imkan tanıyan ICorDebugStepper nesnenin adresini gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Çerçeve etkin değilse, Adımlayıcı nesne genellikle adımı tamamlanmadan önce çerçeveye dönmek gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
