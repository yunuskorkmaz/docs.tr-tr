---
title: _EFN_GetManagedObjectName İşlevi
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectName
helpviewer_keywords:
- _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a95008d98436161ac919ef307273bc797519f15
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698349"
---
# <a name="efngetmanagedobjectname-function"></a>_EFN_GetManagedObjectName İşlevi
Belirtilen yönetilen nesne işaretçisi kullanılarak bir tür adını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `Client`  
 [in] Hata ayıklama istemci için bir işaretçi.  
  
 `objAddr`  
 [in] Bir yönetilen nesne işaretçisi.  
  
 szName  
 [out] Tür adı.  
  
 `cbName`  
 [out] Dize arabellek kullanılabilir karakter sayısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa yönetilen kod yok iş parçacığı üzerinde şu anda bağlamında, işlev HRESULT SOS_E_NOMANAGEDCODE 0xa0 tesis değerini ve 0x1000 hata kodu ile döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** SOS_Stacktrace.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
