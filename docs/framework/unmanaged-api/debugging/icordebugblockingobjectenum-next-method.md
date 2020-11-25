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
ms.openlocfilehash: 232068a5fee8f7bd3dfbddf4d9452e80d6fd6170
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719196"
---
# <a name="icordebugblockingobjectenumnext-method"></a>ICorDebugBlockingObjectEnum::Next Yöntemi

Geçerli konumdan başlayarak Numaralandırmadaki belirtilen [CorDebugBlockingObject](cordebugblockingobject-structure.md) nesnelerinin sayısını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
|S_FALSE|`pceltFetched` eşit değildir `celt` .|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu yöntem tipik bir COM numaralandırıcısı gibi çalışır.  
  
 Giriş dizisi değerleri en az boyutta olmalıdır `celt` . Dizi, `celt` Numaralandırmadaki bir sonraki değerle veya daha az kalırsa kalan tüm değerlerle doldurulur `celt` . Bu yöntem döndüğünde, `pceltFetched` alınan değer sayısıyla doldurulur. `values`Geçersiz işaretçiler içeriyorsa veya daha küçük olan bir arabelleğe işaret ediyorsa ya da `celt` `pceltFetched` geçersiz bir işaretçisiyse, sonuç tanımsızdır.  
  
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
