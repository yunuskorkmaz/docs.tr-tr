---
title: "ICoreClrDebugTarget::EnumProcesses Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICoreClrDebugTarget.EnumProcesses
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8296b4b137032400ee172b6d3670bc1a53dbe60d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a>ICoreClrDebugTarget::EnumProcesses Yöntemi
Bir uzak bilgisayarda çalışan işlemler numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pcProcs`  
 [out] Döndürülen işlemlerin sayısı `ppProcs`. Bu değer, 0 (sıfır) olabilir.  
  
 `ppProcs`  
 [out] Bir dizi [Coreclrdebugprocınfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) uzak bilgisayarda çalışan işlemler temsil eden yapılar.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 Başarılı.  
  
 E_OUTOFMEMORY  
 İçin yeterli bellek ayrılamıyor `ppProcs`.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Diğer hataları.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem tarafından ayrılan belleği boşaltmak için çağrı [Icoreclrdebugtarget::freememory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Kitaplığı:** mscordbi_macx86.dll  
  
 **.NET framework sürümleri:** 3.5 SP1  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICoreClrDebugTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
