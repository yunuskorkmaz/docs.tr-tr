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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7f62385031967c164915fd31735a6d962f557fa
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894993"
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
 Modülün dosya adı diskteki adıyla eşleşiyorsa, yöntemibirS_OKHRESULTdöndürür.`GetName` `GetName`ad, dinamik veya bellek içi bir modül gibi olursa, bir S_FALSE HRESULT döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
