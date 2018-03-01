---
title: ICorPublishProcessEnum Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a3598af7dcdfa106b50e884c0f9d3752a595da89
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishprocessenum-interface"></a>ICorPublishProcessEnum Arabirimi
Öğesinin bir alt [Icorpublishenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) koleksiyonu geçiş için yöntemler sağlar arabirimi [Icorpublishprocess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) nesneleri.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Next Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|Belirtilen sayıda alır `ICorPublishProcess` geçerli konumdan başlayarak koleksiyondan örnekleri.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorPublishProcessEnum` Arabirimini uygulayan soyut arabiriminin yöntemlerini [Icorpublishenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).  
  
 Bir `ICorPublishProcessEnum` örneği tarafından oluşturulan [Icorpublish::enumprocesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) yöntemi. Geçişi koleksiyonunun `ICorPublishProcess` nesneleri aynı anda verilen filtre ölçütünü temel `ICorPublishProcessEnum` örneği oluşturuldu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorPub.idl, CorPub.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [CorpubPublish Coclass](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
