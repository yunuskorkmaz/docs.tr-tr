---
title: "_CorExeMain İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: _CorExeMain
helpviewer_keywords: _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8c341d578a45d72804d9ac33e2aefe513fd33922
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corexemain-function"></a>_CorExeMain İşlevi
Ortak dil çalışma zamanı (CLR) başlatır, yürütülebilir derlemenin CLR üstbilgisinde yönetilen giriş noktasını bulur ve yürütmeye başlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev, Yönetilen yürütülebilir derlemelerden oluşturulan işlemlerde yükleyicisi tarafından çağrılır. DLL derlemeler için yükleyici çağırır [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) yerine işlev.  
  
 İşletim sistemi yükleyicisi görüntü dosyasında belirtilen giriş noktası bağımsız olarak bu yöntemi çağırır.  
  
 Windows 98, Windows ME, Windows NT ve Windows 2000'de, `_CorExeMain` işlevi çağrıldığında dolaylı olarak işletim sistemi yükleyicisi içinde düzeltme aracılığıyla. Tüm diğer Windows sürümlerinde doğrudan işletim sistemi yükleyicisi tarafından çağrılır.  
  
 Ek bilgi için açıklamalar bölümünde bakın [_corvalidateımage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) konu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta veri genel statik işlevleri](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
