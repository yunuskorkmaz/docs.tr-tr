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
ms.openlocfilehash: 1e94e4da0eea06ce9cc0110002b1def9e4dd4989
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939152"
---
# <a name="icordebugblockingobjectenumnext-method"></a>ICorDebugBlockingObjectEnum::Next Yöntemi
Geçerli konumdan başlayarak Numaralandırmadaki belirtilen [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) nesnelerinin sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
## <a name="parameters"></a>Parametreler  
 `celt`  
 'ndaki Alınacak nesne sayısı.  
  
 `values`  
 dışı [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) nesnelerine yönelik işaretçiler dizisi.  
  
 `pceltFetched`  
 dışı Alınan nesne sayısına yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki özel HRESULT'ları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|S_FALSE|`pceltFetched`eşit `celt`değildir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem tipik bir COM numaralandırıcısı gibi çalışır.  
  
 Giriş dizisi değerleri en az boyutta `celt`olmalıdır. Dizi, Numaralandırmadaki bir sonraki `celt` değerle veya `celt` daha az kalırsa kalan tüm değerlerle doldurulur. Bu yöntem döndüğünde, `pceltFetched` alınan değer sayısıyla doldurulur. Geçersiz işaretçiler `celt`içeriyorsaveyadaha küçük olan bir arabelleğe işaret ediyorsa ya `pceltFetched` da geçersiz bir işaretçisiyse, sonuç tanımsızdır. `values`  
  
> [!NOTE]
> [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapısının serbest bırakılması gerekmez, ancak Içindeki "ICorDebugValue" arabiriminin serbest bırakılması gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugDataTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
