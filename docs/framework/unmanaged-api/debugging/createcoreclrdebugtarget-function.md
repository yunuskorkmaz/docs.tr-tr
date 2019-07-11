---
title: CreateCoreClrDebugTarget İşlevi
ms.date: 03/30/2017
api_name:
- CreateCorClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbcf6c842e7eee55609a9ea2a25cda4360f8dc95
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739292"
---
# <a name="createcoreclrdebugtarget-function"></a>CreateCoreClrDebugTarget İşlevi
Uzak bir makinede çalışıyor ve döndüren bir hata ayıklayıcı proxy için bir bağlantı oluşturur bir [Icoreclrdebugtarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) çalışan işlemleri ve uzak makinede yüklü çalışma zamanları sorgulamak için kullanılan nesne.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwAddress`  
 [in] Bir uzak hedef makine IPv4 adresi.  
  
 `ppTarget`  
 [out] Bir işaretçi işaretçisi bir [Icoreclrdebugtarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) oluşturulacak nesne.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 İşlem CLRs sayısında başarıyla belirlendi ve karşılık gelen tanıtıcısı ve yol diziler düzgün doldurulmuş.  
  
 E_OUTOFMEMORY  
 Yeterli bellek ayrılamıyor `ppTarget`.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Diğer hatalar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Library:** mscordbi_macx86.dll  
  
 **.NET framework sürümleri:** 3.5 SP1
