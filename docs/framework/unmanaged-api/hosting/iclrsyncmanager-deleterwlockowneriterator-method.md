---
description: ': ICLRSyncManager::D Eleterwlockownerıterator yöntemi hakkında daha fazla bilgi edinin'
title: ICLRSyncManager::DeleteRWLockOwnerIterator Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.DeleteRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator method [.NET Framework hosting]
- DeleteRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: fcfd340a-b7d6-44e4-8167-2c05b789d483
topic_type:
- apiref
ms.openlocfilehash: 7968f326f1ad92fe6e3a0f91749fb7e462e81c04
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789781"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a>ICLRSyncManager::DeleteRWLockOwnerIterator Yöntemi

Ortak dil çalışma zamanının (CLR) [ICLRSyncManager:: CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md)çağrısıyla oluşturulmuş bir yineleyiciyi yok ettiğini ister.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `Iterator`  
 'ndaki Çağrısı kullanılarak oluşturulan Yineleyici `CreateRWLockOwnerIterator` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`DeleteRWLockOwnerIterator` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  

 Ana bilgisayar bu yöntemi çağırabilir ve `CreateRWLockOwnerIterator` iş parçacığı uygulamasının eşitlenmiş kalmasını sağlamak için kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRSyncManager Arabirimi](iclrsyncmanager-interface.md)
- [IHostSyncManager Arabirimi](ihostsyncmanager-interface.md)
