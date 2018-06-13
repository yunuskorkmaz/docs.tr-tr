---
title: IGCHost::Collect Yöntemi
ms.date: 03/30/2017
api_name:
- IGCHost.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Collect
helpviewer_keywords:
- Collect method, IGCHost interface [.NET Framework hosting]
- IGCHost::Collect method [.NET Framework hosting]
ms.assetid: fc7d9448-3186-494d-9f0d-ea39717e9a82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bce005a677dcb74c176a6dddfb2726f6b1fd0e8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436913"
---
# <a name="igchostcollect-method"></a>IGCHost::Collect Yöntemi
Geçerli çöp toplama durumu bağımsız olarak verilen oluşturma için gerçekleşmesi için bir koleksiyon zorlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `Generation`  
 [in] Çöp toplama gerçekleştirileceği oluşturma. -1 değeri, tüm nesli çöp toplama yapılacaktır gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** GCHost.idl, GCHost.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IGCHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
