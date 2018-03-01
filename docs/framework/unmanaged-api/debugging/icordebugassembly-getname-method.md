---
title: ICorDebugAssembly::GetName Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugAssembly.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetName
helpviewer_keywords:
- ICorDebugAssembly::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: cdeda721-b214-4503-a291-c70b68b5f36b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cf2b84a6ab7cc1745fbf7330e66f94ea04635892
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassemblygetname-method"></a>ICorDebugAssembly::GetName Metodu
Derlemenin adını alır bu `ICorDebugAssembly` örneğini temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cchName`  
 [in] Boyutunu `szName` dizi.  
  
 `pcchName`  
 [out] Gerçek adının uzunluğu belirten bir tamsayı gösteren bir işaretçi.  
  
 `szName`  
 [out] Adını depolar bir dizi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetName` Yöntemi derleme tam yolunu ve dosya adını döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
