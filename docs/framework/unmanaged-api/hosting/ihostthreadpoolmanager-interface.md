---
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
ms.openlocfilehash: bac29b5950f1547c5c60ac716d40d2ef4b1a2cc2
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842487"
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
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [Barındırma Arabirimleri](hosting-interfaces.md)
