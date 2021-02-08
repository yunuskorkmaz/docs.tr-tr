---
description: 'Daha fazla bilgi edinin: NukeDownloadedCache Işlevi'
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
ms.openlocfilehash: 2239473b8e6e43a539b0507c8255d40f87e72043
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800038"
---
# <a name="nukedownloadedcache-function"></a>NukeDownloadedCache İşlevi

Ortak dil çalışma zamanı (CLR) indirme önbelleğini siler.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, WinError. h içinde tanımlanan standart COM hata kodlarını döndürür.  
  
## <a name="remarks"></a>Açıklamalar  

 CLR indirme önbelleği, bir URL 'den indirilen tanımlayıcı adlı derlemelerin olası yeniden kullanım için depolandığı alandır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **Kitaplık:** Fusion.dll ve Mscorwks.dll. Doğru .NET Framework sürümünü hedefliyorsanız emin olmak için Mscorwks.dll yerine Fusion.dll kullanın.  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CreateHistoryReader İşlevi](createhistoryreader-function.md)
- [GetHistoryFileDirectory İşlevi](gethistoryfiledirectory-function.md)
- [Fusion Genel Statik İşlevleri](fusion-global-static-functions.md)
