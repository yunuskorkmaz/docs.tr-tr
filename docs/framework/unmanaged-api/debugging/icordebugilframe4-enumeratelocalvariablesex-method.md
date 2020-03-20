---
title: ICorDebugILFrame4::EnumerateLocalVariablesEx Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type:
- apiref
ms.openlocfilehash: 341a86f4c1c8367f979e193a6284bf89f1b03ca0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178799"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a>ICorDebugILFrame4::EnumerateLocalVariablesEx Yöntemi
[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Çerçevedeki yerel değişken için bir sayıyalı madde alır ve isteğe bağlı olarak profil oluşturucu ReJIT enstrümantasyonuna eklenen değişkenleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `flags`  
 [içinde] Profiloluşturr ReJIT enstrümantasyonuna eklenen değişkenlerin çerçeveye dahil edilip edilmeyeceğini belirten bir [ILCodeKind](ilcodekind-enumeration.md) numaralandırma üyesi.  
  
 `ppValueEnum`  
 [çıkış] Bu çerçevedeki yerel değişkenlerin sayıcısı olan "ICorDebugValueEnum" nesnesinin adresine işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, profiler ReJIT enstrümantasyonuna eklenen değişkenlere isteğe bağlı olarak erişilmesi dışında, [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md) yöntemine benzer. Ayar `flags` `ILCODE_ORIGINAL_IL` [iCorDebugILFrame::EnumerateLocalVariables arama eşdeğerdir.](icordebugilframe-enumeratelocalvariables-method.md) `flags` Hata `ILCODE_REJIT_IL` ayıklayıcının profil oluşturucu ReJIT enstrümantasyonuna eklenen yerel değişkenlere erişmesine olanak sağlayacak ayar. Ara dil (IL) enstrümantasyon aletli değilse, numaralandırma boştur ve yöntem döndürür. `S_OK`  
  
 Enumerator, bazıları etkin olmayabilir, çünkü çalışan yöntemde tüm yerel değişkenleri içermeyebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugILFrame4 Arabirimi](icordebugilframe4-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [ReJIT: Nasıl Yapilir Kılavuzu](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
