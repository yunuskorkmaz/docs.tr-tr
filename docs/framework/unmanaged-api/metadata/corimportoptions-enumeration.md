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
ms.openlocfilehash: 3be8a004be752af8a8675a3499bdb6cbfd785840
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009203"
---
# <a name="corimportoptions-enumeration"></a>CorImportOptions Numaralandırması
Geçerli kapsam dışında bir derlemenin içe aktarılması işlemini sırasında davranışı denetleyen bayrak değerlerini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`MDImportOptionDefault`|Silinen kayıtları atlamak için olan varsayılan davranışı gösterir.|  
|`MDImportOptionAll`|Tüm meta verilerin numaralandırılacağını belirtir.|  
|`MDImportOptionAllTypeDefs`|Silinenler dahil olmak üzere tüm TypeDefs 'un numaralandırılacağını belirtir.|  
|`MDImportOptionAllMethodDefs`|Silinenler dahil olmak üzere tüm MethodDefs 'ın numaralandırılacağını belirtir.|  
|`MDImportOptionAllFieldDefs`|Silinen tüm FieldDefs 'ler dahil olmak üzere numaralandırılacağını belirtir.|  
|`MDImportOptionAllProperties`|Silinen gibi tüm PropertyDefs 'ler de dahil olmak üzere numaralandırılacağını belirtir.|  
|`MDImportOptionAllEvents`|Silinen tüm EventDefs 'ler dahil olmak üzere numaralandırılacağını belirtir.|  
|`MDImportOptionAllCustomAttributes`|Silinen olanlar da dahil olmak üzere tüm özel özniteliklerin numaralandırılacağını belirtir.|  
|`MDImportOptionAllExportedTypes`|Silinmiş olanlar dahil olmak üzere tüm dışarıya aktarılmış türlerin numaralandırılacağını belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
