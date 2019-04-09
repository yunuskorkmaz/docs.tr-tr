---
title: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed1d7ad95b7c8474121994d0f54557c1c36cb531
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095132"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Yöntemi
Önbelleğe alınmış için bir numaralandırıcı alır [!INCLUDE[wrt](../../../../includes/wrt-md.md)] temel alarak kendi arabirimi tanımlayıcılarını uygulama etki alanında tür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cReqTypes`  
 [in] Gerekli türleri sayısı.  
  
 `iidsToResolve`  
 [in] Yönetilen temsillerini karşılık gelen arabirimi tanımlayıcıları içeren bir dizi işaretçi [!INCLUDE[wrt](../../../../includes/wrt-md.md)] alınacak tür.  
  
 `ppTypesEnum`  
 [out] Önbelleğe alınan numaralandırmasına izin veren "ICorDebugTypeEnum" arabirimi nesnenin adresini bir işaretçiye yönetilen temsillerini [!INCLUDE[wrt](../../../../includes/wrt-md.md)] türleri alınan, arabirimi tanımlayıcılara göre `iidsToResolve`.  
  
## <a name="remarks"></a>Açıklamalar  
 Özel arabirim tanımlayıcısı için daha fazla bilgi almak yöntem başarısız olursa, ilgili girişi "ICorDebugTypeEnum" koleksiyonundaki bir türüne sahip `ELEMENT_TYPE_END` hataları veri alma sorunları nedeniyle veya `ELEMENT_TYPE_VOID` bilinmeyen arabirimi tanımlayıcıları.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugAppDomain3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
