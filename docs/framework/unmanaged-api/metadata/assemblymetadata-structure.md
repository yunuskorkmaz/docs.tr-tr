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
ms.openlocfilehash: 24ec1f7d553a59425f7eb02af8e91010d940eb07
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444260"
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
  
## <a name="members"></a>Üyeleri  
  
|Üyesi|Açıklama|  
|------------|-----------------|  
|`usMajorVersion`|Başvurulan derlemenin ana sürüm numarası. Bu değer sıfır olamaz. Tüm `usMajorVersion` bitleri ayarlanırsa, ana sürüm belirtilmez.|  
|`usMinorVersion`|Başvurulan derlemenin ikincil sürüm numarası. Bu değer sıfır olamaz. Tüm `usMinorVersion` bitleri ayarlandıysa, ikincil sürüm belirtilmez.|  
|`usBuildNumber`|Başvurulan derlemenin yapı numarası. Bu değer sıfır olamaz. Tüm `usBuildNumber` bitleri ayarlandıysa, derleme numarası belirtilmez.|  
|`usRevisionNumber`|Başvurulan derlemenin düzeltme numarası. Bu değer sıfır olamaz. Tüm `usRevisionNumber` bitleri ayarlandıysa, düzeltme numarası belirtilmez.|  
|`szLocale`|RFC1766 belirtimine uyan, başvurulan derleme tarafından desteklenen yerel ayarları belirten, noktalı virgülle ayrılmış yerel ayar adlarının listesi. Null değer yerel ayar bağımsızlığını gösterir. **Note:**  .NET Framework sürüm 1,0 ' de birden fazla yerel ayar belirtemezsiniz.|  
|`cbLocale`|`szLocale`geniş karakterdeki boyut.|  
|`rdwProcessor`|Başvurulan derleme tarafından desteklenen işlemci türleri için Winnt. h içinde tanımlanan bir dizi tanımlayıcıdır. NULL değer işlemci bağımsızlığını gösterir.|  
|`ulProcessor`|`rdwProcessor` dizisinin uzunluğu.|  
|`rOS`|Başvurulan derleme tarafından desteklenen işletim sistemlerini belirten bir [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) örnekleri dizisi. NULL değer, işletim sistemi bağımsızlığını gösterir.|  
|`ulOS`|`rOS` dizisinin uzunluğu.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Yapıları](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [OSINFO Yapısı](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
