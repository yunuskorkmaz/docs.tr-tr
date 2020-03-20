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
ms.openlocfilehash: 3777ad4b12c7d0593c095c470aba81088137a859
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179174"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a>ICLRDataTarget::GetThreadContext Metodu
Hedef işlemde verilen iş parçacığı için geçerli yürütme bağlamını alır. Bu yöntem, ortak dil çalışma zamanı veri erişim hizmetleri tarafından çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
 [içinde] Hedef işlemdeki bir iş parçacığının işletim sistemi tanımlayıcısı.  
  
 `contextFlags`  
 [içinde] Bağlamın hangi bölümlerinin döndürülecek olduğunu belirten bayraklar. Uygulama bağlamın en azından bu bölümleri döndürecektir.  
  
 `contextSize`  
 [içinde] Bağlamın boyutu.  
  
 `context`  
 [çıkış] Bağlamı yerleştirmek için bir arabellek işaretçisi.  
  
 Arabellekteki `context` veriler Win32 `CONTEXT` yapısı biçiminde olmalıdır. Bağlam işlemciye özgü kayıt verilerini belirtir, bu nedenle Win32 `CONTEXT` yapısının tanımı işlemcinin mimarisine bağlıdır. Win32 `CONTEXT` yapısının tanımı için WinNT.h üstbilgi dosyasına bakın.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem hata ayıklama uygulamasının yazarı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** ClrData.idl, ClrData.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRDataTarget Arabirimi](iclrdatatarget-interface.md)
