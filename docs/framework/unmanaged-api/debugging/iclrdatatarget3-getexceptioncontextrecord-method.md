---
title: ICLRDataTarget3::GetExceptionContextRecord Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICLRDataTarget3.GetContextRecord
api_location: mscordbi.dll
api_type: COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c2e645222553f4000b300fa4f010ff81ff44d23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a>ICLRDataTarget3::GetExceptionContextRecord Metodu
Hedef işlemle ilişkili bağlam kaydı almak için ortak dil çalışma zamanı (CLR) veri erişim hizmeti tarafından çağrılır. Örneğin, bir döküm hedef için bu aracılığıyla geçilen bağlamı kayda eşdeğer olacaktır `ExceptionParam` bağımsız değişkeni [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360\(v=vs.85\).aspx) işlevi Windows Kitaplığı'nda hata ayıklama yardımcı (DbgHelp).  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `bufferSize`  
 [in] Giriş arabelleği bayt cinsinden boyutu. Bu içerik kaydı uyabilecek kadar büyük olmalıdır.  
  
 `bufferUsed`  
 [out] Bir işaretçi bir `ULONG32` gerçekten arabelleğe yazılan bayt sayısı alan türü.  
  
 `buffer`  
 [out] İçerik kaydı kopyasını alan bir bellek arabelleği için bir işaretçi. Özel durum kaydı olarak döndürülür bir [BAĞLAMI](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) türü.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Dönüş değeri `S_OK` başarı veya hata `HRESULT` hata kodu. `HRESULT` Kodları içerebilir ancak aşağıdaki sınırlı değildir:  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|`S_OK`|Yöntem başarılı oldu. İçerik kaydı çıktı arabelleğine kopyalandı.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|Hedefle ilişkili hiç içerik kayıttır.|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|Giriş arabelleği boyutu içerik kaydı uyabilecek kadar büyük değil.|  
  
## <a name="remarks"></a>Açıklamalar  
 [BAĞLAM](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) olan Windows SDK'sı tarafından sağlanan üstbilgileri tanımlanan bir platforma özgü yapısı.  
  
 Bu yöntem, hata ayıklama uygulama yazıcı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** ClrData.idl, ClrData.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iclrdatatarget3 arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [GetExceptionRecord yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)  
 [Getexceptionthreadıd yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
