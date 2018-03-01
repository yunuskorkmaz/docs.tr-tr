---
title: "ICorDebugThread4::HadUnhandledException Yöntemi"
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
- ICorDebugThread4.HadUnhandledException Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a79d06f0a65facfbaa821d3dd6af547fd3d0305
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread4hadunhandledexception-method"></a>ICorDebugThread4::HadUnhandledException Yöntemi
İş parçacığı işlenmeyen bir özel durum şimdiye kadar süredir sahip olup olmadığını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppBlockingObjectEnum`  
 [out] Sıralanmış numaralandırması adresini gösteren bir işaretçi [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapıları.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|İş parçacığı oluşturulmasından bu yana işlenmeyen bir özel durum oluşturdu.|  
|S_FALSE|İş parçacığı hiçbir zaman işlenmeyen bir özel durum oluşturdu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem iş parçacığı işlenmeyen bir özel durum şimdiye kadar süredir sahip olup olmadığını belirtir. İşlenmeyen özel durum geri çağırma saatle tetiklenen veya yerel JIT-ekleme başlatıldığında, bu yöntem S_OK döndürmek için sağlanır. Garantisi yoktur, [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) yöntemi işlenmeyen bir özel durum döndürür; ancak işlem henüz işlenmeyen bir özel durum geri alma sonra veya sonra devam ettirildi değil, olur Yerel JIT-ekleme. Ayrıca, birden çok iş parçacığı işlenmeyen bir özel durum yerel JIT-ekleme tetiklenir zaman ile sağlamak için (olası rağmen) mümkündür. Böyle bir durumda JIT-ekleme hangi özel durum tetikledi belirlemenin bir yolu yoktur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugThread4 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
