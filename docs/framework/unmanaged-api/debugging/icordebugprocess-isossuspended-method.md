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
ms.openlocfilehash: 140855ca2828ba2a8fdf811d29fc512f6ccd20e0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
