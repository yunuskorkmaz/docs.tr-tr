---
description: ': Icordebugmergedassemblyrecord:: GetIndex yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugmergedassemblyrecord:: GetIndex yöntemi'
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
ms.openlocfilehash: f3a51c5ed5edacc9678c965ac385d0969e2ee8a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801117"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a>Icordebugmergedassemblyrecord:: GetIndex yöntemi

Derlemenin önek dizinini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pIndex`  
 dışı Ön ek dizinine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Ön ek dizini, birleştirilmiş meta veri türü adlarında ad çakışmalarını engellemek için kullanılır.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMergedAssemblyRecord Arabirimi](icordebugmergedassemblyrecord-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
