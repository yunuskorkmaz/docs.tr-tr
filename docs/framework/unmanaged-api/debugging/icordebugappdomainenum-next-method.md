---
title: "ICorDebugAppDomainEnum::Next Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomainEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomainEnum::Next method
helpviewer_keywords:
- ICorDebugAppDomainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: b8d1def7-0ebc-4314-a3a2-fd36a75973e7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c5b773cf49ed67ce6d5981650f2409f7860391a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomainenumnext-method"></a>ICorDebugAppDomainEnum::Next Yöntemi
Uygulama etki alanları belirtilen sayıda geçerli İmleç konumuna başlangıç koleksiyondan alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `celt`  
 [in] Alınacak uygulama etki alanları sayısı.  
  
 `values`  
 [out] Her biri uygulama etki alanını temsil eden bir Icordebugappdomain nesneye işaret eden bir dizi işaretçisi.  
  
 `pceltFetched`  
 [out] Uygulama etki alanları gerçekte döndürülen sayısı için bir işaretçi. Bu değer null ise `celt` biridir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
