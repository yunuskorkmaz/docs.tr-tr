---
title: ICorDebugMDA::GetName Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c31125b1faf9f14262e8e4a4c6269671a35519f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmdagetname-method"></a>ICorDebugMDA::GetName Metodu
Tarafından temsil edilen yönetilen hata ayıklama Yardımcısı (MDA) adını içeren bir dize alır [Icordebugmda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cchName`  
 [in] Boyutunu `szName` dizi.  
  
 `pcchName`  
 [out] Adın uzunluğu için bir işaretçi.  
  
 `szName`  
 [out] Dizi adı depolanacağı.  
  
## <a name="remarks"></a>Açıklamalar  
 MDA adları benzersiz değerlerdir. `GetName` XML akışı alma ve ad şemasını temel alan akıştan ayıklanıyor uygun performans alternatif bir yöntemdir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugMDA Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
