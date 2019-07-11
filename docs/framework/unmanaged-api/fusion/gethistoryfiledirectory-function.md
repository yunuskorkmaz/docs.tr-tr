---
title: GetHistoryFileDirectory İşlevi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10eead2772a2bbd8abaf7b9c090a091687725972
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778659"
---
# <a name="gethistoryfiledirectory-function"></a>GetHistoryFileDirectory İşlevi
Uygulama geçmişi dizininin yolunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `wzDir`  
 [out] Yol uygulama geçmiş dizinine tutan bir arabellek.  
  
 `pdwSize`  
 [out içinde] Arabellek uzunluğu.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki değerlere ek olarak Wınerror dosyasında tanımlanan standart COM hata kodlarını döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_INVALIDARG|`wzDir` veya `pdwSize` null ya da sürüm dizesi yanlış.|  
  
## <a name="remarks"></a>Açıklamalar  
 Başarıyla tamamlandığında, `pdwSize` bağımsız değişkeni yol dizesini uzunluğunu ayarlayın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion.h  
  
 **Kitaplığı:** Fusion.dll ve kullanımda olan mscorwks.dll'ye. Fusion.dll yerine Mscorwks.dll doğru .NET Framework sürümünü hedefleyen emin olmak için kullanın.  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CreateHistoryReader İşlevi](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [NukeDownloadedCache İşlevi](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)
- [Fusion Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
