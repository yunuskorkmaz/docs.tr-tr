---
title: ICLRRuntimeInfo::IsStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsStarted
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
ms.openlocfilehash: 85a7adddf395e07297c8fb6ceab4aa81e0aaf012
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762207"
---
# <a name="iclrruntimeinfoisstarted-method"></a>ICLRRuntimeInfo::IsStarted Yöntemi
Çalışma zamanının başlatıldığını (yani, [ICLRRuntimeHost:: Start yönteminin](iclrruntimehost-start-method.md) çağrıldığından ve başarılı olup olmadığını) gösterir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pbStarted`  
 [out] `true` Bu çalışma zamanı başlatılmışsa; Aksi takdirde, `false` .  
  
 `pdwStartupFlags`  
 dışı Çalışma zamanını başlatmak için kullanılan bayrakları döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_NOTIMPL|Ortak dil çalışma zamanı (CLR) sürümü .NET Framework 4 ' teki CLR sürümünden daha eski.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, .NET Framework 4 ' teki CLR sürümünden önceki CLR sürümleriyle çalışmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRRuntimeInfo Arabirimi](iclrruntimeinfo-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
- [Barındırma](index.md)
