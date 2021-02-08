---
description: ': ICorPublishProcess arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 8dbc619d33c2c9b625dde852948dff00b5be926e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800883"
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess Arabirimi

Bir işlem hakkında görüntülenecek bilgilere erişen yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumAppDomains Yöntemi](icorpublishprocess-enumappdomains-method.md)|Bu tarafından başvurulan işlemdeki uygulama etki alanlarını içeren bir [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) örneği alır `ICorPublishProcess` .|  
|[GetDisplayName Yöntemi](icorpublishprocess-getdisplayname-method.md)|Bu tarafından başvurulan işlem için yürütülebilir dosyanın tam yolunu alır `ICorPublishProcess` .|  
|[GetProcessID Yöntemi](icorpublishprocess-getprocessid-method.md)|Bu tarafından başvurulan işlem için işletim sistemi tanımlayıcısını alır `ICorPublishProcess` .|  
|[IsManaged Yöntemi](icorpublishprocess-ismanaged-method.md)|Bu tarafından başvurulan işlemin `ICorPublishProcess` yönetilen kodu çalıştırıp çalıştırmadığını gösteren bir değer alır.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub. IDL, CorPub. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [CorpubPublish Ortak Sınıfı](corpubpublish-coclass.md)
