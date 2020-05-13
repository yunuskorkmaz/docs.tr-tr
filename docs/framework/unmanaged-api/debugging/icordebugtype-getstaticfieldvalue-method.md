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
ms.openlocfilehash: 83ac91133b226e2ac263356941c3fc3288355e7e
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379932"
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
 'ndaki `mdFieldDef`Statik alanı belirten bir belirteç.  
  
 `pFrame`  
 'ndaki Yığın çerçevesini temsil eden bir ICorDebugFrame işaretçisi.  
  
 `ppValue`  
 dışı `ICorDebugValue`Statik alanın değerini içeren adresinin bir işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetStaticFieldValue`Yöntemi, [ICorDebugType:: GetType](icordebugtype-gettype-method.md) yönteminde gösterildiği gibi, yalnızca tür element_type_class veya element_type_valuetype olduğunda kullanılabilir.  
  
 Genel olmayan türler için, tarafından gerçekleştirilen işlem ICorDebugClass `GetStaticFieldValue` [:: GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) ' ı [ICorDebugType:: GetClass](icordebugtype-getclass-method.md)tarafından döndürülen ICorDebugClass nesnesinde çağırmaya eşdeğerdir.  
  
 Genel türler için, statik bir alan değeri belirli bir örnek oluşturma ile göreli olur. Ayrıca, statik alan muhtemelen bir iş parçacığına, bir içeriğe veya bir uygulama etki alanına göreli olabilir, yığın çerçevesi hata ayıklayıcının doğru değeri belirlemesine yardımcı olur.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetStaticFieldValue`yalnızca bir çağrı `ICorDebugType::GetType` element_type_class veya element_type_valuetype değerini döndürdüğünde kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
