---
title: "StackTrace_SimpleContext Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackTrace_SimpleContext
api_location: diasymreader.dll
api_type: COM
f1_keywords: SimpleContext
helpviewer_keywords:
- SimpleContext structure [.NET Framework debugging]
- StackTrace_SimpleContext structure [.NET Framework debugging]
ms.assetid: d4cef11f-a8ca-49bc-a1b8-6631f9e28f3e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 756c1d4129aebedea46443613d286a51562a3896
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="stacktracesimplecontext-structure"></a>StackTrace_SimpleContext Yapısı
Tam yerine kullanılabilir basit bir bağlam sağlar `CONTEXT` yapısı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`StackOffset`|Yığın işaretçisi veya x86 enter yığın işaretçisi (ESP) platformlar.|  
|`FrameOffset`|Çerçeve uzaklık ya da x86 EBP kasayla platformlar.|  
|`InstructionOffset`|Yönerge işaretçisi veya x86 enter yönerge işaretçisi (EIP) platformlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yığın izleme işlevleri genellikle yalnızca adresini, çerçeve uzaklık ve yığın adresini döndürülecek gerektiğinden, isteğe bağlı olarak kullanabileceğiniz `SimpleContext` büyük yerine yapısı `CONTEXT` yapısı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** SOS_Stacktrace.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
