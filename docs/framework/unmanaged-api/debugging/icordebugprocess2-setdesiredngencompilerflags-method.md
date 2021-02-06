---
description: 'Daha fazla bilgi edinin: ICorDebugProcess2:: SetDesiredNGENCompilerFlags yöntemi'
title: ICorDebugProcess2::SetDesiredNGENCompilerFlags Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags method [.NET Framework debugging]
- SetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: 98320175-7c5e-4dbb-8683-86fa82e2641f
topic_type:
- apiref
ms.openlocfilehash: 3a4749ad26e88d1a602876f28a52754323093fce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650109"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a>ICorDebugProcess2::SetDesiredNGENCompilerFlags Yöntemi

Çalışma zamanının o görüntüyü geçerli işleme yüklemesi için, önceden derlenmiş bir görüntüye katıştırılması gereken bayrakları ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pdwFlags`  
 'ndaki Doğru önceden derlenmiş görüntüyü seçmek için kullanılan derleyici bayraklarını belirten [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) numaralandırması değeri.  
  
## <a name="remarks"></a>Açıklamalar  

 `SetDesiredNGENCompilerFlags`Yöntemi, önceden derlenmiş bir görüntüye katıştırılması gereken bayrakları belirtir, böylece çalışma zamanı bu görüntüyü bu işleme yükleyecek. Bu yöntem tarafından ayarlanan bayraklar yalnızca doğru ön derlenmiş görüntüyü seçmek için kullanılır. Böyle bir görüntü yoksa, çalışma zamanı bunun yerine Microsoft ara dili (MSIL) görüntüsünü ve tam zamanında (JıT) derleyicisini yükler. Bu durumda, hata ayıklayıcı yine de [ICorDebugModule2:: SetJITCompilerFlags](icordebugmodule2-setjitcompilerflags-method.md) metodunu kullanarak bayrakları JIT derlemesi için istediğiniz şekilde ayarlar.  
  
 Bir görüntü yüklenirse, ancak bu görüntü için bazı JıT derleme gerçekleşmelidir (görüntü genel türler içerdiğinde durum olacaktır), yöntem tarafından belirtilen derleyici bayrakları `SetDesiredNGENCompilerFlags` ekstra JIT derlemesi için de geçerlidir.  
  
 `SetDesiredNGENCompilerFlags`Metodun [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) geri çağırması sırasında çağrılması gerekir. `SetDesiredNGENCompilerFlags`Daha sonra yöntemi çağırma girişimleri başarısız olur. Ayrıca, `CorDebugJITCompilerFlags` numaralandırmada tanımlanmayan veya verilen işlem için geçerli olmayan bayrakları ayarlama girişimleri başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](icordebug-interface.md)
- [ICorDebugManagedCallback Arabirimi](icordebugmanagedcallback-interface.md)
