---
description: 'Şu konuda daha fazla bilgi edinin: ICLRDataTarget3:: GetExceptionRecord yöntemi'
title: ICLRDataTarget3::GetExceptionRecord Yöntemi
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
ms.openlocfilehash: cb816d1be72ee57b556b78dba6ed7503d941b210
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794812"
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a>ICLRDataTarget3::GetExceptionRecord Yöntemi

Hedef işlemle ilişkilendirilmiş özel durum kaydını almak için ortak dil çalışma zamanı (CLR) veri erişim hizmetleri tarafından çağrılır. Örneğin, bir döküm hedefi için, bu, `ExceptionParam` Windows hata ayıklama Yardım Kitaplığı 'ndaki (DbgHelp) [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) işlevine bağımsız değişken aracılığıyla geçirilen özel durum kaydıyla eşdeğerdir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `bufferSize`  
 'ndaki Giriş arabelleğinin bayt cinsinden boyutu. Bu, MINIDUMP_EXCEPTION eşit olmalıdır `sizeof(` [](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) `)` .  
  
 `bufferUsed`  
 dışı `ULONG32` Gerçekte arabelleğe yazılan bayt sayısını alan türe yönelik bir işaretçi.  
  
 `buffer`  
 dışı Özel durum kaydının bir kopyasını alan bir bellek arabelleği işaretçisi. Özel durum kaydı bir [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) türü olarak döndürülür.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Dönüş değeri `S_OK` başarılı veya hata durumunda hata `HRESULT` kodu. `HRESULT`Kodlar şunlar olabilir ancak bunlarla sınırlı değildir:  
  
|Dönüş kodu|Description|  
|-----------------|-----------------|  
|`S_OK`|Yöntem başarılı oldu. Özel durum kaydı çıkış arabelleğine kopyalanmış.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|Hedefle ilişkili özel durum kaydı yok.|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|Giriş arabelleği boyutu değerine eşit değil `sizeof(MINIDUMP_EXCEPTION)` .|  
  
## <a name="remarks"></a>Açıklamalar  

 [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) , Windows SDK içinde dbghelp. h ve Imagehlp. h içinde tanımlanan bir yapıdır.  
  
 Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData. IDL, ClrData. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRDataTarget3 Arabirimi](iclrdatatarget3-interface.md)
- [GetExceptionContextRecord Yöntemi](iclrdatatarget3-getexceptioncontextrecord-method.md)
- [GetExceptionThreadID Yöntemi](iclrdatatarget3-getexceptionthreadid-method.md)
