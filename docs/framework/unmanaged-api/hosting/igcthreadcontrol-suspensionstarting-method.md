---
title: "IGCThreadControl::SuspensionStarting Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCThreadControl.SuspensionStarting
api_location: mscoree.dll
api_type: COM
f1_keywords: SuspensionStarting
helpviewer_keywords:
- IGCThreadControl::SuspensionStarting method [.NET Framework hosting]
- SuspensionStarting method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 0af312af-98e9-415e-b182-42e80a1aee51
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9d5f403c2880d0079a89c6de5c2ad9aa4f8d9fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a>IGCThreadControl::SuspensionStarting Yöntemi
Ana bilgisayar, çalışma zamanı modülü çöp toplama için bir iş parçacığı askıya alınması veya diğer askıya başlıyor bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Tüm iş parçacıklarının sırasında yeniden zamanla değil `SuspensionStarting` geri çağırma.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Igcthreadcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
