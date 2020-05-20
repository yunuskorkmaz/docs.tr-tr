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
ms.openlocfilehash: 935ac478fb966315e81fdcc004761038b28e3178
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616600"
---
# <a name="_corexemain-function"></a>_CorExeMain İşlevi
Ortak dil çalışma zamanını (CLR) başlatır, çalıştırılabilir derlemenin CLR üstbilgisindeki yönetilen giriş noktasını bulur ve yürütmeyi başlatır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev, yönetilen yürütülebilir derlemelerden oluşturulan süreçlerdeki yükleyici tarafından çağırılır. DLL derlemeleri için yükleyici bunun yerine [_CorDllMain](cordllmain-function.md) işlevini çağırır.  
  
 İşletim sistemi yükleyicisi, görüntü dosyasında belirtilen giriş noktası ne olursa olsun bu yöntemi çağırır.  
  
 Windows 98, Windows ME, Windows NT ve Windows 2000 ' de, `_CorExeMain` işlev, işletim sistemi yükleyicisinde bir düzeltme aracılığıyla dolaylı olarak çağrılır. Tüm Windows sürümlerinde, işletim sistemi yükleyicisi tarafından doğrudan çağırılır.  
  
 Daha fazla bilgi için, [_CorValidateImage](corvalidateimage-function.md) konusunun açıklamalar bölümüne bakın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Genel Statik İşlevleri](../metadata/metadata-global-static-functions.md)
