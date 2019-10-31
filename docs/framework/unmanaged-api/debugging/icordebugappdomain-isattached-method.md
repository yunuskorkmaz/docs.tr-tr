---
title: ICorDebugAppDomain::IsAttached Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.IsAttached
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type:
- apiref
ms.openlocfilehash: 30e0b0c4ed9bac4abd1dc185031e41c1e3ed014a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134670"
---
# <a name="icordebugappdomainisattached-method"></a>ICorDebugAppDomain::IsAttached Yöntemi
Hata ayıklayıcının uygulama etki alanına bağlı olup olmadığını gösteren bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pbAttached`  
 [out] hata ayıklayıcı uygulama etki alanına iliştirilmişse `true`; Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 ICorDebugController yöntemleri, hata ayıklayıcı uygulama etki alanına iliştirene kadar kullanılamaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
