---
title: ICorDebugFrame::CreateStepper Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3662ed8a3fda5881b0e0929a830d19b0d805299f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411037"
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
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
