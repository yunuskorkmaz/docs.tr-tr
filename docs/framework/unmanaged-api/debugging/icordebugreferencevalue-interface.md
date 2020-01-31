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
ms.openlocfilehash: 2efba22b4ec372c5ddedd4982a29d66945d3511c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792127"
---
# <a name="icordebugreferencevalue-interface"></a>ICorDebugReferenceValue Arabirimi
Bir nesne başvurusu olan bir değeri yöneten yöntemler sağlar. (Diğer bir deyişle, bu arabirim bir işaretçiyi yöneten yöntemler sağlar.) Bu arabirim "ICorDebugValue" uygular.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Dereference Yöntemi](icordebugreferencevalue-dereference-method.md)|Başvurulan nesneyi alır.|  
|[DereferenceStrong Yöntemi](icordebugreferencevalue-dereferencestrong-method.md)|Uygulanmadı. Bu yöntemi çağırmayın.|  
|[GetValue Yöntemi](icordebugreferencevalue-getvalue-method.md)|Başvurulan nesnenin geçerli bellek adresini alır.|  
|[IsNull Yöntemi](icordebugreferencevalue-isnull-method.md)|Bu `ICorDebugReferenceValue` null bir değer olup olmadığını belirten bir değer alır, bu durumda `ICorDebugReferenceValue` bir nesneyi işaret etmez.|  
|[SetValue Yöntemi](icordebugreferencevalue-setvalue-method.md)|Geçerli bellek adresini ayarlar. Diğer bir deyişle, bu yöntem bir nesneyi işaret etmek için bu `ICorDebugReferenceValue` ayarlar.|  
  
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

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
