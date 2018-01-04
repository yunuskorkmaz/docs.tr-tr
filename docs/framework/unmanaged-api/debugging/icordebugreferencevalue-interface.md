---
title: Icordebugreferencevalue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugReferenceValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugReferenceValue
helpviewer_keywords: ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ac6260a601f7fdacf84034a6ae83c9423fafa11
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugreferencevalue-interface1"></a>Icordebugreferencevalue Interface1
Bir nesneye bir başvurusu olan bir değer yönetme yöntemleri sağlar. (Diğer bir deyişle, bu arabirim bir işaretçi yönetme yöntemleri sağlar.) Bu arabirim "ICorDebugValue" uygular.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Dereference Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|Başvurulan nesnesini alır.|  
|[DereferenceStrong Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|Henüz uygulanmadı. Bu yöntemi çağırmanız gerekmez.|  
|[GetValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|Başvurulan nesnenin geçerli bellek adresini alır.|  
|[IsNull Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|Gösteren bir değer alır olup olmadığını bu `ICorDebugReferenceValue` bir null değer; bu durumda olur `ICorDebugReferenceValue` bir nesneye işaret etmiyor.|  
|[SetValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|Geçerli bellek adresini ayarlar. Diğer bir deyişle, bu yöntem bu ayarlar `ICorDebugReferenceValue` bir nesneye işaret edecek şekilde.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı (CLR) nesnelerde çöp toplama ne ve hata ayıklaması işlemi devam. Çöp toplama nesneleri bellekte gezinme. Bir `ICorDebugReferenceValue` ya da kendi bilgilerini sonra atık toplama güncelleştirilir ya da örtük olarak önce çöp toplama geçersiz çöp toplama ile işbirliği.  
  
 `ICorDebugReferenceValue` Hata ayıklaması işlemi devam sonra nesnesi örtük olarak geçersiz kılınan olabilir. Açıkça serbest veya kullanıma sunulan kadar türetilmiş "Icordebughandlevalue" geçersiz kılınan değil.  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
    
    
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
