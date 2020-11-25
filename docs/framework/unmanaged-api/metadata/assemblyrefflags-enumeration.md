---
title: AssemblyRefFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- AssemblyRefFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyRefFlags
helpviewer_keywords:
- AssemblyRefFlags enumeration [.NET Framework metadata]
ms.assetid: decd4f46-f3b2-466f-9501-e74f2b86b846
topic_type:
- apiref
ms.openlocfilehash: 0a99d2f79645bdc46ff4db86d7280614eeb1faf5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732768"
---
# <a name="assemblyrefflags-enumeration"></a>AssemblyRefFlags Numaralandırması

Bir derleme başvurusunun özelliklerini tanımlayan değerleri içerir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`arfFullOriginator`|Derleme başvurusunun, derlemenin yayımcısı hakkında tam, karma olmayan bilgiler içerdiğini belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
- [IMetaDataAssemblyEmit Arabirimi](imetadataassemblyemit-interface.md)
- [DefineAssemblyRef Yöntemi](imetadataassemblyemit-defineassemblyref-method.md)
