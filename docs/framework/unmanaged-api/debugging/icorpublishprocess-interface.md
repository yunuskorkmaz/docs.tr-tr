---
title: ICorPublishProcess Arabirimi
ms.date: 03/30/2017
api_name:
- ICorPublishProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess
helpviewer_keywords:
- ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08dfa3ddbfd9cffdb0cb88d0325e5703a854668a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993518"
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess Arabirimi
Görüntülenecek işlemle ilgili bilgilere erişen yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumAppDomains Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|Alır bir [Icorpublishappdomainenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) bu tarafından başvurulan işlemde uygulama etki alanları içeren örneğini `ICorPublishProcess`.|  
|[GetDisplayName Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|Bu tarafından başvurulan işlemi için yürütülebilir dosyanın tam yolunu alır `ICorPublishProcess`.|  
|[GetProcessID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|Bu tarafından başvurulan işlem için işletim sistemi tanımlayıcısını alır `ICorPublishProcess`.|  
|[IsManaged Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|İşlem bu tarafından başvurulan olup olmadığını gösteren bir değer alır `ICorPublishProcess` yönetilen kod çalıştırması bilinmektedir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub.idl, CorPub.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [CorpubPublish Coclass](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
