---
description: ': ICorDebugModule:: GetName metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0f81271b2be283621027f4c835b6f220a383d771
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660219"
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
 'ndaki `szName` Dizinin boyutu.  
  
 `pcchName`  
 'ndaki Döndürülen adın uzunluğuna yönelik bir işaretçi.  
  
 `szName`  
 dışı Döndürülen adı depolayan bir dizi.  
  
## <a name="remarks"></a>Açıklamalar  

 `GetName`Modülün dosya adı diskteki adla eşleşiyorsa Yöntem bir S_OK HRESULT döndürür. `GetName` ad, dinamik veya bellek içi bir modül için gibi, varsa HRESULT S_FALSE döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
