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
ms.openlocfilehash: cdf5776e1ac9907e63aba0e0d400e48aff683d51
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785294"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a>ICLRDataTarget::SetThreadContext Yöntemi
Hedef işlemde belirtilen iş parçacığının geçerli bağlamını ayarlar. Bu yöntem, ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.  
  
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
 'ndaki Hedef işlemdeki bir iş parçacığının işletim sistemi tanımlayıcısı.  
  
 `contextSize`  
 'ndaki Bağlam boyutu.  
  
 `context`  
 'ndaki Bağlamı içeren bir arabelleğin işaretçisi.  
  
 `context` arabelleğindeki veriler Win32 `CONTEXT` yapısı biçiminde olacaktır. Bağlam, işlemciye özgü kayıt verilerini belirtir, bu nedenle Win32 `CONTEXT` yapısının tanımı işlemcinin mimarisine bağlıdır. Win32 `CONTEXT` yapısının tanımı için WinNT. h üst bilgi dosyasına bakın.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData. IDL, ClrData. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRDataTarget Arabirimi](iclrdatatarget-interface.md)
