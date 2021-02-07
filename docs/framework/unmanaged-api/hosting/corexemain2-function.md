---
description: 'Hakkında daha fazla bilgi edinin: _CorExeMain2 Işlevi'
title: _CorExeMain2 İşlevi
ms.date: 03/30/2017
api_name:
- _CorExeMain2
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain2
helpviewer_keywords:
- _CorExeMain2 function [.NET Framework hosting]
ms.assetid: 72ea68b4-689f-4733-9416-9664b75e8892
topic_type:
- apiref
ms.openlocfilehash: 4629ea2f6c2ba13351c409bc382077eea926b507
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717114"
---
# <a name="_corexemain2-function"></a>_CorExeMain2 İşlevi

Giriş noktasını belirtilen bellek eşlemeli kodda yürütür. Bu işlev, işletim sistemi yükleyicisi tarafından çağırılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pUnmappedPE`  
 'ndaki Bellek eşlemeli koda yönelik bir işaretçi.  
  
 `cUnmappedPE`  
 'ndaki Öğelerin sayısı `pUnmappedPE` tutabilirler.  
  
 `pImageNameIn`  
 'ndaki Yürütülebilir görüntünün adı için bir işaretçi.  
  
 `pLoadersFileName`  
 'ndaki Yükleyici dosyasının adı.  
  
 `pCmdLine`  
 'ndaki Varsa komut satırı parametreleri.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Genel Statik İşlevleri](../metadata/metadata-global-static-functions.md)
