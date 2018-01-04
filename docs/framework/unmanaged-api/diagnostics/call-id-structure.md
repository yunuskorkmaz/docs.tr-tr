---
title: "CALL_ID Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CALL_ID
api_location: diasymreader.dll
api_type: COM
f1_keywords: CALL_ID
helpviewer_keywords: CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71fd69cbcced1440839b9eedf8fbe3d8f5b90646
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="callid-structure"></a>CALL_ID Yapısı
Hata ayıklayıcı çağrıldığından işlevi hakkında bilgi sağlar. Bkz: [Inotifysink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) daha fazla bilgi için arabirim.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`szMachine`|Çağrıyı yapan makineyi tanımlar.|  
|`dwPid`|Makine işlemci tanımlar.|  
|`pUserThread`|Çağrı yürütme iş parçacığı tanımlar.|  
|`addrStackPointer`|Çağrı yığını adresini belirtir.|  
|`szEntryPoint`|Çağrı adresini belirtir.|  
|`szDestinationMachine`|Çağrı yürütecek makineyi tanımlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [INotifySink2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [Tanılama Simge Deposu Yapıları](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
