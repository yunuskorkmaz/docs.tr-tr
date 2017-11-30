---
title: "CoEEShutDownCOM İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CoEEShutDownCOM
helpviewer_keywords: CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8d6d9e3d650f65ef084c63104980bca0ac77f1bd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="coeeshutdowncom-function"></a>CoEEShutDownCOM İşlevi
Ortak dil çalışma zamanı (CLR) çalışma zamanı aranabilir sarmalayıcıları (RCW) içinde tutan tüm arabirim işaretçileri yayımlamayı zorlar. Bu, tüm RCW önbellekleri yayınlama etkisi yoktur. Bu genel işlevi de kullanım dışı [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Bunun yerine, giriş noktası için belirli bir çalışma zamanı kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `CoEEShutDownCOM` İşlevi önce tüm RCWs tüm bağlamları ve tüm önbellekleri serbest bırakır ve kurulumunda varolan herhangi bir kapatmayı aşağı bildirim kaldırır. Hiçbir DLL'i kaldırma oluşur.  
  
> [!CAUTION]
>  Bu işlev işlemi içinde yüklenen tüm çalışma zamanları etkiler.  
  
 İle başlayarak [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], giriş noktası üzerindeki etkiler istediğiniz belirli çalışma zamanı bu işlev çağrısı. Giriş noktası almak için arama [Iclrruntimeınfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) yöntemi ve "CoEEShutDownCOM" belirtin.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta veri genel statik işlevleri](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
