---
title: CreateDebuggingInterfaceFromVersion İşlevi
ms.date: 03/30/2017
api_name:
- CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60d1c49e8762d00e3e154c598c2542c4a76b9b28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985718"
---
# <a name="createdebugginginterfacefromversion-function"></a>CreateDebuggingInterfaceFromVersion İşlevi
Oluşturur bir [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) nesne belirtilen sürüm bilgisi esas alarak.  
  
 Bu işlev kullanılmıyor [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Bunun yerine, Ortak Dil Çalışma Zamanı Modülü (CLR) 2.0 bir arabirimi almak için kullanın [Iclrruntimeınfo::getınterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) yöntemi CLSID_CLRDebuggingLegacy sınıf tanımlayıcısı ve arabirim tanımlayıcısı IID_ICorDebug belirtin. Bir arabirim için CLR 4 veya sonraki sürümlerde, çağrı [Clrcreateınstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) işlev ve sınıf tanımlayıcısı CLSID_CLRDebugging ve IID_ICLRDebugging arabirimi tanımlayıcısını belirtin.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `iDebuggerVersion`  
 [in] Sürümü `ICorDebug` hata ayıklayıcı tarafından bekleniyor. Bkz: [Cordebugınterfaceversion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) numaralandırma değerleri için.  
  
 `szDebuggeeVersion`  
 [in] Ayıklanacak uygulamayı veya işlemi ile ilişkili ortak dil çalışma zamanı sürümü. Bkz: [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) veya [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) bu değer alma hakkında bilgi için yöntemi.  
  
 `ppCordb`  
 [out] Bir işaretçiye alan konumu `ICorDebug` nesne.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki değerlere ek olarak Wınerror dosyasında tanımlanan standart COM hata kodlarını döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_INVALIDARG|`szDebuggeeVersion` veya `ppCordb` null ya da sürüm dizesi yanlış.|  
  
## <a name="remarks"></a>Açıklamalar  
 `szDebuggeeVersion` Parametre MSCorDbi.dll ilgili sürümü için eşler.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
