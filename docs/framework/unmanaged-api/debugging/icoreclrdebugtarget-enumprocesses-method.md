---
title: ICoreClrDebugTarget::EnumProcesses Yöntemi
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumProcesses
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a35f5ff62ca37337b7becb023f2328cbe05aea6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216047"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a>ICoreClrDebugTarget::EnumProcesses Yöntemi
Uzak bir bilgisayarda çalışan işlemler numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pcProcs`  
 [out] Döndürülen işlem sayısı `ppProcs`. Bu değer, 0 (sıfır) olabilir.  
  
 `ppProcs`  
 [out] Bir dizi [Coreclrdebugprocınfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) uzak bilgisayarda çalışan işlemlere temsil eden yapılar.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 Başarılı.  
  
 E_OUTOFMEMORY  
 Yeterli bellek ayrılamıyor `ppProcs`.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Diğer hatalar.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem tarafından ayrılmış olan belleği boşaltmak için çağrı [Icoreclrdebugtarget::freememory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Library:** mscordbi_macx86.dll  
  
 **.NET framework sürümleri:** 3.5 SP1  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICoreClrDebugTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
