---
title: "CorErrorIfEmitOutOfOrder Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorErrorIfEmitOutOfOrder
api_location: mscoree.dll
api_type: COM
f1_keywords: CorErrorIfEmitOutOfOrder
helpviewer_keywords: CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d2cf80375622912c6bb9a59696f37aed2d594253
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corerrorifemitoutoforder-enumeration"></a>CorErrorIfEmitOutOfOrder Numaralandırması
Meta verileri bozuk yayılan zaman altında bir hata iletisi oluşturulan koşulları belirtmek bayrak değerleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorErrorIfEmitOutOfOrder {  
  
    MDErrorOutOfOrderDefault    = 0x00000000,  
    MDErrorOutOfOrderNone       = 0x00000000,  
    MDErrorOutOfOrderAll        = 0xffffffff,  
    MDMethodOutOfOrder          = 0x00000001,  
    MDFieldOutOfOrder           = 0x00000002,  
    MDParamOutOfOrder           = 0x00000004,  
    MDPropertyOutOfOrder        = 0x00000008,  
    MDEventOutOfOrder           = 0x00000010  
  
} CorErrorIfEmitOutOfOrder;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|Hata iletileri oluşturmaz varsayılan davranış gösterir.|  
|`MDErrorOutOfOrderNone`|Derleyici hatası iletileri üretmemelidir gösterir.|  
|`MDErrorOutOfOrderAll`|Derleyici bir hata iletisine yol bir alan, özellik, olay, yöntemi veya parametre bozuk yayılan gösterir.|  
|`MDMethodOutOfOrder`|Bir yöntem bozuk yayılan olduğunda derleyici bir hata iletisi oluşturur gösterir.|  
|`MDFieldOutOfOrder`|Bir alan bozuk yayılan olduğunda derleyici bir hata iletisi oluşturur gösterir.|  
|`MDParamOutOfOrder`|Bir parametre bozuk yayılan olduğunda derleyici bir hata iletisi oluşturur gösterir.|  
|`MDPropertyOutOfOrder`|Bir özellik bozuk yayılan olduğunda derleyici bir hata iletisi oluşturur gösterir.|  
|`MDEventOutOfOrder`|Bir olay bozuk yayılan olduğunda derleyici bir hata iletisi oluşturur gösterir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorHdr.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta veri numaralandırmalar](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
