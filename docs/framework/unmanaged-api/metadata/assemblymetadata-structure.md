---
title: ASSEMBLYMETADATA Yapısı
ms.date: 03/30/2017
api_name:
- ASSEMBLYMETADATA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ASSEMBLYMETADATA
helpviewer_keywords:
- ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83f6190872ecf4435688f3b7c82a61f5f15d9f62
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="assemblymetadata-structure"></a>ASSEMBLYMETADATA Yapısı
Kendi sürüm ve alt düzey yerel ayarlar, işlemcileri ve işletim sistemleri için destek dahil olmak üzere başvurulan derleme hakkında bilgiler içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct {  
    USHORT  usMajorVersion;  
    USHORT  usMinorVersion;  
    USHORT  usBuildNumber;  
    USHORT  usRevisionNumber;  
    LPWSTR  szLocale;  
    ULONG   cbLocale;  
    DWORD*  rdwProcessor[];  
    ULONG   ulProcessor  
    OSINFO* rOS[];  
    ULONG   ulOS;  
} ASSEMBLYMETADATA;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`usMajorVersion`|Başvurulan derlemeyi ana sürüm numarası. Bu değer sıfır olamaz. Varsa, tüm BITS `usMajorVersion` , ana sürüm belirtilmezse ayarlanmıştır.|  
|`usMinorVersion`|Başvurulan derlemeyi ikincil sürüm numarası. Bu değer sıfır olamaz. Varsa, tüm BITS `usMinorVersion` , alt sürüm belirtilmezse ayarlanmıştır.|  
|`usBuildNumber`|Başvurulan derlemeyi yapı sayısı. Bu değer sıfır olamaz. Varsa, tüm BITS `usBuildNumber` , yapı numarası belirtilmezse ayarlanmıştır.|  
|`usRevisionNumber`|Başvurulan derlemeyi düzeltme sayısı. Bu değer sıfır olamaz. Varsa, tüm BITS `usRevisionNumber` , düzeltme numarası belirtilmezse ayarlanmıştır.|  
|`szLocale`|Başvurulan derleme tarafından desteklenen yerel ayarlar belirtme noktalı virgül ile ayrılmış RFC1766 belirtimine uygun yerel ayar adları listesi. Bir null değer yerel bağımsızlığı gösterir. **Not:** .NET Framework sürüm 1.0 birden fazla yerel ayar belirtemezsiniz.|  
|`cbLocale`|Geniş karakter cinsinden boyutu `szLocale`.|  
|`rdwProcessor`|Winnt.h içinde başvurulan derleme tarafından desteklenen İşlemci türleri için tanımlanan tanımlayıcıları dizisi. NULL değeri işlemci bağımsızlığı gösterir.|  
|`ulProcessor`|Uzunluğu `rdwProcessor` dizi.|  
|`rOS`|Bir dizi [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) başvurulan derleme tarafından desteklenen işletim sistemleri belirtme örnekleri. NULL değeri, işletim sistemi bağımsızlığı gösterir.|  
|`ulOS`|Uzunluğu `rOS` dizi.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Yapıları](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [OSINFO Yapısı](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
