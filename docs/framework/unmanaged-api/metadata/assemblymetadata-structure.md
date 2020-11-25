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
ms.openlocfilehash: 8071c3f43775975de37e3255582b6fc8f13f7de3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732794"
---
# <a name="assemblymetadata-structure"></a>ASSEMBLYMETADATA Yapısı

Başvurulan derleme hakkında, sürümü ve yerel ayarlar, işlemciler ve işletim sistemleri için destek düzeyi dahil olmak üzere bilgiler içerir.  
  
## <a name="syntax"></a>Syntax  
  
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
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Yapıları](metadata-structures.md)
- [IMetaDataAssemblyEmit Arabirimi](imetadataassemblyemit-interface.md)
- [OSINFO Yapısı](osinfo-structure.md)
