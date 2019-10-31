---
title: ICorDebugReferenceValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
ms.openlocfilehash: 16d7b89ee441e8d634c36fb87185b3f2846860b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137717"
---
# <a name="icordebugreferencevalue-interface"></a>ICorDebugReferenceValue Arabirimi
Bir nesne başvurusu olan bir değeri yöneten yöntemler sağlar. (Diğer bir deyişle, bu arabirim bir işaretçiyi yöneten yöntemler sağlar.) Bu arabirim "ICorDebugValue" uygular.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Dereference Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|Başvurulan nesneyi alır.|  
|[DereferenceStrong Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|Uygulanmadı. Bu yöntemi çağırmayın.|  
|[GetValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|Başvurulan nesnenin geçerli bellek adresini alır.|  
|[IsNull Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|Bu `ICorDebugReferenceValue` null bir değer olup olmadığını belirten bir değer alır, bu durumda `ICorDebugReferenceValue` bir nesneyi işaret etmez.|  
|[SetValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|Geçerli bellek adresini ayarlar. Diğer bir deyişle, bu yöntem bir nesneyi işaret etmek için bu `ICorDebugReferenceValue` ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı (CLR), hata ayıklama işlemi devam eden nesneler üzerinde çöp toplama işlemi yapamayabilir. Çöp toplama, nesneleri belleğin etrafında taşıyabilir. `ICorDebugReferenceValue`, çöp toplamadan sonra bilgileri güncelleştirilebilmeleri için çöp koleksiyonuyla birlikte çalışır veya çöp toplamadan önce örtük olarak geçersiz kılınacaktır.  
  
 Hata ayıklama işlemi devam ettikten sonra `ICorDebugReferenceValue` nesnesi örtük olarak geçersiz kılınabilir. Türetilmiş "ıcorıı Ghandlevalue", açık veya kullanıma sunuluncaya kadar geçersiz kılınmaz.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
