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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aebc6dfe4830e6477cda8fd279b8ef2a8040895c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149675"
---
# <a name="createasmnameobjflags-enumeration"></a>CREATE_ASM_NAME_OBJ_FLAGS Numaralandırması
Özniteliklerini belirtir bir [Iassemblyname arabirimi](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) nesnesi tarafından oluşturulduğunda [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) işlevi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`CANOF_PARSE_DISPLAY_NAME`|Geçirilen parametre değerinin metinsel bir kimliği olduğunu gösterir.|  
|`CANOF_SET_DEFAULT_VALUES`|Birkaç varsayılan değerlerini ayarlar.|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|Arkadaş derleme kuralı (yalnızca ad ve ortak anahtar) doğrular. Bu üye, yalnızca dahili kullanım içindir.|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|Bir birleşimi `CANOF_PARSE_DISPLAY_NAME` ve `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` bayrakları. Bu üye, yalnızca dahili kullanım içindir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IAssemblyName Arabirimi](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [CreateAssemblyNameObject İşlevi](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)
- [Fusion Sabit Listeleri](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
