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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6503efbaa4db89b243a85b69f60b091c6bb49ef
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215306"
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a>ICLRDataTarget3::GetExceptionThreadID Metodu
Özel durum oluşturan iş parçacığı Kimliğini almak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `threadID`  
 [out] Özel durum oluşturan iş parçacığının kimliği.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Dönüş değeri `S_OK` başarı veya hata üzerinde `HRESULT` kodu. `HRESULT` Kodları içerebilir ancak şu şekilde sınırlı değildir:  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|Özel durum için geçerli iş parçacığı kimliği bulunamadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData.idl, ClrData.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRDataTarget3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [GetExceptionContextRecord Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)
- [GetExceptionRecord Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
