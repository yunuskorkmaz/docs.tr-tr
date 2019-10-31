---
title: ICorDebugMDA::GetName Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetName
helpviewer_keywords:
- ICorDebugMDA::GetName method [.NET Framework debugging]
- GetName method, ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 885bf5e8-00b7-4cd7-9d8d-e720d47918c4
topic_type:
- apiref
ms.openlocfilehash: 1b19ce5e9f795fd9ff4dd15e10256a150063a314
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128035"
---
# <a name="icordebugmdagetname-method"></a>ICorDebugMDA::GetName Yöntemi
[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)tarafından temsil edilen yönetilen hata ayıklama Yardımcısı 'NıN (MDA) adını içeren bir dize alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cchName`  
 'ndaki `szName` dizisinin boyutu.  
  
 `pcchName`  
 dışı Adın uzunluğuna yönelik bir işaretçi.  
  
 `szName`  
 dışı Adın kaydedileceği bir dizi.  
  
## <a name="remarks"></a>Açıklamalar  
 MDA adları benzersiz değerlerdir. `GetName` yöntemi, XML akışının alınması ve şemayı temel alarak akıştan ad ayıklamanın uygun bir performans alternatifidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMDA Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
