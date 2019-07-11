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
ms.openlocfilehash: b12ba5ad5c85643d1f4c91585cf7abca210d22bd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752945"
---
# <a name="icordebugevalgetresult-method"></a>ICorDebugEval::GetResult Yöntemi
Bu değerlendirme sonuçlarını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
