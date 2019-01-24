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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ab94bf7c55d4c19a4f3672ed86808575b8a2239
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536925"
---
# <a name="corpekind-enumeration"></a>CorPEKind Numaralandırması
Çağrısından döndürülen bir taşınabilir yürütülebilir (PE) dosya açıklayan değerleri içeren [Imetadataımport2::getpekind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`peILOnly`|Bu PE dosyası yalnızca yönetilen kod içerdiğini gösterir.|  
|`pe32BitRequired`|Gösterir. Bu PE dosyası Win32 çağrısı yapar.|  
|`pe32Plus`|Bu PE dosyası bir 64-bit platformda çalıştırıldığını gösterir.|  
|`pe32Unmanaged`|Bu PE dosyası yerel kod olduğunu gösterir.|  
|pe32BitPreferred|Bu PE dosyası platformdan bağımsız ve 32-bit ortamında yüklenmesini tercih gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu değerleri bit düzeyinde bileşimlerde kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
