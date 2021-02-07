---
description: 'Şu konuda daha fazla bilgi edinin: ICoreClrDebugTarget:: EnumProcesses yöntemi'
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
ms.openlocfilehash: 73dc8a2b00f7a57879855158e6b871117d015f3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738045"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a>ICoreClrDebugTarget::EnumProcesses Yöntemi

Uzak bir bilgisayarda çalışan işlemi numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pcProcs`  
 dışı İçinde döndürülen işlem sayısı `ppProcs` . Bu değer 0 (sıfır) olabilir.  
  
 `ppProcs`  
 dışı Uzak bilgisayarda çalışan süreçler temsil eden bir [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) yapıları dizisi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 S_OK  
 Başarılı.  
  
 E_OUTOFMEMORY  
 İçin yeterli bellek ayrılamıyor `ppProcs` .  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Diğer sorunlar.  
  
## <a name="remarks"></a>Açıklamalar  

 Bu yöntem tarafından ayrılan belleği boşaltmak için, [ıreclrdebugtarget:: FreeMemory](icoreclrdebugtarget-freememory-method.md) metodunu çağırın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Kitaplık:** mscordbi_macx86.dll  
  
 **.NET Framework sürümleri:** 3,5 SP1  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICoreClrDebugTarget Arabirimi](icoreclrdebugtarget-interface.md)
