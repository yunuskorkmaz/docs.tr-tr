---
description: ': ICorDebugModule:: GetGlobalVariableValue Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugModule::GetGlobalVariableValue Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetGlobalVariableValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetGlobalVariableValue
helpviewer_keywords:
- ICorDebugModule::GetGlobalVariableValue method [.NET Framework debugging]
- GetGlobalVariableValue method [.NET Framework debugging]
ms.assetid: bbc0881c-6a59-41a0-b5ee-2f3d1b71684c
topic_type:
- apiref
ms.openlocfilehash: a4efe2f56387be7351fd5bc16716bcd1f34f7d7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691672"
---
# <a name="icordebugmodulegetglobalvariablevalue-method"></a>ICorDebugModule::GetGlobalVariableValue Metodu

Belirtilen genel değişkenin değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetGlobalVariableValue(  
    [in]  mdFieldDef      fieldDef,  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `fieldDef`  
 'ndaki `mdFieldDef` Genel değişkeni tanımlayan meta verilere başvuruda bulunan bir belirteç.  
  
 `ppValue`  
 dışı Belirtilen genel değişkenin değerini temsil eden bir ICorDebugValue nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
