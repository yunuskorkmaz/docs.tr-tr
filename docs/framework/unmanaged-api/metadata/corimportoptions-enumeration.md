---
title: "CorImportOptions Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e9af7bbb6dd7cfa488f72ec99f9cfd848f04e72f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corimportoptions-enumeration"></a>CorImportOptions Numaralandırması
Geçerli kapsam dışında bir derlemeyi içe aktarılmasını sırasında davranışını denetleyen bayrak değerleri içerir.  
  
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
|`MDImportOptionAll`|Tüm meta veriler numaralandırılan olduğunu gösterir.|  
|`MDImportOptionAllTypeDefs`|Silinen olanlar da dahil olmak üzere tüm tür tanımları numaralandırılan olduğunu gösterir.|  
|`MDImportOptionAllMethodDefs`|Silinen olanlar da dahil olmak üzere tüm MethodDefs numaralandırılan olduğunu gösterir.|  
|`MDImportOptionAllFieldDefs`|Silinen olanlar da dahil olmak üzere tüm FieldDefs numaralandırılan olduğunu gösterir.|  
|`MDImportOptionAllProperties`|Silinen olanlar da dahil olmak üzere tüm PropertyDefs numaralandırılan olduğunu gösterir.|  
|`MDImportOptionAllEvents`|Silinen olanlar da dahil olmak üzere tüm EventDefs numaralandırılan olduğunu gösterir.|  
|`MDImportOptionAllCustomAttributes`|Silinen olanlar da dahil olmak üzere tüm özel öznitelikleri numaralandırılan olduğunu gösterir.|  
|`MDImportOptionAllExportedTypes`|Silinen olanlar da dahil olmak üzere tüm dışarı aktarılan türleri numaralandırılan olduğunu gösterir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorHdr.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
