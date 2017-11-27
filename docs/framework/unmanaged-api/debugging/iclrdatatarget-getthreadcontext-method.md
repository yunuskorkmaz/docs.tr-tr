---
title: ICLRDataTarget::GetThreadContext Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetThreadContext
helpviewer_keywords:
- ICLRDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: b9d8c3b5-3a2e-4225-95d4-dd052c4532c3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 480b65b279dbc0359b078f3f1d543f63a0bfd0f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetgetthreadcontext-method"></a>ICLRDataTarget::GetThreadContext Metodu
Hedef işlemdeki verilen iş parçacığı için geçerli yürütme bağlamı alır. Bu yöntem ortak dil çalışma zamanı veri erişim Hizmetleri tarafından çağrılır.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `threadID`  
 [in] Bir iş parçacığı hedef işlem, işletim sistemi tanımlayıcısı.  
  
 `contextFlags`  
 [in] Döndürülecek bağlam hangi kısımlarının belirtin bayraklar. Uygulama bağlamı en az bu bölümlerini döndürür.  
  
 `contextSize`  
 [in] İçerik boyutu.  
  
 `context`  
 [out] Bağlam yerleştirileceği bir arabellek işaretçi.  
  
 Verileri `context` arabellek Win32 biçiminde olmalıdır `CONTEXT` yapısı. Bağlam işlemciye özgü kayıt verilerini, bu nedenle belirtir Win32 tanımını `CONTEXT` yapısı işlemci mimarisine bağlıdır. Win32 tanımını WinNT.h üstbilgi dosyasına `CONTEXT` yapısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, hata ayıklama uygulama yazıcı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** ClrData.idl, ClrData.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iclrdatatarget arabirimi](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
