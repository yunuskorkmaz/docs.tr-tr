---
title: ICorDebugILFrame::CanSetIP Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
ms.openlocfilehash: 57d83d1f301cbfd43f8f553d9aef4beb3baf95f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131078"
---
# <a name="icordebugilframecansetip-method"></a>ICorDebugILFrame::CanSetIP Yöntemi
Microsoft ara dili (MSIL) kodunda belirtilen konum konumuna yönerge işaretçisini ayarlamak için güvenli olup olmadığını belirten bir HRESULT alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `nOffset`  
 'ndaki Yönerge işaretçisi için istenen ayar.  
  
## <a name="remarks"></a>Açıklamalar  
 [ICorDebugILFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) metodunu çağırmadan önce `CanSetIP` metodunu kullanın. `CanSetIP` S_OK dışında bir HRESULT döndürürse, yine de `ICorDebugILFrame::SetIP`çağırabilirsiniz, ancak hata ayıklamanın hata ayıklamakta olan kodun güvenli ve doğru yürütülmesine devam edeceğini garanti vermez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug, h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
