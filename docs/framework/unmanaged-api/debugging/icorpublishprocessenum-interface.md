---
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
ms.openlocfilehash: 188ff8feabd704d828256a09aca20f9db2227f2c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790504"
---
# <a name="icorpublishprocessenum-interface"></a>ICorPublishProcessEnum Arabirimi
ICorPublishEnum [](icorpublishenum-interface.md) arabiriminin bir [ICorPublishProcess](icorpublishprocess-interface.md) nesneleri koleksiyonunu gezme yöntemleri sağlayan bir alt sınıfı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Next Yöntemi](icorpublishprocessenum-next-method.md)|Geçerli konumdan başlayarak koleksiyondan belirtilen sayıda `ICorPublishProcess` örneği alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorPublishProcessEnum` arabirimi, [ICorPublishEnum](icorpublishenum-interface.md)soyut arabiriminin yöntemlerini uygular.  
  
 [ICorPublish:: EnumProcesses](icorpublish-enumprocesses-method.md) yöntemi tarafından bir `ICorPublishProcessEnum` örneği oluşturulur. `ICorPublishProcess` nesne koleksiyonunun çapraz geçişi, `ICorPublishProcessEnum` örneği oluşturulduğu sırada verilen filtre ölçütüne bağlıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub. IDL, CorPub. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [CorpubPublish Coclass](corpubpublish-coclass.md)
