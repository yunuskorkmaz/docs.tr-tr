---
title: "ICorDebugReferenceValue::Dereference Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugReferenceValue.Dereference
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0dbf2775217a78c1cbb9a96093354f0fc0b278bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugreferencevaluedereference-method"></a>ICorDebugReferenceValue::Dereference Yöntemi
Başvurulan nesnesini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppValue`  
 [out] Bu Icordebugreferencevalue nesne işaret ettiği nesneyi temsil eden bir Icordebugvalue adresini gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugValue` Nesne, yalnızca kendi başvuru olmayan henüz devre dışı bırakılmış ederken geçerlidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
