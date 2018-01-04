---
title: "CoInitializeEE İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoInitializeEE
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CoInitializeEE
helpviewer_keywords: CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ca564830411a9df0d47cc9765958286bbd40f96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="coinitializeee-function"></a>CoInitializeEE İşlevi
Ortak dil çalışma zamanı yürütme altyapısı bir işlemine yüklendi sağlar. Bu işlev de kullanım dışı [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Kullanım [Iclrruntimehost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) yöntemi yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `fFlags`  
 [in] Aşağıdakilerden birini [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) numaralandırma sabitleri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, Winerror.h'de ve değerleri aşağıdaki tabloda tanımlanan standart COM hata kodlarını döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yürütme altyapısı başarıyla yüklendi.|  
|S_FALSE|Yürütme altyapısı zaten yüklenmiş.|  
|E_FAIL|Yürütme alt yapısı yüklü değil.|  
  
## <a name="remarks"></a>Açıklamalar  
 Daha önce yüklü değilse bu yöntem yürütme altyapısı yükler.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
