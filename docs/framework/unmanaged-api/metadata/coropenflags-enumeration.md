---
title: "CorOpenFlags Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorOpenFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorOpenFlags
helpviewer_keywords: CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4447f648277576169c9004d1880283728639c8f3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="coropenflags-enumeration"></a>CorOpenFlags Numaralandırması
Bildirim dosyaları açma bağlı meta veri davranışını denetleyen bayrak değerleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorOpenFlags  
{  
    ofRead              =   0x00000000,  
    ofWrite             =   0x00000001,  
    ofReadWriteMask     =   0x00000001,  
    ofCopyMemory        =   0x00000002,  
    ofCacheImage        =   0x00000004,  
    ofManifestMetadata  =   0x00000008,  
    ofReadOnly          =   0x00000010,  
    ofTakeOwnership     =   0x00000020,  
    ofCacheImage        =   0x00000004,  
    ofNoTypeLib         =   0x00000080,  
    ofNoTransform       =   0x00001000,  
    ofReserved1         =   0x00000100,  
    ofReserved2         =   0x00000200,  
    ofReserved          =   0xffffff40  
} CorOpenFlags;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`ofRead`|Dosya yalnızca okumak için açılmalı gösterir.|  
|`ofWrite`|Dosya yazma için açılmış olduğunu gösterir.<br /><br /> Kullanıyorsanız `ofWrite` ne zaman bayrak .winmd dosyası açılırken, ayrıca geçirdiğiniz `ofNoTransform` bayrağı.|  
|`ofReadWriteMask`|Okuma ve yazma için bir maske.|  
|`ofCopyMemory`|Dosya belleğe okuma olduğunu gösterir. Meta veri kendi kopya korumanız gerekir.|  
|`ofCacheImage`|Kullanımdan kalktı. Bu bayrak göz ardı edilir.|  
|`ofManifestMetadata`|Kullanımdan kalktı. Bu bayrak göz ardı edilir.|  
|`ofReadOnly`|Dosya okuma ve, açılmalı gösteren bir çağrı `QueryInterface` için bir [Imetadataemit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) yapılamaz.|  
|`ofTakeOwnership`|Bellek için bir çağrı kullanılarak ayrıldı gösterir [CoTaskMemAlloc](http://msdn.microsoft.com/library/c4cb588d-9482-4f90-a92e-75b604540d5c) ve meta verileri ile serbest.|  
|`ofNoTypeLib`|Kullanımdan kalktı. Bu bayrak göz ardı edilir.|  
|`ofNoTransform`|.Winmd dosyaların otomatik Dönüşümlerin devre dışı olduğunu gösterir. Diğer bir deyişle, bir .NET Framework türü için bir Windows çalışma zamanı tür projeksiyonu devre dışı bırakılmalıdır. Daha fazla bilgi için bkz: [altındaki başlık .NET ve Windows çalışma zamanı ile](http://msdn.microsoft.com/magazine/jj651569.aspx).|  
|`ofReserved1`|İç kullanım için ayrılmıştır.|  
|`ofReserved2`|İç kullanım için ayrılmıştır.|  
|`ofReserved`|İç kullanım için ayrılmıştır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorHdr.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
