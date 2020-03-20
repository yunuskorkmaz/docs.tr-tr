---
title: ICLRDataTarget::SetThreadContext Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetThreadContext
helpviewer_keywords:
- SetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::SetThreadContext method [.NET Framework debugging]
ms.assetid: 103c8502-81fe-40d7-9c1e-9008d8fb19e1
topic_type:
- apiref
ms.openlocfilehash: d76a907434b12b85aaedeef169390ec6f0df724a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179122"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a>ICLRDataTarget::SetThreadContext Yöntemi
Hedef işlemde belirtilen iş parçacığının geçerli bağlamını ayarlar. Bu yöntem, ortak dil çalışma zamanı (CLR) veri erişim hizmetleri tarafından çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `threadID`  
 [içinde] Hedef işlemdeki bir iş parçacığının işletim sistemi tanımlayıcısı.  
  
 `contextSize`  
 [içinde] Bağlamın boyutu.  
  
 `context`  
 [içinde] Bağlamı içeren bir arabellek işaretçisi.  
  
 Arabellekteki `context` veriler Win32 `CONTEXT` yapısı biçiminde olacaktır. Bağlam işlemciye özgü kayıt verilerini belirtir, bu nedenle Win32 `CONTEXT` yapısının tanımı işlemcinin mimarisine bağlıdır. Win32 `CONTEXT` yapısının tanımı için WinNT.h üstbilgi dosyasına bakın.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem hata ayıklama uygulamasının yazarı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** ClrData.idl, ClrData.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRDataTarget Arabirimi](iclrdatatarget-interface.md)
