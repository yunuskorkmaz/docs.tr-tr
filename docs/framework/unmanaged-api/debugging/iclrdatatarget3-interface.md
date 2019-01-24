---
title: ICLRDataTarget3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 974abb123c4c11f6bb512431cea5cc6460a5c55a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654752"
---
# <a name="iclrdatatarget3-interface"></a>ICLRDataTarget3 Arabirimi
Öğesinin [Iclrdatatarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) , özel durum bilgilerine erişim sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetExceptionRecord Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|Hedef işlemle ilişkilendirilmiş özel durum kaydını almak için ortak dil çalışma zamanı (CLR) veri erişim hizmetleri tarafından çağrılır.|  
|[GetExceptionContextRecord Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|Hedef işlemle ilişkilendirilmiş bağlam kaydını almak için CLR veri erişim hizmetleri tarafından çağrılır.|  
|[GetExceptionThreadID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|Özel durum oluşturan iş parçacığı Kimliğini almak için CLR veri erişim Hizmetleri tarafından çağrılır.|  
  
## <a name="remarks"></a>Açıklamalar  
 API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir. Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur. Hedef, kendi bellek bölümlerinin değiştirilmesini desteklemiyor olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData.idl, ClrData.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICLRDataTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
- [ICLRDataTarget2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
