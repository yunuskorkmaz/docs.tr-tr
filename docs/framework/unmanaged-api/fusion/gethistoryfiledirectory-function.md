---
title: "GetHistoryFileDirectory İşlevi"
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
- GetHistoryFileDirectory
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- GetHistoryFileDirectory
helpviewer_keywords:
- GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5d0ec18a4f95d0d280a66b3b9d9200c560f5f187
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="gethistoryfiledirectory-function"></a>GetHistoryFileDirectory İşlevi
Uygulama geçmişi dizinin yolunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `wzDir`  
 [out] Yol uygulama geçmiş dizinine tutmak için arabellek.  
  
 `pdwSize`  
 [içinde out] Arabellek uzunluğu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki değerleri yanı sıra Winerror.h'de dosyasında tanımlanan standart COM hata kodlarını döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_INVALIDARG|`wzDir`veya `pdwSize` null ya da sürüm dizesi yanlış.|  
  
## <a name="remarks"></a>Açıklamalar  
 Başarıyla tamamlandığında, `pdwSize` bağımsız değişkenini yolu dize uzunluğu ayarlayın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Fusion.h  
  
 **Kitaplığı:** Fusion.dll ve Mscorwks.dll. Fusion.dll Mscorwks.dll yerine .NET Framework'ün doğru sürümünü hedef emin olmak için kullanın.  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CreateHistoryReader İşlevi](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [NukeDownloadedCache İşlevi](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 [Fusion Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
