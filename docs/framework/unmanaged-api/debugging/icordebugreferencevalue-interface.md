---
title: Icordebugreferencevalue arabirimi1
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
ms.openlocfilehash: 3dbe5388d7c18202f4b89269141d33463edb07a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544279"
---
# <a name="icordebugreferencevalue-interface1"></a>Icordebugreferencevalue arabirimi1
Bir nesneye bir başvurusu olan bir değer yönetmek için yöntemler sağlar. (Diğer bir deyişle, bu arabirim işaretçisi yönetme yöntemleri sağlar.) Bu arabirim "ICorDebugValue" uygular.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Dereference Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|Başvurulan nesneyi alır.|  
|[DereferenceStrong Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|Henüz uygulanmadı. Bu yöntemi çağırmanız gerekmez.|  
|[GetValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|Başvurulan nesnenin geçerli bellek adresini alır.|  
|[IsNull Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|Belirten bir değer alır olup bu `ICorDebugReferenceValue` null değeri, bu durumda olur `ICorDebugReferenceValue` bir nesneye işaret etmiyor.|  
|[SetValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|Geçerli bellek adresini ayarlar. Diğer bir deyişle, bu yöntem bu ayarlar `ICorDebugReferenceValue` bir nesneye işaret edecek şekilde.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hataları ayıklanan işlem devam ettirildiğinde, ortak dil çalışma zamanı (CLR) nesnelerde çöp toplama yapabilirsiniz. Çöp toplama nesneleri bellekte değiştirmemiz. Bir `ICorDebugReferenceValue` ya da çöp toplama bilgilerini çöp toplamanın ardından güncelleştirilir ya da örtük olarak önce çöp toplama geçersiz iş Birliği yapacaktır.  
  
 `ICorDebugReferenceValue` Hataları ayıklanan işlem devam sonra nesnesi örtük olarak geçersiz kılınan olabilir. Açıkça serbest veya ifşa kadar türetilmiş "Icordebughandlevalue" geçersiz değil.  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.


- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
