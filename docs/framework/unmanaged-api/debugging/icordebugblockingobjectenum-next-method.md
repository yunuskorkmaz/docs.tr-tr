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
ms.openlocfilehash: 0ef49d2d833841eac62b2b964a0fdc902b4fb6a9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894767"
---
# <a name="icordebugblockingobjectenumnext-method"></a>ICorDebugBlockingObjectEnum::Next Yöntemi
Geçerli konumdan başlayarak Numaralandırmadaki belirtilen [CorDebugBlockingObject](cordebugblockingobject-structure.md) nesnelerinin sayısını alır.  
  
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
 dışı [CorDebugBlockingObject](cordebugblockingobject-structure.md) nesnelerine yönelik işaretçiler dizisi.  
  
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
  
 Giriş dizisi değerleri en az boyutta `celt`olmalıdır. Dizi, Numaralandırmadaki bir sonraki `celt` değerle veya daha az `celt` kalırsa kalan tüm değerlerle doldurulur. Bu yöntem döndüğünde, `pceltFetched` alınan değer sayısıyla doldurulur. Geçersiz `values` işaretçiler içeriyorsa veya daha küçük `celt`olan bir arabelleğe işaret ediyorsa ya `pceltFetched` da geçersiz bir işaretçisiyse, sonuç tanımsızdır.  
  
> [!NOTE]
> [CorDebugBlockingObject](cordebugblockingobject-structure.md) yapısının serbest bırakılması gerekmez, ancak Içindeki "ICorDebugValue" arabiriminin serbest bırakılması gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugDataTarget Arabirimi](icordebugdatatarget-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
