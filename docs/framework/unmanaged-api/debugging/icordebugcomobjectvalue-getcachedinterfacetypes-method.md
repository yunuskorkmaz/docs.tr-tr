---
title: ICorDebugComObjectValue::GetCachedInterfaceTypes Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
helpviewer_keywords:
- GetCachedInterface method, ICorDebugComObjectValue interface [.NET Framework debugging]
- ICorDebugComObjectValue::GetCachedInterface method [.NET Framework debugging]
ms.assetid: d492284f-d3c5-4614-adb8-d718d5042500
topic_type:
- apiref
ms.openlocfilehash: f5f0f11683043f1c287dd3ca3071830bcfb46502
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677563"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a>ICorDebugComObjectValue::GetCachedInterfaceTypes Metodu

Geçerli nesnenin atanmış veya olarak kullanıldığı arabirim türleri için bir Numaralandırıcı sağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a>Parametreler  

 `bIInspectableOnly`  
 'ndaki Yöntemin yalnızca Windows Çalışma Zamanı arabirimleri ( `IInspectable` arabirimler) veya çalışma zamanı çağrılabilir sarmalayıcı (RCW) tarafından önbelleğe alınmış tüm com arabirimlerini döndürüp döndürmediğini belirten bir değer.  
  
 `ppInterfacesEnum`  
 dışı Öğesine göre filtrelenmiş önbelleğe alınmış arabirim türlerini temsil eden ICorDebugType nesnelerine erişim sağlayan ICorDebugTypeEnum Numaralandırıcı adresine yönelik bir işaretçi `bIInspectableOnly` .  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugComObjectValue Arabirimi](icordebugcomobjectvalue-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
