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
ms.openlocfilehash: 6484832e8e737b9a0d0b3eaf3ede4078729f7a4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178435"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a>ICoreClrDebugTarget::EnumProcesses Yöntemi
Uzak bir bilgisayarda çalışan işlemleri sayısalhale eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pcProcs`  
 [çıkış] Döndürülen işlem `ppProcs`sayısı. Bu değer 0 (sıfır) olabilir.  
  
 `ppProcs`  
 [çıkış] Uzak bilgisayarda çalışan işlemleri temsil eden bir dizi [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) yapıları.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 Başarılı.  
  
 E_outofmemory  
 `ppProcs`'ye yeterli bellek ayrılamıyor.  
  
 E_FAIL (veya diğer E_ iade kodları)  
 Diğer başarısızlıklar.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntemle ayrılan belleği serbest etmek için [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) yöntemini arayın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Kütüphane:** mscordbi_macx86.dll  
  
 **.NET Çerçeve Sürümleri:** 3.5 SP1  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICoreClrDebugTarget Arabirimi](icoreclrdebugtarget-interface.md)
