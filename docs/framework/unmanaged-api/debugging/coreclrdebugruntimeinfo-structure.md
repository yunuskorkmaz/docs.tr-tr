---
title: CoreClrDebugRuntimeInfo Yapısı
ms.date: 03/30/2017
api_name:
- CoreClrDebugRuntimeInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugRuntimeInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreDebugRuntimeInfo structure
- Silverlight, remote debugging
ms.assetid: bd01c30f-b7a8-4179-9497-622b6599b1a6
topic_type:
- apiref
ms.openlocfilehash: 92a814d427fcf2e40c7f79e9eb9192e0b7eed4b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132137"
---
# <a name="coreclrdebugruntimeinfo-structure"></a>CoreClrDebugRuntimeInfo Yapısı
Uzak makinedeki bir işlemde yüklenen ortak dil çalışma zamanı (CLR) örneğini temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`m_dwInternalID`|Hedef makinede çalışan uzaktan hata ayıklama proxy 'si tarafından atanan çalışma zamanı tanımlayıcısı.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Kitaplık:** mscordbi_macx86. dll  
  
 **.NET Framework sürümleri:** 3,5 SP1
