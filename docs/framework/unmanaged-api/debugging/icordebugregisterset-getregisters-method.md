---
title: ICorDebugRegisterSet::GetRegisters Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
ms.openlocfilehash: 32e899622b9c649a08e3bca1b6645f70dcbcbb19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178540"
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters Metodu
Bit maskesi tarafından belirtilen her kaydın (şu anda kodu yürüten bilgisayarda) değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `mask`  
 [içinde] Hangi kayıt değerlerinin alıneceğini belirten bir bit maskesi. Her bit bir kayda karşılık gelir. Bir bit bire ayarlanırsa, kaydın değeri alınır; aksi takdirde, kaydın değeri alınmaz.  
  
 `regCount`  
 [içinde] Alınacak kayıt değerlerinin sayısı.  
  
 `regBuffer`  
 [çıkış] Her biri `CORDB_REGISTER` bir kayıt değeri alan bir nesne dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Dizinin boyutu bit maskesinde bire ayarlanmış bit sayısına eşit olmalıdır. Parametre, `regCount` arabellekte kayıt değerlerini alacak öğe sayısını belirtir. `regCount` Değer maske tarafından belirtilen kayıt sayısı için çok küçükse, daha yüksek numaralanmış kayıtlar kümeden kesilir. Değer `regCount` çok büyükse, kullanılmayan `regBuffer` öğeler değiştirilmez.  
  
 Bit maskesi kullanılamayan bir kayıt belirtirse, `GetRegisters` bu kayıt için belirsiz bir değer verir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRegisterSet Arabirimi](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 Arabirimi](icordebugregisterset2-interface.md)
