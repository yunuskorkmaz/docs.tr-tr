---
description: 'Daha fazla bilgi edinin: CorBindToCurrentRuntime Işlevi'
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
ms.openlocfilehash: 7dd2ab7febf4b1f87265a670a1af5d54b1e1102e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790119"
---
# <a name="corbindtocurrentruntime-function"></a>CorBindToCurrentRuntime İşlevi

Bir XML dosyasında depolanan sürüm bilgilerini kullanarak ortak dil çalışma zamanını (CLR) bir işleme yükler. XML dosyasının biçimi, standart uygulama yapılandırma dosyasından sonra modellenir. Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../configure-apps/file-schema/index.md).  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır. Bkz. [ortak dil çalışma zamanını bir Işleme yükleme](/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).  
  
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
  
 Yüklenecek çalışma zamanının sürümü, [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) yapılandırma dosyasının öğesindeki sürüm özniteliğiyle açıklanmıştır.  
  
 Sürüm belirtilmemişse veya `<requiredRuntime>` öğe bulunamazsa, makinede yüklü olan CLR 'nin en son sürümü yüklenir.  
  
 `rclsid`  
 'ndaki `CLSID` [ICorRuntimeHost](icorruntimehost-interface.md) veya [ICLRRuntimeHost](iclrruntimehost-interface.md) arabirimini uygulayan coclass. Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.  
  
 `riid`  
 'ndaki `IID` İstediğiniz arabirim. Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.  
  
 `ppv`  
 dışı Döndürülen arabirim işaretçisi.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CorBindToRuntime İşlevi](corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg İşlevi](corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx İşlevi](corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost İşlevi](corbindtoruntimehost-function.md)
- [ICorRuntimeHost Arabirimi](icorruntimehost-interface.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)
