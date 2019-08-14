---
title: ICorProfilerInfo9::GetILToNativeMapping3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetILToNativeMapping3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 46ceef43806fda9956797935c5eeec61f865dc6e
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973686"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a>ICorProfilerInfo9:: GetILToNativeMapping3 yöntemi
  
 Yerel kod başlangıç adresi verildiğinde, kodun bu jderlenen sürümü için yerel-Il eşleme bilgilerini döndürür.   
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```  
  
#### <a name="parameters"></a>Parametreler  
 `pNativeCodeStartAddress` \
 'ndaki Yerel bir işlevin başlangıcına yönelik bir işaretçi.

 `cMap` \
 'ndaki `map` Dizinin en büyük boyutu. 

 `pcMap` \
 dışı Kullanılabilir COR_DEBUG_IL_TO_NATIVE_MAP yapılarının toplam sayısı.

 `map` \
 dışı Her biri uzaklıkları belirten bir [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) yapıları dizisi. Yöntem döndüğünde, `map` yapıların`COR_DEBUG_IL_TO_NATIVE_MAP` bazılarını veya tümünü içerir. `GetILToNativeMapping3`

## <a name="remarks"></a>Açıklamalar  
 Katmanlı derleme etkinleştirildiğinde, bir yöntem birden fazla yerel kod gövdesine sahip olabilir. [ICorProfilerInfo9:: Getnativecodestartaaddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md) tüm yerel kod gövdelerinin başlangıç adreslerini döndürür.

## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
  
 **Üst bilgi** CorProf. IDL, CorProf. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)] 
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo9 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)

