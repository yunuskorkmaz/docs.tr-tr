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
ms.openlocfilehash: 4e549e13c0d51e4aa708a674a2224168ab66f8ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774536"
---
# <a name="nukedownloadedcache-function"></a>NukeDownloadedCache İşlevi
Ortak dil çalışma zamanı (CLR) indirme önbelleğini siler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, Wınerror içinde tanımlanan standart COM hata kodlarını döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 CLR indirme önbelleğini URL'den indirilen tanımlayıcı adlı derlemeler için olası yeniden depolandığı alanıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion.h  
  
 **Kitaplığı:** Fusion.dll ve kullanımda olan mscorwks.dll'ye. Fusion.dll yerine Mscorwks.dll doğru .NET Framework sürümünü hedefleyen emin olmak için kullanın.  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CreateHistoryReader İşlevi](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [GetHistoryFileDirectory İşlevi](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)
- [Fusion Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
