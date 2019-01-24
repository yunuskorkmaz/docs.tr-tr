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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca33c8eb5e214cdaaa49905c311fd62042285d4f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569301"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a>ICorConfiguration::AddDebuggerSpecialThread Yöntemi
Hata Ayıklama Hizmetleri için hata ayıklayıcı durduruldu sırasında yönetilen veya yönetilmeyen hata ayıklama senaryoları uygulama varken yürütme devam etmek için belirli bir iş parçacığına izin verileceğini gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwSpecialThreadId`  
 [in] Yürütmeye devam izin verilmesi iş parçacığı kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 Belirtilen iş parçacığı herhangi bir şekilde çalışma zamanı girmek veya yönetilen kodu çalıştırmak için izin verilmiyor. Böyle bir iş parçacığı örneği, eski kod hata ayıklayıcıları desteklemek için bir işlemdeki iş parçacığı olacaktır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorConfiguration Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
