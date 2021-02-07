---
description: ': ICorDebugFrame:: CreateStepper yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 394418b89fd7a1c780a5bc33b97b8ef40bab8df2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693102"
---
# <a name="icordebugframecreatestepper-method"></a>ICorDebugFrame::CreateStepper Yöntemi

Hata ayıklayıcının bu ICorDebugFrame 'e göre atlama işlemleri gerçekleştirmesini sağlayan bir Stepper alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppStepper`  
 dışı Hata ayıklayıcının geçerli çerçeveye göre atlama işlemleri gerçekleştirmesini sağlayan bir ICorDebugStepper nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Çerçeve etkin değilse, Stepper nesnesi genellikle adım tamamlanmadan önce çerçeveye geri dönmesi gerekecektir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
