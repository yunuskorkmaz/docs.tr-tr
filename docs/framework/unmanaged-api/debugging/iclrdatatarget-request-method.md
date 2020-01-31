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
ms.openlocfilehash: 0a7e764d89dd42bcaf81da5cf6a16991b6b8a16e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793699"
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
 `Request` yöntemi, belirtilmeyen özel işlemlerin eklenmesini kolaylaştırır. Diğer bir deyişle, bu yöntem, arabirim tanımının düzeltilmesi gerekmeden genişletilebilirlik sağlar.  
  
 Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData. IDL, ClrData. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRDataTarget Arabirimi](iclrdatatarget-interface.md)
