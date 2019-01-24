---
title: ICorDebugProcess5::GetTypeLayout Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f12398a2423e7e0081556dbdb279e4a2f23c3af7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723426"
---
# <a name="icordebugprocess5gettypelayout-method"></a>ICorDebugProcess5::GetTypeLayout Metodu
Kendi tür tanımlayıcısına göre bellekte bir nesne düzeni bilgilerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `id`  
 [in] A [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) düzeni istenen türünü belirten bir belirteç.  
  
 `pLayout`  
 [out] Bir işaretçi bir [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) nesnesinin bellek düzeni hakkındaki bilgileri içeren yapısı.  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugProcess5::GetTypeLayout` Yöntemi temel bir nesne hakkında bilgi sağlar, [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), diğer bir sayı tarafından döndürülen [Icordebugprocess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) yöntemleri. Bilgileri tarafından sağlanan bir [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) yöntemi tarafından doldurulur yapısı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [COR_TYPE_LAYOUT Yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)
- [ICorDebugProcess5 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
