---
description: 'Daha fazla bilgi edinin: CreateDebuggingInterfaceFromVersion Işlevi'
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
ms.openlocfilehash: 163ada49f028071b48c93ee3c565152a773782ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760639"
---
# <a name="createdebugginginterfacefromversion-function"></a>CreateDebuggingInterfaceFromVersion İşlevi

Belirtilen sürüm bilgilerini temel alan bir [ICorDebug](../debugging/icordebug-interface.md) nesnesi oluşturur.  
  
 Bu işlev .NET Framework 4 ' te kullanılmıyor. Bunun yerine, ortak dil çalışma zamanı (CLR) 2,0 için bir arabirim almak üzere [ICLRRuntimeInfo:: GetInterface](iclrruntimeinfo-getinterface-method.md) yöntemini kullanın ve sınıf tanımlayıcısını CLSID_CLRDebuggingLegacy ve arabirim tanımlayıcısını IID_ICorDebug belirtin. CLR 4 veya üzeri bir arabirim almak için, [CLRCreateInstance](clrcreateinstance-function.md) işlevini çağırın ve sınıf tanımlayıcısını CLSID_CLRDebugging ve arabirim tanımlayıcısı IID_ICLRDebugging belirtin.  
  
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
 'ndaki `ICorDebug` Hata ayıklayıcı tarafından beklenen sürümü. Geçerli değerler için [CorDebugInterfaceVersion](../debugging/cordebuginterfaceversion-enumeration.md) numaralandırması bölümüne bakın.  
  
 `szDebuggeeVersion`  
 'ndaki Hata Ayıklanacak uygulamayla veya işlemle ilişkili ortak dil çalışma zamanı sürümü. Bu değeri alma hakkında bilgi için bkz. [GetVersionFromProcess](getversionfromprocess-function.md) veya [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) yöntemi.  
  
 `ppCordb`  
 dışı Nesneye bir işaretçi alan konum `ICorDebug` .  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki değerlere ek olarak WinError. h dosyasında tanımlanan standart COM hata kodlarını döndürür.  
  
|Dönüş kodu|Description|  
|-----------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_INVALIDARG|`szDebuggeeVersion` ya `ppCordb` da null ya da sürüm dizesi yanlış.|  
  
## <a name="remarks"></a>Açıklamalar  

 `szDebuggeeVersion`Parametresi karşılık gelen MSCorDbi.dll sürümüne eşlenir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)
