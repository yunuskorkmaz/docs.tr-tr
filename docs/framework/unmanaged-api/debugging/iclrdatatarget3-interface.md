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
ms.openlocfilehash: 7297bfa5297878dde6867a99029ac88754a05290
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723590"
---
# <a name="iclrdatatarget3-interface"></a>ICLRDataTarget3 Arabirimi

Özel durum bilgilerine erişim sağlayan [ICLRDataTarget2](iclrdatatarget2-interface.md) öğesinin bir alt sınıfı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetExceptionRecord Yöntemi](iclrdatatarget3-getexceptionrecord-method.md)|Hedef işlemle ilişkilendirilmiş özel durum kaydını almak için ortak dil çalışma zamanı (CLR) veri erişim hizmetleri tarafından çağrılır.|  
|[GetExceptionContextRecord Yöntemi](iclrdatatarget3-getexceptioncontextrecord-method.md)|Hedef işlemle ilişkilendirilmiş bağlam kaydını almak için CLR veri erişim hizmetleri tarafından çağrılır.|  
|[GetExceptionThreadID Yöntemi](iclrdatatarget3-getexceptionthreadid-method.md)|Özel durumu oluşturan iş parçacığının KIMLIĞINI almak için CLR veri erişim Hizmetleri tarafından çağırılır.|  
  
## <a name="remarks"></a>Açıklamalar  

 API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir. Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur. Hedef, kendi bellek bölümlerinin değiştirilmesini desteklemiyor olabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData. IDL, ClrData. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRDataTarget Arabirimi](iclrdatatarget-interface.md)
- [ICLRDataTarget2 Arabirimi](iclrdatatarget2-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
