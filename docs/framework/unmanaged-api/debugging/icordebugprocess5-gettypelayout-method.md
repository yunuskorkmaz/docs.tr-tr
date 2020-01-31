---
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
ms.openlocfilehash: 306d881c05c2fcdb15a53a439bfce6eff3afffa8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792308"
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
 `ICorDebugProcess5::GetTypeLayout` yöntemi, bir dizi diğer [ICorDebugProcess5](icordebugprocess5-interface.md) yöntemi tarafından döndürülen [COR_TYPEID](cor-typeid-structure.md)temel alınarak bir nesne hakkında bilgi sağlar. Bilgiler, yöntemi tarafından doldurulan bir [cor_type_layout](cor-type-layout-structure.md) yapısı tarafından sağlanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [COR_TYPE_LAYOUT Yapısı](cor-type-layout-structure.md)
- [ICorDebugProcess5 Arabirimi](icordebugprocess5-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
