---
description: ': ICorConfiguration:: AddDebuggerSpecialThread yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b6904c2e4d5c265244ac096e0d64c2fc7f5d1be5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636721"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a>ICorConfiguration::AddDebuggerSpecialThread Yöntemi

Hata ayıklayıcı yönetilen veya yönetilmeyen hata ayıklama senaryolarında durdurulan bir uygulamaya sahip olsa da, belirli bir iş parçacığının yürütmeye devam etmesine izin verilmesi gerektiğini hata ayıklama hizmetlerine bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
