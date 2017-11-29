---
title: "AssemblyComparisonResult Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyComparisonResult
api_location: fusion.dll
api_type: COM
f1_keywords: AssemblyComparisonResult
helpviewer_keywords: AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75c53e750ad031ccec944625be130547404767bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="assemblycomparisonresult-enumeration"></a>AssemblyComparisonResult Numaralandırması
Tarafından belirlenen iki derleme kimlikleri, eşdeğer gösterir [Compareassemblyıdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) işlevi.  
  
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
|`ACR_EquivalentFullMatch`|Tüm derleme karşılaştırma eşlemesinde alanlarını gösterir.|  
|`ACR_EquivalentFXUnified`|Derlemeleri derleme sürüm numaraları için .NET Framework sürüm 2.0, ortak dil çalışma zamanı (CLR) sürüm Birleştirici göre eşdeğer olarak değerlendiriliyor olduğunu gösterir.|  
|`ACR_EquivalentPartialFXUnified`|.NET Framework 2.0, derleme sürüm numaralarının CLR Birleştirici göre derlemelerin kısmi eşleşme gösterir.|  
|`ACR_EquivalentPartialMatch`|Kısmi eşleşme derlemelerin gösterir.|  
|`ACR_EquivalentPartialUnified`|Sürüm numaraları eski Birleştirici üzerinde temel derlemelerin kısmi eşleşme gösterir.|  
|`ACR_EquivalentPartialWeakNamed`|Yalnızca adlandırılmış derlemelerin kısmi eşleşme gösterir.|  
|`ACR_EquivalentUnified`|Derlemeleri eski sürümlerinde, .NET Framework sürüm numaralarının CLR Birleştirici göre eşdeğer olarak değerlendiriliyor olduğunu gösterir.|  
|`ACR_EquivalentWeakNamed`|Sürüm numaralarını yoksayıldı iki yalnızca adlandırılmış derlemeler arasında bir eşleşme gösterir.|  
|`ACR_NonEquivalent`|Eşleşme iki derlemeler arasında oluştuğunu gösterir.|  
|`ACR_NonEquivalentPartialVersion`|İki derleme yalnızca kısmen eşleşen bunların sürüm numaralarını dışında eşleştiğini gösterir.|  
|`ACR_NonEquivalentVersion`|İki derleme eşleşmiyor bunların sürüm numaralarını dışında eşleştiğini gösterir.|  
|`ACR_Unknown`|Denkliği olmayan nedeni bilinmiyor gösterir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Fusion.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Compareassemblyıdentity işlevi](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 [Fusion numaralandırmaları](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
