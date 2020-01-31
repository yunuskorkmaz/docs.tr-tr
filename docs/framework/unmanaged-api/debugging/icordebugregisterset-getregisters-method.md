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
ms.openlocfilehash: 737993ac80b26d490915af3e97fd6a9552246aee
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792113"
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters Metodu
Bit maskesi tarafından belirtilen her kaydın (Şu anda kod yürüten bilgisayardaki) değerini alır.  
  
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
 'ndaki Hangi yazmaç değerlerinin alınacağını belirten bir bit maskesi. Her bit bir kayda karşılık gelir. Bir bit olarak ayarlandıysa, kaydın değeri alınır; Aksi takdirde, kaydın değeri alınmadı.  
  
 `regCount`  
 'ndaki Alınacak kayıt değerlerinin sayısı.  
  
 `regBuffer`  
 dışı Her biri bir yazmaç değeri alan `CORDB_REGISTER` nesnelerden oluşan bir dizi.  
  
## <a name="remarks"></a>Açıklamalar  
 Dizinin boyutu, bit maskesinde bir tane olarak ayarlanan bit sayısına eşit olmalıdır. `regCount` parametresi, kayıt değerlerini alacak arabellekteki öğelerin sayısını belirtir. `regCount` değeri maskenin gösterdiği kayıt sayısı için çok küçük ise, daha yüksek numaralandırılmış Yazmaçları kümeden kesilecek. `regCount` değeri çok büyükse, kullanılmamış `regBuffer` öğeleri değiştirilmemiş olur.  
  
 Bit maskesi kullanılamayan bir kaydı belirtirse `GetRegisters`, bu kayıt için belirsiz bir değer döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRegisterSet Arabirimi](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 Arabirimi](icordebugregisterset2-interface.md)
