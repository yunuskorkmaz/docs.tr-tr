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
ms.openlocfilehash: 8f97614412eb2d49b202e86bdabc727159deb5d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131694"
---
# <a name="nukedownloadedcache-function"></a>NukeDownloadedCache İşlevi
Ortak dil çalışma zamanı (CLR) indirme önbelleğini siler.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
  
 **Kitaplık:** Fusion. dll ve mscorwks. dll. .NET Framework doğru sürümünü hedefliyorsanız emin olmak için mscorwks. dll yerine Fusion. dll kullanın.  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CreateHistoryReader İşlevi](createhistoryreader-function.md)
- [GetHistoryFileDirectory İşlevi](gethistoryfiledirectory-function.md)
- [Fusion Genel Statik İşlevleri](fusion-global-static-functions.md)
