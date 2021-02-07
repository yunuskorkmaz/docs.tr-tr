---
description: 'Daha fazla bilgi edinin: ICorDebugProcess5:: GetArrayLayout yöntemi'
title: ICorDebugProcess5::GetArrayLayout Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetArrayLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetArrayLayout
helpviewer_keywords:
- ICorDebugProcess5::GetArrayLayout method [.NET Framework debugging]
- GetArrayLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 9a7393b9-9735-43c6-8616-afb103c432fd
topic_type:
- apiref
ms.openlocfilehash: c82b296da3a367f5307240225a560af67a56c866
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746405"
---
# <a name="icordebugprocess5getarraylayout-method"></a>ICorDebugProcess5::GetArrayLayout Yöntemi

Dizi türlerinin yerleşimi hakkında bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a>Parametreler  

 `id`  
 'ndaki Düzeni istenen diziyi belirten [COR_TYPEID](cor-typeid-structure.md) belirteç.  
  
 `pLayout`  
 dışı Dizinin, bellekteki düzeni hakkında bilgi içeren [COR_ARRAY_LAYOUT](cor-array-layout-structure.md) yapısına yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess5 Arabirimi](icordebugprocess5-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
