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
ms.openlocfilehash: 8f0a9b9c149c86b4d9121275aa858dfdc0cdbac7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195169"
---
# <a name="assemblymetadata-structure"></a>ASSEMBLYMETADATA Yapısı
Başvurulan derlemenin sürümü ve yerel ayarlar, işlemcileri ve işletim sistemleri için destek düzeyini de dahil olmak üzere, ilgili bilgiler içerir.  
  
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
|`usMajorVersion`|Başvurulan derlemenin sürüm sayısı. Bu değer sıfır olamaz. Tüm bit'leri `usMajorVersion` , ana sürüm belirtilmezse ayarlanmıştır.|  
|`usMinorVersion`|Başvurulan derlemenin ikincil sürüm sayısı. Bu değer sıfır olamaz. Tüm bit'leri `usMinorVersion` , alt sürüm belirtilmezse ayarlanmıştır.|  
|`usBuildNumber`|Başvurulan derlemenin derleme sayısı. Bu değer sıfır olamaz. Tüm bit'leri `usBuildNumber` , derleme numarası belirtilmemiş ayarlanmıştır.|  
|`usRevisionNumber`|Başvurulan derlemenin düzeltme sayısı. Bu değer sıfır olamaz. Tüm bit'leri `usRevisionNumber` , düzeltme numarası belirtilmezse ayarlanmıştır.|  
|`szLocale`|Yerel ayar adları noktalı virgül, başvurulan derleme tarafından desteklenen yerel ayarlar belirterek ayırarak RFC1766 belirtimine uyan bir listesi. Null değeri, yerel ayar bağımsızlığı gösterir. **Not:**  .NET Framework sürüm 1.0 birden fazla yerel ayar belirtilemez.|  
|`cbLocale`|Geniş karakter cinsinden boyutu `szLocale`.|  
|`rdwProcessor`|Tanımlayıcılar, Winnt.h başvurulan derleme tarafından desteklenmeyen İşlemci türleri için tanımlanan bir dizi. NULL değeri işlemci bağımsızlığı gösterir.|  
|`ulProcessor`|Uzunluğunu `rdwProcessor` dizisi.|  
|`rOS`|Bir dizi [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) başvurulan derleme tarafından desteklenen işletim sistemlerini belirten örneği. NULL değeri, işletim sistemi bağımsızlığı gösterir.|  
|`ulOS`|Uzunluğunu `rOS` dizisi.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Yapıları](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [OSINFO Yapısı](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
