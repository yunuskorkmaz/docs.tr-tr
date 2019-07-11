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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2823c018ff22607052cb9a298f69dbd0c4fe2c23
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769503"
---
# <a name="callid-structure"></a>CALL_ID Yapısı
Bir hata ayıklayıcı çağrılan bir işlev hakkında bilgi sağlar. Bkz: [Inotifysink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) daha fazla bilgi için arabirim.  
  
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
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`szMachine`|Çağrıyı yapan makineyi tanımlar.|  
|`dwPid`|Makine işlemci tanımlar.|  
|`pUserThread`|Çağrıyı yürütmeden iş parçacığını tanımlar.|  
|`addrStackPointer`|Çağrı yığınının adresini belirtir.|  
|`szEntryPoint`|Çağrı adresini belirtir.|  
|`szDestinationMachine`|Çağrı yürütecek makineyi tanımlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Ayrıca bkz.

- [INotifySink2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [Tanılama Simge Deposu Yapıları](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
