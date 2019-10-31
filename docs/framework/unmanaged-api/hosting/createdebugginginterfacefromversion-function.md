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
ms.openlocfilehash: e23dfb86c2129a02a0ca95de8c89d8294e97ad81
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136843"
---
# <a name="createdebugginginterfacefromversion-function"></a>CreateDebuggingInterfaceFromVersion İşlevi
Belirtilen sürüm bilgilerini temel alan bir [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) nesnesi oluşturur.  
  
 Bu işlev .NET Framework 4 ' te kullanılmıyor. Bunun yerine, ortak dil çalışma zamanı (CLR) 2,0 için bir arabirim almak üzere [ICLRRuntimeInfo:: GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) metodunu kullanın ve CLSID_CLRDebuggingLegacy sınıf tanımlayıcısını ve IID_ICorDebug arabirim tanımlayıcısını belirtin. CLR 4 veya üzeri bir arabirim almak için, [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) işlevini çağırın ve sınıf tanımlayıcısı CLSID_CLRDebugging ve arabirim tanımlayıcısı IID_ICLRDebugging belirtin.  
  
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
 'ndaki Hata ayıklayıcı tarafından beklenen `ICorDebug` sürümü. Geçerli değerler için [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) numaralandırması bölümüne bakın.  
  
 `szDebuggeeVersion`  
 'ndaki Hata Ayıklanacak uygulamayla veya işlemle ilişkili ortak dil çalışma zamanı sürümü. Bu değeri alma hakkında bilgi için bkz. [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) veya [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) yöntemi.  
  
 `ppCordb`  
 dışı `ICorDebug` nesnesine bir işaretçi alan konum.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki değerlere ek olarak WinError. h dosyasında tanımlanan standart COM hata kodlarını döndürür.  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_INVALIDARG|`szDebuggeeVersion` veya `ppCordb` null ya da sürüm dizesi yanlış.|  
  
## <a name="remarks"></a>Açıklamalar  
 `szDebuggeeVersion` parametresi, MSCorDbi. dll ' nin ilgili sürümüyle eşlenir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
