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
ms.openlocfilehash: b11cf0fadc9142ee291115cf9f0d84e6429834fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc Arabirimi
Bellek için yeni bir Microsoft Ara dili (MSIL) işlev gövdesi ayırmak için bir yöntem sağlar.  
  
> [!NOTE]
>  `IMethodMalloc` Basit bellek ayırıcısı bir arabirimdir. Bellek ayıramadı, ancak boş olmayan sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Alloc Yöntemi](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|Yeni bir MSIL işlev gövdesi için belirtilen bir bellek miktarı ayırmaya çalışır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her ayırıcısı modülü özeldir ve işlev gövdesi modülü tabanı pozitif uzaklığı en olmasını sağlar. Ayırıcı yalnızca bir işlev gövdesi için bellek tahsis için kullanılması gereken şekilde bir modül tabanı yukarıda bellek değerli, olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
