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
ms.openlocfilehash: 9452f238bd84c9c185ca8e007acac563474d29df
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212067"
---
# <a name="icordebugprocessisossuspended-method"></a>ICorDebugProcess::IsOSSuspended Yöntemi
Hata ayıklayıcının bu işlemi durdurmasından kaynaklanan belirtilen iş parçacığının askıya alınıp alınmadığını belirten bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a>Parametreler  
 `threadID`  
 'ndaki Söz konusu iş parçacığının KIMLIĞI.  
  
 `pbSuspended`  
 dışı `true`Belirtilen iş parçacığı askıya alınmışsa bir Boolean değeri işaretçisi; Aksi halde * `pbSuspended` `false` .  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklayıcının bu işlemi durdurmasının bir sonucu olarak belirtilen iş parçacığı askıya alındığında, belirtilen iş parçacığının Win32 askıya alma sayısı bir artırılır. Hata ayıklayıcı kullanıcı arabirimi (UI), iş parçacığının işletim sistemi (OS) askıya alma sayımını kullanıcıya görüntülerse bu bilgileri hesaba almak isteyebilir.  
  
 `IsOSSuspended`Yöntemi yalnızca yönetilmeyen hata ayıklama bağlamında anlamlı hale gelir. Yönetilen hata ayıklama sırasında, iş parçacıkları işletim sistemi tarafından askıya alınmış değil, birlikte askıya alınır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
