---
title: NukeDownloadedCache İşlevi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0436991512713c05e60a3c10d6fbdaa17bb378c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429833"
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
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CreateHistoryReader İşlevi](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [GetHistoryFileDirectory İşlevi](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 [Fusion Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
