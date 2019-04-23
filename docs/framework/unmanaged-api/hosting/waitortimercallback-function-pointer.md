---
title: WAITORTIMERCALLBACK İşlev İşaretçisi
ms.date: 03/30/2017
api_name:
- WAITORTIMERCALLBACK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAITORTIMERCALLBACK
helpviewer_keywords:
- WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8cf12fc6828c5e439a6a86532f22b8a598a9f03
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120997"
---
# <a name="waitortimercallback-function-pointer"></a>WAITORTIMERCALLBACK İşlev İşaretçisi
Bekleme işleyen ana bildiren bir işleve işaret eder (<xref:System.Threading.WaitHandle>) sinyal veya zaman aşımına uğradı.  
  
 Bu işlev işaretçisi içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `lpParameter`  
 [in] Ana bilgisayar tarafından tanımlanan bilgileri içeren bir nesne için bir işaretçi.  
  
 `TimerOrWaitFired`  
 [in] `true` bekleme tanıtıcısı zaman aşımına uğradı, varsa veya `false` , sinyal değilse.  
  
## <a name="remarks"></a>Açıklamalar  
 İşleve `WAITORTIMERCALLBACK` noktaları bir geri çağırma işlevidir ve uygulamanın barındırma yazıcı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorWks.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
