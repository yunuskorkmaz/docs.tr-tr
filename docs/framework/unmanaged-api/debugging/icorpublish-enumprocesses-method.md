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
ms.openlocfilehash: 5f785b22a3fbda6403c124ec70757b16f5335907
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790762"
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
 Alınacak işlemin türünü belirten [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) numaralandırması değeri. Geçerli sürümde yalnızca COR_PUB_MANAGEDONLY geçerlidir.  
  
 `ppIEnum`  
 İşlemlerin numaralandırıcısı olan [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) örneğinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Numaralandırıcının işlem koleksiyonu, `EnumProcesses` yöntemi çağrıldığında çalışan işlemlerin anlık görüntüsünü temel alır. Numaralandırıcı, `EnumProcesses` çağrıldıktan sonra, önce veya başlamadan sonra sona erecek herhangi bir işlem içermez.  
  
 `EnumProcesses` yöntemi bu [ICorPublish](icorpublish-interface.md) örneğinde birden çok kez çağrılabilir ve bu işlemlerin yeni bir güncellik koleksiyonu oluşturulur. Mevcut koleksiyonlar `EnumProcesses` yönteminin sonraki çağrılarından etkilenmeyecektir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub. IDL, CorPub. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorPublish Arabirimi](icorpublish-interface.md)
