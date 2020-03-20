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
ms.openlocfilehash: e3cdb648397ca4f4aa2326e4f2349a5a14c3edcc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178300"
---
# <a name="assemblycomparisonresult-enumeration"></a>AssemblyComparisonResult Numaralandırması
[CompareAssemblyIdentity](compareassemblyidentity-function.md) işlevi tarafından belirlenen iki derleme kimliğinin eşdeğerliğini gösterir.  
  
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
|`ACR_EquivalentFullMatch`|Karşılaştırma daki tüm montaj alanlarının eşleşdiğini gösterir.|  
|`ACR_EquivalentFXUnified`|Derlemelerin .NET Framework sürüm 2.0'daki derleme sürüm numaralarının ortak dil çalışma zamanı sürümüne (CLR) göre eşdeğer kabul edilir olduğunu gösterir.|  
|`ACR_EquivalentPartialFXUnified`|.NET Framework 2.0'daki derleme sürüm numaralarının CLR birleşmesi temel alınca derlemelerin kısmi eşleşmesini gösterir.|  
|`ACR_EquivalentPartialMatch`|Derlemelerin kısmi eşleşmesini gösterir.|  
|`ACR_EquivalentPartialUnified`|Sürüm numaralarının eski birleşmesi temel alınarak derlemelerin kısmi eşleşmesini gösterir.|  
|`ACR_EquivalentPartialWeakNamed`|Yalnızca adlandırılmış derlemelerin kısmi eşleşmesini gösterir.|  
|`ACR_EquivalentUnified`|Derlemelerin.NET Framework'ün eski sürümlerinde sürüm numaralarının CLR birleşmesi temel alınarak eşdeğer kabul edilir olduğunu gösterir.|  
|`ACR_EquivalentWeakNamed`|Sürüm numaraları yoksayıldı iki basit adlandırılmış derlemeler arasındaki eşleşmeyi gösterir.|  
|`ACR_NonEquivalent`|İki derleme arasında eşleşme oluşmadığını gösterir.|  
|`ACR_NonEquivalentPartialVersion`|İki derlemenin, yalnızca kısmen eşleşen sürüm numaraları dışında eşleşin.|  
|`ACR_NonEquivalentVersion`|İki derlemenin, eşleşmeyan sürüm numaraları dışında eşleşin.|  
|`ACR_Unknown`|Denklik nedeninin bilinmediğini gösterir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** Fusion.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CompareAssemblyIdentity İşlevi](compareassemblyidentity-function.md)
- [Fusion Sabit Listeleri](fusion-enumerations.md)
