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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67006603747abd89f1b635c065860dcbe1c47a29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965641"
---
# <a name="icordebugreferencevalue-interface"></a>ICorDebugReferenceValue Arabirimi
Bir nesne başvurusu olan bir değeri yöneten yöntemler sağlar. (Diğer bir deyişle, bu arabirim bir işaretçiyi yöneten yöntemler sağlar.) Bu arabirim "ICorDebugValue" uygular.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Dereference Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|Başvurulan nesneyi alır.|  
|[DereferenceStrong Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|Uygulanmadı. Bu yöntemi çağırmayın.|  
|[GetValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|Başvurulan nesnenin geçerli bellek adresini alır.|  
|[IsNull Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|Bunun null bir değer olup olmadığını belirten `ICorDebugReferenceValue` bir değer alır, bu `ICorDebugReferenceValue` durumda bir nesneyi işaret etmez.|  
|[SetValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|Geçerli bellek adresini ayarlar. Diğer bir deyişle, bu yöntem bunu `ICorDebugReferenceValue` bir nesnesine işaret etmek üzere ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı (CLR), hata ayıklama işlemi devam eden nesneler üzerinde çöp toplama işlemi yapamayabilir. Çöp toplama, nesneleri belleğin etrafında taşıyabilir. `ICorDebugReferenceValue` , Bilgileri çöp toplamadan sonra güncelleştirilmesini sağlamak için çöp koleksiyonuyla birlikte çalışır veya çöp toplamadan önce örtülü olarak geçersiz kılınacaktır.  
  
 Hata ayıklama işlemi devam ettikten sonra nesneörtükolarakgeçersizkılınabilir.`ICorDebugReferenceValue` Türetilmiş "ıcorıı Ghandlevalue", açık veya kullanıma sunuluncaya kadar geçersiz kılınmaz.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
