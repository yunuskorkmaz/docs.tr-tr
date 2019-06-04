---
title: CoEEShutDownCOM İşlevi
ms.date: 03/30/2017
api_name:
- CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoEEShutDownCOM
helpviewer_keywords:
- CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d2b82bc056acd2e620461081b5f8c9d45fc152c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490637"
---
# <a name="coeeshutdowncom-function"></a>CoEEShutDownCOM İşlevi
Ortak dil çalışma zamanı (CLR) çalışma zamanı aranabilir sarmalayıcılarını (RCW) içinde tutan tüm arabirim işaretçilerini yayımlamayı zorlar. Bu, tüm RCW önbellekleri bırakılıyor etkisi vardır. Bu genel işlev, .NET Framework 4'te kullanım dışıdır. Bunun yerine, belirli bir çalışma zamanı için giriş noktasını kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `CoEEShutDownCOM` İşlevi ilk tüm RCW tüm bağlamlarda ve tüm önbellekleri serbest bırakır ve sonra kurulumunda varolan herhangi bir kapatmayı bildirim kaldırır. Hiçbir DLL'i kaldırma gerçekleşir.  
  
> [!CAUTION]
>  Bu işlev, işlem içine yüklenmiş tüm çalışma zamanları etkiler.  
  
 .NET Framework 4 ile başlayarak, giriş noktası için değiştirmek istediğiniz belirli çalışma zamanı üzerinde bu işlevi çağırın. Giriş noktası almak için arama [Iclrruntimeınfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) yöntemi ve "CoEEShutDownCOM" belirtin.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
