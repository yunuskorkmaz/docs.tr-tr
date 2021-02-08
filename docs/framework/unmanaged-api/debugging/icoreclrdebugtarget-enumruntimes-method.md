---
description: 'Şu konuda daha fazla bilgi edinin: ıvreclrdebugtarget:: Enumbir yöntemi'
title: ICoreClrDebugTarget::EnumRuntimes Yöntemi
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumRuntimes
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumRuntimes
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget::EnumRuntimes method [Silverlight debugging]
- EnumRuntimes method, ICoreClrDebugTarget interface [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 316df866-442d-40cc-b049-45e8adcb65d1
topic_type:
- apiref
ms.openlocfilehash: 675747106b2acec2e8be3fcdf15831958bea7c7c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794630"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a>ICoreClrDebugTarget::EnumRuntimes Yöntemi

Uzak bir bilgisayarda çalışan belirtilen işlemdeki ortak dil çalışma zamanlarını (CLRs) numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a>Parametreler  

 `dwInternalProcessID`  
 'ndaki Çalışma zamanlarını numaralandırmak istediğiniz işlemin iç işlem KIMLIĞI. Bu `m_dwInternalID` , karşılık gelen [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md)olacaktır.  
  
 `pcRuntimes`  
 dışı İçinde döndürülen çalışma zamanlarının sayısı `ppRuntimes` . Bu değer 0 (sıfır) olabilir.  
  
 `ppRuntimes`  
 dışı Uzak hedef işlemde yüklü olan çalışma zamanlarını temsil eden [CoreCLR[gruntimeınfo](coreclrdebugruntimeinfo-structure.md) yapıtlarından oluşan bir dizi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 S_OK  
 Başarılı.  
  
 S_FALSE  
 `dwInternalProcessID` , büyük olasılıkla işlem sonlandırıldığı için, bilgisayar üzerinde çalışan herhangi bir işlemle eşleşmez. `pcRuntimes` ve `ppRuntimes` null olacaktır.  
  
 E_OUTOFMEMORY  
 İçin yeterli bellek ayrılamıyor `ppRuntimes` .  
  
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
