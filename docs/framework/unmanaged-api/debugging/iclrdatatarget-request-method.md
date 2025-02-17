---
description: ': ICLRDataTarget:: Request yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 75c400a51a2fdaf0044d85b5f483d783fae4628b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712174"
---
# <a name="iclrdatatargetrequest-method"></a>ICLRDataTarget::Request Yöntemi

Uygulama tarafından tanımlanan bir işlem istemek için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.  
  
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
 'ndaki Kullanıcı tanımlı.  
  
 `inBufferSize`  
 'ndaki Gelen istek için kullanılan giriş arabelleğinin boyutu.  
  
 `inBuffer`  
 'ndaki İsteği içeren bir arabellek.  
  
 `outBufferSize`  
 'ndaki Yanıt için kullanılan çıkış arabelleğinin boyutu.  
  
 `outBuffer`  
 dışı Yanıtı içeren bir arabellek.  
  
## <a name="remarks"></a>Açıklamalar  

 `Request`Yöntemi, belirtilmeyen özel işlemlerin eklenmesini kolaylaştırır. Diğer bir deyişle, bu yöntem, arabirim tanımının düzeltilmesi gerekmeden genişletilebilirlik sağlar.  
  
 Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData. IDL, ClrData. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRDataTarget Arabirimi](iclrdatatarget-interface.md)
