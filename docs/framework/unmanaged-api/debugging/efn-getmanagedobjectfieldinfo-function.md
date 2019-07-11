---
title: _EFN_GetManagedObjectFieldInfo İşlevi
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectFieldInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectFieldInfo
helpviewer_keywords:
- _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1de0b3b05d38c1fec38b9436c653973dfaa4136
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739005"
---
# <a name="efngetmanagedobjectfieldinfo-function"></a>\_EFN\_GetManagedObjectFieldInfo işlevi
Uzaklık nesnenin başlangıcından bir alan ve sağlanan nesne işaretçisi ve alan adını kullanarak, alanın değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `Client`  
 [in] Hata ayıklama istemci için bir işaretçi.  
  
 `objAddr`  
 [in] Bir yönetilen nesne işaretçisi.  
  
 szFieldName  
 [in] Alan adı için bir yönetilen nesne işaretçisi.  
  
 `pValue`  
 [out] Alan değeri. Bu parametre null olabilir.  
  
 `pOffset`  
 [out] Uzaklığı `objAddr` alan. Bu parametre null olabilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Uzaklık, uzaklık 0 ise, yazılır.  
  
 Varsa yönetilen kod yok iş parçacığı üzerinde şu anda bağlamında, işlev HRESULT SOS_E_NOMANAGEDCODE 0xa0 tesis değerini ve 0x1000 hata kodu ile döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** SOS_Stacktrace.h  
  
 **.NET framework sürümü:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
