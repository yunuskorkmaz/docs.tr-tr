---
title: CoreClrDebugProcInfo Yapısı
ms.date: 03/30/2017
api_name:
- CoreClrDebugProcInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugProcInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreClrDebugProcInfo structure
- Silverlight, remote debugging
ms.assetid: 4ddc37da-5c94-4beb-b61c-b54071c0e749
topic_type:
- apiref
ms.openlocfilehash: e12882e53d1aa2120ab5c4b6793d7f2e34be76eb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132158"
---
# <a name="coreclrdebugprocinfo-structure"></a>CoreClrDebugProcInfo Yapısı
Uzak makinede çalışan bir işlemi temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`m_dwPID`|İşletim sistemi tarafından atanan işlem tanımlayıcısı.|  
|`m_dwInternalID`|Hedef makinede çalışan uzaktan hata ayıklama proxy 'si tarafından atanan işlem tanıtıcısı. Bu tanımlayıcı, işletim sistemi tanımlayıcısından daha az sıklıkta geri dönüştürür.|  
|`m_wszName`|İşlemin komut satırı. Bu üye kesilmiş olabilir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Kitaplık:** mscordbi_macx86. dll  
  
 **.NET Framework sürümleri:** 3,5 SP1
