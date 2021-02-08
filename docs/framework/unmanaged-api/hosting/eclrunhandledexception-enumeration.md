---
description: 'Daha fazla bilgi edinin: EClrUnhandledException numaralandırması'
title: EClrUnhandledException Numaralandırması
ms.date: 03/30/2017
api_name:
- EClrUnhandledException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrUnhandledException
helpviewer_keywords:
- EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type:
- apiref
ms.openlocfilehash: 088d448a92c4d9030208537b9c788477c85f9d37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785555"
---
# <a name="eclrunhandledexception-enumeration"></a>EClrUnhandledException Numaralandırması

Kullanıcı kodunda işlenmemiş özel durumları yönetmeye yönelik kullanılabilir seçenekleri açıklar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|Varsayılan davranışın oluştuğunu belirtir. İşlem bozulmuş.|  
|`eHostDeterminedPolicy`|Ortak dil çalışma zamanının (CLR) işlenmemiş özel durumları yok saymadığını ve konağın başka bir eylem belirlemesine izin verir.|  
  
## <a name="remarks"></a>Açıklamalar  

 CLR 'nin önceki sürümler gibi davrandığını belirtmek için, üyesini kullanın `eHostDeterminedPolicy` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [EClrFailure Numaralandırması](eclrfailure-enumeration.md)
- [EClrOperation Numaralandırması](eclroperation-enumeration.md)
- [ICLRPolicyManager Arabirimi](iclrpolicymanager-interface.md)
- [SetUnhandledExceptionPolicy Yöntemi](iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [IHostPolicyManager Arabirimi](ihostpolicymanager-interface.md)
- [Barındırma Numaralandırmaları](hosting-enumerations.md)
