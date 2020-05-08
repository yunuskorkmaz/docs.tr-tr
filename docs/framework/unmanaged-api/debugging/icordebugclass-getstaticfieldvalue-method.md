---
title: ICorDebugClass::GetStaticFieldValue Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 56e718b4-fabd-418b-a5b3-3cc33c745683
topic_type:
- apiref
ms.openlocfilehash: d4a254853256e1a1440f5588418b94e39eabcc9a
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894107"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a>ICorDebugClass::GetStaticFieldValue Yöntemi
Belirtilen statik alanın değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `fieldDef`  
 'ndaki Alınacak alana `Def` başvuran bir alan belirteci.  
  
 `pFrame`  
 'ndaki İş parçacığı, bağlam veya uygulama etki alanı hazırlama arasında belirsizliği ortadan kaldırmak için kullanılacak çerçeveyi temsil eden ICorDebugFrame nesnesine yönelik bir işaretçi.  
  
 Statik alan bir iş parçacığına, bir içeriğe veya bir uygulama etki alanına göreli ise, çerçeve uygun değeri tespit eder.  
  
 `ppValue`  
 dışı Statik alanın değerini temsil eden bir ICorDebugValue nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Parametreli türler için, statik bir alanın değeri, belirli bir örnek oluşturma ile ilişkilidir. Bu nedenle, sınıf oluşturucusu türünde <xref:System.Type>parametreler alırsa, yerine [ICorDebugType:: GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) çağırın. `ICorDebugClass::GetStaticFieldValue`  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
