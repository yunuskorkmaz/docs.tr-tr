---
title: ICorDebugILFrame4::GetLocalVariableEx Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1de5287331e196355932d20daabe103914cd564
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520018"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a>ICorDebugILFrame4::GetLocalVariableEx Metodu
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Bu Ara dil (IL) yığın çerçevesi içinde belirtilen yerel değişkenin değerini alır ve isteğe bağlı olarak ReJIT izleme profil oluşturucu, eklenen bir değişken erişir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `flags`  
 [in] Bir [Ilcodekind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) ReJIT izleme profil oluşturucu, eklenen bir değişken çerçevede dahil edilip edilmediğini belirten sabit listesi üyesi.  
  
 `dwIndex`  
 [in] IL yığın çerçevesinde yerel değişken dizini.  
  
 `ppValue`  
 [out] Alınan değeri temsil eden bir "ICorDebugValue" nesnenin adresi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem benzer [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) olan isteğe bağlı olarak ReJIT izleme profil oluşturucu, eklenen bir değişken erişen dışında yöntemi. Bu yöntem çağırma bir `flags` değerini `ILCODE_ORIGINAL_IL` çağırmakla eşdeğerdir [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); yöntemin ek yerel değişkenlerle izleme eklenmiş olan değişkenlere erişilemez. `ILCODE_REJIT_IL` eklenen ReJIT izleme profil oluşturucu, yerel değişkenlere erişmek hata ayıklayıcı sağlar. IL varsa izlenmiyor, yöntem döndürür `E_INVALIDARG`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugILFrame4 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ReJIT: Nasıl yapılır Kılavuzu](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
