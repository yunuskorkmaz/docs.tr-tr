---
description: 'Daha fazla bilgi edinin: CoEEShutDownCOM Işlevi'
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
ms.openlocfilehash: 4f1ac8107c9a121ebf52ef21a5f2c9006880914f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799869"
---
# <a name="coeeshutdowncom-function"></a>CoEEShutDownCOM İşlevi

Ortak dil çalışma zamanını (CLR) çalışma zamanı çağrılabilir sarmalayıcılar (RCW) içinde tuttuğu tüm arabirim işaretçilerini serbest bırakmaya zorlar. Bu, tüm RCW önbelleklerini serbest bırakma etkisine sahiptir. Bu genel işlev .NET Framework 4 ' te kullanım dışıdır. Bunun yerine, belirli bir çalışma zamanı için giriş noktasını kullanın.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>Açıklamalar  

 `CoEEShutDownCOM`İşlevi ilk olarak tüm bağlamlardaki ve tüm önbelleklerde tüm RCWs 'ları serbest bırakır ve ardından Kurulum 'da mevcut olan tüm koparma bildirimini kaldırır. DLL kaldırma gerçekleşmediğinde.  
  
> [!CAUTION]
> Bu işlev, işleme yüklenen tüm çalışma zamanlarını etkiler.  
  
 .NET Framework 4 ' ten başlayarak, etkilenmesini istediğiniz belirli çalışma zamanında bu işlevin giriş noktasını çağırın. Giriş noktasını almak için [ICLRRuntimeInfo:: GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) metodunu çağırın ve "CoEEShutDownCOM" belirtin.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Genel Statik İşlevleri](../metadata/metadata-global-static-functions.md)
