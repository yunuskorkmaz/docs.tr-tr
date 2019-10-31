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
ms.openlocfilehash: 4e85a9a98bf0550fa906f8b905c73890948f4ac1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124937"
---
# <a name="coeeshutdowncom-function"></a>CoEEShutDownCOM İşlevi
Ortak dil çalışma zamanını (CLR) çalışma zamanı çağrılabilir sarmalayıcılar (RCW) içinde tuttuğu tüm arabirim işaretçilerini serbest bırakmaya zorlar. Bu, tüm RCW önbelleklerini serbest bırakma etkisine sahiptir. Bu genel işlev .NET Framework 4 ' te kullanım dışıdır. Bunun yerine, belirli bir çalışma zamanı için giriş noktasını kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `CoEEShutDownCOM` işlevi ilk olarak tüm bağlamlardaki ve tüm önbelleklerde tüm RCWs 'ları serbest bırakır ve ardından Kurulum 'da bulunan tüm koparmalar kaldırır. DLL kaldırma gerçekleşmediğinde.  
  
> [!CAUTION]
> Bu işlev, işleme yüklenen tüm çalışma zamanlarını etkiler.  
  
 .NET Framework 4 ' ten başlayarak, etkilenmesini istediğiniz belirli çalışma zamanında bu işlevin giriş noktasını çağırın. Giriş noktasını almak için [ICLRRuntimeInfo:: GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) metodunu çağırın ve "CoEEShutDownCOM" belirtin.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
