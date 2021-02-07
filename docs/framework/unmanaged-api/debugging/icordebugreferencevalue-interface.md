---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugReferenceValue arabirimi'
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
ms.openlocfilehash: e516b1178b4f4268472dedd37d6443e673e16af6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690970"
---
# <a name="icordebugreferencevalue-interface"></a>ICorDebugReferenceValue Arabirimi

Bir nesne başvurusu olan bir değeri yöneten yöntemler sağlar. (Diğer bir deyişle, bu arabirim bir işaretçiyi yöneten yöntemler sağlar.) Bu arabirim "ICorDebugValue" uygular.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Dereference Yöntemi](icordebugreferencevalue-dereference-method.md)|Başvurulan nesneyi alır.|  
|[DereferenceStrong Yöntemi](icordebugreferencevalue-dereferencestrong-method.md)|Uygulanmaz. Bu yöntemi çağırmayın.|  
|[GetValue Yöntemi](icordebugreferencevalue-getvalue-method.md)|Başvurulan nesnenin geçerli bellek adresini alır.|  
|[IsNull Yöntemi](icordebugreferencevalue-isnull-method.md)|Bunun null bir değer olup olmadığını belirten bir değer alır `ICorDebugReferenceValue` , bu durumda `ICorDebugReferenceValue` bir nesneyi işaret etmez.|  
|[SetValue Yöntemi](icordebugreferencevalue-setvalue-method.md)|Geçerli bellek adresini ayarlar. Diğer bir deyişle, bu yöntem bunu `ICorDebugReferenceValue` bir nesnesine işaret etmek üzere ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  

 Ortak dil çalışma zamanı (CLR), hata ayıklama işlemi devam eden nesneler üzerinde çöp toplama işlemi yapamayabilir. Çöp toplama, nesneleri belleğin etrafında taşıyabilir. , `ICorDebugReferenceValue` Bilgileri çöp toplamadan sonra güncelleştirilmesini sağlamak için çöp koleksiyonuyla birlikte çalışır veya çöp toplamadan önce örtülü olarak geçersiz kılınacaktır.  
  
 `ICorDebugReferenceValue`Hata ayıklama işlemi devam ettikten sonra nesne örtük olarak geçersiz kılınabilir. Türetilmiş "ıcorıı Ghandlevalue", açık veya kullanıma sunuluncaya kadar geçersiz kılınmaz.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
