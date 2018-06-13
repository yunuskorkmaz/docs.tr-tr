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
ms.openlocfilehash: a82f092a0f10fd621ac4facdee201fa239e1c1b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414535"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a>ICorDebugILFrame4::GetLocalVariableEx Metodu
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Bu Ara dile (IL) yığın çerçevesinde belirtilen yerel değişkenin değerini alır ve isteğe bağlı olarak profiler ReJIT araçları eklenen bir değişken erişir.  
  
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
 [in] Bir [Ilcodekind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) profiler ReJIT araçları eklenen bir değişken çerçevede dahil edilip edilmediğini belirten numaralandırma üyesi.  
  
 `dwIndex`  
 [in] IL yığın çerçevesi yerel değişkende dizini.  
  
 `ppValue`  
 [out] Alınan değerin temsil eden bir "ICorDebugValue" nesnesinin adresi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem benzer [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) olan isteğe bağlı olarak profiler ReJIT araçları eklenen bir değişken erişen dışında yöntemi. Bu yöntemle çağırma bir `flags` değerini `ILCODE_ORIGINAL_IL` arama için eşdeğer bir gruba [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); yöntemi ek yerel değişkenleriyle izlenmiş olan değişkenlere erişilemiyor. `ILCODE_REJIT_IL` Profil Oluşturucusu ReJIT Araçları'nda eklenen yerel değişkenler erişmek hata ayıklayıcı sağlar. IL izlenmemektedir ise, yöntem `E_INVALIDARG`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugILFrame4 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ReJIT: Nasıl yapılır Kılavuzu](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
