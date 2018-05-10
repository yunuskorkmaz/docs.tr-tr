---
title: ICorDebugRegisterSet2::GetRegisters Metodu
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
ms.openlocfilehash: aca83a66520531074f376a47a7f2994cda237f9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugregisterset2getregisters-method"></a>ICorDebugRegisterSet2::GetRegisters Metodu
Her kasa değerini alır (üzerinde kod şu anda Yürütülüyor platformu için) tarafından verilen bir bit maskesi belirtildi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `maskCount`  
 [in] Bayt olarak boyutu, `mask` dizi.  
  
 `mask`  
 [in] Bir bayt dizisi, bir kasaya her biti karşılık gelir. Bit 1 ise, karşılık gelen kasanın değer alınır.  
  
 `regCount`  
 [in] Alınacak kayıt değerlerinin sayısı.  
  
 `regBuffer`  
 [out] Bir dizi `CORDB_REGISTER` nesneleri, her biri bir kayıt değeri alır.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetRegisters` Yöntemi maskesi tarafından belirtilen kayıtlardaki değerler dizisi döndürür. Dizi maskesi biti ayarlanmamış yazmaçların değerleri içermiyor. Bu nedenle, boyutu `regBuffer` dizi maskesinde 1 sayısına eşit olmalıdır. Varsa değerini `regCount` maskesiyle, değerleri daha yüksek numaralı yazmaçların belirtilen kayıtları sayısını kümesinden kesilecek için çok küçük. Varsa `regCount` çok büyük kullanılmayan `regBuffer` öğeleri değiştirilmemiş olacaktır.  
  
 Kullanılamayan bir kaydı maskesiyle belirtilirse, bu kayıt için belirsiz bir değeri döndürülür.  
  
 `ICorDebugRegisterSet2::GetRegisters` Yöntemi 64 taneden fazla yazmaçlar platformlar için gereklidir. Örneğin, en fazla 64-bit bit maskesi gerekir böylece IA64 128 genel amaçlı kaydeder ve 128 kayan nokta kayıtları vardır.  
  
 X86 gibi platformlardaki olduğu gibi 64 taneden fazla kayıtları yoksa `GetRegisters` yöntemi gerçekte yalnızca bayt cinsinden çevirir `mask` Bayt dizisine bir `ULONG64` ve çağırır [Icordebugregisterset:: GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) geçen yöntemi `ULONG64` maske.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugRegisterSet2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [ICorDebugRegisterSet Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
