---
title: IMethodMalloc Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMethodMalloc
api_location: mscorwks.dll
api_type: COM
f1_keywords: IMethodMalloc
helpviewer_keywords: IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d246f329f80a76d2c93190fd663c7362418385f7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc Arabirimi
Bellek için yeni bir Microsoft Ara dili (MSIL) işlev gövdesi ayırmak için bir yöntem sağlar.  
  
> [!NOTE]
>  `IMethodMalloc` Basit bellek ayırıcısı bir arabirimdir. Bellek ayıramadı, ancak boş olmayan sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Alloc yöntemi](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|Yeni bir MSIL işlev gövdesi için belirtilen bir bellek miktarı ayırmaya çalışır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her ayırıcısı modülü özeldir ve işlev gövdesi modülü tabanı pozitif uzaklığı en olmasını sağlar. Ayırıcı yalnızca bir işlev gövdesi için bellek tahsis için kullanılması gereken şekilde bir modül tabanı yukarıda bellek değerli, olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil oluşturma arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
