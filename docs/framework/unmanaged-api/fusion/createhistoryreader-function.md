---
title: CreateHistoryReader İşlevi
ms.date: 03/30/2017
api_name:
- CreateHistoryReader
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateHistoryReader
helpviewer_keywords:
- CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e9c9866ee5ee3076d144dc732286ee008cd78c4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487267"
---
# <a name="createhistoryreader-function"></a>CreateHistoryReader İşlevi
Belirtilen dosya için geçmiş okuyucu oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a>Parametreler  
 `wzFilePath`  
 [in] Dosya yolu.  
  
 `ppHistoryReader`  
 [out] Başarıyla tamamlandığında, geçmiş Okuyucu için bir işaretçi içerir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki tabloda açıklanan değerlere ek olarak Wınerror içinde tanımlanan standart COM hata kodlarını döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntemi başarıyla tamamlandığını gösterir.|  
|E_INVALIDARG|Bildiren `wzFilePath` veya `ppHistoryReader` null bir başvuru ayarlayın.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Kitaplığı:** Fusion.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Fusion Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
