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
ms.openlocfilehash: 37bf5abf66b613d8432af84c7d73aff60e9127cb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791270"
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
 `GetStaticFieldValue` yöntemi, [ICorDebugType:: GetType](icordebugtype-gettype-method.md) yönteminde gösterildiği gibi, yalnızca tür ELEMENT_TYPE_CLASS veya element_type_valuetype olduğunda kullanılabilir.  
  
 Genel olmayan türler için, `GetStaticFieldValue` tarafından gerçekleştirilen işlem ICorDebugClass [:: GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) ' ı [ICorDebugType:: GetClass](icordebugtype-getclass-method.md)tarafından döndürülen ICorDebugClass nesnesinde çağırma ile aynıdır.  
  
 Genel türler için, statik bir alan değeri belirli bir örnek oluşturma ile göreli olur. Ayrıca, statik alan muhtemelen bir iş parçacığına, bir içeriğe veya bir uygulama etki alanına göreli olabilir, yığın çerçevesi hata ayıklayıcının doğru değeri belirlemesine yardımcı olur.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetStaticFieldValue`, yalnızca `ICorDebugType::GetType` çağrısı ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE değerini döndürdüğünde kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
