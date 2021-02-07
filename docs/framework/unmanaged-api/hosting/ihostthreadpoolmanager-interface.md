---
description: 'Daha fazla bilgi edinin: IHostThreadPoolManager Arabirimi'
title: IHostThreadPoolManager Arabirimi
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager
helpviewer_keywords:
- IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type:
- apiref
ms.openlocfilehash: 0361b7a08f781a8748e43959f65ce0e9f21bbac1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728431"
---
# <a name="ihostthreadpoolmanager-interface"></a>IHostThreadPoolManager Arabirimi

Ortak dil çalışma zamanını (CLR) iş parçacığı havuzunu yapılandırmak ve iş öğelerini iş parçacığı havuzuna sıraya almak için etkinleştiren yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetAvailableThreads Yöntemi](ihostthreadpoolmanager-getavailablethreads-method.md)|İş öğelerini işlemeyen iş parçacığı havuzundaki iş parçacığı sayısını alır.|  
|[GetMaxThreads Yöntemi](ihostthreadpoolmanager-getmaxthreads-method.md)|Konağın iş parçacığı havuzunda eşzamanlı olarak tuttuğu en fazla iş parçacığı sayısını alır.|  
|[GetMinThreads Yöntemi](ihostthreadpoolmanager-getminthreads-method.md)|Olasılığına for isteklerinde konağın sakladığı en az boştaki iş parçacığı sayısını alır.|  
|[QueueUserWorkItem Yöntemi](ihostthreadpoolmanager-queueuserworkitem-method.md)|Yürütme için bir işlevi sıraya alır ve işlev tarafından kullanılacak verileri içeren bir nesne sağlar.|  
|[SetMaxThreads Yöntemi](ihostthreadpoolmanager-setmaxthreads-method.md)|Konağın iş parçacığı havuzunda koruyabileceği en fazla iş parçacığı sayısını ayarlar.|  
|[SetMinThreads Yöntemi](ihostthreadpoolmanager-setminthreads-method.md)|Konağın olasılığına isteklerinde saklanması gereken en az boş iş parçacığı sayısını ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  

 Ana bilgisayar, ve yöntemlerine yapılan çağrılarında belirtilen değerleri kullanarak iş parçacığı havuzunu yapılandırmak için gerekli değildir `SetMaxThreads` `SetMinThreads` . Bu durumda, ana bilgisayar bu yöntemlerden bir E_NOTIMPL HRESULT değeri döndürmelidir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [Barındırma Arabirimleri](hosting-interfaces.md)
