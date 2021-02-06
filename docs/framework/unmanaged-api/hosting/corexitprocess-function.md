---
description: 'Daha fazla bilgi edinin: CorExitProcess Işlevi'
title: CorExitProcess İşlevi
ms.date: 03/30/2017
api_name:
- CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CorExitProcess
helpviewer_keywords:
- CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type:
- apiref
ms.openlocfilehash: 68d33dec76387e103a34e99c529a4e7aff7535b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649591"
---
# <a name="corexitprocess-function"></a>CorExitProcess İşlevi

Geçerli yönetilmeyen işlemi kapatır.  
  
 Bu işlev .NET Framework 4 ' te kullanım dışıdır. Bunun yerine [ICLRMetaHost:: ExitProcess](iclrmetahost-exitprocess-method.md) metodunu kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (
  int  exitCode  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `exitCode`  
 İşlem çıkış kodunu belirten bir tamsayı.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> .NET Framework 4 ' ten başlayarak, `CorExitProcess` yalnızca eski API 'lerin bağlandığı çalışma zamanına değil, işlemdeki tüm başlatılan çalışma zamanından çıkılıyor.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanım Dışı CLR Barındırma İşlevleri](deprecated-clr-hosting-functions.md)
