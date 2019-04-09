---
title: ICorDebugThread4::HadUnhandledException Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12433786f353212c1ffbd57e9bf526c3ecc60e9a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163637"
---
# <a name="icordebugthread4hadunhandledexception-method"></a>ICorDebugThread4::HadUnhandledException Yöntemi
İş parçacığı işlenmeyen bir özel durum sahipti olup olmadığını gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppBlockingObjectEnum`  
 [out] Sıralı sabit listesi adresini bir işaretçiye [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapıları.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|İş parçacığı oluşturulmasından bu yana işlenmeyen bir özel durum oluşturdu.|  
|S_FALSE|İş parçacığı, hiçbir zaman işlenmeyen bir özel durum oluşturdu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, iş parçacığı işlenmeyen bir özel durum sahipti olup olmadığını gösterir. İşlenmeyen özel durum geri çağırma saatle tetiklenen veya yerel JIT-ekleme başlatıldığında, bu yöntem S_OK dönmesi garanti edilir. Garanti yoktur, [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) yöntemi işlenmeyen bir özel durum döndürür; ancak işlem henüz işlenmemiş özel durum geri alma veya üzerine devam ettirildi değil durumunda olur Yerel JIT-ekleme. Ayrıca, birden fazla iş parçacığı yerel JIT-ekleme tetiklenir zaman işlenmeyen bir özel durum ile sağlamak için (olasılığı karşın) mümkündür. Böyle bir durumda, JIT-ekleme hangi özel durum harekete belirlemek için hiçbir yolu yoktur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugThread4 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
