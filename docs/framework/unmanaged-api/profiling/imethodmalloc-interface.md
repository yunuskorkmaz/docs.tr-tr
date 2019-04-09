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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee825da1f3f0fd72a3b47b48783f0f344af99b65
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077790"
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc Arabirimi
Yeni bir Microsoft Ara dili (MSIL) işlev gövdesi için bellek ayırmak için bir yöntem sağlar.  
  
> [!NOTE]
>  `IMethodMalloc` Basit bellek ayırıcı arabirimidir. Bellek ayıramadı, ancak boş değil sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Alloc Yöntemi](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|Yeni bir MSIL işlev gövdesi için belirtilen miktarda bellek ayırmaya çalışır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her ayırıcı modülü özgü olan ve işlev gövdesi modülünün temel pozitif bir sapma olmasını sağlar. Yalnızca bir işlev gövdesi için bellek ayırmak için ayırıcı kullanılması gereken şekilde bellek temel bir modülün yukarıda değerli, olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
