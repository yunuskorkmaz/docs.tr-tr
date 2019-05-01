---
title: ICorDebugRegisterSet2::GetRegisters Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2dc1064656f3493db78d858cf1e86db0cb83d6c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782869"
---
# <a name="icordebugregisterset2getregisters-method"></a>ICorDebugRegisterSet2::GetRegisters Yöntemi
Her kaydın değerini alır (üzerinde kod şu anda Yürütülüyor platform için) belirli bir bit maskesi kullanılarak belirtilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `maskCount`  
 [in] Bayt cinsinden boyutu, `mask` dizisi.  
  
 `mask`  
 [in] Bir bayt dizisi, bir kasaya her bitini karşılık gelir. 1 bit ise karşılık gelen kasanın değer alınır.  
  
 `regCount`  
 [in] YAZMAÇ değerlerini alınacak sayısı.  
  
 `regBuffer`  
 [out] Bir dizi `CORDB_REGISTER` nesneleri, her biri bir kayıt değeri alır.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetRegisters` Yöntemi maskesi tarafından belirtilen kayıtlardaki değerler dizisi döndürür. Dizi maskesi biti ayarlanmamış yazmaçların değerleri içermiyor. Bu nedenle, boyutu `regBuffer` dizi maskesi 1 sayıya eşit olmalıdır. Varsa değerini `regCount` sayı değerleri daha yüksek numaralı yazmaçların maskesi tarafından belirtilen yazmaçların kümesinden kesilecek için yeterli büyüklükte değil. Varsa `regCount` çok büyük kullanılmayan `regBuffer` öğeleri değiştirilmemiş olacaktır.  
  
 Kullanılamayan bir kaydı maskesiyle belirtilirse, bu kasa için belirsiz bir değer döndürülür.  
  
 `ICorDebugRegisterSet2::GetRegisters` Yöntemi 64'den fazla kayda sahip platformları için gereklidir. Örneğin, en fazla 64-bit bit maskesi erişebilmeleri IA64 128 genel amaçlı kaydeder ve 128 kayan nokta kayıtlarını vardır.  
  
 X86 gibi platformlarda olduğu gibi 64'den fazla kayda sahip değilseniz `GetRegisters` yöntemi, bayt cinsinden aslında çevirir `mask` Bayt dizisine bir `ULONG64` ve [Icordebugregisterset:: GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) gereken yöntemini `ULONG64` maskesi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRegisterSet2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
