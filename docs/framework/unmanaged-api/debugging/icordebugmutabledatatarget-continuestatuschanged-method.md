---
description: ': Icordebugmutabledatatarget:: ContinueStatusChanged yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugmutabledatatarget:: ContinueStatusChanged yöntemi'
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
ms.openlocfilehash: 6655d6f1a115b4879c73e356faa8e8785a110078
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722509"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a>Icordebugmutabledatatarget:: ContinueStatusChanged yöntemi

Belirtilen iş parçacığında bekleyen hata ayıklama olayının devamlılık durumunu değiştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
## <a name="parameters"></a>Parametreler  

 `dwThreadId`  
 İşletim sistemi tanımlı iş parçacığı tanımlayıcısı.  
  
 `continueStatus`  
 İstenen yeni Devamlılık durumunu temsil eden bir [COREDB_CONTINUE_STATUS](../common-data-types-unmanaged-api-reference.md) değeri.  
  
## <a name="remarks"></a>Açıklamalar  

 Hata ayıklayıcı, `ContinueStatusChanged` geçerli hata ayıklama olayının normalde işlenme yönteminden farklı olabilecek bir şekilde işlenmesini gerektiren bir ICorDebug yöntemi çağırdığında yöntemini çağırır. Örneğin, bekleyen bir özel durum varsa ve hata ayıklayıcı özel durumu iptal eden bir işlem isterse ( [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) veya `FuncEval` ), bu API, özel durumun iptal edilmesini istemek için kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMutableDataTarget Arabirimi](icordebugmutabledatatarget-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
