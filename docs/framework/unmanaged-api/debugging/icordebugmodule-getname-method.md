---
title: ICorDebugModule::GetName Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetName
helpviewer_keywords:
- ICorDebugModule::GetName method [.NET Framework debugging]
- GetName method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: db499637-7ba9-421e-b8b1-35856995e80b
topic_type:
- apiref
ms.openlocfilehash: b27e7a2cdcbfc3a88a734230118d99c2dd5c700e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129533"
---
# <a name="icordebugmodulegetname-method"></a>ICorDebugModule::GetName Metodu
Modülün dosya adını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cchname`  
 'ndaki `szName` dizisinin boyutu.  
  
 `pcchName`  
 'ndaki Döndürülen adın uzunluğuna yönelik bir işaretçi.  
  
 `szName`  
 dışı Döndürülen adı depolayan bir dizi.  
  
## <a name="remarks"></a>Açıklamalar  
 Modülün dosya adı diskteki adla eşleşiyorsa `GetName` yöntemi bir S_OK HRESULT döndürür. `GetName`, bir dinamik veya bellek içi modül gibi bir ad olursa, bir S_FALSE HRESULT döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
