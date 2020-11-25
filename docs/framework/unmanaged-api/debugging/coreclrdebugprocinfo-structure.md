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
ms.openlocfilehash: 5996393fd1a0504f9c3d3f9f07aa0e3d886a0787
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719703"
---
# <a name="coreclrdebugprocinfo-structure"></a>CoreClrDebugProcInfo Yapısı

Uzak makinede çalışan bir işlemi temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
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

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Kitaplık:** mscordbi_macx86.dll  
  
 **.NET Framework sürümleri:** 3,5 SP1
