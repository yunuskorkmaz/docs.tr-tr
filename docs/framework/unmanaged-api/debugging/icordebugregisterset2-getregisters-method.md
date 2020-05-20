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
ms.openlocfilehash: 71b9d59621efb547713cb4a6c9df7a7142f4a677
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615195"
---
# <a name="icordebugregisterset2getregisters-method"></a>ICorDebugRegisterSet2:: Getyazmaçları yöntemi

Verilen bit maskesi tarafından belirtilen her kaydın değerini alır (kodun Şu anda yürütüldüğü platform için).  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Dizinin bayt cinsinden boyutu `mask` .  
  
 `mask`  
 'ndaki Her bitin bir kayda karşılık gelen bir bayt dizisi. Bit 1 ise, karşılık gelen yazmaç değeri alınacaktır.  
  
 `regCount`  
 'ndaki Alınacak kayıt değerlerinin sayısı.  
  
 `regBuffer`  
 dışı `CORDB_REGISTER`Her biri bir yazmaç değerini alan bir nesne dizisi.  
  
## <a name="remarks"></a>Açıklamalar

 `GetRegisters`Yöntemi, maske tarafından belirtilen yazmaçlardan bir değer dizisi döndürür. Dizi, maske biti ayarlanmamış yazmaçların değerlerini içermiyor. Bu nedenle, `regBuffer` dizinin boyutu maskenin içindeki 1 sayısına eşit olmalıdır. Değeri, `regCount` maske tarafından belirtilen kayıt sayısı için çok küçükse, daha yüksek numaralandırılmış yazmaçların değerleri kümeden kesilir. `regCount`Çok büyükse, kullanılmamış `regBuffer` öğeler değiştirilmemiş olur.  
  
 Maske tarafından kullanılamayan bir kayıt belirtilmişse, bu kayıt için belirsiz bir değer döndürülür.  
  
 `ICorDebugRegisterSet2::GetRegisters`Yöntemi 64 'den fazla kaydı olan platformlar için gereklidir. Örneğin, ıA64 128 genel amaçlı kayıt kayıtları ve 128 kayan nokta kayıtları içerir, bu nedenle bit maskesinde en fazla 64 bit olmalıdır.  
  
 64 ' den fazla kayıt yoksa, x86 gibi platformlarda olduğu gibi, `GetRegisters` yöntemi yalnızca `mask` bayt dizisindeki baytları a 'ya çevirir `ULONG64` ve ardından maskeyi alan [ICorDebugRegisterSet:: getyazmaçları](icordebugregisterset-getregisters-method.md) yöntemini çağırır `ULONG64` .  
  
## <a name="requirements"></a>Gereksinimler

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRegisterSet2 Arabirimi](icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet Arabirimi](icordebugregisterset-interface.md)
