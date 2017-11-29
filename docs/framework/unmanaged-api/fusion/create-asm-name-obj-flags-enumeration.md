---
title: "CREATE_ASM_NAME_OBJ_FLAGS Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CREATE_ASM_NAME_OBJ_FLAGS
api_location: fusion.dll
api_type: COM
f1_keywords: CREATE_ASM_NAME_OBJ_FLAGS
helpviewer_keywords: CREATE_ASM_NAME_OBJ_FLAGS enumeration [.NET Framework fusion]
ms.assetid: a5ed2fd0-c7d2-4603-aaca-5d0caad92675
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4982b33643d855be4b8cace59f1c5cac4201d5ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
|`CANOF_PARSE_DISPLAY_NAME`|Geçirilen parametre değerinin metinsel bir kimlik olduğunu gösterir.|  
|`CANOF_SET_DEFAULT_VALUES`|Birkaç varsayılan değerlerini ayarlar.|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|Arkadaş derleme kuralı (yalnızca ad ve ortak anahtar) doğrular. Bu üye, yalnızca dahili kullanım içindir.|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|Bir birleşimini `CANOF_PARSE_DISPLAY_NAME` ve `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` bayrakları. Bu üye, yalnızca dahili kullanım içindir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Fusion.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iassemblyname arabirimi](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [CreateAssemblyNameObject işlevi](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 [Fusion numaralandırmaları](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
