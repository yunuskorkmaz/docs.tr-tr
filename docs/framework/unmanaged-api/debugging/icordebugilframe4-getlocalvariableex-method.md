---
title: ICorDebugILFrame4::GetLocalVariableEx Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetCodeEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type:
- apiref
ms.openlocfilehash: ee263e8c49cd6da7278bd2299557336629720d2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178772"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a>ICorDebugILFrame4::GetLocalVariableEx Yöntemi
[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Bu ara dil (IL) yığın çerçevesinde belirtilen yerel değişkenin değerini alır ve isteğe bağlı olarak profiloluşturucu ReJIT enstrümantasyonuna eklenen bir değişkene erişir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,
   [in] DWORD dwIndex,
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `flags`  
 [içinde] Profiloluşturr ReJIT enstrümantasyonuna eklenen bir değişkenin çerçeveye dahil edilip edilmeyeceğini belirten bir [ILCodeKind](ilcodekind-enumeration.md) numaralandırma üyesi.  
  
 `dwIndex`  
 [içinde] IL yığın çerçevesinde yerel değişkenin dizin.  
  
 `ppValue`  
 [çıkış] Alınan değeri temsil eden bir "ICorDebugValue" nesnesinin adresine işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, profiler ReJIT enstrümantasyonuna eklenen bir değişkene isteğe bağlı olarak erişilmesi dışında [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) yöntemine benzer. Bu yöntemi `flags` bir değerle çağırmak [GetLocalVariable'i](icordebugilframe-getlocalvariable-method.md)aramaya `ILCODE_ORIGINAL_IL` eşdeğerdir; yöntem ek yerel değişkenlerle çalgılanmışsa, bu değişkenlere erişilemez. `ILCODE_REJIT_IL`hata ayıklayıcının profil oluşturucu ReJIT enstrümantasyonuna eklenen yerel değişkenlere erişmesine izin verir. IL aracılı değilse, yöntem döndürür. `E_INVALIDARG`  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugILFrame4 Arabirimi](icordebugilframe4-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [ReJIT: Nasıl Yapilir Kılavuzu](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
