---
title: CorBindToRuntimeByCfg İşlevi
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeByCfg
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeByCfg
helpviewer_keywords:
- CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type:
- apiref
ms.openlocfilehash: 8b7dcdcc6d9d0106af1bb83ee591cff76239b416
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504462"
---
# <a name="corbindtoruntimebycfg-function"></a>CorBindToRuntimeByCfg İşlevi
Bir XML dosyasından okunan sürüm bilgilerini kullanarak ortak dil çalışma zamanını (CLR) bir işleme yükler.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,
    [out] LPVOID FAR*  ppv  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pCfgStream`  
 'ndaki `IStream`XML dosyasını okuyan bir nesne işaretçisi.  
  
 `reserved`  
 'ndaki Gelecekte kullanılmak üzere ayrılmıştır. Değer olarak 0 (sıfır) kullanın.  
  
 `startupFlags`  
 'ndaki CLR 'nin başlangıç davranışını belirten [startup_flags](startup-flags-enumeration.md) numaralandırması değeri.  
  
 `rclsid`  
 'ndaki `CLSID` [ICorRuntimeHost](icorruntimehost-interface.md) veya [ICLRRuntimeHost](iclrruntimehost-interface.md) arabirimini uygulayan coclass. Desteklenen değerler CLSID_CorRuntimeHost veya CLSID_CLRRuntimeHost.  
  
 `riid`  
 'ndaki `IID` `ICorRuntimeHost` Ya da `ICLRRuntimeHost` arabirimi. Desteklenen değerler IID_ICorRuntimeHost veya IID_ICLRRuntimeHost.  
  
 `ppv`  
 dışı Döndürülen arabirimin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 XML dosyasının biçimi, standart uygulama yapılandırma dosyasından sonra modellenir. XML dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosya şeması](../../configure-apps/file-schema/index.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CorBindToCurrentRuntime İşlevi](corbindtocurrentruntime-function.md)
- [CorBindToRuntime İşlevi](corbindtoruntime-function.md)
- [CorBindToRuntimeEx İşlevi](corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost İşlevi](corbindtoruntimehost-function.md)
- [ICorRuntimeHost Arabirimi](icorruntimehost-interface.md)
- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)
