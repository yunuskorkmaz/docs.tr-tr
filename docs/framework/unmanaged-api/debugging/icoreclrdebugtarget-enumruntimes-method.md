---
title: "ICoreClrDebugTarget::EnumRuntimes Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICoreClrDebugTarget.EnumRuntimes
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: ICoreClrDebugTarget::EnumRuntimes
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget::EnumRuntimes method [Silverlight debugging]
- EnumRuntimes method, ICoreClrDebugTarget interface [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 316df866-442d-40cc-b049-45e8adcb65d1
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d28e5f3f529f72607e2ddd84789e89f82dcdaba0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a>ICoreClrDebugTarget::EnumRuntimes Yöntemi
Ortak dil çalışma zamanları (CLRs) bir uzak bilgisayarda çalışan belirtilen işlemde numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwInternalProcessID`  
 [in] Çalışma zamanları listeleme istediğiniz işlemin iç işlem kimliği. Bu `m_dwInternalID` karşılık gelen gelen [Coreclrdebugprocınfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).  
  
 `pcRuntimes`  
 [out] Döndürülen çalışma zamanları sayısı `ppRuntimes`. Bu değer, 0 (sıfır) olabilir.  
  
 `ppRuntimes`  
 [out] Bir dizi [Coreclrdebugruntimeınfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) çalışma zamanları temsil eden yapılar uzak hedefe işleminde yüklendi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 Başarılı.  
  
 S_FALSE  
 `dwInternalProcessID`işlemin sonlandırıldığından bilgisayar üzerinde çalışan herhangi bir işlem büyük olasılıkla eşleşmiyor. `pcRuntimes`ve `ppRuntimes` null olur.  
  
 E_OUTOFMEMORY  
 İçin yeterli bellek ayrılamıyor `ppRuntimes`.  
  
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
 [Icoreclrdebugtarget arabirimi](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
