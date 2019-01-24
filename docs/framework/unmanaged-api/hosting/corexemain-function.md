---
title: _CorExeMain İşlevi
ms.date: 03/30/2017
api_name:
- _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain
helpviewer_keywords:
- _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c6887d390ded1846e201711c9278663b9ff2888
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520285"
---
# <a name="corexemain-function"></a>_CorExeMain İşlevi
Ortak dil çalışma zamanı (CLR) başlatır, derlemesinin CLR başlığındaki yönetilen giriş noktasını bulur ve yürütmeyi başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev, yürütülebilir yönetilen derlemelerden oluşturan işlemlerde yükleyicisi tarafından çağrılır. DLL derlemeler için yükleyici çağırır [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) işlevini.  
  
 İşletim sistemi yükleyicisi görüntü dosyasında belirtilen giriş noktası bakılmaksızın bu yöntemi çağırır.  
  
 Windows 98, Windows ME, Windows NT, Windows 2000'de, `_CorExeMain` çağrıldığında dolaylı olarak işletim sistemi yükleyicisi'nde bir düzeltme aracılığıyla. Tüm diğer Windows sürümlerinde, doğrudan işletim sistemi yükleyicisi tarafından çağrılır.  
  
 Ek bilgi için bkz açıklamalar bölümünde [_corvalidateımage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) konu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Meta Veri Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
