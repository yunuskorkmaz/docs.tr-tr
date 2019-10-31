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
ms.openlocfilehash: 8e5583acfe338c185200c0b8e41b7d6e051fa146
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131351"
---
# <a name="icordebugregisterset2getregisters-method"></a>ICorDebugRegisterSet2::GetRegisters Yöntemi
Verilen bit maskesi tarafından belirtilen her kaydın değerini alır (kodun Şu anda yürütüldüğü platform için).  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `maskCount`  
 'ndaki `mask` dizisinin bayt cinsinden boyutu.  
  
 `mask`  
 'ndaki Her bitin bir kayda karşılık gelen bir bayt dizisi. Bit 1 ise, karşılık gelen yazmaç değeri alınacaktır.  
  
 `regCount`  
 'ndaki Alınacak kayıt değerlerinin sayısı.  
  
 `regBuffer`  
 dışı Her biri bir yazmaç değerini alan `CORDB_REGISTER` nesnelerden oluşan bir dizi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetRegisters` yöntemi, maske tarafından belirtilen yazmaçlardan bir değer dizisi döndürür. Dizi, maske biti ayarlanmamış yazmaçların değerlerini içermiyor. Bu nedenle, `regBuffer` dizisinin boyutu maskenin içindeki 1 sayısına eşit olmalıdır. `regCount` değeri maskenin gösterdiği kayıt sayısı için çok küçükse, daha yüksek numaralandırılmış yazmaçların değerleri kümeden kesilir. `regCount` çok büyükse kullanılmayan `regBuffer` öğeleri değiştirilmemiş olur.  
  
 Maske tarafından kullanılamayan bir kayıt belirtilmişse, bu kayıt için belirsiz bir değer döndürülür.  
  
 `ICorDebugRegisterSet2::GetRegisters` yöntemi 64 taneden fazla kayıt olan platformlar için gereklidir. Örneğin, ıA64 128 genel amaçlı kayıt kayıtları ve 128 kayan nokta kayıtları içerir, bu nedenle bit maskesinde en fazla 64 bit olmalıdır.  
  
 64 ' den fazla kayıt yoksa, x86 gibi platformlarda olduğu gibi `GetRegisters` yöntemi aslında yalnızca `mask` bayt dizisindeki baytları bir `ULONG64` içine çevirir ve sonra [ICorDebugRegisterSet:: Getyazmaçları](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) metodunu çağırır `ULONG64` maskesini alır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRegisterSet2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
