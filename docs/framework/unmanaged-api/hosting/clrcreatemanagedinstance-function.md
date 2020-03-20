---
title: ClrCreateManagedInstance İşlevi
ms.date: 03/30/2017
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
ms.openlocfilehash: 7fbe0cf3e93d75749fa3f463f3f97dbd1bfe27a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176545"
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance İşlevi
Belirtilen yönetilen türbir örneği oluşturur.  
  
 Bu işlev .NET Framework 4'te amortismana hazırlanmıştır. Yönetilen türün bir örneğini oluşturmak veya barındırma kullanmak için COM etkinleştirme sini kullanın (bkz. [.NET Framework 4 ve 4.5'te eklenen CLR Barındırma Arabirimleri).](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,
    [in]  REFIID   riid,
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pTypeName`  
 [içinde] İstenilen örnek türü adına bir işaretçi.  
  
 `riid`  
 [içinde] `IID` İstenen örnek türü.  
  
 `ppObject`  
 [çıkış] Arayan tarafından istenen yönetilen tür örneğine işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma süresi zaten bir işleme yüklenmelidir. Örneğin, `ClrCreateManagedInstance` işlev çağrılmadan önce [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevine bir çağrı kullanılarak yüklenebilir. Çalışma süresi yüklenmezse, `ClrCreateManagedInstance` ilk olarak çalışma süresinin v1.0.3705'ini yüklemeye çalışır. Bu başarısız olursa, çalışma zamanının en son sürümünü yüklemeye çalışır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MSCorEE.h  
  
 **Kütüphane:** Mscoree.dll  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)
