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
ms.openlocfilehash: 5f0dd814ad5adfa1b0dd7199530a3f993634a548
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121792"
---
# <a name="icorpublishenumprocesses-method"></a>ICorPublish::EnumProcesses Yöntemi
Bu bilgisayarda çalışan yönetilen işlemlere yönelik bir Numaralandırıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `Type`  
 Alınacak işlemin türünü belirten [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) numaralandırması değeri. Geçerli sürümde yalnızca COR_PUB_MANAGEDONLY geçerlidir.  
  
 `ppIEnum`  
 İşlemlerin numaralandırıcısı olan [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) örneğinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Numaralandırıcının işlem koleksiyonu, `EnumProcesses` yöntemi çağrıldığında çalışan işlemlerin anlık görüntüsünü temel alır. Numaralandırıcı, `EnumProcesses` çağrıldıktan sonra, önce veya başlamadan sonra sona erecek herhangi bir işlem içermez.  
  
 `EnumProcesses` yöntemi bu [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) örneğinde birden çok kez çağrılabilir ve bu işlemlerin yeni bir güncellik koleksiyonu oluşturulur. Mevcut koleksiyonlar `EnumProcesses` yönteminin sonraki çağrılarından etkilenmeyecektir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub. IDL, CorPub. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorPublish Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
