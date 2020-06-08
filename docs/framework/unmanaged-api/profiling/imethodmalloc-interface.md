---
title: IMethodMalloc Arabirimi
ms.date: 03/30/2017
api_name:
- IMethodMalloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc
helpviewer_keywords:
- IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type:
- apiref
ms.openlocfilehash: 12b97b28383eb7c39f20ee0e88f55d48e60ad956
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494117"
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc Arabirimi
Yeni bir Microsoft ara dili (MSIL) işlev gövdesi için bellek ayırmak üzere bir yöntem sağlar.  
  
> [!NOTE]
> `IMethodMalloc`Arabirim basit bir bellek ayırıcıdır. Bellek ayırmayı, ancak serbest bırakmanıza izin vermez.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Description|  
|------------|-----------------|  
|[Alloc Yöntemi](imethodmalloc-alloc-method.md)|Yeni bir MSIL işlev gövdesi için belirtilen miktarda bellek ayırmaya çalışır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her ayırıcı modüle özeldir ve işlev gövdesinin, modülün temelini pozitif bir uzaklığa göre olacağını sağlar. Modülün temel aldığı bellek çok değerli olabilir, bu nedenle ayırıcı yalnızca bir işlev gövdesi için bellek ayırmak için kullanılmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
