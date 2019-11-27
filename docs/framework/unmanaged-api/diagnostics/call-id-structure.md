---
title: CALL_ID Yapısı
ms.date: 03/30/2017
api_name:
- CALL_ID
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- CALL_ID
helpviewer_keywords:
- CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type:
- apiref
ms.openlocfilehash: 8c606f67766334800444f39b115d90f65ecca13d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448586"
---
# <a name="call_id-structure"></a>CALL_ID Yapısı
Çağrılmakta olan bir işlev hakkında bilgi bir hata ayıklayıcıyla ilgili bilgiler sağlar. Daha fazla bilgi için bkz. [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) arabirimi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
  
## <a name="members"></a>Üyeleri  
  
|Üyesi|Açıklama|  
|------------|-----------------|  
|`szMachine`|Çağrıyı yapan makineyi tanımlar.|  
|`dwPid`|Makine işlemcisini tanımlar.|  
|`pUserThread`|Çağrıyı yürüten iş parçacığını tanımlar.|  
|`addrStackPointer`|Çağrı yığınının adresini belirtir.|  
|`szEntryPoint`|Çağrının adresini belirtir.|  
|`szDestinationMachine`|Çağrıyı yürütecek makineyi tanımlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** ProtocolNotify2. IDL  
  
## <a name="see-also"></a>Ayrıca bkz.

- [INotifySink2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [Tanılama Simge Deposu Yapıları](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
