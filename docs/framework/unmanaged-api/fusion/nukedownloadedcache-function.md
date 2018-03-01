---
title: "NukeDownloadedCache İşlevi"
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
- NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- NukeDownloadedCache
helpviewer_keywords:
- NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 31d7ba7d5f4a9268ea1e04a4c9f09cd17ebfd5bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="nukedownloadedcache-function"></a>NukeDownloadedCache İşlevi
Ortak dil çalışma zamanı (CLR) indirme önbelleğini siler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, Winerror.h'de içinde tanımlanan standart COM hata kodlarını döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 CLR yükleme önbelleği bir URL'den indirilen tanımlayıcı adlı derlemeler için olası yeniden depolandığı alanıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Fusion.h  
  
 **Kitaplığı:** Fusion.dll ve Mscorwks.dll. Fusion.dll Mscorwks.dll yerine .NET Framework'ün doğru sürümünü hedef emin olmak için kullanın.  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CreateHistoryReader İşlevi](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [GetHistoryFileDirectory İşlevi](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 [Fusion Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
