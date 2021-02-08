---
description: ': ICorPublishProcessEnum arabirimi hakkında daha fazla bilgi edinin'
title: ICorPublishProcessEnum Arabirimi
ms.date: 03/30/2017
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
ms.openlocfilehash: 87d80d066995dbeca67f461e01652dd3deb3bf1b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790496"
---
# <a name="icorpublishprocessenum-interface"></a>ICorPublishProcessEnum Arabirimi

ICorPublishEnum [](icorpublishenum-interface.md) arabiriminin bir [ICorPublishProcess](icorpublishprocess-interface.md) nesneleri koleksiyonunu gezme yöntemleri sağlayan bir alt sınıfı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Next Yöntemi](icorpublishprocessenum-next-method.md)|`ICorPublishProcess`Geçerli konumdan başlayarak koleksiyondan belirtilen sayıda örnek alır.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ICorPublishProcessEnum`Arabirim, [ICorPublishEnum](icorpublishenum-interface.md)soyut arabiriminin yöntemlerini uygular.  
  
 `ICorPublishProcessEnum` [ICorPublish:: EnumProcesses](icorpublish-enumprocesses-method.md) yöntemi tarafından bir örnek oluşturulur. Nesne koleksiyonunun çapraz geçişi, `ICorPublishProcess` örnek oluşturulduğu sırada verilen filtre ölçütlerini temel alır `ICorPublishProcessEnum` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub. IDL, CorPub. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [CorpubPublish Ortak Sınıfı](corpubpublish-coclass.md)
