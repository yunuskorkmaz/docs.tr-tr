---
title: ICorConfiguration::SetGCThreadControl Yöntemi
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type:
- apiref
ms.openlocfilehash: 7874424150e0f4e1818ad9c72e31fd584e016829
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762402"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a>ICorConfiguration::SetGCThreadControl Yöntemi
Bir çöp toplama işlemi için engellenmeyen çalışma zamanı olmayan görevler için iş parçacıkları zamanlama için geri çağırma arabirimini ayarlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pGCThreadControl`  
 'ndaki Çalışma zamanı olmayan görevler için iş parçacıklarının askıya alınma hakkında bilgi veren bir [IGCThreadControl](igcthreadcontrol-interface.md) nesnesine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Konak, bir iş parçacığını yeniden zamanlamalı [IGCThreadControl:: Threadıblockingforaskıya](igcthreadcontrol-threadisblockingforsuspension-method.md) alma geri araması içinde seçim gösterebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorConfiguration Arabirimi](icorconfiguration-interface.md)
