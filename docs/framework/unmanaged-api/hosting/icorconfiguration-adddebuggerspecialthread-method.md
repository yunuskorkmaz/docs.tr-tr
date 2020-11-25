---
title: ICorConfiguration::AddDebuggerSpecialThread Yöntemi
ms.date: 03/30/2017
api_name:
- ICorConfiguration.AddDebuggerSpecialThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AddDebuggerSpecialThread
helpviewer_keywords:
- AddDebuggerSpecialThread method [.NET Framework hosting]
- ICorConfiguration::AddDebuggerSpecialThread method [.NET Framework hosting]
ms.assetid: 1f1e3239-438e-4be9-a3bb-7d0722d3a76d
topic_type:
- apiref
ms.openlocfilehash: bd89db3fa0b1814a98b016fcf9d1aeeabfff718b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715855"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a>ICorConfiguration::AddDebuggerSpecialThread Yöntemi

Hata ayıklayıcı yönetilen veya yönetilmeyen hata ayıklama senaryolarında durdurulan bir uygulamaya sahip olsa da, belirli bir iş parçacığının yürütmeye devam etmesine izin verilmesi gerektiğini hata ayıklama hizmetlerine bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `dwSpecialThreadId`  
 'ndaki Yürütülmeye devam etmesi için izin verilmesi gereken iş parçacığının KIMLIĞI.  
  
## <a name="remarks"></a>Açıklamalar  

 Belirtilen iş parçacığının yönetilen kodu çalıştırmasına izin verilmez veya çalışma zamanını herhangi bir şekilde giremeyecektir. Bu tür bir iş parçacığına bir örnek, eski betik hata ayıklayıcılarını desteklemek için işlem içi bir iş parçacığı olacaktır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorConfiguration Arabirimi](icorconfiguration-interface.md)
