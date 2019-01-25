---
title: CorImportOptions Numaralandırması
ms.date: 03/30/2017
api_name:
- CorImportOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorImportOptions
helpviewer_keywords:
- CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a4cc17bdcaea5099d0d2b0195ae4fa28e3d4744
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744618"
---
# <a name="corimportoptions-enumeration"></a>CorImportOptions Numaralandırması
Geçerli kapsam dışında bir derleme içeri aktarma sırasında davranışını denetleyen bayrak değerlerini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorImportOptions {  
  
    MDImportOptionDefault                = 0x00000000,  
    MDImportOptionAll                    = 0xFFFFFFFF,  
    MDImportOptionAllTypeDefs            = 0x00000001,  
    MDImportOptionAllMethodDefs          = 0x00000002,  
    MDImportOptionAllFieldDefs           = 0x00000004,  
    MDImportOptionAllProperties          = 0x00000008,  
    MDImportOptionAllEvents              = 0x00000010,  
    MDImportOptionAllCustomAttributes    = 0x00000020,  
    MDImportOptionAllExportedTypes       = 0x00000040  
  
} CorImportOptions;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`MDImportOptionDefault`|Silinmiş kayıtlar atlamak için varsayılan davranış gösterir.|  
|`MDImportOptionAll`|Tüm meta veriler listelenmiş olduğunu gösterir.|  
|`MDImportOptionAllTypeDefs`|Silinmiş olanlar da dahil olmak üzere tüm tür tanımları, listelenmiş olduğunu gösterir.|  
|`MDImportOptionAllMethodDefs`|Silinmiş olanlar da dahil olmak üzere tüm MethodDefs listelenmiş olduğunu gösterir.|  
|`MDImportOptionAllFieldDefs`|Silinmiş olanlar da dahil olmak üzere tüm FieldDefs listelenmiş olduğunu gösterir.|  
|`MDImportOptionAllProperties`|Silinmiş olanlar da dahil olmak üzere tüm PropertyDefs listelenmiş olduğunu gösterir.|  
|`MDImportOptionAllEvents`|Silinmiş olanlar da dahil olmak üzere tüm EventDefs listelenmiş olduğunu gösterir.|  
|`MDImportOptionAllCustomAttributes`|Silinmiş olanlar da dahil olmak üzere tüm özel öznitelikleri listelenmiş olduğunu gösterir.|  
|`MDImportOptionAllExportedTypes`|Silinmiş olanlar da dahil olmak üzere dışarı aktarılan tüm türler listelenmiş olduğunu gösterir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
