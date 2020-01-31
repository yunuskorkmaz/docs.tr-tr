---
title: ICLRDataTarget3::GetExceptionContextRecord Metodu
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetContextRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type:
- apiref
ms.openlocfilehash: aed301fa136ff3d45269c82b46e4cad699074874
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785245"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a>ICLRDataTarget3::GetExceptionContextRecord Metodu
Hedef işlemle ilişkili bağlam kaydını almak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır. Örneğin, bir döküm hedefi için, bu, Windows hata ayıklama Yardım Kitaplığı 'nda (DbgHelp [), `ExceptionParam`](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) bağımsız değişkeni aracılığıyla geçirilen bağlam kaydıyla eşdeğerdir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `bufferSize`  
 'ndaki Giriş arabelleğinin bayt cinsinden boyutu. Bu, bağlam kaydına uyum sağlayacak kadar büyük olmalıdır.  
  
 `bufferUsed`  
 dışı Gerçekten arabelleğe yazılan bayt sayısını alan `ULONG32` türüne yönelik bir işaretçi.  
  
 `buffer`  
 dışı Bağlam kaydının bir kopyasını alan bir bellek arabelleği işaretçisi. Özel durum kaydı, [bağlam](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) türü olarak döndürülür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Dönüş değeri `S_OK` başarılı veya hata durumunda bir hata `HRESULT`. `HRESULT` kodları şunları içerebilir, ancak bunlarla sınırlı değildir:  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|`S_OK`|Yöntem başarılı oldu. Bağlam kaydı çıkış arabelleğine kopyalanmış.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|Hedefle ilişkili bağlam kaydı yok.|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|Giriş arabelleği boyutu, bağlam kaydına uyum sağlayacak kadar büyük değil.|  
  
## <a name="remarks"></a>Açıklamalar  
 [Bağlam](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) , Windows SDK tarafından belirtilen üst bilgilerde tanımlanan platforma özgü bir yapıdır.  
  
 Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData. IDL, ClrData. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRDataTarget3 Arabirimi](iclrdatatarget3-interface.md)
- [GetExceptionRecord Yöntemi](iclrdatatarget3-getexceptionrecord-method.md)
- [GetExceptionThreadID Yöntemi](iclrdatatarget3-getexceptionthreadid-method.md)
