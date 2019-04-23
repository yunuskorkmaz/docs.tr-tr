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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03b8ecc996e14263510e2d0a658cec020696c263
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141706"
---
# <a name="assemblycomparisonresult-enumeration"></a>AssemblyComparisonResult Numaralandırması
İki derleme kimliklerinin denklik tarafından belirlenen şekilde gösteren [Compareassemblyıdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) işlevi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`ACR_EquivalentFullMatch`|Tüm derleme karşılaştırma eşlemesinde alanları gösterir.|  
|`ACR_EquivalentFXUnified`|Derlemeleri derleme sürüm numaralarının .NET Framework sürüm 2.0 ortak dil çalışma zamanı (CLR) sürümünü Birleştirici göre eşdeğer olarak kabul edilir olduğunu gösterir.|  
|`ACR_EquivalentPartialFXUnified`|.NET Framework 2.0 derleme sürüm numaraları CLR birleştirmesi göre derlemelerin kısmi eşleşme gösterir.|  
|`ACR_EquivalentPartialMatch`|Kısmi eşleşme derlemelerin gösterir.|  
|`ACR_EquivalentPartialUnified`|Eski sürüm numaraları birleştirmesi alarak derlemeleri kısmi bir eşleşme belirtir.|  
|`ACR_EquivalentPartialWeakNamed`|Kısmi eşleşme yalnızca adlandırılmış derlemelerin gösterir.|  
|`ACR_EquivalentUnified`|Derlemeler sürüm numaraları .NET Framework'ün eski sürümlerinde CLR birleştirmesi göre eşdeğer olarak kabul edilir olduğunu gösterir.|  
|`ACR_EquivalentWeakNamed`|Olan sürüm numaraları yoksayıldı iki yalnızca adlandırılmış derlemeler arasında bir eşleşme belirtir.|  
|`ACR_NonEquivalent`|İki derleme eşleşme oluştuğunu gösterir.|  
|`ACR_NonEquivalentPartialVersion`|İki derlemenin yalnızca kısmen eşleşen kendi sürüm numaraları dışında eşleştiğini gösterir.|  
|`ACR_NonEquivalentVersion`|İki derlemenin eşleşmiyor, sürüm numaraları dışında eşleştiğini gösterir.|  
|`ACR_Unknown`|Denkliği olmayan nedeni bilinmiyor gösterir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CompareAssemblyIdentity İşlevi](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)
- [Fusion Sabit Listeleri](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
