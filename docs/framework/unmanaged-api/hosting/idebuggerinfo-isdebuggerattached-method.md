---
title: IDebuggerInfo::IsDebuggerAttached Yöntemi
ms.date: 03/30/2017
api_name:
- IDebuggerInfo.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IsDebuggerAttached
helpviewer_keywords:
- IDebuggerInfo::IsDebuggerAttached method [.NET Framework hosting]
- IsDebuggerAttached method, IDebuggerInfo interface [.NET Framework hosting]
ms.assetid: 6e21872f-602f-411a-a423-bff5cdf27000
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91acfa5545f3115c9e95207f05708ff32530994f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437287"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a>IDebuggerInfo::IsDebuggerAttached Yöntemi
Bu işlem için yönetilen bir hata ayıklayıcısı ekli olup olmadığını belirten bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbAttached`  
 [out] Bir değer için bir işaretçi `true` yönetilen bir hata ayıklayıcısı ekli işlemine; Aksi takdirde ise `false`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebuggerInfo Arabirimi](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)
