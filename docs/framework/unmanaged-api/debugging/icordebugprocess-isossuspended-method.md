---
title: ICorDebugProcess::IsOSSuspended Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsOSSuspended
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 275f62c8211f71f067d310dd4b3af2ddb11e93d7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755464"
---
# <a name="icordebugprocessisossuspended-method"></a>ICorDebugProcess::IsOSSuspended Yöntemi
Bu işlem durdurulurken bir hata ayıklayıcı sonucu olarak belirtilen iş parçacığını askıya olup olmadığını gösteren bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a>Parametreler  
 `threadID`  
 [in] Söz konusu iş parçacığı kimliği.  
  
 `pbSuspended`  
 [out] Boolean bir değer için bir işaretçi `true` belirtilen iş parçacığı çağrıldıysa, aksi takdirde askıya alınmış *`pbSuspended` olduğu `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Belirtilen iş parçacığı bu işlem durdurulurken bir hata ayıklayıcı sonucu olarak askıya alındı, belirtilen iş parçacığının Win32 askıya alma sayı bir artırılır. Hata ayıklayıcı kullanıcı arabirimi (UI) işletim sistemini görüntülerse bu bilgileri dikkate almak isteyebilirsiniz (OS) askıya alma, kullanıcı iş parçacığı sayısı.  
  
 `IsOSSuspended` Yöntemi yönetilmeyen hata ayıklama yalnızca bağlamında göre mantıklı. Yönetilen hata ayıklama sırasında iş parçacıklarını işbirliği ile askıya alınmış yerine işletim sistemi askıya alındı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
