---
title: ICorDebugEval::GetResult Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8e7fcb4f44d6bdf6f18c93b1046b549331621a4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470802"
---
# <a name="icordebugevalgetresult-method"></a>ICorDebugEval::GetResult Yöntemi
Bu değerlendirme sonuçlarını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppResult`  
 [out] Değerlendirme normalde tamamlanırsa Bu değerlendirme sonuçlarını temsil eden bir Icordebugvalue nesnenin adresini işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetResult` Yöntemi, yalnızca değerlendirme tamamlandıktan sonra geçerlidir.  
  
 Normalde, değerlendirme tamamlanırsa `ppResult` sonuçları belirtir. Bir özel durumla sona ererse, oluşturulan özel durum oluşur. Değerlendirme için yeni bir nesne ise, yeni nesneye başvuru sonucudur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
