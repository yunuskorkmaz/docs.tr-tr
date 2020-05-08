---
title: ICorDebug::DebugActiveProcess Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebug.DebugActiveProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type:
- apiref
ms.openlocfilehash: 3630e25b6c24edaa366f1b0fae088e760e851fa4
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895401"
---
# <a name="icordebugdebugactiveprocess-method"></a>ICorDebug::DebugActiveProcess Yöntemi
Hata ayıklayıcıyı mevcut bir işleme iliştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `id`  
 'ndaki Hata ayıklayıcının eklendiği işlemin KIMLIĞI.  
  
 `win32Attach`  
 'ndaki Hata ayıklayıcı, işlem için Win32 `true` hata ayıklayıcısı olarak davranması ve yönetilmeyen geri çağırmaları dağıtmak için olarak ayarlanan Boole değeri; Aksi takdirde `false`,.  
  
 `ppProcess`  
 dışı Hata ayıklayıcının eklendiği işlemi temsil eden bir "ICorDebugProcess" nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 , IA-64 tabanlı ve AMD64 tabanlı platformlar gibi Win9x ve x86 olmayan platformlarda birlikte çalışma hata ayıklaması desteklenmez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](icordebug-interface.md)
