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
ms.openlocfilehash: fec049297bfa12d86cb2a7f7950e84ae540832b1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007448"
---
# <a name="corerrorifemitoutoforder-enumeration"></a>CorErrorIfEmitOutOfOrder Numaralandırması
Meta veriler sıralı dışı bırakıldığında bir hata iletisinin oluşturulması gereken koşulları belirten bayrak değerlerini içerir.  
  
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
|`MDErrorOutOfOrderDefault`|Hata iletileri oluşturabilen varsayılan davranışı gösterir.|  
|`MDErrorOutOfOrderNone`|Derleyicinin hata iletileri üretmemelidir anlamına gelir.|  
|`MDErrorOutOfOrderAll`|Bir alan, özellik, olay, yöntem veya parametre sıralı olarak yayıldığınızda derleyicinin bir hata mesajı oluşturması gerektiğini gösterir.|  
|`MDMethodOutOfOrder`|Bir yöntem bir sıra dışına yayıldığınızda derleyicinin bir hata mesajı oluşturması gerektiğini gösterir.|  
|`MDFieldOutOfOrder`|Bir alan sipariş dışı bırakıldığında derleyicinin bir hata mesajı oluşturması gerektiğini gösterir.|  
|`MDParamOutOfOrder`|Bir parametre sıralı olarak yayıldığınızda derleyicinin bir hata mesajı oluşturması gerektiğini gösterir.|  
|`MDPropertyOutOfOrder`|Bir özellik sıralı olarak yayıldığınızda derleyicinin bir hata mesajı oluşturması gerektiğini gösterir.|  
|`MDEventOutOfOrder`|Bir olay bir sıra dışına yayıldığınızda derleyicinin bir hata mesajı oluşturması gerektiğini gösterir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
