---
title: ICLRDataTarget::GetThreadContext Metodu
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetThreadContext
helpviewer_keywords:
- ICLRDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: b9d8c3b5-3a2e-4225-95d4-dd052c4532c3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88d563918709a6cf31d9c14a52bbd461ae004420
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116161"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a>ICLRDataTarget::GetThreadContext Metodu
Hedef işlemde verilen iş parçacığı için geçerli yürütme bağlamı alır. Bu yöntem, ortak dil çalışma zamanı veri erişim Hizmetleri tarafından çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `threadID`  
 [in] Bir iş parçacığı hedef işlem, işletim sistemi tanımlayıcısı.  
  
 `contextFlags`  
 [in] Hangi parçalarının dönmek bağlamının belirten bayraklar. Uygulama bağlamı en az bu bölümlerini döndürür.  
  
 `contextSize`  
 [in] İçerik boyutu.  
  
 `context`  
 [out] Bağlam yerleştirileceği bir arabellek için işaretçi.  
  
 Verileri `context` arabellek Win32 biçiminde olmalıdır `CONTEXT` yapısı. Bağlam nedenle işlemciye özel kayıt veri belirtir Win32 tanımını `CONTEXT` yapısı işlemci mimarisine bağlıdır. Win32 tanımını WinNT.h üstbilgi dosyasına `CONTEXT` yapısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData.idl, ClrData.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRDataTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
