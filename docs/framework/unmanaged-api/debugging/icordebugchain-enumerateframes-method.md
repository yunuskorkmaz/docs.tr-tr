---
title: ICorDebugChain::EnumerateFrames Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
ms.openlocfilehash: ae6d81e6fdab0f8e3346d8a08a3b5ebc329a542a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730155"
---
# <a name="icordebugchainenumerateframes-method"></a>ICorDebugChain::EnumerateFrames Yöntemi

En son kareyle başlayarak zincirdeki tüm yönetilen yığın çerçevelerini içeren bir Numaralandırıcı alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppFrames`  
 dışı Yığın çerçevelerinin Numaralandırıcı olan ICorDebugFrameEnum nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Zincir, iş parçacığı için fiziksel çağrı yığınını temsil eder.  
  
 `EnumerateFrames`Yöntemi yalnızca yönetilen zincirler için çağrılmalıdır. Hata ayıklama API 'SI, yönetilmeyen Zincirlerdeki çerçeveleri almak için yöntemler sağlamaz. Hata ayıklayıcı, bu bilgileri almak için diğer yolları kullanmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
