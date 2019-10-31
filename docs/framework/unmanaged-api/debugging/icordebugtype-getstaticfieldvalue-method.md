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
ms.openlocfilehash: 95183701987d3ddec3835a17c5d256c25c2c4c64
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132074"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a>ICorDebugType::GetStaticFieldValue Metodu
Belirtilen yığın çerçevesindeki belirtilen alan belirtecinin başvurduğu statik alanın değerini içeren bir ICorDebugValue nesnesine bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `fieldDef`  
 'ndaki Statik alanı belirten `mdFieldDef` belirteç.  
  
 `pFrame`  
 'ndaki Yığın çerçevesini temsil eden bir ICorDebugFrame işaretçisi.  
  
 `ppValue`  
 dışı Statik alanın değerini içeren `ICorDebugValue` adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetStaticFieldValue` yöntemi, [ICorDebugType:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) yönteminde gösterildiği gibi yalnızca tür element_type_class veya element_type_valuetype olduğunda kullanılabilir.  
  
 Genel olmayan türler için, `GetStaticFieldValue` tarafından gerçekleştirilen işlem ICorDebugClass [:: GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) ' ı [ICorDebugType:: GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)tarafından döndürülen ICorDebugClass nesnesinde çağırma ile aynıdır.  
  
 Genel türler için, statik bir alan değeri belirli bir örnek oluşturma ile göreli olur. Ayrıca, statik alan muhtemelen bir iş parçacığına, bir içeriğe veya bir uygulama etki alanına göreli olabilir, yığın çerçevesi hata ayıklayıcının doğru değeri belirlemesine yardımcı olur.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetStaticFieldValue`, yalnızca `ICorDebugType::GetType` çağrısı ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE değerini döndürdüğünde kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
