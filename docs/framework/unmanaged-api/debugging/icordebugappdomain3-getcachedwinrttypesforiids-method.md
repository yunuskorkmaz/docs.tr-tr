---
title: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a7ce44dcfc709b4fea1952471cf31f5f07d4d0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Metodu
Önbelleğe alınan için bir numaralandırıcı alır [!INCLUDE[wrt](../../../../includes/wrt-md.md)] kendi arabirim tanımlayıcıları temel alarak bir uygulama etki alanındaki tür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cReqTypes`  
 [in] Gerekli türlerinin sayısı.  
  
 `iidsToResolve`  
 [in] Yönetilen gösterimlerini karşılık gelen arabirim tanımlayıcıları içeren bir dizi için bir işaretçi [!INCLUDE[wrt](../../../../includes/wrt-md.md)] alınacak türleri.  
  
 `ppTypesEnum`  
 [out] Önbelleğe alınan listesi izin veren bir "ICorDebugTypeEnum" arabirimi nesnesi adresini gösteren bir işaretçi yönetilen gösterimlerini [!INCLUDE[wrt](../../../../includes/wrt-md.md)] türleri alınan, arabirim tanımlayıcıları temel `iidsToResolve`.  
  
## <a name="remarks"></a>Açıklamalar  
 Belirli bir arabirim tanımlayıcısı bilgilerini almak yöntem başarısız olursa, karşılık gelen bir giriş "ICorDebugTypeEnum" koleksiyonundaki bir türüne sahip `ELEMENT_TYPE_END` veri alma sorunları nedeniyle hatalara veya `ELEMENT_TYPE_VOID` bilinmeyen arabirimi tanımlayıcıları.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugAppDomain3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
