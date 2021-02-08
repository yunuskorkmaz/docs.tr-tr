---
description: ': ICorDebugAppDomain:: ısekli yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 79427d08be9ffea253695b67767d68589edf6979
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772392"
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
 [out] `true` hata ayıklayıcı uygulama etki alanına eklenmişse; Aksi takdirde, `false` .  
  
## <a name="remarks"></a>Açıklamalar  

 ICorDebugController yöntemleri, hata ayıklayıcı uygulama etki alanına iliştirene kadar kullanılamaz.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
