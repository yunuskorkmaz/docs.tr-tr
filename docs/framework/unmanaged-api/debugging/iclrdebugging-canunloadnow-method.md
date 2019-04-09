---
title: ICLRDebugging::CanUnloadNow Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDebugging.CanUnloadNow Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::CanUnloadNow
helpviewer_keywords:
- CanUnloadNow method [.NET Framework debugging]
- ICLRDebugging::CanUnloadNow method [.NET Framework debugging]
ms.assetid: 62e0630c-8cb7-45d2-b622-5a472abfd8cf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80559ef685a2dbf48d65e0d81432a5edbd5528bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072876"
---
# <a name="iclrdebuggingcanunloadnow-method"></a>ICLRDebugging::CanUnloadNow Yöntemi
Tarafından sağlanan bir kitaplığı olup olmadığını belirleyen bir [Iclrdebugginglibraryprovider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) arabirimi hala kullanımda olduğu veya kaldırılmış olabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a>Parametreler  
 `hmodule`  
 [in] Hedef işlemde bir modülün temel adres.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Tarafından başvurulan modül `hmodule` kaldırılmış olabilir.|  
|S_FALSE|Tarafından başvurulan modül `hmodule` hala kullanılıyor.|  
|COR_E_NOT_CLR|Belirtilen modül bir CLR modülünü değil.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem tüm olup olmadığını denetler örneklerini `ICorDebug*` arabirimi yayımladı ve iş parçacığı şu anda bir çağrı içinde [Iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
