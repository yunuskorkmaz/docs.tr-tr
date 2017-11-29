---
title: "PFN_CLRDataCreateInstance İşlev İşaretçisi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: PFN_CLRDataCreateInstance
api_location: mscordbi.dll
api_type: COM
f1_keywords: PFN_CLRDataCreateInstance
helpviewer_keywords: PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7ec5783381c667d666c447b6d9861d9baaad3907
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="pfnclrdatacreateinstance-function-pointer"></a>PFN_CLRDataCreateInstance İşlev İşaretçisi
Belirtilen hedef öğesi için bir arabirimi nesnesi oluşturan bir işlev noktalarına.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `iid`  
 [in] Arabirim örneğinin oluşturulması için tanımlayıcı.  
  
 `target`  
 [in] Kullanıcı uygulanan bir işaretçi [Iclrdatatarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) arabirimi nesnesi oluşturulacağı hedef öğeyi temsil eden nesne.  
  
 `iface`  
 [out] Döndürülen arabirimi nesnesi adresini gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `ICLRDataTarget` Nesnesi, hata ayıklama uygulama yazıcı tarafından gerçekleştirilir. Uygulama temsil ettiği hedef öğesi türüne bağlıdır. Hedef öğesi, bir işlem, bellek dökümü, uzak makine vb. olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** ClrData.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama genel statik işlevleri](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
