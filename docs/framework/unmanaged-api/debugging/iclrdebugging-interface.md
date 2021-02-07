---
description: ': ICLRDebugging arabirimi hakkında daha fazla bilgi edinin'
title: ICLRDebugging Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging
helpviewer_keywords:
- ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type:
- apiref
ms.openlocfilehash: 647b6f7634ef3b9f6ec6080aaff19476c027952a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723345"
---
# <a name="iclrdebugging-interface"></a>ICLRDebugging Arabirimi

Hata ayıklama amacıyla modülleri yükleme ve kaldırma işlemlerini yapan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[OpenVirtualProcess Yöntemi](iclrdebugging-openvirtualprocess-method.md)|İşlemde yüklenen ortak dil çalışma zamanı (CLR) modülüne karşılık gelen "ICorDebugProcess" arabirimini alır.|  
|[CanUnloadNow Yöntemi](iclrdebugging-canunloadnow-method.md)|Bir [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) arabirimi tarafından sağlanmış bir kitaplığın hala kullanımda olup olmadığını veya kaldırılabileceğini belirler.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bir `ICLRDebugging` arabirimin örneğini [CLRCreateInstance](../hosting/clrcreateinstance-function.md) işlevini kullanarak elde edebilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
