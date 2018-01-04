---
title: "ICorDebugEval::CreateValue Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.CreateValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 64d55a951795cc5efc1bfc624dbe07575be153aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalcreatevalue-method"></a>ICorDebugEval::CreateValue Yöntemi
Belirtilen türde bir değer sıfır ya da null bir başlangıç değeriyle birlikte oluşturur.  
  
 Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır. Kullanım [Icordebugeval2::createvaluefortype](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `elementType`  
 [in] Değerini [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) numaralandırma değeri türünü belirtir.  
  
 `pElementClass`  
 [in] İşaretçi bir [Icordebugclass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) değer sınıfının türü basit tür değilse belirten nesne.  
  
 `ppValue`  
 [out] İşaretçi adresine "ICorDebugValue" nesnenin değerini temsil eder.  
  
## <a name="remarks"></a>Açıklamalar  
 `CreateValue`oluşturur bir `ICorDebugValue` bir işlev değerlendirmesi kullanmanın tek amacı için belirli türde nesne. Bu değer nesnesi kullanıcı sabitleri parametre olarak geçirmek için kullanılabilir.  
  
 Değerin türü basit tür ilk değeri sıfır ise, veya null. Kullanım [Icordebuggenericvalue::SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) basit tür değeri ayarlanamıyor.  
  
 Varsa değerini `elementType` ELEMENT_TYPE_CLASS, olan bir "Icordebugreferencevalue" Al (döndürülen `ppValue`) null Nesne başvurusu temsil eden. Nesne başvurusu parametrelerine sahip İşlev değerlendirmesi için null geçirmek için bu nesneyi kullanabilirsiniz. Ayarlayamazsınız `ICorDebugValue` şey; her zaman null kalır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** 1.1, 1.0  
  
## <a name="see-also"></a>Ayrıca Bkz.  
    
 [CreateValueForType Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)  
 Icordebugvalue
