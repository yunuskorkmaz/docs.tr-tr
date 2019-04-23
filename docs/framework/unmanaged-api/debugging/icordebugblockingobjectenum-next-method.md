---
title: ICorDebugBlockingObjectEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
- ICorDebugBlockingObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 0121753f-ebea-48d0-aeb2-ed7fda76dc60
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 889c3bb2d5e0cd1feb9e592e667d47dedd4ede36
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59171151"
---
# <a name="icordebugblockingobjectenumnext-method"></a>ICorDebugBlockingObjectEnum::Next Yöntemi
Belirtilen sayıda alır [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) nesneleri geçerli konumunda başlayan sabit listesi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
## <a name="parameters"></a>Parametreler  
 `celt`  
 [in] Alınacak nesne sayısı.  
  
 `values`  
 [out] Bir işaretçiler dizisi [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) nesneleri.  
  
 `pceltFetched`  
 [out] Alınan nesne sayısı için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki özel HRESULT'ları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|S_FALSE|`pceltFetched` eşit değildir `celt`.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tipik bir COM Numaralandırıcı gibi bu yöntem çalışır.  
  
 Giriş dizisinin en az olmalıdır boyutunun `celt`. Dizi ile birlikte sonraki doldurulur `celt` değerleri sabit listesi veya tüm kalan değerler ile az olursa `celt` kalır. Bu yöntem döndürüldüğünde, `pceltFetched` alınan değer sayısı ile doldurulur. Varsa `values` geçersiz işaretçi içerir ya da daha küçük olan bir arabellek işaret `celt`, veya `pceltFetched` geçersiz bir işaretçi sonuç tanımsızdır.  
  
> [!NOTE]
>  Ancak [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapısı yayımlanması gerekmez, içindeki "ICorDebugValue" arabirimi serbest bırakılması gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugDataTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
