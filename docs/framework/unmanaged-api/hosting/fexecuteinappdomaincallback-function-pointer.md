---
title: FExecuteInAppDomainCallback İşlev İşaretçisi
ms.date: 03/30/2017
api_name:
- FExecuteInAppDomainCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FExecuteInAppDomainCallback
helpviewer_keywords:
- FExecuteInAppDomainCallback function pointer [.NET Framework hosting]
ms.assetid: 2709f18f-3eee-497f-bc33-3ab7a485599b
topic_type:
- apiref
ms.openlocfilehash: 8b9c6bb41b7438b9764ac2a8a7fc1677bc08557a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733691"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a>FExecuteInAppDomainCallback İşlev İşaretçisi

Yönetilen kodu yürütmek için ortak dil çalışma zamanı (CLR) tarafından çağrılan bir işleve işaret eder.  
  
 Bu işlev işaretçisi .NET Framework 4 ' te kullanım dışı bırakıldı.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `cookie`  
 'ndaki Yürütülebilecek yönetilen kodu içeren, bir veya daha fazla arayana ayrılan belleğe yönelik işaretçi.  
  
 Bu belleğin ayrılması ve ömrü, çağıran tarafından denetlenir (yani, CLR). Bu, CLR tarafından yönetilen yığın belleği değildir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorWks.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)
