---
title: ICorDebugAppDomain::EnumerateBreakpoints Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateBreakpoints
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints method [.NET Framework debugging]
- EnumerateBreakpoints method [.NET Framework debugging]
ms.assetid: 206069c5-25cb-4794-9d69-67c5aa7ed0af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a683f1531ed28fbd8ef085414bb7cb365762ffde
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738044"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a>ICorDebugAppDomain::EnumerateBreakpoints Yöntemi
Bir numaralandırıcı, uygulama etki alanı için tüm etkin kesme noktalarını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppBreakpoints`  
 [out] Icordebugbreakpointenum nesnenin uygulama etki alanındaki tüm etkin kesme noktaları için bir numaralandırıcı adresi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Numaralandırıcı, kesme noktaları, işlev kesme noktaları ve veri kesme noktaları da dahil olmak üzere tüm türleri içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
