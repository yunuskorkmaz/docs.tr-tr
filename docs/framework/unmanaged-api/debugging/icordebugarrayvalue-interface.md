---
title: ICorDebugArrayValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
ms.openlocfilehash: 0944f3379c18cba56ab65fe40a5b94a64d8a8991
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778197"
---
# <a name="icordebugarrayvalue-interface"></a>ICorDebugArrayValue Arabirimi

Tek boyutlu veya çok boyutlu bir diziyi temsil eden ICorDebugHeapValue öğesinin alt sınıfı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetBaseIndicies Yöntemi](icordebugarrayvalue-getbaseindicies-method.md)|Dizideki her boyutun temel dizinini alır.|  
|[GetCount Yöntemi](icordebugarrayvalue-getcount-method.md)|Dizideki toplam öğe sayısını alır.|  
|[GetDimensions Yöntemi](icordebugarrayvalue-getdimensions-method.md)|Dizinin boyutlarını alır.|  
|[GetElement Yöntemi](icordebugarrayvalue-getelement-method.md)|Dizide verilen öğeyi temsil eden bir değer alır.|  
|[GetElementAtPosition Yöntemi](icordebugarrayvalue-getelementatposition-method.md)|Diziyi sıfır tabanlı, tek boyutlu bir dizi olarak düşünerek belirtilen konumdaki öğeyi alır.|  
|[GetElementType Yöntemi](icordebugarrayvalue-getelementtype-method.md)|Dizideki öğelerin basit türünü alır.|  
|[GetRank Yöntemi](icordebugarrayvalue-getrank-method.md)|Dizideki boyut sayısını alır.|  
|[HasBaseIndicies Yöntemi](icordebugarrayvalue-hasbaseindicies-method.md)|Dizinin temel dizinlere sahip olup olmadığını belirler.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugArrayValue` hem tek boyutlu hem çok boyutlu dizileri destekler.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
