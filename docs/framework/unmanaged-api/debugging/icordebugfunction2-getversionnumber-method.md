---
title: ICorDebugFunction2::GetVersionNumber Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cc9c2af62184c83857b82445941f6087a05c2c3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497177"
---
# <a name="icordebugfunction2getversionnumber-method"></a>ICorDebugFunction2::GetVersionNumber Yöntemi
Bu işlev Düzenle ve devam et sürümünü alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pnVersion`  
 [out] Sürüm numarasını bu Icordebugfunction2 nesnesi tarafından temsil edilen işlev bir tamsayı işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Çalışma zamanı, her modül için hata ayıklama oturumu sırasında meydana gelen düzenlemeleri sayısını izler. Bir işlev sürüm numarasını biridir işlevi sunulan düzenleme sayısından daha fazla. İşlevin özgün sürüm 1 sürümüdür. Sayı, her bir modül için artırılır [Icordebugmodule2::applychanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) üzerinde bu modül çağrılır. Bu nedenle, ilk ve üçüncü aramasında bir işlev gövdesini değiştirildiyse `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` sürüm 1, 2 veya 4: Bu işlev, ancak sürüm 3 döndürebilir. (İşlev sürüm 3 olması.)  
  
 Sürüm numarası, her modül için ayrı ayrı izlenir. Modül 1 ve 2 modül yok dört düzenlemeler yapabilirsiniz, bu nedenle, sonraki düzenlemeniz modülü 1 sürüm numarası 6 modülü 1 düzenlenen tüm işlevler için atar. Aynı dokunmalar Modül 2 düzenlerseniz, Modül 2 işlevleri sürüm numarası 2 olarak alırsınız.  
  
 Sürüm numarası elde tarafından `GetVersionNumber` yöntemi tarafından alınan daha düşük [ICorDebugFunction::getcurrentversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).  
  
 [Icordebugcode::getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) yöntemi olarak aynı işlemi yapar `ICorDebugFunction2::GetVersionNumber`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
