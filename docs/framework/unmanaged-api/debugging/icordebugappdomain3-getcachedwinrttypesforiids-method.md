---
title: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type:
- apiref
ms.openlocfilehash: f8e92ec4f813e8810273a1514298d0739a3d2406
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179058"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Yöntemi
Arabirim tanımlayıcılarını temel alan bir uygulama etki alanında önbelleğe alınmış Windows Runtime türleri için bir sayı eritici alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cReqTypes`  
 [içinde] Gerekli türlerin sayısı.  
  
 `iidsToResolve`  
 [içinde] Alınacak Windows Runtime türlerinin yönetilen gösterimlerine karşılık gelen arabirim tanımlayıcılarını içeren bir diziiçin işaretçi.  
  
 `ppTypesEnum`  
 [çıkış] Alınan Windows Runtime türlerinin önbelleğe alınmış yönetilen gösterimlerinin numaralandırılmasına olanak tanıyan "ICorDebugTypeEnum" arabirimi `iidsToResolve`nesnesinin adresine işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntem belirli bir arabirim tanımlayıcısı için bilgi almak için başarısız olursa, "ICorDebugTypeEnum" koleksiyonunda `ELEMENT_TYPE_END` karşılık gelen giriş veri alma sorunları `ELEMENT_TYPE_VOID` nedeniyle hatalar için bir tür veya bilinmeyen arabirim tanımlayıcıları için olacaktır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Windows Çalışma Zamanı  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugAppDomain3 Arabirimi](icordebugappdomain3-interface.md)
