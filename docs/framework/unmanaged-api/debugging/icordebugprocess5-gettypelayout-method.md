---
description: 'Daha fazla bilgi edinin: ICorDebugProcess5:: GetTypeLayout yöntemi'
title: ICorDebugProcess5::GetTypeLayout Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeLayout
helpviewer_keywords:
- ICorDebugProcess5::GetTypeLayout method [.NET Framework debugging]
- GetTypeLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: bd62f5d1-e874-41f1-81e5-a29a7572c15d
topic_type:
- apiref
ms.openlocfilehash: d4496fa832b048dfc0bbe792aeb8fdcd460f5158
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746288"
---
# <a name="icordebugprocess5gettypelayout-method"></a>ICorDebugProcess5::GetTypeLayout Yöntemi

Bir nesnenin tür tanımlayıcısına göre bellek içindeki düzeni hakkında bilgi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a>Parametreler  

 `id`  
 'ndaki Düzeni istenen türü belirten [COR_TYPEID](cor-typeid-structure.md) belirteç.  
  
 `pLayout`  
 dışı Bellekteki nesnenin düzeni hakkında bilgi içeren [cor_type_layout](cor-type-layout-structure.md) yapısına yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 `ICorDebugProcess5::GetTypeLayout`Yöntemi, bir dizi diğer [ICorDebugProcess5](icordebugprocess5-interface.md) yöntemi tarafından döndürülen [COR_TYPEID](cor-typeid-structure.md)temel alınarak bir nesne hakkında bilgiler sağlar. Bilgiler, yöntemi tarafından doldurulan bir [cor_type_layout](cor-type-layout-structure.md) yapısı tarafından sağlanır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [COR_TYPE_LAYOUT Yapısı](cor-type-layout-structure.md)
- [ICorDebugProcess5 Arabirimi](icordebugprocess5-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
