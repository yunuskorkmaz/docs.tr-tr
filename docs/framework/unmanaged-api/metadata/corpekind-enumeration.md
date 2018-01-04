---
title: "CorPEKind Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorPEKind
api_location: mscoree.dll
api_type: COM
f1_keywords: CorPEKind
helpviewer_keywords: CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 612c71db092e7a3474d262c1d601335a5f416791
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corpekind-enumeration"></a>CorPEKind Numaralandırması
Taşınabilir yürütülebilir (PE) dosyasını tanımlamak değerleri çağrısından döndürülen içeren [Imetadataımport2::getpekind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).  
  
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
|`peILOnly`|Bu PE dosya yönetilen kodu yalnızca içerdiğini gösterir.|  
|`pe32BitRequired`|Bu PE dosya Win32 çağrılar olduğunu gösterir.|  
|`pe32Plus`|Bu PE dosya bir 64-bit platformda çalıştırıldığını gösterir.|  
|`pe32Unmanaged`|Bu PE dosyanın yerel kod olduğunu gösterir.|  
|pe32BitPreferred|Bu PE dosya platformdan bağımsız ve 32-bit ortamında yüklenmesini tercih gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu değerlerin Bitsel bileşimlerde kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorHdr.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
