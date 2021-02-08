---
description: ': ICLRMetadataLocator arabirimi hakkında daha fazla bilgi edinin'
title: ICLRMetadataLocator Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator
helpviewer_keywords:
- ICLRMetadataLocator interface [.NET Framework debugging]
ms.assetid: 43c944f4-406a-4df6-981e-0eabb33dd5d0
topic_type:
- apiref
ms.openlocfilehash: 6e7fd45197294563e12da020379d1bd54b088698
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772630"
---
# <a name="iclrmetadatalocator-interface"></a>ICLRMetadataLocator Arabirimi

Hedef işlemdeki derlemelerin meta verilerini bulmak için veri erişim Hizmetleri katmanı tarafından kullanılır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetMetadata Yöntemi](iclrmetadatalocator-getmetadata-method.md)|Hedef işlemden bir görüntünün meta verilerini alır.|  
  
## <a name="remarks"></a>Açıklamalar  

 API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir. Örneğin, canlı bir işlem için uygulama, bellek dökümünden farklı olabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData. IDL, ClrData. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
