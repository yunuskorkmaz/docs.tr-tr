---
title: ICorDebugModule::GetMetaDataInterface Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type:
- apiref
ms.openlocfilehash: fb96949e22b4edfc0e64780a54bb38da44eb8369
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129542"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a>ICorDebugModule::GetMetaDataInterface Metodu
Modülün meta verilerini incelemek için kullanılabilecek bir meta veri arabirimi nesnesi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `riid`  
 'ndaki Meta veri arabirimini belirten başvuru Kımlığı.  
  
 `ppObj`  
 dışı [Meta veri arabirimlerinden](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)biri olan `T:IUnknown` nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklayıcı, Bu modülün düzenlenmesi için yapması gereken bir modül için özgün meta verilerin bir kopyasını oluşturmak üzere `GetMetaDataInterface` yöntemini kullanabilir. Hata ayıklayıcı, modül için bir [ımetadatayayma](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) arabirimi nesnesi almak üzere `GetMetaDataInterface` çağırır, ardından modülün meta verilerinin bir kopyasını belleğe kaydetmek Için [ımetadatayayma:: SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) öğesini çağırır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veriler](../../../../docs/framework/unmanaged-api/metadata/index.md)
