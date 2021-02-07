---
description: 'Daha fazla bilgi edinin: IHostMAlloc arabirimi'
title: IHostMalloc Arabirimi
ms.date: 03/30/2017
api_name:
- IHostMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc
helpviewer_keywords:
- IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type:
- apiref
ms.openlocfilehash: cd04a0f71fd429ea10b9edcce02806f4afa57148
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708183"
---
# <a name="ihostmalloc-interface"></a>IHostMalloc Arabirimi

Ortak dil çalışma zamanının (CLR) ana bilgisayar aracılığıyla yığından hassas ayırmalar istemesine izin veren yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Alloc Yöntemi](ihostmalloc-alloc-method.md)|Konağın, istenen bellek miktarını yığından ayırmasını ister.|  
|[DebugAlloc Yöntemi](ihostmalloc-debugalloc-method.md)|Konağın, istenen bellek miktarını yığından ayırmasını ister ve ayrıca belleğin nerede ayrıldığını izler.|  
|[Free Yöntemi](ihostmalloc-free-method.md)|Yöntemi kullanılarak ayrılan belleği boşaltır `Alloc` .|  
  
## <a name="remarks"></a>Açıklamalar  

 CLR, `IHostMalloc` [IHostMemoryManager:: createmayırma](ihostmemorymanager-createmalloc-method.md) yöntemini çağırarak bir örneğe bir arabirim işaretçisi alır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostMemoryManager Arabirimi](ihostmemorymanager-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
