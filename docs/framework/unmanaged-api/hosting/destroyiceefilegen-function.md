---
title: "DestroyICeeFileGen İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: DestroyICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type: COM
f1_keywords: DestroyICeeFileGen
helpviewer_keywords: DestroyICeeFileGen function [.NET Framework hosting]
ms.assetid: dc1e2235-e721-4cb2-a0b8-6b0c030d7bab
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6c3e326aa71adc1bc9abe350cfc0528c88905cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="destroyiceefilegen-function"></a>DestroyICeeFileGen İşlevi
Bozar bir [Iceefilegen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) nesnesi.  
  
 Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ceeFileGen`  
 [in] `ICeeFileGen` Nesne yok.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem standart COM hata kodlarını döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 `DestroyICeeFileGen`bozar `ICeeFileGen` tarafından oluşturulan nesne [Createıceefilegen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) işlevi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** ICeeFileGen.h  
  
 **Kitaplığı:** MSCorPE.dll  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
