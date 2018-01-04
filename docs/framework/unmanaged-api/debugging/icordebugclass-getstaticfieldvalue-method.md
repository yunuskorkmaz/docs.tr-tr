---
title: ICorDebugClass::GetStaticFieldValue Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass.GetStaticFieldValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 56e718b4-fabd-418b-a5b3-3cc33c745683
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 21176eb73b3655fe8bd4b2187b6da49a3c31bd82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
