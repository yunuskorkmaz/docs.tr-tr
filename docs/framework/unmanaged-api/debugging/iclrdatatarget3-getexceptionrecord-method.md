---
title: ICLRDataTarget3::GetExceptionRecord Metodu
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6643c2af-2ee6-4789-aa25-1d8eaf500c94
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db48febc34514f51ffc4b2e1222af3bf652a67a9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499795"
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a>ICLRDataTarget3::GetExceptionRecord Metodu
Hedef işlemle ilişkilendirilmiş özel durum kaydını almak için ortak dil çalışma zamanı (CLR) veri erişim hizmetleri tarafından çağrılır. Örneğin, bir döküm hedef için bu aracılığıyla geçirilen özel durum kaydını eşdeğer olacaktır `ExceptionParam` bağımsız değişkeni [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) işlev kitaplığında Windows hata ayıklama yardımcı (DbgHelp).  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `bufferSize`  
 [in] Giriş arabelleği bayt cinsinden boyutu. Bu eşit olmalı `sizeof(` [MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception)`)`.  
  
 `bufferUsed`  
 [out] Bir işaretçi bir `ULONG32` gerçekte arabelleğe yazılan bayt sayısı alan türü.  
  
 `buffer`  
 [out] Özel durum kaydını bir kopyasını alır bir ara belleğe yönelik işaretçi. Özel durum kaydını olarak döndürülen bir [MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception) türü.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Dönüş değeri `S_OK` başarı veya hata üzerinde `HRESULT` kodu. `HRESULT` Kodları içerebilir ancak şu şekilde sınırlı değildir:  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|`S_OK`|Yöntem başarılı oldu. Çıkış arabelleği için özel durum kaydını kopyalandı.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|Hedefle ilişkili hiçbir özel durum kaydıdır.|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|Giriş arabelleği boyutu eşit değil `sizeof(MINIDUMP_EXCEPTION)`.|  
  
## <a name="remarks"></a>Açıklamalar  
 [MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception) dbghelp.h ve Windows SDK'sındaki imagehlp.h tanımlanmış bir yapı olduğunu.  
  
 Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData.idl, ClrData.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICLRDataTarget3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [GetExceptionContextRecord Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)
- [GetExceptionThreadID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
