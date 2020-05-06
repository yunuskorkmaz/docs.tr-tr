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
ms.openlocfilehash: 40dbfc60f8bde1198fd56a4a8aeed1dd6879d1ae
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795631"
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
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Kitaplık:** mscordbi_macx86. dll  
  
 **.NET Framework sürümleri:** 3,5 SP1
