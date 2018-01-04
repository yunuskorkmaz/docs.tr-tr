---
title: "ICorPublish::EnumProcesses Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublish.EnumProcesses
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d7e0af492cbec401d7470502de807033f21e39f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishenumprocesses-method"></a>ICorPublish::EnumProcesses Yöntemi
Bu bilgisayarda çalışan yönetilen işlemler için bir numaralandırıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `Type`  
 Değerini [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) alınacak işlemi türünü belirtir numaralandırması. Geçerli sürümde, yalnızca COR_PUB_MANAGEDONLY geçerli değil.  
  
 `ppIEnum`  
 Adresine bir işaretçi bir [Icorpublishprocessenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) işlemlerin Numaralandırıcı olan örneği.  
  
## <a name="remarks"></a>Açıklamalar  
 Numaralandırıcının koleksiyonu işlemlerinin ne zaman çalışan işlemler üzerinde bir anlık görüntü tabanlı `EnumProcesses` yöntemi çağrılır. Numaralayıcı önce sonlandırma veya sonrasında herhangi bir işlem içermeyecek `EnumProcesses` olarak adlandırılır.  
  
 `EnumProcesses` Yöntemi çağrılabilir birden çok kez bu [Icorpublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) işlemleri yeni güncel bir koleksiyonunu oluşturmak için örnek. Var olan koleksiyonları sonraki çağrılar tarafından etkilenmez `EnumProcesses` yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorPub.idl, CorPub.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorPublish Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
