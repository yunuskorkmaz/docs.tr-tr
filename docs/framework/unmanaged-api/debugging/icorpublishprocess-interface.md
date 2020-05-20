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
ms.openlocfilehash: 8d958e949612b502ab218f5c6b75779174d34e19
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421091"
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
