---
description: ': ICLRMetaHost:: ExitProcess yöntemi hakkında daha fazla bilgi edinin'
title: ICLRMetaHost::ExitProcess Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.ExitProcess
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type:
- apiref
ms.openlocfilehash: 3bc832538a5ad2b457de758fc35a632b09c02974
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689163"
---
# <a name="iclrmetahostexitprocess-method"></a>ICLRMetaHost::ExitProcess Yöntemi

Tüm yüklenen çalışma zamanlarını sorunsuz bir şekilde kapatmaya çalışır ve sonra işlemi sonlandırır. [CorExitProcess](corexitprocess-function.md) işlevinin yerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a>Parametreler  

 `iExitCode`  
 'ndaki İşlemin çıkış kodu.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem hiçbir şekilde döndürmez, bu nedenle dönüş değeri tanımsız olur.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRMetaHost Arabirimi](iclrmetahost-interface.md)
- [Hosting](index.md)
