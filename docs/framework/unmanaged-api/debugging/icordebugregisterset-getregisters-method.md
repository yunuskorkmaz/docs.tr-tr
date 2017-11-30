---
title: ICorDebugRegisterSet::GetRegisters Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet.GetRegisters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7edae3d3be1bcfb80b7a1e432fd5f25e119f078f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters Metodu
Her kayıt değerini (kod şu anda yürütülmekte bilgisayarda) alır bit maskesi kullanılarak belirtilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `mask`  
 [in] Bir bit maskesi alınacak değerler hangi kaydı belirtir. Her bitin bir kasaya karşılık gelir. Bir bit birine ayarlanırsa, kasanın değer alınır; Aksi takdirde kasanın değeri alınamadı.  
  
 `regCount`  
 [in] Alınacak kayıt değerlerinin sayısı.  
  
 `regBuffer`  
 [out] Bir dizi `CORDB_REGISTER` nesneleri, her biri bir kayıt değeri alır.  
  
## <a name="remarks"></a>Açıklamalar  
 Dizinin boyutu bir bit maskesi için bitler sayısına eşit olmalıdır. `regCount` Parametresi kayıt değerlerini alacak arabellek öğe sayısını belirtir. Varsa `regCount` değeri maskesiyle belirtilen yazmaçlar sayısı için çok küçük, daha yüksek numaralı yazmaçlar kümesinden kesilir. Varsa `regCount` değer çok büyük, kullanılmayan `regBuffer` öğeleri değiştirilmemiş olacaktır.  
  
 Bit maskesi kullanılamıyor, bir kayıt belirtiyorsa `GetRegisters` konusu kasaya belirsiz bir değer döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icordebugregisterset arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [Icordebugregisterset2 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
