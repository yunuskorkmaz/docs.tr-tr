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
ms.openlocfilehash: 873dd5a1eb2c9356049d2d0c0cb495b963c2ae46
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784186"
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
 'ndaki Alınacak alana başvuran bir alan `Def` belirteç.  
  
 `pFrame`  
 'ndaki İş parçacığı, bağlam veya uygulama etki alanı hazırlama arasında belirsizliği ortadan kaldırmak için kullanılacak çerçeveyi temsil eden ICorDebugFrame nesnesine yönelik bir işaretçi.  
  
 Statik alan bir iş parçacığına, bir içeriğe veya bir uygulama etki alanına göreli ise, çerçeve uygun değeri tespit eder.  
  
 `ppValue`  
 dışı Statik alanın değerini temsil eden bir ICorDebugValue nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Parametreli türler için, statik bir alanın değeri, belirli bir örnek oluşturma ile ilişkilidir. Bu nedenle, sınıf Oluşturucu <xref:System.Type>türü parametreler alırsa, `ICorDebugClass::GetStaticFieldValue`yerine [ICorDebugType:: GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) öğesini çağırın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
