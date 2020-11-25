---
title: ICorDebugController::EnumerateThreads Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugController.EnumerateThreads
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::EnumerateThreads
helpviewer_keywords:
- ICorDebugController::EnumerateThreads method [.NET Framework debugging]
- EnumerateThreads method [.NET Framework debugging]
ms.assetid: 73f536f6-4668-4a4a-b3e4-ac7df862d5be
topic_type:
- apiref
ms.openlocfilehash: f98118f9206d9ccd7dc9dc9a943500c7b4cd676a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732664"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a>ICorDebugController::EnumerateThreads Yöntemi

İşlemdeki etkin yönetilen iş parçacıkları için bir Numaralandırıcı alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppThreads`  
 dışı İşlemde etkin olan tüm yönetilen iş parçacıkları için bir numaralandırıcısı temsil eden "ICorDebugThreadEnum" nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 [ICorDebugManagedCallback:: CreateThread](icordebugmanagedcallback-createthread-method.md) geri çağırması gönderildikten sonra ve [ICorDebugManagedCallback:: ExitThread](icordebugmanagedcallback-exitthread-method.md) geri çağırması gönderildikten sonra bir iş parçacığı etkin kabul edilir. Yönetilen bir iş parçacığında Stack üzerinde herhangi bir yönetilen çerçeve bulunmayabilir. İş parçacıkları [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) geri çağırmadan önce bile Numaralandırılabilir. Sabit Listesi doğal olarak boş olur.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
