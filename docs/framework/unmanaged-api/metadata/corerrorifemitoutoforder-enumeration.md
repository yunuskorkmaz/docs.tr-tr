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
ms.openlocfilehash: 16f6d7bf6fa1730d50cfe81526817e492a453dad
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781979"
---
# <a name="corerrorifemitoutoforder-enumeration"></a>CorErrorIfEmitOutOfOrder Numaralandırması
Meta veri sıralamaya yayıldığını zaman altında bir hata iletisi oluşturulan koşulları belirten bayrak değerlerini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`MDErrorOutOfOrderAll`|Derleyici bir hata iletisi oluşturur, bir alan, özellik, olay, yöntemi veya parametre sıralamaya yayıldığını gösterir.|  
|`MDMethodOutOfOrder`|Bir yöntem sıralamaya yayıldığını, derleyici bir hata iletisi oluşturmasını belirtir.|  
|`MDFieldOutOfOrder`|Bir alan sıralamaya yayıldığını, derleyici bir hata iletisi oluşturmasını belirtir.|  
|`MDParamOutOfOrder`|Bir parametre sıralamaya yayıldığını, derleyici bir hata iletisi oluşturmasını belirtir.|  
|`MDPropertyOutOfOrder`|Bir özellik sıralamaya yayıldığını, derleyici bir hata iletisi oluşturmasını belirtir.|  
|`MDEventOutOfOrder`|Bir olay sıralamaya yayıldığını, derleyici bir hata iletisi oluşturmasını belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
