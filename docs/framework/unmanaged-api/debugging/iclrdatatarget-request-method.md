---
title: ICLRDataTarget::Request Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.Request
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type:
- apiref
ms.openlocfilehash: 336ba38bc80fcb2649a12c78691e52c5e4d70bfe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179107"
---
# <a name="iclrdatatargetrequest-method"></a>ICLRDataTarget::Request Yöntemi
Uygulama tarafından tanımlandığı gibi bir işlem istemek için ortak dil çalışma zamanı (CLR) veri erişim hizmetleri tarafından çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Request (  
    [in] ULONG32            reqCode,  
    [in] ULONG32            inBufferSize,  
    [in, size_is(inBufferSize)]
        BYTE                *inBuffer,  
    [in] ULONG32            outBufferSize,  
    [out, size_is(outBufferSize)]
        BYTE                *outBuffer  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `reqCode`  
 [içinde] Kullanıcı tanımlı.  
  
 `inBufferSize`  
 [içinde] Gelen istek için kullanılan giriş arabelleği boyutu.  
  
 `inBuffer`  
 [içinde] İsteği içeren bir arabellek.  
  
 `outBufferSize`  
 [içinde] Yanıt için kullanılan çıktı arabelleği boyutu.  
  
 `outBuffer`  
 [çıkış] Yanıtı içeren bir Arabellek.  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntem, `Request` belirtilmeyen özel işlemlerin eklenmesini kolaylaştırır. Diğer bir zamanda, bu yöntem arabirim tanımının gözden geçirilmesini gerektirmeden genişletilebilirlik sağlar.  
  
 Bu yöntem hata ayıklama uygulamasının yazarı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** ClrData.idl, ClrData.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRDataTarget Arabirimi](iclrdatatarget-interface.md)
