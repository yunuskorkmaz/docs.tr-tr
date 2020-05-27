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
ms.openlocfilehash: 5c7211fc2523b70313a1e4d4d9d2da0dcecd1d32
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009437"
---
# <a name="assemblymetadata-structure"></a>ASSEMBLYMETADATA Yapısı
Başvurulan derleme hakkında, sürümü ve yerel ayarlar, işlemciler ve işletim sistemleri için destek düzeyi dahil olmak üzere bilgiler içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`usMajorVersion`|Başvurulan derlemenin ana sürüm numarası. Bu değer sıfır olamaz. Tüm bitleri `usMajorVersion` ayarlandıysa, ana sürüm belirtilmez.|  
|`usMinorVersion`|Başvurulan derlemenin ikincil sürüm numarası. Bu değer sıfır olamaz. Tüm bitleri `usMinorVersion` ayarlandıysa, ikincil sürüm belirtilmez.|  
|`usBuildNumber`|Başvurulan derlemenin yapı numarası. Bu değer sıfır olamaz. Tüm bitleri `usBuildNumber` ayarlandıysa, yapı numarası belirtilmez.|  
|`usRevisionNumber`|Başvurulan derlemenin düzeltme numarası. Bu değer sıfır olamaz. Tüm bitleri `usRevisionNumber` ayarlandıysa, düzeltme numarası belirtilmez.|  
|`szLocale`|RFC1766 belirtimine uyan, başvurulan derleme tarafından desteklenen yerel ayarları belirten, noktalı virgülle ayrılmış yerel ayar adlarının listesi. Null değer yerel ayar bağımsızlığını gösterir. **Note:**  .NET Framework sürüm 1,0 ' de birden fazla yerel ayar belirtemezsiniz.|  
|`cbLocale`|Öğesinin geniş karakterdeki boyutu `szLocale` .|  
|`rdwProcessor`|Başvurulan derleme tarafından desteklenen işlemci türleri için Winnt. h içinde tanımlanan bir dizi tanımlayıcıdır. NULL değer işlemci bağımsızlığını gösterir.|  
|`ulProcessor`|`rdwProcessor`Dizinin uzunluğu.|  
|`rOS`|Başvurulan derleme tarafından desteklenen işletim sistemlerini belirten bir [OSINFO](osinfo-structure.md) örnekleri dizisi. NULL değer, işletim sistemi bağımsızlığını gösterir.|  
|`ulOS`|`rOS`Dizinin uzunluğu.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Yapıları](metadata-structures.md)
- [IMetaDataAssemblyEmit Arabirimi](imetadataassemblyemit-interface.md)
- [OSINFO Yapısı](osinfo-structure.md)
