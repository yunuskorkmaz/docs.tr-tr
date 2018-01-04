---
title: "ICorPublishAppDomainEnum::Next Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishAppDomainEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishAppDomainEnum::Next
helpviewer_keywords:
- Next method, ICorPublishAppDomainEnum interface [.NET Framework debugging]
- ICorPublishAppDomainEnum::Next method [.NET Framework debugging]
ms.assetid: ad37cd10-0339-4d08-9b0e-4b3428bb4dc3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c9823c0e4a471a398285c5960f3ce7bfc60fb23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishappdomainenumnext-method"></a>ICorPublishAppDomainEnum::Next Yöntemi
Geçerli konumdan başlayarak işleminde, şu anda mevcut uygulama etki alanları belirtilen sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `celt`  
 [in] Alınacak öğe sayısı.  
  
 `objects`  
 [out] Dizi için bir işaretçi alınan [Icorpublishappdomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) nesneleri, her biri uygulama etki alanını temsil eder.  
  
 `pceltFetched`  
 [out] Uygulama etki alanları sayısı işaretçisine gerçekte döndürdü. Bu değer null ise `celt` biridir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorPub.idl, CorPub.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorPublishAppDomainEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)
