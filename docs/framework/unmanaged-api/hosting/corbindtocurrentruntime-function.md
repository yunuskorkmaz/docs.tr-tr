---
title: CorBindToCurrentRuntime İşlevi
ms.date: 03/30/2017
api_name:
- CorBindToCurrentRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- HeaderDef
f1_keywords:
- CorBindToCurrentRuntime
helpviewer_keywords:
- CorBindToCurrentRuntime function [.NET Framework hosting]
ms.assetid: 6105c13e-d9cd-44d2-a95a-924e042830c7
topic_type:
- apiref
ms.openlocfilehash: 77a0a8f58c11673a1958d837b4c3a21a05754c94
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138326"
---
# <a name="corbindtocurrentruntime-function"></a>CorBindToCurrentRuntime İşlevi
Bir XML dosyasında depolanan sürüm bilgilerini kullanarak ortak dil çalışma zamanını (CLR) bir işleme yükler. XML dosyasının biçimi, standart uygulama yapılandırma dosyasından sonra modellenir. Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../../../docs/framework/configure-apps/file-schema/index.md).  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır. Bkz. [ortak dil çalışma zamanını bir Işleme yükleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pwszFileName`  
 'ndaki Yüklenecek CLR sürümünü belirten bir uygulama yapılandırma dosyasının adı. Dosya adı tam nitelikli değilse, çağrıyı yapan yürütülebilirle aynı dizinde olduğu varsayılır.  
  
 Yüklenecek çalışma zamanının sürümü, yapılandırma dosyasının [\<requiredRuntime >](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) öğesindeki sürüm özniteliğiyle açıklanır.  
  
 Sürüm belirtilmemişse veya `<requiredRuntime>` öğesi bulunamazsa, makinede yüklü olan CLR 'nin en son sürümü yüklenir.  
  
 `rclsid`  
 'ndaki [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) veya [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) arabirimini uygulayan coclass 'ın `CLSID`. Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.  
  
 `riid`  
 'ndaki İstediğiniz arabirimin `IID`. Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.  
  
 `ppv`  
 dışı Döndürülen arabirim işaretçisi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CorBindToRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
