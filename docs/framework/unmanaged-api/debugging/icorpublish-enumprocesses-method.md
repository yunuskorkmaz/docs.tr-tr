---
title: ICorPublish::EnumProcesses Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3af824a23d683f4d450ef6f60fd407928c41d51e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536964"
---
# <a name="icorpublishenumprocesses-method"></a>ICorPublish::EnumProcesses Yöntemi
Bu bilgisayar üzerinde çalışan yönetilen işlemler için bir numaralandırıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `Type`  
 Değerini [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) alınacak işlem türünü belirten sabit listesi. Geçerli sürümde, yalnızca COR_PUB_MANAGEDONLY geçerli değil.  
  
 `ppIEnum`  
 Adresine bir işaretçi bir [Icorpublishprocessenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) Numaralandırıcı işlemlerin örneği.  
  
## <a name="remarks"></a>Açıklamalar  
 Numaralandırıcının toplama işlemlerinin ne zaman çalışan işlemler üzerinde bir anlık görüntü alır `EnumProcesses` yöntemi çağrılır. Numaralandırıcı önce sonlandırma veya sonrasında herhangi bir işlem içermez `EnumProcesses` çağrılır.  
  
 `EnumProcesses` Yöntemi çağrılabilir birden çok kez bu [Icorpublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) işlemlerinin yeni ve güncel bir koleksiyon oluşturmak için örneği. Mevcut koleksiyonlar sonraki çağrılar tarafından etkilenmez `EnumProcesses` yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub.idl, CorPub.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorPublish Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
