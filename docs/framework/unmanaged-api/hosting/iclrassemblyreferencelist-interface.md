---
title: ICLRAssemblyReferenceList Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList
helpviewer_keywords:
- ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type:
- apiref
ms.openlocfilehash: a75235cd0ac0e55412f0ba58881796e3ebc801f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679247"
---
# <a name="iclrassemblyreferencelist-interface"></a>ICLRAssemblyReferenceList Arabirimi

Ana bilgisayar tarafından değil, ortak dil çalışma zamanı (CLR) tarafından yüklenen derlemelerin listesini yönetir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IsAssemblyReferenceInList Yöntemi](iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|Sağlanan işaretçinin listedeki bir derlemeye başvuru yapıp olmadığını gösteren bir değer alır.|  
|[IsStringAssemblyReferenceInList Yöntemi](iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|Sağlanan adın listedeki bir derlemenin adıyla eşleşip eşleşmediğini gösteren bir değer alır.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bir örneğine bir işaretçi almak için [ICLRAssemblyIdentityManager:: GetCLRAssemblyReferenceList](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) metodunu çağırın `ICLRAssemblyReferenceList` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRAssemblyIdentityManager Arabirimi](iclrassemblyidentitymanager-interface.md)
- [IHostAssemblyStore Arabirimi](ihostassemblystore-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
