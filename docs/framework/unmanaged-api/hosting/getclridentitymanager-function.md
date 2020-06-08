---
title: GetCLRIdentityManager İşlevi
ms.date: 03/30/2017
api_name:
- GetCLRIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetCLRIdentityManager
helpviewer_keywords:
- GetCLRIdentityManager function [.NET Framework hosting]
ms.assetid: 66eeca30-adb4-45f4-aff5-347564c95724
topic_type:
- apiref
ms.openlocfilehash: 8b1e918edf641d38dd6b91d790bcaff8020293a0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493272"
---
# <a name="getclridentitymanager-function"></a>GetCLRIdentityManager İşlevi
Ortak dil çalışma zamanının (CLR) kimlikleri yönetmesine izin veren bir arabirime yönelik bir işaretçi alır.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `riid`  
 'ndaki `REFIID`Hangi arabirimin alınacağını belirten bir (bir arabirim tanımlayıcısı). Bu değer IID_ICLRAssemblyIdentityManager ya da IID_ICLRHostBindingPolicyManager olmalıdır.  
  
 `ppManager`  
 dışı Bir [ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md) veya [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 İşleve bir işaretçi almak için [GetRealProcAddress](getrealprocaddress-function.md) işlevini çağırın `GetCLRIdentityManager` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorWks. dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)
