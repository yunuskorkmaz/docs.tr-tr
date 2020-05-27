---
title: CorPEKind Numaralandırması
ms.date: 03/30/2017
api_name:
- CorPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPEKind
helpviewer_keywords:
- CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type:
- apiref
ms.openlocfilehash: 8b6eab8156f72847eb6dd3369950f9b46a3fc877
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007565"
---
# <a name="corpekind-enumeration"></a>CorPEKind Numaralandırması
[IMetaDataImport2:: GetPEKind](imetadataimport2-getpekind-method.md)çağrısından döndürülen bir taşınabilir YÜRÜTÜLEBILIR (PE) dosyasını tanımlayan değerleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`peNot`|Bunun bir PE dosyası olmadığını gösterir.|  
|`peILOnly`|Bu PE dosyasının yalnızca yönetilen kod içerdiğini belirtir.|  
|`pe32BitRequired`|Bu PE dosyasının Win32 çağrıları yaptığını gösterir.|  
|`pe32Plus`|Bu PE dosyasının 64 bitlik bir platformda çalıştığını gösterir.|  
|`pe32Unmanaged`|Bu PE dosyasının yerel kod olduğunu gösterir.|  
|pe32BitPreferred|Bu PE dosyasının platformdan bağımsız olduğunu ve 32 bitlik bir ortamda yüklenmesinin tercih edildiğini gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu değerler bit düzeyinde kombinasyonlara uygulanabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
