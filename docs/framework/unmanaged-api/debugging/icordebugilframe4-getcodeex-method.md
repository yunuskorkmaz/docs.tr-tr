---
title: ICorDebugILFrame4::GetCodeEx Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
ms.openlocfilehash: ef2e4bc0caddd6b13c8dbe8edb59e0673519421b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178790"
---
# <a name="icordebugilframe4getcodeex-method"></a>ICorDebugILFrame4::GetCodeEx Yöntemi
[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Bu yığın çerçevesinin yürütüldettiği koda bir işaretçi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `flags`  
 [içinde] Profilcinin ReJIT isteği tarafından tanımlanan ara dilin (IL) çerçeveye dahil edilip edilmeyeceğini belirten bir [ILCodeKind](ilcodekind-enumeration.md) numaralandırma üyesi.  
  
 `ppCode`  
 [çıkış] Bu yığın çerçevesinin yürütüldettiği kodu temsil eden bir "ICorDebugCode" nesnesinin adresine işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, profilcinin ReJIT isteği tarafından tanımlanan koda isteğe bağlı olarak erişmesi dışında [ICorDebugFrame::GetCode](icordebugframe-getcode-method.md) yöntemine benzer. Bu yöntemi `flags` bir değerle çağırmak [GetCode'u](icordebugframe-getcode-method.md)aramaya `ILCODE_ORIGINAL_IL` eşdeğerdir; yöntem işletilmişse, IL'sine erişilemez. `ILCODE_REJIT_IL`hata ayıklayıcının profilcinin ReJIT isteği tarafından tanımlanan IL'ye erişmesine izin verir. IL enstrümante değilse, `ppCode` **null**ise , ve `S_OK`yöntem döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugILFrame4 Arabirimi](icordebugilframe4-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [ReJIT: Nasıl Yapilir Kılavuzu](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
