---
title: CorAssemblyFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CorAssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAssemblyFlags
helpviewer_keywords:
- CorAssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: bb8db3b6-d81d-49fc-b74c-dbc908a9eab9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f99fb7a693c47b257abe9c0b783856179fc9f0eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582388"
---
# <a name="corassemblyflags-enumeration"></a>CorAssemblyFlags Numaralandırması
Bir derleme derlemeye uygulanan meta verileri tanımlayan değerlerini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorAssemblyFlags {  
  
    afPublicKey             =   0x0001,  
    afPA_None               =   0x0000,  
    afPA_MSIL               =   0x0010,  
    afPA_x86                =   0x0020,  
    afPA_IA64               =   0x0030,  
    afPA_AMD64              =   0x0040,  
    afPA_ARM                =   0x0050,  
    afPA_NoPlatform         =   0x0070,  
    afPA_Specified          =   0x0080,  
    afPA_Mask               =   0x0070,  
    afPA_FullMask           =   0x00F0,  
    afPA_Shift              =   0x0004,  
  
    afEnableJITcompileTracking  =   0x8000,  
    afDisableJITcompileOptimizer=   0x4000,  
  
    afRetargetable          =   0x0100,  
    afContentType_Default        =   0x0000,  
    afContentType_WindowsRuntime =   0x0200,  
    afContentType_Mask           =   0x0E00,  
  
} CorAssemblyFlags;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`afPublicKey`|Bütünleştirilmiş kod başvurusu tam, bütün ortak anahtarı saklar gösterir.|  
|`afPA_None`|İşlemci mimarisi belirtilmeyen olduğunu gösterir.|  
|`afPA_MSIL`|İşlemci mimarisi nötr olduğunu gösterir (PE32).|  
|`afPA_x86`|İşlemci mimarisi x86 (PE32) olduğunu gösterir.|  
|`afPA_IA64`|İşlemci mimarisi Itanium (PE32 +) olduğunu gösterir.|  
|`afPA_AMD64`|İşlemci mimarisi AMD X64 (PE32 +) olduğunu gösterir.|  
|`afPA_ARM`|İşlemci mimarisi ARM (PE32) olduğunu gösterir.|  
|`afPA_NoPlatform`|Derlemeye bir başvuru bütünleştirilmiş kodu olduğunu gösterir; diğer bir deyişle, tüm mimarisi için geçerlidir ancak herhangi bir mimari üzerinde çalıştırılamaz. Bu nedenle, bayrağı aynıdır `afPA_Mask`.|  
|`afPA_Specified`|İşlemci mimarisi bayrakları için dağıtılmasını belirten `AssemblyRef` kaydı.|  
|`afPA_Mask`|İşlemci mimarisini açıklar maskesi.|  
|`afPA_FullMask`|İşlemci mimarisi açıklaması dahil olduğunu belirtir.|  
|`afPA_Shift`|Bir kaydırma sayısı İşlemci mimarisi bayrakları dizini gelen ve giden olarak gösterir.|  
|`afEnableJITcompileTracking`|Karşılık gelen değeri gösteren <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> , <xref:System.Diagnostics.DebuggableAttribute>.|  
|`afDisableJITcompileOptimizer`|Karşılık gelen değeri gösteren <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> , <xref:System.Diagnostics.DebuggableAttribute>.|  
|`afRetargetable`|Derleme çalışma zamanında bir derlemeye farklı bir yayımcı tarafından hedeflenmesi olduğunu gösterir.|  
|`afContentType_Mask`|İçerik türünü açıklayan maskesi.|  
|`afContentType_Default`|Varsayılan içerik türünü belirtir.|  
|`afContentType_WindowsRuntime`|Gösterir [!INCLUDE[wrt](../../../../includes/wrt-md.md)] içerik türü.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
