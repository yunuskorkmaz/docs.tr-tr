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
ms.openlocfilehash: a7fed8cb70785f0ccfcadf1e16181db303ac98e0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789189"
---
# <a name="createcoreclrdebugtarget-function"></a>CreateCoreClrDebugTarget İşlevi
Uzak makinede çalışan bir hata ayıklayıcı Proxy 'sine bir bağlantı oluşturur ve çalışan işlemlerin ve uzak makinedeki yüklü [](icoreclrdebugtarget-interface.md) çalışma zamanlarının sorgulanmasıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwAddress`  
 'ndaki Uzak hedef makinenin IPv4 adresi.  
  
 `ppTarget`  
 dışı Oluşturulacak [ıreclrdebugtarget](icoreclrdebugtarget-interface.md) nesnesine yönelik işaretçinin işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 İşlemdeki CLRs sayısı başarıyla belirlendi ve karşılık gelen tanıtıcı ve yol dizileri doğru şekilde dolduruldu.  
  
 E_OUTOFMEMORY  
 `ppTarget`için yeterli bellek ayrılamıyor.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Diğer sorunlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Kitaplık:** mscordbi_macx86. dll  
  
 **.NET Framework sürümleri:** 3,5 SP1
