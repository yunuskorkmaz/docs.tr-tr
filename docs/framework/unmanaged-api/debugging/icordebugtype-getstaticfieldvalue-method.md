---
title: ICorDebugType::GetStaticFieldValue Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c6b86c5ce3cc246af600d9b65d2fe12a0427f9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663849"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a>ICorDebugType::GetStaticFieldValue Metodu
Bir arabirim işaretçisi Icordebugvalue nesneye belirtilen alan tarafından başvurulan statik alanının değeri içeren belirtilen bir yığın çerçevesine belirtecini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `fieldDef`  
 [in] Bir `mdFieldDef` statik alanı belirten belirteç.  
  
 `pFrame`  
 [in] Yığın çerçevesini temsil eden bir Icordebugframe işaretçisi.  
  
 `ppValue`  
 [out] Adresine bir işaretçi bir `ICorDebugValue` statik alanı değerini içeren.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetStaticFieldValue` Yöntemi kullanılabilir yalnızca tür ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE, ise tarafından belirtildiği şekilde [Icordebugtype::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) yöntemi.  
  
 Genel olmayan türler için işlemin gerçekleştirilmesinden tarafından `GetStaticFieldValue` çağırmakla aynıdır [Icordebugclass::getstaticfieldvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) tarafından döndürülen Icordebugclass nesne [Icordebugtype::getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).  
  
 Genel türler için statik alan değerine göre belirli bir örneğini oluşturmada olacaktır. Ayrıca, statik alan büyük olasılıkla bir iş parçacığı, bir bağlamı veya uygulama etki alanı göreli olabilir, yığın çerçevesinin uygun değeri belirlemek hata ayıklayıcı yardımcı olur.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetStaticFieldValue` yalnızca bir çağrı kullanılabilir `ICorDebugType::GetType` ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE değerini döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
