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
ms.openlocfilehash: e9cbf4551c2f8b183e9e6c37a74b13aff3a19ec1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860989"
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc Arabirimi
Yeni bir Microsoft ara dili (MSIL) işlev gövdesi için bellek ayırmak üzere bir yöntem sağlar.  
  
> [!NOTE]
> `IMethodMalloc` arabirimi basit bir bellek ayırıcıdır. Bellek ayırmayı, ancak serbest bırakmanıza izin vermez.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Alloc Yöntemi](imethodmalloc-alloc-method.md)|Yeni bir MSIL işlev gövdesi için belirtilen miktarda bellek ayırmaya çalışır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her ayırıcı modüle özeldir ve işlev gövdesinin, modülün temelini pozitif bir uzaklığa göre olacağını sağlar. Modülün temel aldığı bellek çok değerli olabilir, bu nedenle ayırıcı yalnızca bir işlev gövdesi için bellek ayırmak için kullanılmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
