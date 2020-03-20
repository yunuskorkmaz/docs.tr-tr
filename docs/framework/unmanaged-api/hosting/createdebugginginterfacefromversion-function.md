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
ms.openlocfilehash: adc8ea16f0ab2bf383f8a63c49ba7d61c6bac113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176454"
---
# <a name="createdebugginginterfacefromversion-function"></a>CreateDebuggingInterfaceFromVersion İşlevi
Belirtilen sürüm bilgilerini temel alan bir [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) nesnesi oluşturur.  
  
 Bu işlev .NET Framework 4'te geçersizdir. Bunun yerine, ortak dil çalışma süresi (CLR) 2.0 için bir arayüz elde etmek [için, ICLRRuntimeInfo kullanın::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) yöntemi ve sınıf tanımlayıcıCLSID_CLRDebuggingLegacy ve arayüz tanımlayıcıIID_ICorDebug belirtin. CLR 4 veya sonraki bir arabirim almak için [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) işlevini arayın ve sınıf tanımlayıcısını CLSID_CLRDebugging ve arayüz tanımlayıcısını IID_ICLRDebugging belirtin.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,
    [in]  LPCWSTR  szDebuggeeVersion,
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `iDebuggerVersion`  
 [içinde] Bunun sürümü `ICorDebug` hata ayıklayıcı tarafından bekleniyor. Geçerli değerler için [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) numaralandırmabölümüne bakın.  
  
 `szDebuggeeVersion`  
 [içinde] Hata ayıklanacak uygulama veya işlemle ilişkili ortak dil çalışma zamanı sürümü. Bu değeri alma hakkında bilgi almak için [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) veya [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) yöntemine bakın.  
  
 `ppCordb`  
 [çıkış] `ICorDebug` Nesneye işaretçi alan konum.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki değerlere ek olarak WinError.h dosyasında tanımlandığı gibi standart COM hata kodlarını döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_ınvalıdarg|`szDebuggeeVersion`veya `ppCordb` null veya sürüm dizesi yanlıştır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `szDebuggeeVersion` Parametre, MSCorDbi.dll'nin ilgili sürümüyle eşler.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MSCorEE.h  
  
 **Kütüphane:** Mscoree.dll  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
