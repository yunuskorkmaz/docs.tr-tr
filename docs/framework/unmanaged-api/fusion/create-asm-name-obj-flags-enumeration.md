---
title: CREATE_ASM_NAME_OBJ_FLAGS Numaralandırması
ms.date: 03/30/2017
api_name:
- CREATE_ASM_NAME_OBJ_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS
helpviewer_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS enumeration [.NET Framework fusion]
ms.assetid: a5ed2fd0-c7d2-4603-aaca-5d0caad92675
topic_type:
- apiref
ms.openlocfilehash: ee856dbd398d0fa5e3eee7d9b2b2cfc7c7a57ecf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176597"
---
# <a name="create_asm_name_obj_flags-enumeration"></a>CREATE_ASM_NAME_OBJ_FLAGS Numaralandırması
[CreateAssemblyNameObject](createassemblynameobject-function.md) işlevi tarafından oluşturulduğunda bir [IAssemblyName Arabirimi](iassemblyname-interface.md) nesnesinin özniteliklerini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|Geçirilen parametrenin metinsel bir kimlik olduğunu gösterir.|  
|`CANOF_SET_DEFAULT_VALUES`|Birkaç varsayılan değer ayarlar.|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|Arkadaş derleme kuralını (yalnızca ad ve ortak anahtar) doğrular. Bu üye yalnızca dahili kullanım içindir.|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|Bayraklar ve `CANOF_PARSE_DISPLAY_NAME` `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` bayrakların birleşimi. Bu üye yalnızca dahili kullanım içindir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** Fusion.h  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IAssemblyName Arabirimi](iassemblyname-interface.md)
- [CreateAssemblyNameObject İşlevi](createassemblynameobject-function.md)
- [Fusion Sabit Listeleri](fusion-enumerations.md)
