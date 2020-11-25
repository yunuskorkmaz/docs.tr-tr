---
title: ICLRDataTarget3::GetExceptionThreadID Metodu
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionThreadID
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 307d6ac7-4a86-45f3-999d-6b47004a68f2
topic_type:
- apiref
ms.openlocfilehash: 0a8b7a90cd909379f870f6a501a940386d2e1451
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723603"
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a>ICLRDataTarget3::GetExceptionThreadID Metodu

Özel durumu oluşturan iş parçacığının KIMLIĞINI almak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `threadID`  
 dışı Özel durumu oluşturan iş parçacığının KIMLIĞI.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Dönüş değeri `S_OK` başarılı veya hata durumunda hata `HRESULT` kodu. `HRESULT`Kodlar şunlar olabilir ancak bunlarla sınırlı değildir:  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|Özel durum için geçerli bir iş parçacığı KIMLIĞI bulunamadı.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData. IDL, ClrData. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRDataTarget3 Arabirimi](iclrdatatarget3-interface.md)
- [GetExceptionContextRecord Yöntemi](iclrdatatarget3-getexceptioncontextrecord-method.md)
- [GetExceptionRecord Yöntemi](iclrdatatarget3-getexceptionrecord-method.md)
