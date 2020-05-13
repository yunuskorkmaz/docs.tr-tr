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
ms.openlocfilehash: 8f3cc16054d4b5340c9460e9c3fbcba6e563567a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212561"
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
 dışı `T:IUnknown` [Meta veri arabirimlerinden](../metadata/metadata-interfaces.md)biri olan bir nesnenin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklayıcı, `GetMetaDataInterface` Bu modülü düzenlemek için yapması gereken bir modül için özgün meta verilerin bir kopyasını oluşturmak üzere yöntemini kullanabilir. Hata ayıklayıcı `GetMetaDataInterface` Modül için bir [ımetadatayayma](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) arabirimi nesnesi almak için öğesini çağırır ve modülün meta verilerinin bir kopyasını belleğe kaydetmek Için [ımetadatayayma:: SaveToMemory](../metadata/imetadataemit-savetomemory-method.md) öğesini çağırır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veriler](../metadata/index.md)
