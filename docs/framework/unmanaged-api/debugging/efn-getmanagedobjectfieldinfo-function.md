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
ms.openlocfilehash: 4c088b7e1096f8b4cad11a3e27b4045e233989ae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676224"
---
# <a name="_efn_getmanagedobjectfieldinfo-function"></a>\_EFN \_ getmanagedobjectfieldınfo işlevi

Belirtilen nesne işaretçisini ve alan adını kullanarak bir nesnenin başından bir alana ve alanın değerine kadar olan sapmayı alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Hata ayıklama istemcisine yönelik bir işaretçi.  
  
 `objAddr`  
 'ndaki Yönetilen nesne işaretçisi.  
  
 szFieldName  
 'ndaki Alan adı için yönetilen bir nesne işaretçisi.  
  
 `pValue`  
 dışı Alan değeri. Bu parametre null olabilir.  
  
 `pOffset`  
 dışı `objAddr` Alana yapılan konum. Bu parametre null olabilir.  
  
## <a name="remarks"></a>Açıklamalar  

 Eğer fark 0 ise, hiçbir fark yazılmaz.  
  
 Şu anda bağlamda iş parçacığında yönetilen kod yoksa, işlev, bir 0xa0 tesis değeri ve 0x1000 hata kodu ile HRESULT SOS_E_NOMANAGEDCODE döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** SOS_Stacktrace. h  
  
 **.NET Framework sürümü:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Genel Statik İşlevleri](debugging-global-static-functions.md)
