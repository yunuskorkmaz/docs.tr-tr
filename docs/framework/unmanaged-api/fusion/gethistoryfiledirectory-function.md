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
ms.openlocfilehash: 484adf288356b9955fe0cac0bb30002ec1f012d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724444"
---
# <a name="gethistoryfiledirectory-function"></a>GetHistoryFileDirectory İşlevi

Uygulama geçmişi dizininin yolunu alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `wzDir`  
 dışı Uygulama geçmişi dizininin yolunu tutan bir arabellek.  
  
 `pdwSize`  
 [in, out] Arabelleğin uzunluğu.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki değerlere ek olarak WinError. h dosyasında tanımlanan standart COM hata kodlarını döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_INVALIDARG|`wzDir` ya `pdwSize` da null ya da sürüm dizesi yanlış.|  
  
## <a name="remarks"></a>Açıklamalar  

 Başarıyla tamamlandığında `pdwSize` bağımsız değişkeni yol dizesinin uzunluğuna ayarlanır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **Kitaplık:** Fusion.dll ve Mscorwks.dll. Doğru .NET Framework sürümünü hedefliyorsanız emin olmak için Mscorwks.dll yerine Fusion.dll kullanın.  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CreateHistoryReader İşlevi](createhistoryreader-function.md)
- [NukeDownloadedCache İşlevi](nukedownloadedcache-function.md)
- [Fusion Genel Statik İşlevleri](fusion-global-static-functions.md)
