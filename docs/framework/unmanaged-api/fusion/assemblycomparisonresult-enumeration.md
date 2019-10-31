---
title: AssemblyComparisonResult Numaralandırması
ms.date: 03/30/2017
api_name:
- AssemblyComparisonResult
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- AssemblyComparisonResult
helpviewer_keywords:
- AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type:
- apiref
ms.openlocfilehash: 3d3fd88a2c1ac90f823b23d8d2bcb5b177a625c3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109005"
---
# <a name="assemblycomparisonresult-enumeration"></a>AssemblyComparisonResult Numaralandırması
[CompareAssemblyIdentity](compareassemblyidentity-function.md) işlevi tarafından belirlendiği şekilde, iki derleme kimliğinin denklik olduğunu gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum _tagAssemblyComparisonResult {  
    ACR_Unknown,   
    ACR_EquivalentFullMatch,  
    ACR_EquivalentWeakNamed,  
    ACR_EquivalentFXUnified,  
    ACR_EquivalentUnified,    
    ACR_NonEquivalentVersion,  
    ACR_NonEquivalent,      
    ACR_EquivalentPartialMatch,  
    ACR_EquivalentPartialWeakNamed,    
    ACR_EquivalentPartialUnified,  
    ACR_EquivalentPartialFXUnified,  
    ACR_NonEquivalentPartialVersion    
} AssemblyComparisonResult;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye adı|Açıklama|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|Karşılaştırmayla eşleşen tüm derleme alanlarının eşleştiğini gösterir.|  
|`ACR_EquivalentFXUnified`|Derlemelerin .NET Framework sürüm 2,0 ' deki derleme sürüm numaralarının ortak dil çalışma zamanı sürümü 'ne (CLR) göre eşit kabul edileceğini gösterir.|  
|`ACR_EquivalentPartialFXUnified`|.NET Framework 2,0 ' deki derleme sürümü numaralarının CLR içeriğini temel alarak derlemelerin kısmi bir eşleşme olduğunu gösterir.|  
|`ACR_EquivalentPartialMatch`|Derlemelerin kısmi bir eşleşmesini gösterir.|  
|`ACR_EquivalentPartialUnified`|Sürüm numaralarının eski listesini temel alarak derlemelerin kısmi bir eşleşmesinin olduğunu gösterir.|  
|`ACR_EquivalentPartialWeakNamed`|Yalnızca adlandırılmış derlemelerin kısmi bir eşleşmesini gösterir.|  
|`ACR_EquivalentUnified`|Derlemelerin, .NET Framework eski sürümlerindeki sürüm numaralarının CLR 'ye göre eşit kabul edileceğini gösterir.|  
|`ACR_EquivalentWeakNamed`|Sürüm numaraları yoksayılmış olan iki adet adlandırılmış derleme arasındaki eşleşmeyi gösterir.|  
|`ACR_NonEquivalent`|İki derleme arasında hiçbir eşleşme olmadığını gösterir.|  
|`ACR_NonEquivalentPartialVersion`|İki derlemenin, yalnızca kısmen eşleşen sürüm numaraları hariç eşleştiğini gösterir.|  
|`ACR_NonEquivalentVersion`|Eşleşmeyen iki derlemenin sürüm numaraları hariç eşleştiğini belirtir.|  
|`ACR_Unknown`|Non-denkliği için nedenin bilinmediğini gösterir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CompareAssemblyIdentity İşlevi](compareassemblyidentity-function.md)
- [Fusion Sabit Listeleri](fusion-enumerations.md)
