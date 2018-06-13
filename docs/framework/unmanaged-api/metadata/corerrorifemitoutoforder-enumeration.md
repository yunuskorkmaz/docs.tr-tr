---
title: CorErrorIfEmitOutOfOrder Numaralandırması
ms.date: 03/30/2017
api_name:
- CorErrorIfEmitOutOfOrder
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorErrorIfEmitOutOfOrder
helpviewer_keywords:
- CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4e9d03dcf4603f9470f8f2509050eb6f875746a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442646"
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
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
