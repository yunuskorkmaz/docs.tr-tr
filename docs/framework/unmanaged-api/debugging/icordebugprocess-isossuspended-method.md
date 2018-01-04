---
title: "ICorDebugProcess::IsOSSuspended Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.IsOSSuspended
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 97c394e3084007227cf157c62a12df3f5cfac8e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessisossuspended-method"></a>ICorDebugProcess::IsOSSuspended Yöntemi
Belirtilen iş parçacığı bu işlem durdurma hata ayıklayıcı sonucunda askıya olup olmadığını belirten bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `threadID`  
 [in] Söz konusu iş parçacığı kimliği.  
  
 `pbSuspended`  
 [out] Boolean bir değer için bir işaretçi `true` belirtilen iş parçacığı olması durumunda, aksi askıya alınmış *`pbSuspended` olan `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Belirtilen iş parçacığı bu işlem durdurma hata ayıklayıcı sonucu olarak askıya alındı, belirtilen iş parçacığının Win32 askıya alma sayısı bir artırılır. Hata ayıklayıcı kullanıcı arabirimi (UI) işletim sistemini görüntülenirse, bu bilgileri dikkate almak isteyebilirsiniz (OS) askıya kullanıcı için iş parçacığı sayısı.  
  
 `IsOSSuspended` Yöntemi yönetilmeyen hata ayıklama yalnızca bağlamında mantıklı hale getirir. Yönetilen hata ayıklama sırasında iş parçacıklarını işbirliği ile askıya alınmış yerine OS askıya alındı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
