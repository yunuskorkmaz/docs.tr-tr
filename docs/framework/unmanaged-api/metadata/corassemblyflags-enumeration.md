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
ms.openlocfilehash: b1a83f07f03ddb17d5c306453cf838101a77ed65
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007942"
---
# <a name="corassemblyflags-enumeration"></a>CorAssemblyFlags Numaralandırması
Bir derleme derlemesine uygulanan meta verileri tanımlayan değerleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`afPublicKey`|Derleme başvurusunun tam, karma olmayan ortak anahtarı tuttuğunda olduğunu gösterir.|  
|`afPA_None`|İşlemci mimarisinin belirtilmemiş olduğunu gösterir.|  
|`afPA_MSIL`|İşlemci mimarisinin nötr (PE32) olduğunu gösterir.|  
|`afPA_x86`|İşlemci mimarisinin x86 (PE32) olduğunu gösterir.|  
|`afPA_IA64`|İşlemci mimarisinin Itanium (PE32 +) olduğunu gösterir.|  
|`afPA_AMD64`|İşlemci mimarisinin AMD x64 (PE32 +) olduğunu gösterir.|  
|`afPA_ARM`|İşlemci mimarisinin ARM (PE32) olduğunu gösterir.|  
|`afPA_NoPlatform`|Derlemenin bir başvuru derlemesi olduğunu belirtir; diğer bir deyişle, her türlü mimari için geçerlidir, ancak herhangi bir mimaride çalıştırılamaz. Bu nedenle, bayrak ile aynıdır `afPA_Mask` .|  
|`afPA_Specified`|İşlemci mimarisi bayraklarının kayda yayıldığını gösterir `AssemblyRef` .|  
|`afPA_Mask`|İşlemci mimarisini tanımlayan bir maske.|  
|`afPA_FullMask`|İşlemci mimarisi açıklamasının dahil edildiğini belirtir.|  
|`afPA_Shift`|Dizin ve dizinden gelen işlemci mimarisi bayraklarının bir kaydırma sayısını gösterir.|  
|`afEnableJITcompileTracking`|Öğesinden karşılık gelen değeri gösterir <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> <xref:System.Diagnostics.DebuggableAttribute> .|  
|`afDisableJITcompileOptimizer`|Öğesinden karşılık gelen değeri gösterir <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> <xref:System.Diagnostics.DebuggableAttribute> .|  
|`afRetargetable`|Derlemenin çalışma zamanında farklı bir yayımcıdan bir derlemeye yeniden hedeflenebileceğini belirtir.|  
|`afContentType_Mask`|İçerik türünü tanımlayan bir maske.|  
|`afContentType_Default`|Varsayılan içerik türünü gösterir.|  
|`afContentType_WindowsRuntime`|Windows Çalışma Zamanı içerik türünü gösterir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
