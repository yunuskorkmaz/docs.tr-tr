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
ms.openlocfilehash: 3ae48df9e66890161c1aef944d37b0a279939d56
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790536"
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess Arabirimi
Bir işlem hakkında görüntülenecek bilgilere erişen yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumAppDomains Yöntemi](icorpublishprocess-enumappdomains-method.md)|Bu `ICorPublishProcess`başvurduğu işlem içindeki uygulama etki alanlarını içeren bir [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) örneği alır.|  
|[GetDisplayName Yöntemi](icorpublishprocess-getdisplayname-method.md)|Bu `ICorPublishProcess`başvurduğu işlem için yürütülebilir dosyanın tam yolunu alır.|  
|[GetProcessID Yöntemi](icorpublishprocess-getprocessid-method.md)|Bu `ICorPublishProcess`başvurduğu işlemin işletim sistemi tanımlayıcısını alır.|  
|[IsManaged Yöntemi](icorpublishprocess-ismanaged-method.md)|Bu `ICorPublishProcess` başvurduğu işlemin yönetilen kodu çalıştırıp çalıştırmadığını gösteren bir değer alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub. IDL, CorPub. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [CorpubPublish Coclass](corpubpublish-coclass.md)
