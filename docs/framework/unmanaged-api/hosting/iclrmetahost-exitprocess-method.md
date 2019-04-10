---
title: ICLRMetaHost::ExitProcess Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.ExitProcess
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64c212d064ad658678926690d1e680afe27c7c99
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219245"
---
# <a name="iclrmetahostexitprocess-method"></a>ICLRMetaHost::ExitProcess Yöntemi
Yüklenen tüm çalışma zamanları düzgün biçimde kapatılamadı dener ve sonra da işlemi sonlandırır. Yerine geçen [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) işlevi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a>Parametreler  
 `iExitCode`  
 [in] İşlem çıkış kodu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Dönüş değeri tanımlanmamış, bu nedenle bu yöntem hiçbir zaman, döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRMetaHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
