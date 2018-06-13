---
title: ICorDebugClass::GetStaticFieldValue Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d3c3c0c5634653d14577de9a1334048d75216b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405632"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a>ICorDebugClass::GetStaticFieldValue Metodu
Belirtilen statik alanın değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `fieldDef`  
 [in] Bir alan `Def` alınacak alanın başvuran belirteci.  
  
 `pFrame`  
 [in] Bir işaretçi Icordebugframe nesneye iş parçacığı, bağlamı veya uygulama etki alanı istatistikleri arasında belirsizliğini ortadan kaldırmak için kullanılacak çerçeveyi temsil eder.  
  
 Statik alan bir iş parçacığı, bir içerik veya uygulama etki alanı göreli ise, çerçeve uygun değeri belirler.  
  
 `ppValue`  
 [out] Bir işaretçi adresine Icordebugvalue nesnenin statik alanın değerini temsil eder.  
  
## <a name="remarks"></a>Açıklamalar  
 Parametreli türler için statik bir alana göre belirli örneklemesi değeridir. Bu nedenle, sınıf oluşturucu türünde parametre sürerse <xref:System.Type>, çağrı [Icordebugtype::getstaticfieldvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) yerine `ICorDebugClass::GetStaticFieldValue`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
