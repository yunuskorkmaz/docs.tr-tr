---
title: ICorPublishProcess Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess
helpviewer_keywords: ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 765be4e0ae7657d169ea561bc6a36bcf8cc11153
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess Arabirimi
Görüntülenecek bir işlemle ilgili bilgileri erişim yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumAppDomains Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|Alır bir [Icorpublishappdomainenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) bu tarafından başvurulan işlemindeki uygulama etki alanları içeren örneği `ICorPublishProcess`.|  
|[GetDisplayName Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|Bu tarafından başvurulan işlem yürütülebilir dosyasının tam yolunu alır `ICorPublishProcess`.|  
|[GetProcessID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|Bu tarafından başvurulan işlem için işletim sistemi tanımlayıcısını alır `ICorPublishProcess`.|  
|[IsManaged Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|İşlemin bu tarafından başvurulan olup olmadığını belirten bir değer alır `ICorPublishProcess` yönetilen kod çalıştırması bilinmektedir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorPub.idl, CorPub.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [CorpubPublish Coclass](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
