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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77bd3bc239d0101f02cd515b0ec2a8bec3372882
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596910"
---
# <a name="iclrdatatargetrequest-method"></a>ICLRDataTarget::Request Yöntemi
Uygulama tarafından tanımlanan bir işlemi istemek için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
  
#### <a name="parameters"></a>Parametreler  
 `reqCode`  
 [in] Kullanıcı tanımlı.  
  
 `inBufferSize`  
 [in] Gelen istek için kullanılan giriş arabellek boyutu.  
  
 `inBuffer`  
 [in] İstek içeren arabellek.  
  
 `outBufferSize`  
 [in] Yanıt için kullanılan çıkış arabelleği boyutu.  
  
 `outBuffer`  
 [out] Yanıtı içeren arabellek.  
  
## <a name="remarks"></a>Açıklamalar  
 `Request` Yöntemi belirtilmeyen özel işlemler eklenmesini kolaylaştırır. Diğer bir deyişle, bu yöntem, arabirim tanımı gözden geçirilmesini gerek kalmadan genişletilebilirlik sağlar.  
  
 Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData.idl, ClrData.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICLRDataTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
