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
ms.openlocfilehash: e1455ce7c3b07809d1dead8e98019c991475eb02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442153"
---
# <a name="waitortimercallback-function-pointer"></a>WAITORTIMERCALLBACK İşlev İşaretçisi
İşaret bekleme işlemek konak bildiren bir işlev (<xref:System.Threading.WaitHandle>) işaret ya da zaman aşımına uğradı.  
  
 Bu işlev işaretçisi kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `lpParameter`  
 [in] Ana bilgisayar tarafından tanımlanan bilgileri içeren bir nesne için bir işaretçi.  
  
 `TimerOrWaitFired`  
 [in] `true` bekleme tanıtıcısı zaman aşımına uğradı, varsa veya `false` işaret durumunda.  
  
## <a name="remarks"></a>Açıklamalar  
 İşleve `WAITORTIMERCALLBACK` noktaları bir geri çağırma işlevidir ve barındırma uygulama yazıcı tarafından uygulanmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorWks.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
